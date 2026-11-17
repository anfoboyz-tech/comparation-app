# Morning brief

Overnight research on the deal-finding app, 17 November 2026.

## Verdict

**Build it, but not as "search the whole internet". Build the fair-price check for second-hand listings.**

You share a listing from Facebook Marketplace, Gumtree or eBay. In about ten seconds the app shows what the item costs new today and where, a fair used range, the total cost including the drive, a buy / negotiate / skip verdict and an offer to make.

This is the 50–100 minutes of your fishing-rod evening. It does not replace the 20 minutes of browsing Marketplace, because nothing lawful can.

## Read this before trusting the detail

The research is a first pass, not a verified one. This session could not open web pages, and the search allowance ran out at about 20–30 queries per track. Nearly every external fact comes from a search-result summary; quotes and figures were not checked at the source. The conclusions below are the ones several tracks reached independently. The individual figures need checking, and the first phase of the methodology does that.

## What the research found

1. **The whole product has not been found anywhere. Its parts have.**
   - New-price comparison in Australia is free and crowded (Zyft, BuyWisely, Google). Little Birdie closed in September 2025 after A$30m from CBA.
   - Second-hand aggregators with funding are fashion-only and avoid Facebook Marketplace.
   - Small apps that rate used listings exist (Grabbit, YrdSale, Spottable and others). They are mostly US, aimed at resellers, and compare used against used.
   - None was seen to put the new price beside a used listing for general goods. That piece looks open.
2. **"Scan the entire internet" is not obtainable.**
   - Facebook Marketplace has no official route to its listings, Meta's terms ban automated collection, and Meta sues.
   - The lawful route is the user bringing the listing in. New prices and eBay listings are reachable through official routes.
3. **The technology is affordable.** About US$0.02–0.07 per check with a fixed pipeline, on estimates; nothing has been run yet.
4. **The money is the hard part.**
   - Private second-hand sales pay no commission. One estimate puts affiliate income at about A$0.06 per check.
   - Shopping apps keep about 3% of users after 30 days.
   - On current evidence this is a small real business, not an obvious venture-scale one.
5. **The literature has the same gap.** Nothing was found on how buyers judge a used price against new, or on total-cost comparison across new, used, shipped and local.
6. **The real competitors are general AI assistants and Meta.**
   - Nobody tested how well ChatGPT or Gemini judge a real Australian listing. That test takes an hour and should come before any code.
   - Meta already suggests prices to sellers; a buyer-facing price rating would be a short step.

## The research question

> For an Australian shopper looking at a specific second-hand listing, can a tool built only on lawfully obtainable data return, within ten seconds, the current new price, a fair used range and a buy / negotiate / skip verdict that is accurate enough to trust and that replaces most of the manual checking?

Eight measurable sub-questions with pass and stop thresholds are in `research/synthesis/research-question.md`.

## The methodology

| Phase | When | What | Decides |
|---|---|---|---|
| 0. Verify | Today | Check competitors and general assistants on real listings; test what the Facebook app shares; apply to eBay and affiliate networks | Proceed, change, or stop |
| 1. Coverage experiment | Days 1–2 | 30 real items in three categories: can current Australian new prices be found? | Data route and first category |
| 2. Pipeline, no interface | Days 3–7 | Build the check as a command-line tool; score it on 100–200 labelled listings against general assistants | Whether to build the app |
| 3. Thin app | Weeks 2–3 | iOS and Android: share a listing, get a verdict | — |
| 4. Field study | Weeks 3–6 | 30–50 real buyers: time saved, repeat use, whether they report what they paid, whether they pay | Launch, change, or stop |
| 5. Widen | Later | More categories; "cheapest way to own X" search over lawful sources; price alerts; public fair-price pages | — |

Full detail: `methodology/methodology.md`. System design: `methodology/pipeline.md`. Risks: `methodology/risk-register.md`.

## What would make it memorable

- **One action on the thing you are already looking at.** Carsales, Vivino and Yuka all attach a verdict to an item in front of you. None asks you to start a search.
- **Neutral.** "It's cheaper new at BCF this week" is the answer Facebook, eBay and Amazon are least likely to give.
- **Shows its working.** Sources, times and comparables on every verdict, and "not enough data" when that is true.
- **Gets better with use.** Every check adds a price observation, and the follow-up "what did you pay?" builds data nobody outside the platforms has. In time that supports a public price guide: the RedBook for everything that isn't a car.

That last point is the route to something defensible, and it is slow. In year one the advantage is thin.

## Decisions I need from you

1. **Accept the narrower product?** Fair-price check first, wider search later over lawful sources only. I recommend yes.
2. **Which category first?** One track says cameras and power tools on economics; another says fishing because you know it. I recommend testing reels with named models, power tools and cameras in the coverage experiment and choosing on the numbers.
3. **Affiliate links?** I recommend allowing them, labelled, with the verdict computed before any link is attached, and testing a paid tier early.
4. **Will you do the Phase 0 checks today?** They need a phone and about three hours. They are the cheapest way to find out whether to stop.
5. **Open network access for this project?** A request should be waiting for your approval. With it, I can run a second pass that reads the sources the first pass could only see in summary.

## Where everything is

| File | Contents |
|---|---|
| `research/synthesis/gap-analysis.md` | Has it been done, the gap, agreements, disagreements, research gaps and how to close them |
| `research/synthesis/literature-review.md` | What the academic and market evidence says |
| `research/synthesis/research-question.md` | The question, sub-questions, thresholds, hypotheses |
| `methodology/` | Methodology, pipeline, risk register |
| `research/findings/` | The eight raw track reports, with sources |
| `research/prompts/` | The research briefs, re-runnable |
