# Gap analysis

Synthesis of the eight research tracks in `research/findings/`. Date: 2026-11-17.

## How much weight this can carry

Every track ran under two limits: the session could not open web pages, and the shared search allowance ran out after roughly 20–30 queries per track. Almost every external fact below comes from a search-result summary, not a page that was read. The tracks label each claim (searched, background knowledge, inference); this synthesis keeps the claims that several tracks agree on and flags the ones a decision should not rest on until checked.

Treat this as a well-founded first pass. The verification list is in `methodology/methodology.md`, Phase 0.

## 1. Has it been done?

The whole product has not been found. Each of its parts has.

| Part of the vision | Who already does it | State |
|---|---|---|
| Compare new prices across Australian retailers | Zyft, BuyWisely, PriceHipster, Google Shopping, Gemini with Australian retailers | Free and crowded. Little Birdie closed in September 2025 after A$30m from CBA. |
| Ask an assistant for the best new price | ChatGPT, Gemini, Perplexity. About 61% of Australian online shoppers use AI tools at least sometimes, half of those to compare prices (IAB Australia, May 2026) | Being absorbed by general assistants. |
| Search several second-hand sites at once | Phia, Beni, Gem, Encore (fashion, US); Faircado (Europe); Bountye (Australia, 2015, faded) | Funded players are fashion-only and avoid Facebook Marketplace. |
| Monitor Facebook Marketplace and Gumtree in Australia | Swoopa (Melbourne), Classifindr | Alert tools for resellers. No comparison, no verdict. Appear to rely on automated access the platforms prohibit. |
| Rate a used listing as a good or bad deal | Carsales and CarGurus (vehicles); Grabbit, YrdSale, Spottable, Underpriced, DealRater and others (general goods, 2025–26) | Proven for vehicles. The general-goods tools are tiny, mostly US, aimed at resellers, and compare used against used. |
| Show the new price beside a used listing and say which is the better buy | Phia (fashion, US); Booko (books, Australia) | Not found for general goods. Amazon Australia's used offers and refurbished sellers such as Back Market and Reebelo were not checked. |

## 2. The gap

**No product found tells an Australian buyer, for a specific second-hand listing of a general-goods item, what it costs new today, what a fair used price is, and whether to buy, negotiate or walk away.**

That is narrower than the founder's pitch and closer to the founder's story. The 20 minutes on Marketplace found the rod. The 50–100 minutes went on deciding whether the price was fair. Tracks 1, 2, 4 and 7 reached this without being asked about it; Track 7 found it is the question people actually post in forums: "I found this, is the price fair?" Tracks 3, 5 and 8 were asked to assess a listing-check option among others and favoured it.

Three things make the gap real, and the same three make it hard:

1. **Data access.** Facebook Marketplace and Gumtree have no official route to listing data. Funded companies avoid them; small tools scrape and stay small.
2. **Matching without a catalogue.** Verdicts work where items have clean identifiers (vehicles, phones). A listing titled "Shimano reel good cond" does not.
3. **Money.** A cash pickup pays no commission, and a buyer of one fishing rod has no profit motive to justify a subscription the way a reseller does.

The gap is structural, not undiscovered. A product that fills it has to route around all three.

## 3. What the tracks agree on

