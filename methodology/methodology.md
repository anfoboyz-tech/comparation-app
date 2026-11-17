# Methodology

How to get from the research to a validated product, in stages, with a decision at the end of each. It answers the research question in `research/synthesis/research-question.md`, where the pass and stop thresholds are defined.

## Product definition this methodology tests

**Share any second-hand listing; get the new price, a fair used range and a verdict in ten seconds.**

- The user finds a listing on Facebook Marketplace, Gumtree or eBay and brings it to the product (screenshot, share sheet or pasted link).
- The product identifies the item, finds the current best new price at Australian retailers, estimates a fair used range, works out total cost including travel, and returns buy / negotiate / skip with the evidence shown and a suggested offer.
- The forum evidence says buyers usually know the new price already. What they ask for is the fair used value and whether the saving is worth giving up a warranty, so those two answers are the centre of the product, with a warning when a price is suspiciously low.
- A typed search ("Shimano Stradic 4000") runs the same pipeline without a listing.

The reasons for this shape, and for not building "search everything" first, are in `research/synthesis/gap-analysis.md`.

## Principles

1. **Lawful data only in production.** Official APIs the app is approved for, affiliate feeds, and what the user brings. No automated access to logged-in marketplaces. Search-results vendors are a grey route: acceptable for experiments, and a production dependency only if nothing better exists and a lawyer has looked at it.
2. **The model never produces a number.** Code computes every figure from retrieved evidence. The model reads, matches and explains.
3. **Show the working.** Every verdict displays the new price with its source and time, the comparables, and how sure the tool is.
4. **Decline when the data is thin.** "Not enough data to judge" is a valid output. Carsales and CarGurus both withhold ratings in that case.
5. **A price far below the range is a warning, not a bargain.** The tool flags it as a risk to check and never calls a listing safe.
6. **Every check leaves data behind.** Item, price, condition, suburb and date are stored. Seller names, faces and profile links are not, and users' screenshots are discarded after extraction.
7. **The verdict ignores commission.** It is computed before any retailer link is attached, and links that earn money are labelled.
8. **Measure before building more.** Each phase ends with numbers against the thresholds.

## Phases

### Phase 0 — Verify, and test demand (week 1; mostly the founder with a phone)

The overnight research could not open web pages and did not measure demand. These checks decide whether to build at all. Allow one to two full days of effort spread over the week, not a morning.

| Check | Method | Stop if |
|---|---|---|
| General-assistant baseline | Ten to twenty real Australian listings as screenshots to ChatGPT, Gemini and Meta AI. For each, hand-check the best new price (cap it at 15 minutes per listing) and write your own verdict first. Score each assistant on new price within 5% and verdict the same as yours | The best assistant scores 70% or more on both |
| Demand | Offer a manual service for one week in at least five Australian hobby groups: "send me a second-hand listing and I'll tell you if the price is fair". Answer by hand | Fewer than 5 people use it |
| Existing Australian app | Search the App Store and Play Store for "used price checker", "is it a good deal", "compare second hand prices", "marketplace search all" | A funded local app does this |
| Nearest competitors on Australian listings | Run five real Australian listings each through Deal Scout, PriceSnap, Spottable and PriceVet, which are the closest found. Check by hand whether BuyWisely shows used prices beside new | One gives Australian new prices and a sound verdict |
| Meta price rating | Look for any buyer-facing price rating on a non-vehicle Marketplace listing | It exists in Australia |
| Share-sheet payload | Share a Marketplace and a Gumtree listing from the phone apps to Notes on iPhone and Android; record what arrives | Does not stop anything; decides link versus screenshot as the main entry |

The manual service doubles as the first labelled data: every listing answered by hand is a golden-set case.

Start in parallel, because they take days to weeks:

- Apply to the eBay Partner Network for production access to the Buy APIs, which eBay reserves for approved partners and reviews against a mock-up. Ask in the application whether eBay asking prices, shown in a separate eBay section, may inform a fair-price range for a listing on another site, and whether sold-price access is available.
- Open publisher accounts on Commission Factory, Impact, Rakuten and Partnerize. Record which target retailers have product feeds, at what commission, and whether they accept comparison publishers. Of the retailers checked so far, Commission Factory lists BCF, Anaconda, Supercheap Auto, CameraPro and Camera House; the big tool retailers and Bunnings were not found there.
- Ask the lawyer specifically about Gumtree's terms, which ban copying "by any means (manual or automated)", and whether a user sharing their own screenshot is caught.
- Book a short consultation with an Australian technology lawyer on the points flagged in `research/findings/03-data-access-and-legal.md`.

**Decision at the end of Phase 0:** proceed, change the offer, or stop.

### Phase 1 — Coverage experiment (2–3 days, no app code)

Answers sub-question 1 and narrows the category.

- **Sample:** 60 real items, 20 each from fishing reels with named models, power tools, and cameras and lenses. Include the founder's rod and reel as a known hard case. With 20 per category, pass and stop differ by four items, which is enough to see a clear result and not enough to see a fine one.
- **Ground truth:** for each item, record by hand the best current Australian new price and where it is.
- **Routes compared:** a search-results vendor; model web search restricted to named Australian retailers; eBay's Browse API; affiliate feeds for any retailer approved by then (probably none this early).
- **Measures per route:** share of items with the best price found within 2%; time per lookup; cost per lookup in Australian dollars; which retailers are missing; and whether the route is official, grey or unknown.
- **Economics per category, recorded alongside:** typical order value; commission rate at the main retailers, from the affiliate accounts; how often listings name a model.

