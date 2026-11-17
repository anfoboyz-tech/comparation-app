# Second pass — demand and market (tracks 6 and 7)

Read date for every source below: 2026-11-17. First-pass files checked: `research/findings/07-user-pain-and-demand.md` (T7) and `research/findings/06-business-model-and-market.md` (T6).

How sources were read: `curl` for static pages, Playwright for the Scamwatch statistics dashboard. Web searches used: 22 of 25. Sites that refused automated requests and were not pursued: Reddit, Whirlpool forums, Fishraider, StereoNET, BuyWisely, auspost.com.au main site, adjust.com (rate-limited), Choosi (site down for maintenance). Anything from those is labelled "search summary".

## 1. What changed

Most important first.

1. **The scam figure the first pass leaned on is wrong by a factor of about 25.** "Nearly A$260m lost to shopping scams" is a misreading of a headline. The ACCC release says A$259.5m was lost to *all* scams reported to Scamwatch in January–September 2025. Shopping scams were A$8.6m of that. For the full year, the Targeting Scams report gives A$10.8m lost to shopping scams (12,248 reports with a loss). The A$25.5m figure is a different, wider Scamwatch category ("buying and selling scams", 44,553 reports in 2025), which I confirmed on the Scamwatch dashboard. Safety is a real and frequently mentioned worry, but reported dollar losses are small next to investment scams (A$837.7m combined), and no official source isolates Facebook Marketplace or Gumtree.
2. **Users' own words do not support the "50–100 minutes checking new prices" pain.** In the Australian threads I read, people asking "is this a fair price?" already knew the new price and quoted it in their first post. What they could not work out was what the *used* item should be worth and whether the saving justified no warranty and scam risk. Replies came within the hour, for free, and the commonest advice was "just buy new" or "ignore it and move on". The one original poster who reported an outcome bought new.
3. **Nobody in any thread read mentioned an AI assistant, eBay sold listings or a price tool.** The twelve OzBargain threads read (first page of each, 2021 to November 2026) contain no mention of ChatGPT or any assistant. I found no account anywhere of someone pasting a listing into an assistant and reporting what they thought. That is absence of evidence for the "assistants are the incumbent workaround" claim in the specific case of used listings, not evidence against it.
4. **Evidence against demand is stronger than the first pass recorded.** Forum regulars say plainly that many buyers do not compare ("There is also lots of people out there that don't compare prices"), that there is no right answer ("There's not really a definitive 'good price/deal' for second hand items"), and that overpriced listings are simply skipped ("just ignore and pass because it's not worth the time"). Gumtree's Android app holds 4.6 stars from about 155,000 reviews, so the 1.5–2.4 star ProductReview ratings are a complaints channel, not a measure of general dissatisfaction.
5. **Low-star reviews do not ask for price guidance.** On the ProductReview pages for Facebook Marketplace and Gumtree, the complaints are account suspensions, scammers and bots, no human support, and poor search. The words "overpriced" and "lowball" appear zero times in either page as loaded; "fair price" appears once, in a positive seller review.
6. **BCF's commission is not a flat 0.5%.** The Commission Factory listing headline is 0.50%, but the body says: "Split commission rate - 0.5% for coupon sites, 2% for content sites, 3% for loyalty/cashback sites" and "0% CPA for Clearance items". If a price checker is classed as a content site, the fishing row in section 2.4 rises from A$0.014 to about A$0.056 per search, close to the base case. Clearance items, which are often what makes new cheaper than used, pay nothing.
7. **Swoopa is dearer in Australia than reported and has few Australian ratings.** Australian App Store prices are A$69, A$129 and A$229.99 a month (the US$47 / US$88 / US$144.99 figures are the US store, confirmed). The Australian listing has 34 ratings; the US one has 560. Its description is now aimed at car dealers. This is thin evidence of a paying Australian reseller market.
8. **The "A$62b second-hand market" is not a market size at all.** Gumtree's 2022 figure is the estimated value of unsold items sitting in homes (about 21 items worth A$6,964 per household, survey of 1,052). eBay's A$32b (May 2026) is the same kind of number. Neither measures what Australians spend on used goods. No transaction-based figure was found.
9. **Confirmed as stated:** Australia Post A$82.6b and 14% growth; 9.8m households; IAB "six in ten" AI use and "half compare prices"; the 3% and 6% trust figures (source identified as Ideally, sample size still unknown); every sum in section 2.4.

