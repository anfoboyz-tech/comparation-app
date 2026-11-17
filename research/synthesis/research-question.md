# Research question

## The question

> For an Australian shopper looking at a specific second-hand listing, can a tool built only on lawfully obtainable data return, within ten seconds, the current new price, a fair used range and a buy / negotiate / skip verdict that is accurate enough to trust, that beats asking a general AI assistant, and that people come back to?

"Lawfully obtainable" means official APIs the app is approved for, affiliate feeds, and listings the user brings in. The second pass found each of these narrower than hoped: eBay's production API is for approved partners, few of the target retailers are on the affiliate network checked, and Gumtree's terms may reach even user-shared listings. Results bought from search-results vendors are a legally grey route (see `research/findings/03-data-access-and-legal.md`); they may be used for experiments, and whether they can be a production dependency is one of the things to settle.

## Sub-questions and what would count as an answer

The thresholds are proposals to make each question decidable. They are judgement calls, not industry standards. Change them before the experiments start, not after. Where a sample is too small to separate pass from stop, the table says so.

| # | Sub-question | Measure | Pass | Stop and rethink |
|---|---|---|---|---|
| 0 | Does anyone want this? | Requests received by a one-week manual "send me a listing, I'll tell you if it's fair" service posted to Australian hobby groups; share who send a second listing | 20 or more people use it, and several return unprompted | Fewer than 5 people use it after posting in at least five groups |
| 1 | Can the new price be found, by a route that can be used in production? | Share of test items where the route finds the best current Australian new price within 2%; whether the route is lawful, its cost and its speed | 80% or more in at least one category, by a route that is lawful and costs under A$0.03 per lookup | Under 60% in every category, or only the grey route works |
| 2 | Can the item be identified from a real listing? | Share of listings assigned the right match tier (same / same family / substitute / different) against a hand label | 80% or more | Under 65% |
| 3 | Is the verdict sound? | Agreement with a hand-researched verdict on a labelled set; share of fair-value ranges that contain the hand-researched fair price; count of figures in the output that do not trace to retrieved evidence | 80% agreement; zero untraceable figures | Under 65% agreement, or any untraceable figure that survives validation |
| 4 | Is it better than what exists? | The same listings given as screenshots to ChatGPT, Gemini and Meta AI, and run through Deal Scout, PriceSnap and Spottable. Scored on: new price within 5% of the hand-checked best price; verdict the same as the hand-researched one | The tool beats the best alternative by 15 points or more on both measures | The best alternative scores 70% or more on both measures, or the tool does not beat it |
| 5 | Is it fast, and does it save time? | Median time for the tool to answer; median time for a tester to reach a decision with the tool, with a general assistant, and unaided | Answer in 10 seconds or less; decision faster than with an assistant | Slower than using an assistant |
| 6 | Do people come back? | Share of testers who check a second listing within 14 days | One in three or more | Under one in three |
| 7 | Will people tell us what they paid? | Response rate to the follow-up prompt | 20% or more | Under 5% |
| 8 | Can it pay for itself? | Cost per check in Australian dollars; click-through to retailers; payments actually made for a paid tier | Cost at or under the break-even for the chosen category (see below); at least some testers pay real money | Cost above break-even with nobody paying |

Notes on the thresholds:

- **Sub-question 3, fair value.** This is the part buyers say they lack, and the hardest. Xianyu's published system, using the platform's own listings, lands within 20% of the asking price 54.6% of the time. A small tool without sold prices should expect to do worse and should withhold a range often.
- **Sub-question 2.** Published accuracy for matching clean retail product offers is 0.64–0.89 (F1) depending on difficulty, and used listings are expected to be harder. Tiers are coarser than exact matching, which is why 80% is plausible, but it is a guess until measured.
- **Sub-question 3.** "Sound" means agreement with one person's hand research. That person has no sold-price data either. Use a second labeller on a subset and report how often the two disagree.
- **Sub-question 4** is the one most likely to stop the project. In Phase 0 there is no tool yet, so only the stop criterion applies.
- **Sub-question 6.** The stop line is the one the differentiation track set. A 30–50 person study gives a direction, not a precise rate.
- **Sub-question 8.** Break-even depends on the category. On the business track's assumptions it is about A$0.09 per check where commission is around 3% and 2% of users pay A$4.99 a month, and about A$0.04 for fishing gear at BCF's reported 0.5%. The architecture track's recommended design is estimated at about US$0.05 per check, which is more than A$0.05; the cheaper variant is about US$0.02.

Sub-questions 0–4 can be answered before any app is built.

## Hypotheses

- **H1.** In categories where listings name a model (reels, power tools, cameras), new-price retrieval and matching will pass. For bundles and unbranded goods they will not, and the tool should say so instead of guessing.
- **H2.** Showing the new price and the comparables beside the verdict will matter more to trust than the verdict label itself.
- **H3.** General assistants will do reasonably on identifying the item and poorly on current Australian prices and on consistency between runs.
- **H4.** Repeat use will be concentrated in hobbyists and frequent second-hand buyers, not one-off shoppers.

H3 is the hypothesis the project depends on, and no track tested it. One outside data point supports it: Which? found in October 2026 that ChatGPT gave the correct lowest price and retailer for 8 of 25 products.

## Out of scope for this question

- Searching Facebook Marketplace or Gumtree on the user's behalf.
- A general new-goods price comparison engine.
- Vehicles and property, which have established valuation products.
- Markets outside Australia.

These are deferred, not rejected. The staged path back to the wider vision is in `methodology/methodology.md`.