**Decision rule:** a category goes forward if at least one route finds 80% of prices, and its expected revenue per check is not below its cost. If only the grey route works, that is recorded as an open risk, not a pass. The two best categories go to Phase 2.

### Phase 2 — Pipeline without an interface (about 2 weeks)

Answers sub-questions 2, 3 and 4. Build the pipeline in `methodology/pipeline.md` as a command-line tool.

- **Golden set:** about 100 real listings across the two categories, collected by the founder as screenshots with seller details cropped out, plus the Phase 0 cases. Each is labelled with the correct item, match tier, hand-checked new price, a reasonable used range and a verdict. A second person labels 20 of them, and the disagreement rate is reported.
- **Measures:** match-tier accuracy; new-price accuracy; verdict agreement; count of untraceable figures; measured cost in Australian dollars and time per check.
- **Baseline:** the same listings through general assistants, scored identically.
- **Regression rule:** the golden set is re-run on every prompt or model change.
- **eBay gate:** the design must work without eBay data until eBay has approved the app. Even then, eBay data must be under six hours old and cannot be stored in the price history or used to train anything, so it can inform a live answer only. Without eBay, the fair range rests on the new price and a percent-of-new table by category and condition. That table is hand-built from the Phase 0 and golden-set cases and is labelled as an assumption wherever it is shown.

**Decision:** build a user-facing version only if the tool beats the assistant baseline by the margin in sub-question 4 and passes sub-questions 2 and 3 in at least one category. That category becomes the first.

### Phase 3 — First user-facing version (2–3 weeks)

One flow: bring a listing, watch progress, read the verdict card, tap through to the new price or message the seller with the suggested offer. A few days later it asks "Did you buy it? For how much?"

**Open decision: web first or app first.** The business track recommends a web version first, then a thin app, because shopping apps keep about 3% of users at day 30, store fees apply to subscriptions, and a web page can take real payments and be shared in a link. The idea brief asks for an App Store and Play Store app, and the share sheet is only available to an installed app. A workable order is a web version for the field study (upload a screenshot or paste a link), then the thin app once repeat use is shown. The founder decides.

- Recommended stack from the architecture track: TypeScript throughout, Supabase, a durable job runner, small model for extraction and matching, stronger model for the explanation; Expo for the app.
- Not in this version: searching marketplaces, accounts beyond anonymous sign-in, alerts, barcode scanning, more than the first category.

### Phase 4 — Field study (3–4 weeks)

Answers sub-questions 5–8. With 30–50 people this shows direction, not precise rates.

- **Participants:** 30–50 people who buy second-hand in the first category, recruited from the groups used in Phase 0.
- **Timed comparison:** each participant decides on three listings: one with the tool, one with a general assistant, one unaided. Record time and confidence.
- **Instrumented use:** checks per user, second check within 14 days, taps on retailer links, response to the outcome prompt, time to answer.
- **Willingness to pay:** a paid tier with a real price and real payment, offered to everyone after their second check. This needs the web version or a public store build; test builds do not take real money.
- **Interviews:** ten short calls on what they trusted, what they ignored and what was missing.

**Decision:** launch publicly in the category, change the offer, or stop. Sub-question 6 is the main gate: fewer than one in three returning within a fortnight means the product is a feature, not a destination.

### Phase 5 — Widen, only on evidence

Each step is taken when the previous one has the numbers to support it.

1. **Saved items and price-drop alerts**, as the reason to return. Amazon's API terms bar price tracking and alerts, so these cannot use Amazon data.
2. **More categories**, chosen by measured coverage, match accuracy and economics.
3. **Cheapest way to own X:** a search across the sources with official routes (retailers, eBay, refurbished sellers) ranked by total cost. This is the founder's search vision for everything except Marketplace and Gumtree.
4. **Public fair-price pages** per model, built from accumulated checks, so search engines and assistants cite the product.
5. **Marketplace and Gumtree coverage** through a licence or partnership if one becomes available.

## Evaluation summary

| Phase | Sub-questions | Main measure | Who does it |
|---|---|---|---|
| 0 | 0, 4 (stop criterion only) | Demand for a manual service; assistant baseline | Founder |
| 1 | 1 | New-price coverage and economics on 60 items | Founder and coding agent |
| 2 | 2, 3, 4 | Golden-set accuracy against baseline | Coding agent; founder and a second labeller |
| 3 | — | Working product | Coding agent |
| 4 | 5, 6, 7, 8 | Time saved, repeat use, outcomes reported, payment | Founder with testers |

## What this methodology does not establish

- **Market size.** A 50-person study shows whether the behaviour exists, not how many people share it.
- **True accuracy of verdicts.** Without sold prices, "correct" means agreement with hand research.
- **Long-run accuracy of fair-value ranges.** Those improve only as observed prices and outcomes accumulate.
- **Legal clearance.** The lawyer consultation and eBay's written answer are inputs, not something the experiments can supply.
