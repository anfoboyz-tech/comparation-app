# Morning brief

Overnight research on the deal-finding app, 17 November 2026.

## Verdict

**Don't build "search the whole internet". The version worth testing is a fair-price check for second-hand listings, and it should be tested for a week before any app code is written.**

In that version you bring a listing from Facebook Marketplace, Gumtree or eBay. In about ten seconds it shows what the item costs new today and where, a fair used range, the total cost including the drive, a buy / negotiate / skip verdict and an offer to make.

This targets the 50–100 minutes of your fishing-rod evening. It does not replace the 20 minutes of browsing Marketplace, because nothing lawful can.

No research track called this a clear win. The strongest wording any gave was "a reasonable small bet, not an obviously defensible business". Two things could stop it this week, and both are cheap to check: whether a general AI assistant already does it well enough, and whether anyone besides you wants it.

## Read this before trusting the detail

The research is a first pass, not a verified one. This session could not open web pages, and the search allowance ran out at about 20–30 queries per track. Nearly every external fact comes from a search-result summary; quotes and figures were not checked at the source. An independent review then checked this brief against the raw reports, and its corrections are included.

## What the research found

1. **The whole product was not found anywhere. Its parts were.**
   - New-price comparison in Australia is free and crowded (Zyft, BuyWisely, Google). Little Birdie closed in September 2025 after A$30m from CBA.
   - Second-hand aggregators with funding are fashion-only and avoid Facebook Marketplace.
   - At least nine small apps rate used listings (Grabbit, YrdSale, Spottable and others). They are mostly US, aimed at resellers, and compare used against used. None has visibly won users, which is either an opening or a warning.
   - None was seen to put the new price beside a used listing for general goods. That piece looks open. Australian app stores were not searched, so a recent local app cannot be ruled out.
2. **Demand is unproven.**
   - People do post "is this listing a fair price?" in forums, so the pain exists.
   - Nothing was found measuring how common it is or showing anyone would pay.
   - The academic evidence is that most shoppers check little and decide early, so most may not spend your 100 minutes.
3. **General AI assistants are the incumbent, and nobody tested them.**
   - About 61% of Australian online shoppers use AI tools at least sometimes, and half of those use them to compare prices.
   - For new goods, a free assistant already does a rough version of your retailer check in a minute or two.
   - Assistants are weaker on local second-hand listings today, but one track expects that advantage to last only 12–24 months.
   - Meta is testing price information for buyers on vehicle listings and already suggests prices to sellers.
4. **"Scan the entire internet" is not obtainable.**
   - Facebook Marketplace has no official route to its listings, Meta's terms ban automated collection, and Meta sues. The lawful route is the user bringing the listing in.
   - How to get current Australian new prices lawfully is not yet confirmed. Affiliate product feeds are the main lawful source, but which retailers offer them (BCF included) was not verified. The cheap route the cost estimates assume buys Google results from a vendor, which is legally grey.
   - eBay has an official API, but its licence, as quoted in search results, bars combining eBay data with other sources and using it to "suggest or model prices". That needs eBay's written answer before the design relies on it.
5. **Cost and revenue are close, and the gap may be negative.**
   - Estimated cost per check: about US$0.05 for the recommended design, about US$0.02 for a cheaper variant. Nothing has been run.
   - Estimated affiliate revenue per check: A$0.014 in the low case, A$0.06 in the base case, A$0.36 for a high-value category like cameras. For fishing gear at BCF's reported 0.5% commission it is A$0.014.
   - So the recommended design costs more than it earns in the base case, and fishing loses money on commission alone. Every revenue input except BCF's rate is an assumption.
   - Private second-hand sales pay no commission. Paid advertising for installs does not pay back at these numbers, and shopping apps keep about 3% of users after 30 days.
   - On current evidence this is a small real business at best, not a venture-scale one.
6. **The literature has the same gap.** Nothing was found on how buyers judge a used price against new, or on total-cost comparison across new, used, shipped and local.