Effect on the build decision: the case for a *price* check rests on forum anecdotes that, read in full, mostly show people resolving the question quickly and for free. The case for a *safety* check rests on a real worry but much smaller reported losses than the first pass implied. Neither is disproved. The Phase 0 manual test in the morning brief matters more than it did yesterday, and its question should be "what is this used item worth and is it safe", not "what does it cost new".

## 2. Claim table

Status: **C** confirmed at source, **X** corrected, **U** still unverified.

### Scams

| Claim | File | Status | What the source says | URL |
|---|---|---|---|---|
| "Nearly $260m" lost to shopping scams in 2025 | T7 Q6 | **X** | "Between January and September 2025, the National Anti-Scam Centre's Scamwatch service received 159,319 scam reports with financial losses of $259.5 million." That is all scam types. "Shopping scams were the most reported scam type involving financial loss so far this year, with 9,628 of the total 19,662 reports received resulting in $8.6 million in losses." Dated 18 November 2025. | https://www.accc.gov.au/media-release/australians-report-nearly-260m-in-losses-as-shopping-scams-surge |
| 481,523 reports; 274,577 with loss; $2.18b (2025, combined) | T7 Q6 | **C** | Exactly as stated, p.4. Scamwatch alone: 200,675 reports, $334.8m. | https://www.nasc.gov.au/system/files/targeting-scams-report-2025.pdf |
| Shopping scams, full-year 2025 | not in first pass | new | "There were 12,248 Australians who reported a loss to shopping scams, reporting total overall losses of $10.8 million in 2025. This is a 22.2% increase from the 10,022 who reported financial loss to shopping scams in 2024." Footnote: shopping scams are "online shopping scams and classified scams". | same PDF, p.33 |
| More than 44,000 buying and selling scams, over $25.5m lost (2025) | T7 Q6 | **C** | Scamwatch dashboard, filtered to 2025 and "Buying and selling scams": $25,511,524.78 lost, 44,553 reports. This is a broader Scamwatch type than the report's "shopping scams". Dashboard total for 2025 matches the report ($334,834,647.50; 200,675). | https://www.scamwatch.gov.au/research-and-resources/scam-statistics |
| Buying and selling scams, Jan–Sep 2026 | not in first pass | new | $17,211,036.91 of $250,441,924.20 total; 138,392 reports of all types. | same dashboard |
| More than 6,300 loss reports to shopping scams, H1 2025 | T7 Q6 | **C** | "Scamwatch received more than 6,300 reports of financial loss to shopping scams in the first half of 2025: the highest of any scam type." | https://www.nasc.gov.au/news/national-anti-scam-centre-calls-for-continued-action-this-scams-awareness-week-as-scam-losses-trend-up-at-174m |
| No official figure isolates Marketplace or Gumtree | T7 Q6 | **C** | The 2025 report names Facebook only for "over 7,000 suspected Facebook scam URLs" referred to Meta. No platform-level loss table. Contact method is reported only as "online", which merged internet, mobile apps and social media. | same PDF |
| 36% have encountered scams on second-hand marketplaces (Choosi) | T7 Q3, Q6 | **U** | Choosi's site shows a maintenance notice: "Choosi is currently paused". Page could not be read. | https://choosi.com.au/home-contents-insurance/articles/avoid-getting-scammed-online-marketplace |
| Survey-based scam prevalence | not in first pass | new | ABS Personal Fraud 2024-25: 2.7% of people 15+ (596,600) experienced a scam; "buying or selling scams (1.4% or 306,400)" were the most common type. | https://www.abs.gov.au/statistics/people/crime-and-justice/personal-fraud/latest-release |

Reconciliation in one line: A$259.5m is all Scamwatch losses for nine months; A$25.5m is the full-year "buying and selling" type; A$10.8m is the narrower "shopping" (online shopping plus classifieds) group. The three are nested, not conflicting.

### Surveys

