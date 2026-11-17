# Gap analysis

Synthesis of the eight research tracks in `research/findings/`. Date: 2026-11-17.

## How much weight this can carry

Every track ran under two limits: the session could not open web pages, and the shared search allowance ran out after roughly 20–30 queries per track. Almost every external fact below comes from a search-result summary, not a page that was read. The tracks label each claim (searched, background knowledge, inference); this synthesis keeps the claims that several tracks agree on and flags the ones a decision should not rest on until checked.

Treat this as a well-founded first pass. The verification list is in `methodology/methodology.md`, Phase 0.

## Second pass: what changed after reading the sources

Network access was opened and four agents re-checked the decision-critical claims at the source. Their reports are in `research/findings/second-pass/`. Reddit, Whirlpool, eBay's developer site and several product sites refused automated requests, so some items stay unverified. The sections below have been updated; the main changes are:

| First-pass claim | What the sources show |
|---|---|
| No product shows the new price beside a used-listing verdict for general goods | Two do: Deal Scout (Chrome extension, 36 users, no mention of Australia) and PriceSnap (web and Android, lists an Australian-dollar market, 1,000+ downloads). Neither was run on a real Australian listing. |
| The verdict tools are US-based | Spottable is a Sydney company and supports Australia; PriceVet is "built for NZ & AU buyers". Both compare against used prices, not new retail. |
| People spend a long time finding the new price | In twelve OzBargain threads, people asking "is this fair?" already knew the new price. They lacked a fair used value and a view on whether the saving justified no warranty. Free answers came within the hour. |
| Shopping scams cost about A$260m | That was all Scamwatch scams for nine months. Shopping scams were A$10.8m in 2025; the wider buying-and-selling type was A$25.5m across 44,553 reports. |
| BCF pays 0.5% | 0.5% for coupon sites, 2% for content sites, 3% for cashback sites, 0% on clearance. Fishing could earn about A$0.056 per check, close to the base case. |
| eBay's API is open | Production use is for approved eBay partners only, by application with a mock-up review. eBay data must be under six hours old, deleted when no longer needed, and not used to train algorithms, so it cannot go into a stored price history. |
| Affiliate feeds cover most big retailers | Commission Factory lists BCF, Anaconda, Supercheap Auto, CameraPro and Camera House of those checked. Bunnings, Total Tools, Sydney Tools, Tackle World, JB Hi-Fi, Ted's, Kogan, Officeworks and others are not listed there. BCF's page mentions no product feed. |
| Amazon's API needs sales first | Confirmed (10 sales in 30 days), and its terms bar price tracking and price alerts, require approval for mobile apps, and limit caching to 24 hours. |
| The user sharing a Gumtree listing is safe | Gumtree's terms (12 October 2026) ban copying "by any means (manual or automated)" and use to build a competing service. Needs a lawyer. |
| Nothing in the literature on new-versus-used choice or used-to-new price ratios | Both are studied (books, video games, remanufactured goods, resale as a share of retail). What is still not found: decision support for a specific used listing, fair ratios by category and condition on classifieds, and a single total-cost figure. |
| Matching used listings to products is unstudied | eBay, Mercari and Xianyu have published on it. No public benchmark, but it is less of a barrier to others than claimed. |

Two findings bear on how hard the core is. Xianyu's published price-suggestion system, with the platform's own 90 days of listings, lands within 20% of the seller's asking price 54.6% of the time, and 17.4% without comparables. And Which? found in October 2026 that ChatGPT gave the correct lowest price and retailer for 8 of 25 products.

## 1. Has it been done?

The whole product has not been found working for Australia. Each of its parts has, and two small tools combine most of them.

