# Morning brief

Research on the deal-finding app, 17 November 2026. Two passes: an overnight first pass from search summaries, then a second pass that read the key sources directly.

## Verdict

**Don't build the app yet. Spend one week testing whether anyone wants it and whether existing tools already do it, then decide.**

The second pass made the case weaker, not stronger:

- **It has been built.** Two small tools already show a new retail price beside a verdict on a used listing, and about a dozen rate used listings some other way. None has found users.
- **The pain in your story is not the pain in the forums.** Buyers asking "is this fair?" already knew the new price. They wanted a fair used value and a view on whether the saving was worth losing the warranty.
- **Lawful data is thinner than it looked.** eBay's production API is for approved partners, few of the target retailers offer affiliate feeds, and Marketplace cannot be searched at all.

If the week's tests go well, the version worth building is a fair-price check: you bring a second-hand listing and get a fair used range, the new price at Australian retailers, the total cost including the drive, a warning if the price is suspiciously low, and a buy / negotiate / skip verdict. "Search the whole internet" is not buildable lawfully.

## How far to trust this

- **First pass:** eight research tracks that could not open web pages. Their claims came from search-result summaries.
- **Second pass:** four agents read the decision-critical sources directly, including eBay's licence, Amazon's and Gumtree's terms, Commission Factory's directory, app store listings, OzBargain threads, the scam reports and paper abstracts.
- **Still unread:** Reddit, Whirlpool, eBay's developer site and several product sites refused automated requests.
- **Never run:** no tool was installed, and no assistant was tested on a real listing.

## What the research found

1. **Has it been done? Yes, repeatedly, and badly.**
   - Deal Scout (Chrome extension) gives buy / caution / avoid on a Marketplace or eBay listing with the new retail price and where to buy new. It has 36 users and does not mention Australia.
   - PriceSnap (web and Android) rates a pasted listing and lists retail offers. It lists an Australian-dollar market and has over 1,000 downloads.
   - Spottable is a Sydney company that scores Marketplace listings against other asking prices. It has six Australian App Store ratings.
   - Grabbit shows US$30 of lifetime verified revenue.
   - New-price comparison is free and crowded: Zyft claims 700,000 users, and Little Birdie closed after A$30m of funding.
2. **What is still open.** No tool found uses Australian retailer prices, accepts Gumtree listings, pairs a phone share flow with a new price, or includes travel cost. That is a thin opening: a better-executed local version of something nobody has made stick.
3. **Demand is the main doubt.**
   - In twelve OzBargain threads, people got free answers within the hour, mostly "just buy new" or "ignore it".
   - Low-star reviews of Marketplace and Gumtree complain about scammers, suspensions and search. Price guidance did not come up.
   - No public demand was found in fishing communities.
   - Nothing measures how common the pain is or whether anyone would pay.
4. **General assistants are beatable on prices today.** Which? found in October 2026 that ChatGPT gave the correct lowest price and retailer for 8 of 25 products. Google's own pages confirm Gemini shopping in Australia. Meta's buyer price insights are a vehicle-only test.
5. **The thing buyers want is the hardest part.** A fair used value needs sale prices nobody outside the platforms has. Xianyu's published system, using its own platform's listings, lands within 20% of the asking price 54.6% of the time.
6. **Data access.**
   - Facebook Marketplace: no lawful automated route. The user brings the listing.
   - Gumtree: terms from 12 October 2026 ban copying "by any means (manual or automated)", which may reach even a user-shared listing. Needs a lawyer.
   - eBay: approved partners only. Its data must be under six hours old and cannot be stored or used to train anything, so it cannot build a price history.
   - Amazon Australia: needs 10 sales in 30 days and approval for mobile apps, and bars price tracking and alerts.
   - Retailers: Commission Factory lists BCF, Anaconda, Supercheap Auto, CameraPro and Camera House. Bunnings, Total Tools, Sydney Tools, Tackle World and others were not found there.
   - In practice the new-price lookup would depend on buying search results from a vendor, which is legally grey, or on model web search, which is slower and costlier.
7. **Money.**
   - Estimated cost per check is about US$0.02–0.05; nothing has been run.
   - Estimated affiliate revenue per check is A$0.014 in the low case and A$0.06 in the base case.
   - Fishing is better than first reported: BCF pays 2% to content sites, not a flat 0.5%, which gives about A$0.056 per check. Amazon Australia pays 5% on sports and cameras and 10% on tools.
   - A$1m a year on affiliate alone needs about 460,000 monthly users. This is a small business at best on current evidence.
8. **A real opening on safety.** Buying-and-selling scams drew 44,553 Scamwatch reports and A$25.5m in losses in 2025. In one thread the warning sign was a price far too low, so a "suspiciously cheap" flag answers a question buyers get wrong.

## The research question

> For an Australian shopper looking at a specific second-hand listing, can a tool built only on lawfully obtainable data return, within ten seconds, the current new price, a fair used range and a buy / negotiate / skip verdict that is accurate enough to trust, that beats asking a general AI assistant, and that people come back to?

Nine measurable sub-questions with pass and stop thresholds are in `research/synthesis/research-question.md`.

## The methodology

| Phase | Length | What | Decides |
|---|---|---|---|
| 0. Verify and test demand | Week 1 | Run a manual "send me a listing" service in hobby groups; try Deal Scout, PriceSnap, Spottable and PriceVet on real listings; score general assistants on the same listings; apply to eBay and affiliate networks; see a lawyer | Proceed, change, or stop |
| 1. Coverage experiment | 2–3 days | 60 real items in three categories: can current Australian new prices be found, by what route, at what cost? | Data route and the two best categories |
| 2. Pipeline, no interface | About 2 weeks | Build the check as a command-line tool; score it on about 100 labelled listings against assistants and existing tools | Whether to build a user-facing version, and in which category |
| 3. First user-facing version | 2–3 weeks | Bring a listing, get a verdict | — |
| 4. Field study | 3–4 weeks | 30–50 real buyers: time saved, repeat use, whether they report what they paid, whether they pay | Launch, change, or stop |
| 5. Widen | Later | Alerts; more categories; search over lawful sources; public fair-price pages | — |

Full detail: `methodology/methodology.md`. System design: `methodology/pipeline.md`. Risks: `methodology/risk-register.md`.

## Decisions I need from you

1. **Test before building?** I recommend running Phase 0 this week instead of starting the app today. It needs a phone and one to two days of effort, and it is where this is most likely to stop.
2. **If you want to build today anyway,** the useful thing to build is the Phase 1 coverage experiment, not an app. It answers whether Australian new prices can be retrieved at all.
3. **Which category?** Fishing is now competitive on economics, and you know it. I recommend reels with named models, power tools and cameras in Phase 1, chosen on coverage and economics together.
4. **Web first or app first?** I recommend a web version for the field study, because it can take real payments and be shared as a link, then the app once repeat use is shown.
5. **Affiliate links?** Contested between the research tracks. I recommend allowing them, labelled, with the verdict computed before any link is attached.

## Where everything is

| File | Contents |
|---|---|
| `research/synthesis/gap-analysis.md` | Has it been done, the gap, what the second pass changed, research gaps and how to close them |
| `research/synthesis/literature-review.md` | What the academic and market evidence says |
| `research/synthesis/research-question.md` | The question, sub-questions, thresholds, hypotheses |
| `methodology/` | Methodology, pipeline, risk register |
| `research/findings/` | The eight first-pass reports |
| `research/findings/second-pass/` | The four verification reports |
| `research/prompts/` | The research briefs, re-runnable |
