# Track 5 — Technical architecture and per-search cost

Research date: 2026-11-17. All prices in USD unless marked.

**Read this first: how much of this was verified tonight.** This session's network allowlist blocked direct page fetches for almost every site (OpenAI, Google, eBay, SerpApi, DataForSEO, Apify, Expo docs, arXiv all failed DNS), and the shared web-search budget ran out after about 20 queries. So each claim below carries one of three labels:

- **[V]** verified tonight at a primary source I could read in full (Anthropic pricing page, npm registry, Expo and expo-share-intent source on GitHub).
- **[S]** seen tonight only as a search-result summary of the cited page. The number is probably right but I did not read the page myself.
- **[K]** from my own background knowledge, not looked up tonight. Treat as a lead to confirm, not a fact.

Latency figures and token counts are my engineering estimates, not measurements. Nothing was built or run.

---

## 1. Bottom line

1. **Per-search cost is not the problem.** A deterministic pipeline (API connectors plus small-model extraction plus one mid-tier verdict call) comes to roughly **$0.02–$0.07 per search**. An LLM agent that searches the web itself comes to roughly **$0.09–$0.45**, and takes 30–90 seconds instead of 5–10. Arithmetic is in section 2.7.
2. **A web search costs about one US cent whoever sells it to you.** Anthropic's web search tool is $10 per 1,000 searches [V], OpenAI's is reported at $10 per 1,000 [S], Gemini grounding at $14 per 1,000 [S], SerpApi at $9–$25 per 1,000 depending on plan [S]. Retrieval calls, not model tokens, dominate the cheap design's cost now that Claude Haiku 5.5 is $0.10 / $0.50 per million tokens [V].
3. **The hard problem is data access to used listings, not AI.** Facebook Marketplace has no official listings API [S], and eBay's sold-price API (Marketplace Insights) is restricted to approved partners [S]. The founder's own use case started on Marketplace, which is the one source the app cannot cleanly search.
4. **This points to a different first product than "search everything".** The buildable version is: the user finds a used listing themselves and shares it into the app; the app finds the new price and comparable listings, computes total cost, and returns a verdict. That removes Marketplace search from the critical path and directly attacks the 50–100 minutes the founder spent, rather than the 20.
5. **Fair used-value estimation will be weak at launch.** Without sold comparables, the estimate rests on asking prices, percent-of-new priors and thin data. It must be shown as a range with the evidence count, and for many items the honest output is "new costs $X; this is Y% of new; here are three other used asks", not a precise fair value.
6. **Matching errors are the main trust risk.** A verdict built on the wrong variant (wrong model year, rod only versus rod-and-reel combo) is confidently wrong. Published zero-shot LLM product matching sits around 0.9 F1 on clean retail data [S, unverified leaderboard figure]; noisy used listings will be worse. The design needs a "same / near / different" tier and must show the user what it matched.
7. **Stack recommendation:** Expo (React Native) with TypeScript end to end, Supabase for Postgres/auth, a durable job runner for searches, Claude Haiku 5.5 for extraction and matching, a stronger Claude model for the verdict. Expo SDK 58 has receiving shares from other apps built into `expo-sharing`, marked experimental [V].
8. **The first day of building should be a coverage spike, not app code.** Take 30 real Australian items and measure whether each candidate retrieval route actually returns BCF, Anaconda and similar retailers' current prices. I could not test this tonight and it decides the architecture.

---

## 2. Findings

### 2.1 Query understanding

Three input types, one output: a structured `ItemSpec` (category, brand, model, variant attributes, bundle contents, condition if a listing, price if a listing, confidence, and whether it resolved to an exact product or only a product class).

| Input | Approach | Cost per call | Latency (est.) | Notes |
|---|---|---|---|---|
| Free text ("fishing rod and reel combo around $200") | Small LLM with structured output | ~$0.0003 on Haiku 5.5 (1.5k in, 300 out) | 0.5–1 s | Usually resolves to a product class, not a product. Ask one clarifying question when the class is wide. |
| Pasted or shared listing link | Fetch page server-side, then LLM extraction | ~$0.001 | 1–3 s | Works for eBay and retailer pages. Marketplace links generally need a logged-in session [K], so expect the fetch to fail and fall back to screenshot. |
| Screenshot or photo of listing | Vision LLM extraction | ~$0.0005–$0.002 on Haiku 5.5 | 1–2 s | The reliable path for Marketplace. Reads title, price, description, location from the screenshot. |
| Photo of the item itself | Vision LLM, optionally eBay image search | similar | 1–3 s | Identifies brand and family well, exact model poorly unless a label is visible [K]. Defer. |
| Barcode / GTIN | Lookup API | varies | <1 s | Useful in-store for new goods. Rarely present on used listings. Defer. |