| Conclusion | Tracks | Confidence |
|---|---|---|
| Do not build a new-goods comparison engine | 1, 6, 8 | High |
| "Search everything, including Marketplace" cannot be delivered lawfully or reliably | 2, 3, 5, 8 | High on Marketplace; medium on Gumtree |
| The buildable product starts from a listing the user brings (screenshot, share sheet, pasted link) | 1, 2, 4, 7 unprompted; 3, 5, 8 when asked | High |
| The new-price anchor beside the used listing is the uncontested piece | 1, 2, 8 | Medium (app store searches in Australia were not run) |
| Per-check cost is small but not negligible: about US$0.02–0.07 with a fixed pipeline, on a retrieval route that is legally grey | 5 | Medium (estimates, nothing was run) |
| Revenue per check is the commercial obstacle: A$0.014 (low case, and fishing at BCF's rate), A$0.06 (base), A$0.36 (cameras) on affiliate alone. The recommended design at about US$0.05 costs more than the base case earns | 6 | Low (every input but BCF's rate is an assumption) |
| Demand is unmeasured: the pain is visible in forums, but nothing shows how common it is or that anyone would pay | 4, 7, 8 | Medium |
| A verdict alone is not defensible; the durable assets are observed prices, reported outcomes and a published accuracy record | 5, 8 | Medium (inference) |
| Trust depends on showing the comparables, not just the verdict: 3% of shoppers would buy on an AI recommendation alone | 7 | Medium (survey details unseen) |
| Scam and legitimacy concern is better quantified than price pain: 36% report encountering scams on second-hand marketplaces. Track 7 ranks "is this listing legitimate?" as the second job and says it belongs beside the price check | 7 | Low–medium (an insurer's article, date unseen) |

## 4. Where the tracks disagree

**Which category first.** Track 6 scores cameras and lenses, then power tools, highest on economics, and scores fishing lowest (BCF reportedly pays 0.5%; rod-and-reel combos are hard to match). Track 8 says start with fishing because the founder knows it. Both are judgement, not measurement. Resolution: Phase 1 covers reels with named models, power tools and cameras side by side and records coverage together with order value and commission rate. The two best go to Phase 2, where match accuracy is measured, and the first category is chosen after that.

**Affiliate revenue.** Track 6 plans on commission from the start. Track 8 says not to earn from the items being judged, citing Honey's collapse in trust, and Track 7 says to avoid revenue that depends on the recommendation or disclose it per result. Resolution proposed in the methodology: the verdict is computed in code before any link is attached, links are disclosed, ranking never depends on commission, and the paid tier is tested early so the business does not depend on steering people to buy new.

**Standalone app.** The idea brief wants an App Store and Play Store app. Track 6 recommends web first, then a thin app built around the share sheet, and counts day-30 retention near 3% and store fees against building a full app first. This is unresolved and is a founder decision. A workable order is a web version for the field study, then the thin app once repeat use is shown.

## 5. Threats that could close the gap

| Threat | Evidence | What to watch |
|---|---|---|
| Meta adds a fair-price badge for buyers on general listings | Meta already suggests prices to sellers (March 2026) and has been testing price information for buyers on vehicle listings (November 2025). Its Muse agent (US, September 2026) reportedly watches Marketplace for an item | A buyer-facing rating on non-vehicle listings in any market |
| General assistants give a good-enough verdict from a screenshot | Not tested by any track. For new goods an assistant already does a rough version of the retailer check in a minute or two. One reviewer got ChatGPT's agent to log in to Marketplace and compile listings, slowly. Track 8 expects the Australian-knowledge advantage to last 12–24 months | The Phase 0 baseline test on real Australian listings, before building |
| A small verdict tool adds new prices and Australian coverage | Nine or more exist; the parts are cheap | Whether Grabbit, YrdSale, Spottable or Swoopa work on Australian listings today |
| eBay's API licence forbids the intended use | Search results quoting the agreement: no combining with non-eBay content, no use "to suggest or model prices" | The agreement text, and a written answer from eBay |

What the platforms are unlikely to offer is a neutral cross-platform answer such as "cheaper new at BCF this week". That is the position this product can hold.

## 6. Research gaps and how to close them

| Gap | Why it matters | How to close it | Effort |
|---|---|---|---|
| Is there already an Australian app doing this? | The gap claim depends on it | Search the Australian App Store and Play Store for the phrases in Track 2, open question 1 | 30 min |
| Do existing verdict tools work on Australian listings? | They are the nearest competitors | Install Grabbit, YrdSale, Spottable, Underpriced and Swoopa; test with five real listings each | 1–2 hours |
| How good are general assistants at this today? | If good enough, do not build | Ten to twenty real listings, screenshot to ChatGPT, Gemini and Meta AI, scored against hand research | Half a day to a day |
| Does anyone besides the founder want this? | Demand is unmeasured | A one-week manual "send me a listing" service in hobby groups | A week, an hour a day |
| Can current Australian retail prices be retrieved reliably and lawfully, including BCF and Anaconda? | The whole product rests on the new-price anchor | Coverage experiment on 60 items across three categories | 2–3 days |
| What does the Facebook app hand over through the share sheet? | Decides link versus screenshot as the main entry | Test on an iPhone and an Android phone | 30 min |
| What does eBay's licence actually permit? | eBay is the only official source of used comparables | Read the agreement; email eBay with a mock-up; lawyer | Days to weeks, start now |
| Which Australian retailers offer affiliate feeds, at what rates? | Revenue and a lawful price source | Open publisher accounts on Commission Factory, Impact, Rakuten, Partnerize | 2 hours plus approvals |
| How common is the pain, and will anyone pay? | Track 7 found the pain but not its size | Prototype with real users; measure repeat use and willingness to pay | 2–4 weeks |
| Will users report what they paid? | The only route to data others lack | Follow-up prompt in the prototype; measure response rate | With the prototype |
| How large is the gap between asking and sold prices? | Fair-value ranges built on asking prices run high | Needs eBay sold data or reported outcomes | Ongoing |
