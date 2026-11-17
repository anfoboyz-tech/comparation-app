# Brief

Research on the deal-finding app, 17 November 2026, after three passes.

## Where this has landed

**The product worth testing is a sourcing agent, not a price checker: you tell it what you need, it does the searching and the asking, and it comes back with one ranked answer.** The first market to test is car parts, from the drive-shaft example.

No product found, in Australia or overseas, does that whole job. But the simple version of it for car parts already exists four times in Australia, so the first step is to find out whether those services already solve the problem.

## How the idea changed over three passes

| Pass | Question | Answer |
|---|---|---|
| 1 | Can an app scan the whole internet for the best new or used deal? | No. Facebook Marketplace cannot be searched lawfully, and new-price comparison is free and crowded. A fair-price check on a listing you bring looked like the buildable part. |
| 2 | Does that fair-price check hold up when the sources are read? | Weakly. It has been built about a dozen times and none has found users. Buyers in forums already know the new price. |
| 3 | Does your own permission make marketplace search feasible, and should the product do the legwork instead? | Permission helps on a desktop, not in a phone app. Doing the legwork is the real gap. |

## Does giving the app permission make it feasible?

Partly.

- **What permission fixes.** An agent running on your own device, in your own logged-in browser, at your direction, is legally different from a company scraping from its servers. A US appeals court said in August 2026 that in that setup the user is the one accessing the site.
- **What it does not fix.** Meta, Gumtree and eBay each forbid automated access by their own users. The same US ruling left terms-of-service claims standing, and it is not Australian law. You risk your account; the app's maker risks a legal letter and removal from the stores.
- **Desktop works, phone does not.** Browser extensions and browser agents such as Claude in Chrome already search Marketplace in the user's session, all at small scale. A phone app would need your Facebook password typed into it, cannot run in the background on an iPhone, and runs against Apple's and Google's store rules.
- **Where that leaves it.** Marketplace search can be an optional desktop companion for people who already run a browser agent. It cannot be the foundation of a phone app. The app's reach has to come from official sources and from asking suppliers directly, which no platform's terms restrict.

## The gap

**No product takes a specific need, makes the enquiries itself across listed stock, request networks, marketplaces and suppliers who have to be asked, and returns one ranked answer across new, used, refurbished and wrecked.**

The evidence behind it:

- **A verdict is not the job.** Thirteen tools grade a listing you already found; six have no Australian App Store ratings. The usual complaint is "I can do this myself, free".
- **Collecting answers from many suppliers is the job.** CarEdge reports 163,096 AI negotiation sessions with US car dealers since July 2025. A UK service that sends parts requests to breakers has about 26,000 Trustpilot reviews.
- **Nobody in Australia makes the enquiries for you.** The AI calling products are US-only. Locally there are only request boards that suppliers opt into.
- **Much of the supply is offline.** eBay says about 80% of recycled-parts sales happen offline.

## What already exists in car parts

Four Australian services send one request to many wreckers, free to buyers:

- **Findapart**, since 2000.
- **Hollander Parts**, since 2018, claiming over a million parts of live stock.
- **PartsClub**, with 100+ wreckers and quotes "usually within 1 hour".
- **WrecKonnect**, since 2025, for mechanics.

None was tested. If they work well, your four hours were a problem of not knowing they existed. What they do not do is cover each other plus eBay, new-part prices and phone-only yards in one request, ask the fitment questions up front, or chase suppliers who do not reply.

## The limits

- **"Five minutes" is your time, not the clock.** Listed stock can be searched in minutes. Suppliers who have to be asked answer in hours; CarEdge's dealers average 18.4 hours and 35% never reply.
- **Consumers need a car part rarely.** The repeat buyer is the mechanic, and trade tools already aim there.
- **The law on AI enquiries needs a lawyer.** An enquiry to buy looks lawful on a first reading. Promoting the app to the supplier in the same message does not; one company paid A$75,600 for texting businesses from public directories.
- **Bigger players can follow.** Google's AI already phones US businesses for prices and began with auto shops.
- **Money is better than before but unproven.** A completed parts purchase might support about A$10, against about A$0.06 per check for the fair-price product. That is one track's rough arithmetic.