What works today: LLM extraction with a strict JSON schema is the practical default; it needs no training data and no product knowledge graph. A knowledge graph is something you accumulate from your own resolved queries, not something to build first.

Engineering notes for the Claude API [V, from the current API reference]: use `output_config.format` for structured output; forced `tool_choice` returns a 400 on Sonnet 5.5 and Opus 5.5; set `effort: "low"` on Haiku 5.5 for extraction (its default is `medium`); always check `stop_reason` for `refusal` before reading content.

### 2.2 Retrieval design

| Design | Latency (est.) | Cost per search | Coverage | Reliability | Legal exposure |
|---|---|---|---|---|---|
| **Live federated connectors** (official APIs and SERP/shopping APIs called at query time) | 3–8 s, parallel | $0.01–$0.03 retrieval | Good for eBay and whatever Google Shopping indexes; nothing for Marketplace | Depends on 2–3 vendors | Low for official APIs; medium for SERP vendors (see below) |
| **Pre-built index** (crawl or ingest feeds ahead of time) | <1 s | Near zero per query, high fixed cost | Only what you ingested; stale for one-off used listings | High once built | Depends entirely on how it was acquired; crawling retailers and marketplaces is where the exposure is |
| **LLM agent with web search tool** | 30–90 s | $0.09–$0.45 | Broadest for new retail; still cannot see logged-in marketplaces | Variable; different answers run to run | Lowest for you (the model vendor does the fetching), but no control over which sources are used |
| **Hybrid** (live connectors, cache results, grow an index from what users search) | 3–8 s cold, <1 s warm | $0.01–$0.03 cold | Grows with usage | Good | Same as live connectors |

Recommendation: **hybrid, starting as live connectors with a cache.** Deterministic connectors for sources with an API, with the LLM agent held back as a fallback for items the connectors cannot price (obscure specialty goods), where a slow answer beats none.

Source-by-source access, as far as I could establish:

| Source | Route | Status |
|---|---|---|
| eBay AU, active listings (new and used) | Browse API | Default 5,000 calls/day per application; higher after eBay's free Application Growth Check, which is not guaranteed [S]. Returns active items only [S]. |
| eBay sold prices | Marketplace Insights API | Limited release, approved partners only; forum reports of small developers being declined [S]. A petition claims access was narrowed further in February 2026 [S, weak source]. |
| New retail prices (BCF, Anaconda, Amazon AU, etc.) | Google Shopping results via a SERP API; or merchant/affiliate feeds; or LLM web search | SerpApi: $25/1,000, $75/5,000, $150/15,000, $275/30,000 searches per month [S]. DataForSEO Google Shopping from about $0.001–$0.002 per result page on the standard queue, which can take up to 45 minutes and so does not suit live search; live price not confirmed [S]. **AU retailer coverage untested.** |
| Facebook Marketplace | No official API [S]. Third-party scrapers on Apify list $0.10–$5.00 per 1,000 results; some require Facebook session cookies [S]. | Technically available, legally and operationally fragile. Track 3 should rule on this. Do not put it on the critical path. |
| Gumtree AU | Not researched tonight (budget ran out). I am not aware of a public listings API [K]. | Open. |
| Cash Converters and similar resale stores | Not researched tonight. | Open. |

On SERP vendors: Google sued SerpApi in the Northern District of California (No. 4:25-cv-10826-YGR). The DMCA claims were dismissed on 20 July 2026 on the ground that public search results are not Google's copyrighted work, and one report says the amended complaint was also dismissed; terms-of-service and contract theories were not resolved by that ruling [S]. Reddit has a separate suit against SerpApi and others [S]. Practical reading: SERP APIs are usable today, but treat any single vendor as replaceable and keep the connector behind an interface.