| Claim | File | Status | What the source says | URL |
|---|---|---|---|---|
| About 61% of online shoppers use AI tools at least sometimes | T7 Q2; brief | **C** | Pureprofile release, 6 July 2026: "Six in ten online shoppers use AI-powered tools or features at least sometimes when shopping. Among shoppers aged 18–39, this rises to 75%." Capital Brief gives the split: "30% use AI tools often when shopping, 31% sometimes, 16% rarely and 24% never." | https://business.pureprofile.com/stretched-budgets-sharper-shoppers-australians-research-more-before-they-buy/ ; https://www.capitalbrief.com/briefing/online-shopping-hits-fresh-record-as-consumers-tap-into-ai-tools-5d0ff112-6504-423c-867e-57fc279bda45/ |
| Half of AI users compare prices; 45% products; 38% reviews | T7 Q2 | **C** | "Half use the tools to compare prices, 45% to answer product questions or compare products and brands, 38% to summarise customer reviews, 37% to narrow down options before buying, 35% to find a cheaper option". Secondary source; the report itself was not opened. Nothing here is about second-hand listings. | Capital Brief, above |
| Sample 1,079 (or 1,076); fieldwork May 2026 | T7 Q3 | **C** / **U** | "nationally representative survey of 1,079 Australians and 877 New Zealanders aged 18–70 who have shopped online at least once in the last 12 months". Fieldwork month not stated in anything I read. | Pureprofile release |
| 71% changed choices; 69% rely on online research | T7 Q3 | **C** | As stated. Also new: "78% use AI summaries for a quick answer and then click through", "74% use AI as one of several sources", and eight in ten have some concern about AI for product research. | Pureprofile release |
| 3% would buy on AI recommendation alone; 6% trust AI most | T7 Q5 | **C**, sample **U** | B&T, 14 September 2026. The research is by **Ideally** (quote from its CEO, James Donald), a firm that sells AI-visibility services to brands. Figures as stated: 3%; 6% versus Google 26%, friends and family 25%, reviews 20%. Also: 27% "regularly use AI to research products or services", 23% once or twice; "31 per cent selected ChatGPT" as used the last time they researched a purchase, behind Google at 66%. **No sample size, method or fieldwork date is given.** A different Ideally study in B&T used 400 people; do not assume the same here. | https://www.bandt.com.au/just-3-of-aussies-would-buy-a-product-on-an-ai-recommendation-alone/ |
| 43% bought second-hand in the past year (PayPal) | T7 Q3; T6 2.1 | **C** | PayPal Australia newsroom, 15 November 2024: "Two-in-five (43%) Australians have bought something second-hand in the past year". 35% sold. 63% cite saving money. Sample size not given. | https://newsroom.au.paypal-corp.com/side_hustles_to_survive_cost_of_living_and_staying_safe_Depop |
| 84% bought or sold pre-loved in 12 months (eBay) | T7 Q3; T6 2.1 | **C** (2024 edition, buy *or* sell) | RetailBiz, 5 June 2024, on eBay's 2024 Recommerce Report: "More than four in five (84%) Australians said they have bought or sold pre-loved goods in the last 12 months... Australians aged 18-24 are most likely to have bought pre-loved goods in the last 12 months (64%)". So the all-ages buying share is below 64%. eBay's own report page was not opened. | https://retailbiz.com.au/?p=48504 |
| A$62b "circular economy" value, up from A$48b | T6 2.1 | **X** | Published 24 August 2022. "the average Australian household has approximately 21 sellable items in their home, with an average value of $6,964. This equates to a total value of $62 billion". It is unsold stock in homes, not spending. Survey of 1,052. No newer Gumtree edition found. | https://www.savings.com.au/news/gumtree-pre-loved-items-worth-small-fortune |
| eBay A$32b | T6 sources | **X** (same issue) | eBay Australia, 19 May 2026: "$32 billion in estimated potential resale value nationwide". Potential, not sales. | https://www.ebayinc.com/stories/press-room/au/aussies-sitting-on-a-32-billion-goldmine-as-ebay-drops-selling-fees/ |
| 23% spending more time researching (NAB) | T7 Q3 | **U** | URL returns 404. | https://news.nab.com.au/news/fashion-follows-the-brave-aussies-exercise-caution-when-shopping-online |
| No figure exists for time spent researching a purchase | T7 Q3 | **C** (still not found) | One search found only a car-buying figure (about three months, CarExpert/Nielsen, search summary). Nothing for general goods. | — |

### Market facts