## The research question

> For an Australian who needs a specific item sold through fragmented, partly offline supply, starting with a car part, can an agent using only lawful routes cut hours of searching and phoning to under five minutes of the user's own time, and return within a working day a ranked, fitment-checked set of options at least as good as the user would have found alone?

Nine measurable sub-questions with pass and stop thresholds are in `research/synthesis/research-question.md`.

## The pipeline

1. You state the need.
2. The agent asks the fitment questions a wrecker would ask.
3. It plans which sources to try.
4. It searches listed stock, lodges requests with the existing networks, and sends enquiries to yards that have to be asked.
5. It reads and matches the replies.
6. It chases suppliers who have not answered, once.
7. It works out total cost for each option and checks it against the new price.
8. It gives a first answer in minutes and updates it as replies arrive.
9. You pick; it drafts the message or call notes.
10. It records what you bought and which suppliers answered.

Full detail: `methodology/pipeline.md`.

## The methodology

| Phase | Length | What | Decides |
|---|---|---|---|
| 0. Is it already solved? | Week 1 | Put 20 real part requests through the four existing locators; search eBay and phone yards for the same parts; trial Claude in Chrome on your own account; talk to five mechanics; see a lawyer | Build, change market, or stop |
| 1. Do it by hand | Weeks 2–3 | Fulfil 20–30 real requests manually, following the pipeline as a checklist | Which stages to automate; consumers or mechanics |
| 2. Agent, no app | Weeks 3–6 | Build the pipeline as a tool you operate; score it against the by-hand results | Whether to build a user-facing version |
| 3. First user-facing version | 2–3 weeks | State the need, get a ranked answer | — |
| 4. Field study | 4 weeks | 30–50 users including mechanics: time saved, repeat use, payment | Launch, narrow, change category, or stop |
| 5. Widen | Later | Truck and machinery parts, tyres, appliance spares, building materials; "find it for me" for second-hand hobby goods | — |

Full detail: `methodology/methodology.md`. Risks: `methodology/risk-register.md`.

## How far to trust this

- Three passes, twenty research reports. The second and third read sources directly where the sites allowed it.
- Reddit, Whirlpool, Trustpilot, Product Hunt and the telecoms regulator's site refused automated requests or could not be read.
- Nothing was installed or run. No locator, verdict tool, browser agent or assistant was tested on a real request. Product behaviour is from vendors' own descriptions.
- The legal points are research, not advice.

## Decisions I need from you

1. **Run the Phase 0 tests this week?** Putting your drive shaft and 19 other requests through the four locators is the single most useful thing to do next, and only you can do it. I recommend yes.
2. **Car parts as the first market?** I recommend testing it first, because the pain is clear and the supply is offline. It is medium confidence, and Phase 0 could overturn it.
3. **Consumers or mechanics?** Leave open until Phase 1 shows who comes back.
4. **Marketplace through your own browser agent?** I recommend treating it as an optional desktop extra after a lawyer's view, and keeping it out of the phone app.
5. **Web first or app first?** Still yours to decide. Requests that take hours favour a phone app for notifications; a web version is quicker to test.

## Where everything is

| File | Contents |
|---|---|
| `research/synthesis/gap-analysis.md` | The gap, restated after each pass |
| `research/synthesis/research-question.md` | The question, sub-questions, thresholds, hypotheses |
| `research/synthesis/literature-review.md` | What the academic evidence says |
| `methodology/` | Methodology, pipeline, risk register |
| `research/findings/` | Eight first-pass reports |
| `research/findings/second-pass/` | Four reports checking the first pass at the source |
| `research/findings/third-pass/` | Three reports: the permission route, competitor teardown, car parts |
| `research/prompts/` | The research briefs, re-runnable |