What current products appear to use [K, not checked tonight; tracks 1 and 2 should confirm]: Google Shopping is a pre-built index fed by merchant feeds; classic price-comparison sites are feed-and-crawl indexes; the 2025–26 assistant shopping features (ChatGPT, Perplexity, Google AI Mode) are agents over an index. One thing I did see tonight: Google's agentic checkout (Universal Commerce Protocol) went live in Australia around June 2026 with Bunnings, Kogan, THE ICONIC, Adore Beauty and Petbarn [S]. None of the results mentioned used goods.

Caching and freshness: cache new-retail prices per canonical product for 6–24 hours; cache used listings for minutes to an hour and always re-check the specific listing before a verdict; store every observation with a timestamp, because the accumulated price history becomes the index and later the fair-value data.

### 2.3 Product matching across sources

Practical pipeline:

1. **Candidate generation.** Run each connector with 2–3 query variants built from the `ItemSpec` (brand + model, brand + family + key attribute). Keyword search at the source does most of the blocking.
2. **Cheap filter.** Embedding similarity between spec and listing title, plus hard rules (brand must match; price within a sane band for the category). Embedding cost is negligible at this volume.
3. **LLM verification.** One batched small-model call over the surviving 30–60 candidates, returning for each: tier (`same` / `same-family-different-variant` / `substitute` / `different`), the attribute differences, and bundle contents. About $0.003 on Haiku 5.5 (16.5k in, 2.4k out).
4. **Photos only where they decide something**, for the top few used candidates.

Expected accuracy: a third-party leaderboard lists zero-shot GPT-4 at 89.6 F1 on the hard (80% corner-case) WDC Products benchmark, flagged there as unverified [S]. The underlying papers are Peeters, Der and Bizer's benchmark and their LLM entity-matching work [S]. That benchmark is clean retailer text. My inference for noisy used listings ("Shimano reel good cond"): often there is not enough information in the listing to resolve the exact model at all, so the right target is correct tiering, not exact-match F1. Confidence in that inference: medium.

Near-matches and substitutes: do not force them into match / no-match. Keep the tier, show it ("previous model year of the same rod"), and let the value model apply a discount for the difference. Bundles need explicit handling: decompose a rod-and-reel combo into components and price each, otherwise a combo compared against a rod-only new price produces a wrong verdict.

### 2.4 Used-condition normalisation and fair value

**Condition.** Map to a five-point scale (new/sealed, like new, good, fair, for parts) using the seller's stated condition where the platform gives one (eBay has structured condition [K]) and otherwise an LLM reading of text plus one or two photos. Photos catch visible damage and missing parts; they cannot show function. Store the grade with a confidence and the phrases that drove it. I found no evidence tonight on how accurate LLM condition grading is; plan to measure it on your own labelled set.

**Fair value with thin data.** In order of evidential strength:

| Evidence | Availability in AU today | Use |
|---|---|---|
| Sold comparables | eBay's API for this is restricted [S]. Not available at launch without a partner agreement or scraping. | Best signal; pursue eBay partner access early. |
| Active asking prices for the same or near item | eBay Browse API [S]; other marketplaces as access allows | Upper bound. Asks sit above sale prices; the size of that gap by category is something to measure, not assume. |
| Current best new price | SERP/shopping connector | Anchor. Percent-of-new is the most robust single number when comps are thin. |
| Category depreciation priors | You write these; refine from data | Fallback. Start with a small hand-built table for the launch categories and mark it as a prior. |
| Your own observation history | Accumulates with use | A listing that disappears quickly at a given price is weak evidence of a sale near that price. |
| LLM estimate with retrieved comps | Always available | Use the LLM to weigh and explain comps, never to produce a price from memory. |

**Expressing uncertainty.** Show a range, not a point, with the evidence behind it: "Fair used price $110–$150, based on 4 similar listings and a new price of $219." Use three plain confidence tiers tied to objective conditions (number of comps, match tier, age of data). When there are no comps, say so and fall back to percent-of-new with the prior labelled as an assumption. Do not show a range the data cannot support.

### 2.5 Total cost of acquisition

A defensible formula keeps every term visible and editable by the user:

```
TCA = price
    + shipping
    + travel_cost            (2 × road_km × cost_per_km, pickup only)
    + time_cost              (round-trip minutes × user's value of time, default 0)
    + risk_allowance         (peer-to-peer only: price × r, r set by category and testability)
    − protection_value       (warranty and return rights on new/retail; zero for private sales)
```

