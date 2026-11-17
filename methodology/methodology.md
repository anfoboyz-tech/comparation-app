# Methodology

How to get from the research to a validated product, in stages, with a decision at the end of each. It answers the research question in `research/synthesis/research-question.md`.

## Product definition this methodology tests

**Share any second-hand listing; get the new price, a fair used range and a verdict in ten seconds.**

- The user finds a listing on Facebook Marketplace, Gumtree or eBay and shares it into the app (share sheet, pasted link or screenshot).
- The app identifies the item, finds the current best new price at Australian retailers, gathers comparable used prices, works out total cost including travel, and returns buy / negotiate / skip with the evidence shown and a suggested offer.
- A typed search ("Shimano Stradic 4000") runs the same pipeline without a listing.

The reasons for this shape, and for not building "search everything" first, are in `research/synthesis/gap-analysis.md`.

## Principles

1. **Lawful data only.** Official APIs, affiliate feeds, licensed search results, and what the user brings. No automated access to logged-in marketplaces.
2. **The model never produces a number.** Code computes every figure from retrieved evidence. The model reads, matches and explains.
3. **Show the working.** Every verdict displays the new price with its source and time, the comparables, and how sure the tool is.
4. **Decline when the data is thin.** "Not enough data to judge" is a valid output. Carsales and CarGurus both withhold ratings in that case.
5. **Every check leaves data behind.** Item, price, condition, suburb and date are stored. Seller names, faces and profile links are not.
6. **The verdict ignores commission.** It is computed before any retailer link is attached, and links that earn money are labelled.
7. **Measure before building more.** Each phase ends with numbers against the thresholds in the research question.

## Phases

### Phase 0 — Verify and decide (day 1, mostly the founder with a phone)

The overnight research could not open web pages. These checks close the gaps a build decision depends on.

| Check | Method | Outcome that changes the plan |
|---|---|---|
| Existing Australian app | Search the App Store and Play Store for "used price checker", "is it a good deal", "compare second hand prices", "marketplace search all" | A funded local app doing this |
| Nearest competitors on Australian listings | Install Grabbit, YrdSale, Spottable, Underpriced; five real listings each | Any of them shows Australian new prices and a sound verdict |
| General-assistant baseline | Twenty real listings as screenshots to ChatGPT, Gemini and Meta AI; record the new price and verdict each gives | An assistant is already good enough (sub-question 4) |
| Share-sheet payload | Share a Marketplace and a Gumtree listing from the phone apps to Notes on iPhone and Android; record what arrives | Decides link versus screenshot as the main entry |
| Meta price rating | Look for any buyer-facing price rating on a non-vehicle Marketplace listing | It exists in Australia |

Start in parallel, because they take days to weeks:

- Apply to the eBay developer programme and eBay Partner Network. Email eBay with a mock-up asking whether a separate eBay section beside other sources, and a verdict that uses eBay asking prices, are permitted.
- Open publisher accounts on Commission Factory, Impact, Rakuten and Partnerize. Record which target retailers have feeds and at what rate.
- Book a short consultation with an Australian technology lawyer on the points flagged in `research/findings/03-data-access-and-legal.md`.

**Decision at the end of Phase 0:** proceed, change category, or stop.

### Phase 1 — Coverage experiment (days 1–2, no app code)

Answers sub-question 1 and decides the retrieval design.

- **Sample:** 30 real items, 10 each from fishing reels with named models, power tools, and cameras and lenses. Include the founder's rod and reel as a known hard case.
- **Ground truth:** for each item, record by hand the best current Australian new price and where it is.
- **Routes compared:** a shopping-search API; model web search restricted to Australian retailers; eBay's Browse API; affiliate feeds if any are approved by then.
- **Measures:** share of items where each route finds the best price within 2%; latency; cost per lookup; which retailers are missing.

**Decision:** which route or combination to build on, and which category goes first.

### Phase 2 — Pipeline as a command-line tool (days 3–7)

Answers sub-questions 2, 3 and 4. Build the pipeline in `methodology/pipeline.md` without an interface.

- **Golden set:** 100–200 real listings in the chosen categories, collected as screenshots, each labelled by someone who knows the category with the correct item, match tier, new price on the day, a reasonable used range and a verdict.
- **Measures:** match-tier accuracy; new-price accuracy; verdict agreement; count of untraceable figures; cost and latency per check from real usage logs.
- **Baseline:** the same listings through general assistants, scored identically.
- **Regression rule:** the golden set is re-run on every prompt or model change.

**Decision:** build the app only if the tool beats the baseline and passes sub-questions 2 and 3 in at least one category.

### Phase 3 — Thin app (weeks 2–3)

One flow: share or paste a listing, watch progress, read the verdict card, tap through to the new price or message the seller with the suggested offer. Typed search as a second entry. After a few days the app asks "Did you buy it? For how much?"

- iOS through TestFlight and Android through internal testing.
- Recommended stack from Track 5: Expo with TypeScript, Supabase, a durable job runner, small model for extraction and matching, stronger model for the explanation.
- Not in this version: searching marketplaces, accounts beyond anonymous sign-in, alerts, barcode scanning, more than the chosen categories.

### Phase 4 — Field study (weeks 3–6)

Answers sub-questions 5–8.

- **Participants:** 30–50 people who buy second-hand in the chosen categories, recruited from hobby groups and forums.
- **Timed comparison:** each participant decides on two listings, one with the tool and one without; record time and confidence.
- **Instrumented use:** checks per user, second check within 14 days, taps on retailer links, response to the outcome prompt.
- **Willingness to pay:** offer a paid tier with a real price to half the participants after their third check.
- **Interviews:** ten short calls on what they trusted, what they ignored and what was missing.

**Decision:** launch publicly in the category, change the offer, or stop.

### Phase 5 — Widen, only on evidence

Each step is taken when the previous one has the numbers to support it.

1. **More categories**, chosen by measured coverage and match accuracy.
2. **Cheapest way to own X:** a search across the sources with official routes (retailers, eBay, refurbished sellers) ranked by total cost. This is the founder's search vision for everything except Marketplace and Gumtree.
3. **Watch a price:** alerts on new-price drops and on eBay listings for a saved item.
4. **Public fair-price pages** per model, built from accumulated checks, so search engines and assistants cite the product.
5. **Marketplace and Gumtree coverage** through a licence or partnership if one becomes available.

## Evaluation summary

| Phase | Sub-questions | Main measure | Who does it |
|---|---|---|---|
| 0 | 4 (first look) | Competitor and assistant checks | Founder |
| 1 | 1 | New-price coverage on 30 items | Founder and coding agent |
| 2 | 2, 3, 4 | Golden-set accuracy against baseline | Coding agent, founder labels |
| 3 | — | Working app | Coding agent |
| 4 | 5, 6, 7, 8 | Time saved, repeat use, outcomes reported, payment | Founder with testers |

## What this methodology does not establish

- Market size for the paid product. A 50-person study shows whether the behaviour exists, not how many people share it.
- Long-run accuracy of fair-value ranges. Those improve only as observed prices and outcomes accumulate.
- Legal clearance. The lawyer consultation and eBay's written answer are inputs, not something the experiments can supply.