## The research question

> For an Australian shopper looking at a specific second-hand listing, can a tool built only on lawfully obtainable data return, within ten seconds, the current new price, a fair used range and a buy / negotiate / skip verdict that is accurate enough to trust, that beats asking a general AI assistant, and that people come back to?

Nine measurable sub-questions with pass and stop thresholds are in `research/synthesis/research-question.md`.

## The methodology

| Phase | Length | What | Decides |
|---|---|---|---|
| 0. Verify and test demand | Week 1 | Score general assistants on real listings; run a manual "send me a listing" service in hobby groups; check competitors; apply to eBay and affiliate networks | Proceed, change, or stop |
| 1. Coverage experiment | 2–3 days | 60 real items in three categories: can current Australian new prices be found, by what route, at what cost? | Data route and the two best categories |
| 2. Pipeline, no interface | About 2 weeks | Build the check as a command-line tool; score it on about 100 labelled listings against general assistants | Whether to build a user-facing version, and in which category |
| 3. First user-facing version | 2–3 weeks | Bring a listing, get a verdict | — |
| 4. Field study | 3–4 weeks | 30–50 real buyers: time saved, repeat use, whether they report what they paid, whether they pay | Launch, change, or stop |
| 5. Widen | Later | Alerts; more categories; "cheapest way to own X" search over lawful sources; public fair-price pages | — |

Full detail: `methodology/methodology.md`. System design: `methodology/pipeline.md`. Risks: `methodology/risk-register.md`.

## What could make it memorable

- **One action on the thing you are already looking at.** Carsales, Vivino and Yuka all attach a verdict to an item in front of you. None asks you to start a search.
- **Neutral.** "It's cheaper new at BCF this week" is the answer Facebook, eBay and Amazon are least likely to give.
- **Shows its working.** Sources, times and comparables on every verdict, and "not enough data" when that is true.
- **Gets better with use.** Every check adds a price observation, and the follow-up "what did you pay?" builds data nobody outside the platforms has. In time that could support a public price guide: the RedBook for everything that isn't a car.

That last point is the only route found to something defensible, and it is slow. In year one the advantage is thin.

## Decisions I need from you

1. **Accept the narrower product?** Fair-price check first, wider search later over lawful sources only. I recommend yes.
2. **Will you run the Phase 0 tests this week before we build?** They need a phone and one to two days of effort. I recommend yes; they are the cheapest way to find out whether to stop.
3. **Which category first?** On economics, cameras and power tools score best and fishing worst. You know fishing. I recommend testing reels with named models, power tools and cameras in Phase 1 and choosing on coverage and economics together.
4. **Web first or app first?** The business track recommends a web version first, because it can take real payments and be shared as a link, then a thin app built around the share sheet. You asked for an app. I recommend the web version for the field study and the app once repeat use is shown.
5. **Affiliate links?** This is contested. Two tracks advise against earning from the items being judged; one plans on it. I recommend allowing them, labelled, with the verdict computed before any link is attached, and testing a paid tier early.
6. **Open network access for this project?** My request to set this up was rejected by the service, so it needs doing by hand: in the session's title bar open the cloud environment menu, choose Edit, and under Network access either pick a broader level or add the research sites as allowed domains (steps: https://code.claude.com/docs/en/cloud-environments#network-access). With that, and a fresh search allowance, I can run a second pass that reads the sources the first pass saw only in summary.

## Where everything is

| File | Contents |
|---|---|
| `research/synthesis/gap-analysis.md` | Has it been done, the gap, agreements, disagreements, research gaps and how to close them |
| `research/synthesis/literature-review.md` | What the academic and market evidence says |
| `research/synthesis/research-question.md` | The question, sub-questions, thresholds, hypotheses |
| `methodology/` | Methodology, pipeline, risk register |
| `research/findings/` | The eight raw track reports, with sources |
| `research/prompts/` | The research briefs, re-runnable |