Compare `TCA_used` with `TCA_new_best × remaining_value_factor(condition, age)`.

Inputs and where they come from:

| Input | Source | Note |
|---|---|---|
| Price, shipping | Listing or connector | Shipping is often missing on used listings; ask or estimate by size class. |
| Distance and drive time | Suburb or postcode centroids with straight-line distance × a detour factor for v1; a routing API later | Google Route Matrix Essentials is reported at $5 per 1,000 elements [S], so five pickup candidates is 5 elements = $0.025, which would be a large share of the per-search cost. Use it only for the final one or two candidates, or not at all in v1. Free-tier cap not confirmed. |
| Cost per km | User setting | The ATO business rate (88c/km in recent years [K, confirm current]) is a full-cost figure; marginal fuel cost is a fraction of it. Default to a marginal figure and let the user change it. |
| Value of time | User setting, default zero | Showing minutes separately is more honest than pricing them by default. |
| Risk allowance `r` | Category table | Higher for electronics and anything untestable at pickup, lower for simple mechanical goods. This is a judgement parameter; label it. |
| Protection value | Retailer warranty and returns | Consumer guarantees apply to purchases from businesses and largely do not cover private sales [K; track 3 to confirm]. A simple default is a percentage of new price by category. |

The risk and protection parameters are assumptions, not measurements. The defensible position is to expose them ("we allowed 10% for no warranty") rather than hide them inside a score.

### 2.6 Verdict generation

Rule: **the model never produces a number.** Code computes every figure; the model chooses among them and explains.

1. Build an evidence pack in code: each observation has an id, source, URL, price, timestamp, match tier. Computed fields (best new TCA, fair range, percent-of-new, suggested offer) are added with ids too.
2. Compute the verdict class deterministically from thresholds on `TCA_used` versus the fair range and the new anchor: buy / negotiate / wait / skip. "Wait" needs price history or a known sale pattern, so it will rarely fire at launch; do not fake it.
3. Compute the suggested offer in code (for example, the lower of the fair-range midpoint and a fixed discount on the ask, floored at the fair-range low).
4. Call the model with the pack and a schema: verdict (it may downgrade confidence but not override the class without citing a reason code), three reasons each referencing evidence ids, caveats.
5. Validate after generation: every dollar figure and percentage in the output text must equal a value in the pack. On failure, regenerate once, then fall back to a template. Note that the Claude API's citations feature cannot be combined with structured outputs (it returns a 400) [V], so evidence ids in the schema are the way to do this.

Evaluation:

- A golden set of 100–200 real cases, hand-labelled by someone who knows the category, starting with the founder's rod and reel. Labels: correct product, correct new price on the day, reasonable used range, verdict.
- Metrics: new-price accuracy (within 2% of the true best price), match-tier accuracy, verdict agreement with the labeller, and invented-number rate, which must be zero.
- Run the set on every prompt or model change. An LLM judge can help triage but should not be the measure of record.
- After launch: track whether users who got "negotiate" report the price they paid. That is also the start of a sold-price dataset.

### 2.7 Model and API costs

**Prices used**

| Item | Price | Status |
|---|---|---|
| Claude Haiku 5.5 (prompts up to 100k tokens) | $0.10 in / $0.50 out per MTok; cache read $0.01 | [V] |
| Claude Sonnet 5.5 | $2 in / $10 out per MTok; cache read $0.10; 5-min cache write $2.50 | [V] |
| Claude Opus 5.5 | $4 in / $20 out per MTok; cache read $0.20 | [V] |
| Claude Batch API | 50% off input and output | [V] |
| Claude web search tool | $10 per 1,000 searches, plus result tokens billed as input | [V] |
| Claude web fetch tool | No fee; fetched content billed as input tokens | [V] |
| OpenAI web search tool | $10 per 1,000 calls (reported cut from $25 in early 2026) | [S] |
| OpenAI GPT-5.4 mini / nano | $0.75 / $4.50 and $0.20 / $1.25 per MTok | [S] |
| OpenAI GPT-5.6 tiers | Sources conflict ($4–$5 in / $20–$30 out for the top tier; $0.20 / $1.20 for the smallest) | [S, unreliable] |
| Gemini grounding with Google Search (Gemini 3 and later) | $14 per 1,000 search queries after 5,000 free per month, billed per query not per prompt | [S] |
| Gemini Flash (3.6–3.8) | $0.75 / $3.75 per MTok introductory through 31 Dec 2026; third-party sources report token prices doubling on 1 Dec 2026 or 1 Jan 2027 | [S] |
| SerpApi | $25/1k, $75/5k, $150/15k, $275/30k searches per month | [S] |
| eBay Browse API | Free, 5,000 calls/day default | [S] |
| Apify Marketplace scrapers | $0.10–$5.00 per 1,000 results | [S] |
| Google Route Matrix Essentials | $5 per 1,000 elements | [S] |

