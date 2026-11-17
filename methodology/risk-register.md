# Risk register

Ranked by how likely each is to end or reshape the project. Sources are the track findings in `research/findings/`. Most underlying facts are from search summaries and still need checking at the source.

| # | Risk | Severity | Evidence | Response |
|---|---|---|---|---|
| 1 | **A general assistant already does this well enough.** | Could end it | 61% of Australian online shoppers use AI tools; no track tested assistants on real listings | Phase 0 baseline test on twenty listings before any build. Re-run it quarterly. |
| 2 | **Meta adds a buyer-facing fair-price rating to Marketplace.** | Could end it | Seller price suggestions (March 2026); buyer price information on vehicles (November 2025) | Hold the position Meta will not: the new price elsewhere and listings on other platforms. Build the outcome data early. |
| 3 | **Revenue per check does not cover cost, and nobody pays.** | Could end it | Track 6 base case about A$0.06 per check on affiliate alone; shopping apps retain about 3% at day 30 | Keep cost at or under A$0.05. Test a paid tier in Phase 4. No paid installs until revenue per user is measured. |
| 4 | **eBay's licence forbids combining its data with other sources or using it for price verdicts.** | High | Search results quoting the agreement | Read the agreement; get eBay's written answer; show eBay results in a separate section; design fair value to work without eBay if needed. |
| 5 | **Australian new prices cannot be retrieved reliably for the chosen category.** | High | Untested; BCF and Anaconda coverage unknown | Phase 1 coverage experiment decides. Fallbacks: affiliate feeds, model web search restricted to named retailers, a different category. |
| 6 | **The verdict is built on the wrong item.** | High | Used listings often lack model detail; combos are compared with single items | Tiered matching shown to the user; bundle splitting; lower confidence when the match is not exact; "not enough data" as an output. |
| 7 | **A wrong or invented figure reaches a user.** | High | OpenAI itself warns its shopping prices may be wrong; one bad figure costs trust | Figures computed in code; validator on every explanation; time stamp and source on every price. |
| 8 | **Fair used range is weak at launch.** | High | eBay's sold-price API is restricted to approved partners; asking prices run above sale prices | Lead with the new price and percent-of-new; show ranges with evidence counts; apply for eBay partner access; collect outcomes. |
| 9 | **People use it once and never return.** | High | Existing verdict tools have tiny followings; buying a rod is occasional | Start with hobbyists and frequent second-hand buyers. Measure second check within 14 days. Saved items and price-drop alerts as the return trigger. |
| 10 | **Consumer-law exposure from claims or rankings.** | Medium | ACCC comparator guidance; Trivago penalised A$44.7m for presenting paid rankings as best prices | Never claim "every retailer" or "best price". List sources checked. Disclose commission. Verdict independent of commission. Lawyer review of the wording. |
| 11 | **Privacy exposure from seller data in screenshots.** | Medium | Listings carry names, faces and suburbs; privacy reforms in progress | Store item facts only. Do not retain screenshots after extraction. Lawyer review. |
| 12 | **Search-data vendor disappears or reprices.** | Medium | Google v. SerpApi ongoing on non-copyright claims | Connector interface, a second vendor tested, caching. |
| 13 | **App store rejection.** | Medium | Apple requires permission to display third-party content; thin link-aggregator apps are rejected | Native verdict logic and interface; official data routes; no logged-in automation. Check current guidelines at the source. |
| 14 | **Affiliate networks reject or suspend the app.** | Medium | Phia reportedly suspended by Impact.com in July 2026 over cookie stuffing | Links only on explicit user taps; no background affiliate activity; apply as a comparison publisher. |
| 15 | **A small competitor adds new prices and Australian coverage.** | Medium | Nine or more verdict tools exist; the parts are cheap | Speed in one category, Australian retailer coverage, and the accumulating price and outcome data. |
| 16 | **Cost runs away through alerts or abuse.** | Low–medium | Re-checking five saved items daily costs more than a user's interactive checks | Rate limits, shared watches per product, scheduled re-checks, batch pricing for background work. |
| 17 | **The share-sheet route does not work as hoped on iOS.** | Low–medium | Expo's share-receiving support is marked experimental | Screenshot and pasted link as equal entry points from the start. |

## Things deliberately not done, and why

- **Scraping Facebook Marketplace or Gumtree.** Breaches their terms, risks users' accounts and the app's store listing, and Meta has a record of suing.
- **Automating a user's logged-in Facebook session.** A 2022 US ruling went against exactly this pattern.
- **A single "search the whole internet" promise.** Cannot be delivered, and saying it would be a misleading claim.
- **Targeting resellers.** That segment is already served by subscription alert tools.