| Claim | File | Status | What the source says | URL |
|---|---|---|---|---|
| Online spend A$82.6b in 2025; growth 14% or 19.9% | T6 2.1 | **C**, growth settled at **14%** | "Australians spent a total of $82.6b online in 2025, up 14% YoY." 2024 was $72.5b. "24% of all retail spend is now made online." The 19.9% figure is not in the report. | https://ecommerce-report.auspost.com.au/ |
| 9.8m households; 41% at least fortnightly | T6 2.1 | **C** | "82% of Australian households shopped online in 2025. That's 9.8 million households... 41% of these are now shopping online at least fortnightly." | same |
| Marketplaces' share | not in first pass | new | "Shoppers spent $18.9b on online marketplaces last year, +13% YoY." This means retail marketplaces such as Amazon and eBay, not peer-to-peer classifieds. | same |
| Adjust: shopping apps keep about 3% at day 30 (2% for "shopping" sub-category) | T6 2.6; brief | **U** | adjust.com returned HTTP 429 on three attempts across two pages; the secondary summary returned 503. Search summary only: Adjust's H1 2025 data gives day-1 retention of 12.8% for shopping apps, 16% for deal-discovery apps and about 25% for marketplace apps, and a cost per install of about US$1.01 for shopping apps. Day-30 figure not seen. | https://www.adjust.com/blog/what-makes-a-good-retention-rate/ |
| Swoopa US$47 / US$88 / US$144.99 a month | T6 2.2 | **C** for the US; **X** for Australia | US store: "Swoopa Go $47.00", "Swoopa Nitro $88.00", "Swoopa Turbo $144.99"; 560 ratings, 4.4. Australian store: "Swoopa Go $69.00", "Swoopa Nitro $129.00", "Swoopa Turbo $229.99"; 34 ratings, 4.6. Swoopa's site lists committed six-month plans at $99 and $199 a month, currency not shown. | https://apps.apple.com/us/app/swoopa/id6475300269 ; https://apps.apple.com/au/app/swoopa/id6475300269 ; https://www.getswoopa.com/pricing |
| BCF pays 0.50%, 10-day cookie, 45-day validation | T6 2.2, 2.4 | **X** (incomplete) | Headline "0.50% per sale, 10 days tracking period, 45 days validation period". Body: "Split commission rate - 0.5% for coupon sites, 2% for content sites, 3% for loyalty/cashback sites" and "Restrictions – 0% CPA for Clearance items". | https://www.commissionfactory.com/my/advertiser-directory/bcf-affiliate-program/91580 |

### Review ratings

| Claim | File | Status | What the source says | URL |
|---|---|---|---|---|
| Facebook Marketplace 1.5 from 160, 92% negative | T7 Q4 | **C** (now 164 reviews, 7% positive, 93% negative) | Rating 1.5. | https://www.productreview.com.au/listings/facebook-marketplace |
| Gumtree 1.7 from 1,775, 84% negative | T7 Q4 | **X** | Now **2.4 from 1,941 reviews**: 18% positive, 5% neutral, 77% negative. Many recent five-star reviews are from sellers and some are marked as incentivised. | https://www.productreview.com.au/listings/gumtree |
| Gumtree app-store rating | not in first pass | new | Google Play: 4.6 stars, about 155,000 reviews, 5M+ downloads. | https://play.google.com/store/apps/details?id=com.ebay.gumtree.au&hl=en_AU&gl=AU |

### Forum quotes

| Claim | File | Status | What the source says | URL |
|---|---|---|---|---|
| Steam Deck thread quotes | T7 Q1 | **C** | All three quotes are verbatim and in context. Thread dated 11–13 December 2025. The original poster already had the new price: "1 year old steam deck oled, with a cheap case or a dock and asking $1200. They are $1050 new with warranty... What's a reasonable price for a used 1TB OLED with or without accessories?" | https://www.ozbargain.com.au/node/939631 |
| Yahoo article reports a Reddit thread on Kmart/IKEA goods above retail | T7 Q1 | **X** | Dated 23 July 2023. The article is about a TikTok creator. The Reddit reference is one closing paragraph about an earlier post: "hundreds of fellow shoppers shared their own experiences with sellers jacking up prices up used goods." It is three years old and concerns unbranded homewares, not model-numbered goods. | https://au.news.yahoo.com/kmart-scam-facebook-seller-aussie-shopper-000359709.html |
| Reddit threads and r/isthisagooddeal | T7 Q1 | **U** | Reddit returned "You've been blocked by network security." Not pursued. | — |

### Section 2.4 arithmetic (T6)