I could not open OpenAI's or Google's own pricing pages, so the cost models below are built on Claude prices, which I verified. The OpenAI and Google figures suggest the same order of magnitude.

**Design A — LLM agent with web search (model does the retrieval)**

Assumptions: 8 searches; about 3k tokens of results each (24k); 3 page fetches capped at 5k tokens each (15k); 2k system and tool definitions; final context about 45k. Anthropic's page says search results count as input "in search iterations run during a single turn", so across about 6 model passes the cumulative billed input is somewhere between 45k (billed once) and about 150k (re-read each pass). Output plus thinking: 5k tokens.

| Component | Haiku 5.5 | Sonnet 5.5 | Opus 5.5 |
|---|---|---|---|
| Input, 45k–150k tokens | $0.0045–$0.015 | $0.09–$0.30 | $0.18–$0.60 |
| Output, 5k tokens | $0.0025 | $0.05 | $0.10 |
| Search fees, 8 × $0.01 | $0.08 | $0.08 | $0.08 |
| **Total per search** | **$0.09–$0.10** | **$0.22–$0.43** | **$0.36–$0.78** |

Latency estimate: 30–90 seconds. Cap spend with the tool's `max_uses`, restrict sources with `allowed_domains`, and localise with `user_location` [V, these parameters exist]. The newer web search variant with built-in result filtering is listed for Sonnet and Opus tiers but not Haiku [V], so the Haiku column probably understates its token use.

**Design B — deterministic connectors plus small models (recommended)**

| Step | Model / service | Tokens or calls | Cost |
|---|---|---|---|
| Parse query | Haiku 5.5 | 1.5k in, 0.3k out | 1,500 × $0.10/M + 300 × $0.50/M = $0.0003 |
| eBay active listings, new and used | Browse API | 2 calls | $0 |
| New retail prices | SerpApi shopping search | 1 call | $0.010 (15k plan) to $0.025 (1k plan); $0.015 used below |
| Match and tier 60 candidates | Haiku 5.5 | 16.5k in, 2.4k out | $0.00165 + $0.0012 = $0.003 |
| Condition from photos, top 5 used | Haiku 5.5 vision | ~15k in (10 images at an assumed 1.5k each), 1k out | $0.0015 + $0.0005 = $0.002 |
| Distance | Straight-line estimate | — | $0 |
| Verdict | Sonnet 5.5 | 6k in, 1.8k out including thinking | $0.012 + $0.018 = $0.030 |
| **Total** | | | **$0.050** |

Variants: verdict on Haiku 5.5 instead ($0.0015) gives **$0.022**. Verdict on Opus 5.5 ($0.024 + $0.036 = $0.060) gives **$0.080**. A second SERP call for per-product offers adds $0.015. Adding a Marketplace scraper for 30 results adds $0.003–$0.15 depending on the actor.

Latency estimate: connectors in parallel 2–5 s; matching 1–2 s; verdict streams from about 1 s after that. Show retailer prices as they arrive and the verdict last: first useful content at 2–4 s, complete at 6–10 s.

**Design C — shared-listing check (the suggested first product)**

| Step | Cost |
|---|---|
| Extract listing from screenshot or page (Haiku 5.5 vision, ~3k in, 0.4k out) | $0.0005 |
| New price lookup, 1 SERP call | $0.015 |
| Comparable used listings, eBay Browse | $0 |
| Match and tier ~30 candidates (Haiku 5.5) | $0.0015 |
| Verdict (Sonnet 5.5) | $0.030 |
| **Total** | **$0.047**, or about $0.02 with a Haiku verdict |

**What this means per user and per month**