| Part of the vision | Who already does it | State |
|---|---|---|
| Compare new prices across Australian retailers | Zyft, BuyWisely, PriceHipster, Google Shopping, Gemini with Australian retailers | Free and crowded. Little Birdie closed in September 2025 after A$30m from CBA. |
| Ask an assistant for the best new price | ChatGPT, Gemini, Perplexity. About 61% of Australian online shoppers use AI tools at least sometimes, half of those to compare prices (IAB Australia, May 2026) | Being absorbed by general assistants. |
| Search several second-hand sites at once | Phia, Beni, Gem, Encore (fashion, US); Faircado (Europe); Bountye (Australia, 2015, faded) | Funded players are fashion-only and avoid Facebook Marketplace. |
| Monitor Facebook Marketplace and Gumtree in Australia | Swoopa (Melbourne), Classifindr | Alert tools for resellers. No comparison, no verdict. Appear to rely on automated access the platforms prohibit. |
| Rate a used listing as a good or bad deal | Carsales and CarGurus (vehicles); Grabbit, YrdSale, Spottable, Underpriced, DealRater and others (general goods, 2025–26) | Proven for vehicles. The general-goods tools are tiny, mostly US, aimed at resellers, and compare used against used. |
| Show the new price beside a used listing and say which is the better buy | Deal Scout and PriceSnap (general goods); Phia (fashion); Booko (books, Australia) | Exists, with almost no users. None found using Australian retailer prices, accepting Gumtree listings, pairing a phone share flow with a new price, or including travel cost. A search summary suggests BuyWisely may show a used eBay price beside new prices; its site refused requests, so check by hand. |

## 2. The gap

**No product found does this well for Australia: for a specific second-hand listing, a fair used price grounded in Australian data, the new price at Australian retailers, the total cost, and whether the saving is worth giving up a warranty.** The idea itself has been built several times in the last two years, and none of the builders has found users.

The forum evidence shifts the centre of the problem. Buyers usually know the new price already. What they lack is the fair used value, and that is the part with the least data behind it.

The gap is narrower than the founder's pitch and closer to the founder's story. The 20 minutes on Marketplace found the rod. The 50–100 minutes went on deciding whether the price was fair. Tracks 1, 2, 4 and 7 reached this without being asked about it; Track 7 found it is the question people actually post in forums: "I found this, is the price fair?" Tracks 3, 5 and 8 were asked to assess a listing-check option among others and favoured it.

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
| The new-price anchor beside the used listing is the uncontested piece | 1, 2, 8 | Overturned in the second pass: two small tools do it, and forum posters already know the new price. What is uncontested is doing it with Australian retailer prices and a sound used value |
| Per-check cost is small but not negligible: about US$0.02–0.07 with a fixed pipeline, on a retrieval route that is legally grey | 5 | Medium (estimates, nothing was run) |
| Revenue per check is the commercial obstacle: A$0.014 (low case, and fishing at BCF's rate), A$0.06 (base), A$0.36 (cameras) on affiliate alone. The recommended design at about US$0.05 costs more than the base case earns | 6 | Low (every input but BCF's rate is an assumption) |
| Demand is unmeasured: the pain is visible in forums, but nothing shows how common it is or that anyone would pay | 4, 7, 8 | Medium |
| A verdict alone is not defensible; the durable assets are observed prices, reported outcomes and a published accuracy record | 5, 8 | Medium (inference) |
| Trust depends on showing the comparables, not just the verdict: 3% of shoppers would buy on an AI recommendation alone | 7 | Medium (survey details unseen) |
| Scam and legitimacy concern is better quantified than price pain: buying-and-selling scams drew 44,553 Scamwatch reports and A$25.5m in losses in 2025, and one survey says 36% have met scams on second-hand marketplaces (source site was down, unverified). Track 7 ranks "is this listing legitimate?" as the second job and says it belongs beside the price check | 7 | Low–medium (an insurer's article, date unseen) |

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
| eBay does not approve the app, or its licence blocks the use | Confirmed at source: production access is for approved partners; a separate eBay section is the licence's own example of acceptable display; the price-modelling clause covers items listed on eBay; data cannot be stored beyond need or used to train algorithms | eBay's answer to the partner application |
| Gumtree's terms catch even user-shared listings | Terms of 12 October 2026 ban copying "by any means (manual or automated)" and use to build a competing service | A lawyer's reading |

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