Every sum recomputed; all are correct.

| Line | First pass | Recomputed |
|---|---|---|
| Low / base / high / fishing revenue per search | 0.014 / 0.060 / 0.36 / 0.014 | 0.0144 / 0.0605 / 0.360 / 0.0140 |
| A$4.99 less 15% | 4.24 | 4.2415 |
| Subscription per monthly user at 1% / 2% / 4% | 0.042 / 0.085 / 0.170 | 0.042 / 0.085 / 0.170 |
| Affiliate base per user per month | 0.18 | 0.181 |
| Break-even cost per search, affiliate plus 2% subscribers | 0.09 | 0.0888 |
| Searches for A$1m, affiliate only | 16.5m a year; 1.38m a month; 460,000 users; about 5% of households | 16.53m; 1.378m; 459,000; 4.7% |
| Users for A$1m, affiliate plus subscription | 310,000 | 313,000 |
| Reseller subscribers for A$1m | 2,200 | 2,193 |
| Revenue per install | 0.30 | 0.295 (4.88 searches) |

Inputs against what I read:

| Input | Assessment |
|---|---|
| BCF commission 0.5% | **Contradicted in part.** 0.5% is the coupon-site rate; content sites get 2%. At 2% the fishing row is 0.35 × 0.04 × 250 × 0.02 × 0.8 = A$0.056. Clearance items pay 0%. Which class a price checker falls into is BCF's decision. |
| Reseller tier at A$39 a month | Not contradicted, but the only reference product charges A$69–A$230 in Australia and has 34 local ratings. One Australian reviewer wrote the app "doesn't worth more than $5 a month". No evidence of how many Australians pay. |
| Paid acquisition loses money above A$0.30 per install | **Supported**, by search summary only: Adjust puts shopping-app cost per install at about US$1.01 in H1 2025. |
| 8% of installs still active over a year | No source. Adjust's day-1 figure for shopping apps (12.8%, search summary) makes 8% sustained for twelve months look generous. |
| Click-out 35%, purchase 4%, order value, 3 searches a month | Still assumptions; nothing read bears on them directly. One indirect point in favour of click-outs: in one PS5 thread the outcome of a used-price check was a new purchase, and in the other the advice was to buy new. One against: the user arrives looking at a used listing, and second-hand purchases are occasional, so 3 checks a month per active user has no support. |
| 9.8m online-shopping households | Confirmed. |
| 15% store fee | Not checked. |

## 3. New findings

### 3.1 What Australians actually write when they ask

All quotes verbatim from pages read today.

**They ask about the used value, with the new price already in hand.**

- "Looking on FB marketplace for a cracker second hand deal and every second hand console is priced so high, with a minimal discount from retail pricing... Are people really buying second hand with no warranty for $50 off full retail?" Later: "I find that you can buy them new for 1190 or second hand for 1100... I feel like if I'm buying with no warranty it's only worth 800 in good condition. Do you think I'm being unreasonable?" Outcome, two days later: "Ended up just buying a PS5 standard". (January 2025) https://www.ozbargain.com.au/node/889514
- "What would be a good price to pay for a second hand on on facebook, I am talking with a seller who agreed on $500... not sure if it's a good deal for a second hand one." (December 2022) https://www.ozbargain.com.au/node/746789
- Cars: "I've seen a few cars I like on marketplace, but they all seem to be a fair bit overpriced... Any other ideas on how to accurately value a car?" The poster's own method was to take the Carsales instant-offer quote and add a couple of thousand. (May 2022) https://www.ozbargain.com.au/node/700132

**The answers they get, free and within the hour.**

- "Saving $150 and risking a dodgy facebook seller and potential issues with warranty. No thanks. If you don't want to pay over $700 then just buy a brand new digital one for $650." (node 746789)
- "See/compare to what other sellers are posting their PS5s for? Check Gumtree as well. There's not really a definitive 'good price/deal' for second hand items". (node 746789)
- "If you want to buy second hand have a price in mind and offer the people on fb marketplace". (node 889514)
- "decide how bad you want it and how much you would be happy to buy it for based on the average selling price across FB marketplace, gumtree, and whatever is local to your area... automated market values are rarely accurate to the current avg pricing so make your own judgement". (node 700132)
- "sellers are delusional because they only think about what they paid. they barely used it, knock off 10%, and call that a 'reasonable' price." (23 votes, node 939631)