- 15 searches a month per active user on Design B: 15 × $0.05 = **$0.75 per user per month**. On Design A with Sonnet: 15 × $0.22–$0.43 = **$3.30–$6.45**.
- 1,000 active users, 15,000 searches: Design B about $750 a month (SerpApi's $150 plan covers exactly 15,000 searches; the rest is model spend, mostly the verdict). Design A with Sonnet: $3,300–$6,450.
- Caching new-price lookups shared across users cuts the SERP line roughly in proportion to the hit rate.
- **Price alerts are where cost can run away.** Re-checking 5 watched items per user daily is 150 SERP calls per user per month, about $1.50–$2.25 on retrieval alone, more than all their interactive searches. Deduplicate watches by canonical product across users, re-check on a schedule that matches how often prices move, and run the model side through the Batch API at half price.
- Vendor prices are moving: Gemini token prices are reported to double within weeks [S]. Keep model and SERP vendors behind interfaces.

### 2.8 Mobile stack

| Option | Fit for a solo founder with an AI coding agent | Receiving a shared link | Verdict |
|---|---|---|---|
| **Expo / React Native** (Expo SDK 58.0.26, React Native 0.88.1, both current on npm today [V]) | One language (TypeScript) across app and backend; large body of examples; over-the-air updates through Expo's services [K] | Built into `expo-sharing` as of recent SDKs: a config plugin adds the iOS share extension and Android intent filter, and a `useIncomingShare` hook reads the payload. **Marked experimental**; on iOS the extension opens the main app rather than showing its own sheet, which the docs note is not an officially supported pattern [V]. Alternative: `expo-share-intent` 9.0 supports SDK 58, handles URLs and text, and needs a custom dev build, not Expo Go [V]. | **Recommended.** |
| Flutter | Mature and capable; Dart is a second language alongside a TypeScript backend | Community packages exist [K, not checked tonight] | Reasonable, no advantage here. |
| Native (Swift + Kotlin) | Two codebases | Full control of the share extension UI | Not for a small team at this stage. |

Share-sheet specifics:

- **Android:** an intent filter for `text/plain`; the shared URL arrives as text. Low risk [K].
- **iOS:** needs a share extension target and an App Group to pass data to the main app. Both Expo routes generate this [V]. Budget time for signing and provisioning and for App Store review of the extension.
- **The real risk is the payload, not the plumbing.** What the Facebook app puts on the share sheet, and whether that URL can be read without a login, must be tested on a real device on day one. Assume the link alone will not be enough and build the screenshot path at the same time.

Other pieces:

- **Push:** `expo-notifications` (current on npm [V]) over APNs and FCM.
- **Location:** `expo-location` (current on npm [V]). Ask for suburb or postcode first; request device location only in the foreground and only when the user wants pickup distance. Background location is not needed and makes review harder.
- **Backend:** Supabase (Postgres with pgvector, auth, storage) plus a durable job runner for searches, since a search is a multi-step job that outlives a serverless request. Inngest is one option with a current SDK [V]; Trigger.dev and Cloudflare Workflows are alternatives [K, pricing not checked]. Stream progress to the app over server-sent events or Supabase Realtime.
- **Keys stay server-side.** The app never calls a model or SERP API directly. Add per-user rate limits from day one; an unauthenticated search endpoint that costs five cents a call is an abuse target.

### 2.9 Build sequence

**Days 1–2: coverage spike, no app.**
Take 30 real Australian items across 3–4 categories (include the rod and reel). For each, record by hand the true best new price and where it is. Then measure, per retrieval route (SerpApi shopping, Claude web search restricted to AU retailers, eBay Browse), how often it finds that price. Also test on a phone what the Facebook and Gumtree apps actually share. This decides sections 2.2 and 2.8.

**Days 3–7: the pipeline as a command-line tool.**
`ItemSpec` extraction, two or three connectors, matching, TCA, deterministic verdict, model-written explanation, validator. Run it against the 30 items; this is the first version of the golden set.

**Weeks 2–3: the app, one flow.**
Share or paste a listing (link or screenshot) → progress screen → verdict card showing new price with source links, comparable used listings, fair range, total cost, suggested offer. Text search as a second entry point that runs the same pipeline. TestFlight and Play internal testing.

**Defer:** Marketplace and Gumtree search inside the app; price-drop alerts; item-photo identification; barcode scan; routing API; accounts beyond anonymous sign-in; the "wait" verdict; any pre-built index or crawler; more than three or four categories.

### 2.10 Hard problems, ranked

| # | Risk | Severity | Why | How to reduce it |
|---|---|---|---|---|
| 1 | Access to used-marketplace listings | Critical | No official Marketplace API [S]; login walls; scraping carries terms-of-service and account risk. The originating use case lives there. | Make the user the retriever (share / screenshot). Use eBay's official API for comps. Take track 3's ruling before touching scrapers. |
| 2 | No sold-price ground truth | High | eBay's sold-data API is restricted [S]. Fair value from asking prices is biased high. | Apply for eBay partner access now. Anchor on percent-of-new. Show ranges with evidence counts. Collect outcomes from users. |
| 3 | AU new-price coverage for specialty retailers | High | Untested whether shopping results include BCF and similar at current prices. | The day-1 spike. Fallbacks: retailer-restricted LLM web search; affiliate product feeds (not researched tonight). |
| 4 | Wrong-variant matches | High | A wrong match gives a confident wrong verdict; used listings often lack the detail to resolve. | Tiered matches shown to the user; bundle decomposition; lower verdict confidence when the tier is not `same`; golden-set regression. |
| 5 | Invented or stale numbers in verdicts | High | One fabricated price destroys trust. | Numbers computed in code; evidence ids; post-generation validator; timestamps on every price. |
| 6 | Dependence on SERP vendors | Medium | Litigation is ongoing on non-copyright theories [S]; pricing can change. | Connector interface; second vendor tested; cache. |
| 7 | Cost blow-outs | Medium | Alerts and agent fallbacks multiply calls; open endpoints invite abuse. | Per-user limits; dedupe watches; cap agent use with `max_uses`; Batch API for background work. |
| 8 | Latency | Medium | Over ~10 s feels broken on mobile. | Parallel connectors, streaming partial results, cache, small models for everything but the verdict. |
| 9 | iOS share extension and store review | Low–medium | Expo's receive-share support is experimental [V]. | Prototype in week 1; keep paste-link and screenshot as equal entry points. |

---

## 3. Implications for the product

- **Build the checker before the searcher.** "Share a listing, get a verdict" is feasible this month on official APIs and costs about five cents a use. "Search every marketplace" depends on data access that is not cleanly available.
- **The 50–100 minutes is the addressable part.** The founder spent 20 minutes finding the item on Marketplace and far longer establishing what it was worth. The app can replace the second part without needing access to the first.
- **Do not promise a precise fair price.** Lead with what can be stood behind: best new price with links, percent-of-new, comparable asks, total cost including travel. Add the fair-value range where the evidence supports it.
- **Avoid the agent-first architecture as the default path.** It is 5–10 times the cost, several times slower, and less repeatable. Keep it as a fallback for items the connectors miss.
- **Every search should leave data behind.** Timestamped price observations and user-reported outcomes are what eventually produce a fair-value model competitors cannot buy. Design the schema for that from the first day.
- **Start narrow.** Three or four categories where new prices are easy to find and models are identifiable (fishing and outdoor gear, power tools, a slice of electronics) make matching and priors tractable.

## 4. Open questions

| Question | How to settle it |
|---|---|
| Do shopping/SERP APIs return current BCF, Anaconda and similar AU retailer prices? | Day-1 spike on 30 items. |
| What does the Facebook app share on iOS and Android, and can the URL be read without login? | Test on two phones, 30 minutes. |
| Will eBay grant Marketplace Insights access, or a higher Browse limit, to a new AU app? | Apply through the developer programme this week. |
| Gumtree AU and resale-store data access. | Not researched tonight; check track 3's findings, then their terms and any partner programmes. |
| Are affiliate product feeds a usable source of AU new prices? | Check the AU affiliate networks' feed access; track 6 may cover it. |
| Current OpenAI and Google model prices from their own pages. | Open the official pricing pages; mine are from search summaries and third-party trackers that disagree with each other. |
| Real token counts and latency for each step. | Instrument the command-line pipeline; replace my estimates in 2.7. |
| How accurate is LLM condition grading and match tiering on used listings? | Label 100 listings; measure. |
| Gap between asking and sold prices by category. | Needs sold data or user-reported outcomes. |
| Whether Claude's server-side web search re-bills accumulated results on each pass within one turn. | Run one agent query and read `usage`. It moves Design A's cost by up to 3×. |
| Routing API free tier and whether straight-line distance is good enough. | Read Google's pricing page; compare against real drives for 20 suburb pairs. |

## 5. Sources

Read in full tonight:
- Anthropic pricing — https://platform.claude.com/docs/en/about-claude/pricing
- npm registry (versions and publish dates for expo, react-native, expo-sharing, expo-share-intent, expo-notifications, expo-location, @supabase/supabase-js, inngest, @anthropic-ai/sdk) — https://registry.npmjs.org/
- Expo `expo-sharing` documentation source — https://github.com/expo/expo/blob/main/docs/pages/versions/unversioned/sdk/sharing.mdx
- expo-share-intent README — https://github.com/achorein/expo-share-intent

Seen as search-result summaries only (page not opened):
- SerpApi pricing — https://serpapi.com/pricing ; https://serpapi.com/blog/breakdown-of-serpapis-subscriptions/
- DataForSEO Google Shopping API — https://dataforseo.com/google-shopping-api ; https://dataforseo.com/apis/serp-api/pricing
- eBay API call limits — https://developer.ebay.com/develop/get-started/api-call-limits
- eBay Marketplace Insights overview — https://www.developer.ebay.com/api-docs/buy/marketplace-insights/overview.html
- eBay community thread on Marketplace Insights access — https://community.ebay.com/t5/eBay-APIs-Talk-to-your-fellow/Marketplace-Insights-API-query-about-small-project/m-p/34874973
- Third-party note on eBay free tier (Oct 2026) — https://apiserpent.com/blog/free-ebay-api
- Petition on sold-API access (weak source) — https://www.change.org/p/grant-the-card-huddle-access-to-ebay-s-sold-api
- Apify Facebook Marketplace scrapers — https://apify.com/apify/facebook-marketplace-scraper/pricing ; https://apify.com/blackfalcondata/facebook-marketplace-scraper ; https://apify.com/futurafree/facebook-marketplace-0-10-1k-results-discord-alerts
- OpenAI pricing (official page not reachable; third-party trackers) — https://developers.openai.com/api/docs/pricing ; https://developer.puter.com/tutorials/openai-api-pricing/ ; https://spendlint.dev/pricing/openai-api ; https://www.tldl.io/resources/openai-api-pricing
- Gemini pricing and grounding (official page not reachable; third-party trackers) — https://ai.google.dev/gemini-api/docs/pricing ; https://cloud.google.com/vertex-ai/generative-ai/pricing ; https://www.morphllm.com/gemini-api-pricing ; https://fastero.com/blog/gemini-api-pricing ; https://justinmckelvey.com/blog/gemini-api-pricing
- Google Routes API billing — https://developers.google.com/maps/documentation/routes/usage-and-billing ; https://developers.google.com/maps/billing-and-pricing/pricing
- Google v. SerpApi — https://ppc.land/google-loses-dmca-bid-to-treat-search-scraping-like-dvd-piracy/ ; https://seroundtable.com/google-lawsuit-serpapi-dismissed-41731.html ; https://www.vondranlegal.com/federal-court-rejects-google-s-broad-dmca-anti-scraping-theory ; https://ppc.land/serpapi-faces-revived-google-scraping-claims-built-on-reddit-licensing-terms/
- Google UCP / agentic checkout in Australia — https://itbrief.com.au/story/google-unveils-open-ucp-standard-for-ai-driven-shopping ; https://au.pattern.com/blog/universal-cart-australia/ ; https://www.channelnews.com.au/google-taps-aussie-retailers-for-ai-shopping-checkout-launch/
- Product matching literature — https://arxiv.org/pdf/2409.08185 ; https://arxiv.org/pdf/2305.03423 ; https://hyper.ai/en/sota/tasks/entity-resolution/benchmark/entity-resolution-on-wdc-products-80-cc-seen

Not reachable from this session (DNS blocked by the session's network allowlist): ai.google.dev, platform.openai.com, developers.openai.com, serpapi.com, dataforseo.com, developer.ebay.com, docs.expo.dev, apify.com, developers.google.com, arxiv.org.
