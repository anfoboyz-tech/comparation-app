# Research question

## The question

> For an Australian shopper looking at a specific second-hand listing, can a tool built only on lawfully obtainable data return, within ten seconds, the current new price, a fair used range and a buy / negotiate / skip verdict that is accurate enough to trust and that replaces most of the manual checking?

"Lawfully obtainable" means official APIs, affiliate feeds, licensed search results, and listings the user brings in. "Replaces most of the manual checking" refers to the 50–100 minutes in the founder's story.

## Sub-questions and what would count as an answer

The thresholds are proposals to make each question decidable. They are judgement calls, not industry standards; change them before the experiments start, not after.

| # | Sub-question | Measure | Pass | Stop and rethink |
|---|---|---|---|---|
| 1 | Can the new price be found? | Share of test items where the tool finds the best current Australian new price within 2% | 80% or more in at least one category | Under 60% in every category |
| 2 | Can the item be identified from a real listing? | Share of listings assigned the right match tier (same / same family / substitute / different) against a hand label | 90% or more | Under 75% |
| 3 | Is the verdict right? | Agreement with a knowledgeable human's verdict on a labelled set; count of figures in the output that do not trace to retrieved evidence | 80% agreement; zero untraceable figures | Under 65% agreement, or any untraceable figure that survives validation |
| 4 | Is it better than what people already have? | Same listings given as screenshots to ChatGPT, Gemini and Meta AI, scored the same way | Clearly better on new-price accuracy and verdict agreement | A general assistant matches it |
| 5 | Does it save the time? | Median time for a tester to reach a decision, with the tool versus without | Under 2 minutes with the tool | No meaningful difference |
| 6 | Do people come back? | Share of testers who check a second listing within 14 days | One in three or more | Under one in five |
| 7 | Will people tell us what they paid? | Response rate to the follow-up prompt | 20% or more | Under 5% |
| 8 | Can it pay for itself? | Cost per check; click-through to retailers; stated and actual willingness to pay for a paid tier | Cost at or under A$0.05; a revenue line that covers it | Cost above A$0.09 with no paying users |

Sub-questions 1–4 can be answered at a desk in the first week. Sub-questions 5–8 need a working prototype in real hands.

## Hypotheses

- **H1.** In categories where listings name a model (reels, power tools, cameras), new-price retrieval and matching will pass. For bundles and unbranded goods they will not, and the tool should say so instead of guessing.
- **H2.** Showing the new price and the comparables beside the verdict will matter more to trust than the verdict label itself.
- **H3.** General assistants will do reasonably on identifying the item and poorly on current Australian prices and on consistency between runs.
- **H4.** Repeat use will be concentrated in hobbyists and frequent second-hand buyers, not one-off shoppers.

## Out of scope for this question

- Searching Facebook Marketplace or Gumtree on the user's behalf.
- A general new-goods price comparison engine.
- Vehicles and property, which have established valuation products.
- Markets outside Australia.

These are deferred, not rejected. The staged path back to the wider vision is in `methodology/methodology.md`.