**Evidence that many do not check, or do not need to.**

- "Lots of people list high hoping for a poor informed buyer andvarebin no hurry to sell. There is also lots of people out there that don't compare prices." (node 939631)
- "Is pretty common to see a lot of listings asking more than the current sales price, just ignore and pass because it's not worth the time." (node 939631)
- "I've been told a couple of times that everything on FB Maketplace is 10% below the asking price at least. I'll always low ball". (node 939631)
- A seller: "I recently sold a vacuum cleaner for almost the same price what you could buy a new one for. No haggling and the buyer came from a two hour drive away." (January 2021) https://www.ozbargain.com.au/node/599783
- Experienced buyers describing no difficulty: "Recently bought a router for $50 that retails for $250... Also bought a fridge for $300 that retails for $900" (40 votes). https://www.ozbargain.com.au/node/599074

**Evidence that the complaint is long-standing.**

- "every time I go to check Gumtree or Ebay for something that I wouldn't be fussed about if it was second hand, half the time the prices are near retail prices." (January 2021, node 599074)
- "It seems most sellers expect near full rrp for used goods - I've often found what I'm looking for cheaper (or only a few $s more) new!" (January 2021, node 599783)

**Safety runs through every pricing thread.**

- "Don't buy used electronics from FB Marketplace with no recourse if there's any issues." (18 votes, node 939631)
- "it happened to me three times until I just gave up and bought on eBay." (node 939631)
- A buyer lost A$1,100 on a sealed counterfeit phone with a matching IMEI and a forged receipt. The top reply: "you really thought you were getting a $2,000+ phone, that's been out for a month, brand new sealed for half-price from some random joe?" (50 votes, March 2025) https://www.ozbargain.com.au/node/898205

That last thread points at a use the first pass did not name: a price that is *too low* is the scam signal. A check that says "this is 45% below every comparable; treat as suspect" answers a question buyers demonstrably get wrong.

**Poll.** An OzBargain poll from January 2021 (490 votes, self-selected bargain hunters): 327 "It depends", 124 "I will search second-hand option before buying new", 32 "I never buy second-hands", 7 "I only buy second-hands". https://www.ozbargain.com.au/node/599074

### 3.2 Fishing, tools and cameras

- **Fishing: nothing found.** Two searches returned no Australian thread asking whether a used rod or reel was fairly priced. Fishraider refused automated requests. OzBargain's fishing content is new-stock deals. The only relevant line is a general one: "there is a huge range of items that can't be bought new at anywhere the same quality as you can get secondhand. Hand tools are a great example. Some camera lenses... Lots of fishing gear" (node 599074). The founder's own category is the one with no visible public demand. That may be because fishing buyers ask in Facebook groups, which cannot be read.
- **Tools: buyers sound confident, not confused.** "Makita, DeWalt and the like have a pretty good second hand market going. You can get some pretty nice stuff used." (June 2025) https://www.ozbargain.com.au/node/910782 . "Milwaukee M18BI0 18V Li-ion Cordless Tyre Inflator - Skin Only @ $275 keep an eye out on the fb marketplace. I managed to pick up one for half price." (9 November 2026) https://www.ozbargain.com.au/node/982112 . No thread found asking whether a used tool price was fair. A ProductReview complaint describes a Marketplace seller offering Milwaukee batteries "at ridiculous cheap prices like 12amp forge batteries for $130, retail for $400" who never delivered.
- **Cameras: a dealer already supplies the comparison.** "Most items for the system I'm familiar with (L-Mount) are around or below the prices you can find on Facebook Marketplace, with the added bonus of all second hand goods coming with Ted's 12 month 2nd hand warranty." A reply: "Although some of the items are lower priced than those you find in Marketplace, they did not describe the condition and post photos of the actual items." (August 2024) https://www.ozbargain.com.au/node/862012 . In the business track's preferred beachhead, buyers already benchmark Marketplace against a warrantied dealer. Whirlpool photography threads could not be opened; a search summary reports posters citing used lenses at 20–50% of original price and eBay sold items as the reference.

### 3.3 Assistants

- No first-hand account found of anyone pasting a second-hand listing into an assistant. Two searches; Reddit unreadable.
- A study by Product.ai, reported by Tech.co on 25 September 2026, put the same 220 shopping questions to free and paid ChatGPT, Claude, Gemini and Perplexity and found conflicting or incorrect information "86% of the time"; "When a price was wrong, it was wrong by a median of $300". The questions were about new goods. Product.ai sells a competing product, and the original report was not opened. https://tech.co/news/ai-shopping-assistants-not-ready-holidays
- A resale-tool vendor's own blog says of ChatGPT: "It does not pull live completed-sale data, so any price it gives is an educated guess." Vendor claim, US product. https://underpricedai.com/blog/can-chatgpt-tell-you-what-your-item-is-worth
- The Ideally figures cut both ways: 31% of Australians used ChatGPT the last time they researched a purchase, yet only 3% would buy on its word alone. Assistants are widely consulted and not trusted to decide, which describes any verdict product, the founder's included.

### 3.4 Low-star review themes

Counts are keyword hits in the review text loaded on each ProductReview page (roughly the first 30 to 40 reviews of each), so they indicate themes, not totals.

| Theme | Facebook Marketplace | Gumtree |
|---|---|---|
| Scam, scammer | 25 | 6 |
| Bot or automated enquiry | 17 | 3 |
| Fake | 10 | 1 |
| Support, customer service | 11 | 11 |
| Suspended or disabled account | 12 | 0 |
| Search | 8 | 6 |
| Price (any mention) | 8 | 6 |
| Overpriced, lowball | 0 | 0 |

- Facebook Marketplace: the dominant complaint is sellers locked out by automated moderation with no appeal ("Meta and Marketplace - No Home for Real People - Only AI"), then scammers not removed after being reported, then wasted trips ("Drove up from Rosebud to Brighton 72km... as I was travelling up the seller sold the item"). Search relevance gets one detailed complaint.
- Gumtree: ProductReview's own summary lists scam enquiries, unresponsive support, irrelevant search results and bugs. Google Play's top review (May 2026) is about an update that broke location search.
- Swoopa: the one critical Australian review says it misses recent Marketplace listings because Facebook's systems block it, the trial is one to two hours, and the price is too high. The developer's reply: "We have people who make between 4k to 30k a month using Swoopa and to them its cheap. If you cant make money from it then its not going to be worth it".
- Most reviewers on both platforms are sellers. Buyers' complaints are about fraud and no-shows. **No reviewer on any page asked for price guidance, comparables or a new-price reference.**

### 3.5 Found in passing, outside this assignment

A search summary showed BuyWisely product pages for Shimano Stradic reels listing a used eBay Australia price beside new retailer prices. BuyWisely refused the fetch, so this is unconfirmed, but it bears on the brief's statement that no one puts a new price beside a used one. The competitor tracks should check it.

## 4. Still open

| Question | Why it is open | What would settle it |
|---|---|---|
| How common is the pain; will anyone pay | No source measures it. Forum threads show the question exists and is usually answered quickly and for free. | The Phase 0 manual service. Count requests per group per week, and ask for A$2 on the third check. |
| Do people paste used listings into assistants, and are the answers good enough | No account found; Reddit unreadable | Score 20 real Australian listings through two assistants, as the brief already plans |
| Fishing, tradie and camera communities | Fishraider, Whirlpool and StereoNET refused requests; the active groups are on Facebook | A person joining three Facebook groups and reading a month of posts |
| Reddit evidence, including r/isthisagooddeal size | Blocked | Read in a normal browser |
| Sample size and method of the Ideally survey | Not in the B&T article | Ask Ideally or find its release |
| Adjust day-30 retention | adjust.com rate-limited | Open the page in a browser |
| Choosi 36% scam-exposure figure | Site down | Retry later, or drop the figure; the ABS 1.4% a year is the better number |
| NAB 23% figure | 404 | Drop it |
| eBay Australian buying share, current edition | Only the 2024 buy-or-sell figure was confirmed | eBay's 2025 or 2026 report PDF |
| A transaction-based size for Australian second-hand | Not found; the Gumtree and eBay figures are unsold stock | Possibly none exists; do not quote a market size |
| Which BCF commission class a price checker falls into | BCF decides on application | Apply through Commission Factory |
| Share of buying-and-selling scam losses on Marketplace or Gumtree | Not published | Ask the National Anti-Scam Centre; the dashboard exports by contact method only |
| IAB report's own tables on AI for price comparison | Read through Capital Brief, not the report | Download the report from IAB Australia |
