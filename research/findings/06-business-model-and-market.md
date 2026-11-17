# Track 6 — Market size, business model and go-to-market

Research date: 2026-11-17.

**Read this first: how far to trust this file.** Two tool limits shaped tonight's work. (1) Direct page fetches failed for every site I tried (eBay Partner Network, Amazon Associates AU, Commission Factory, ACCC, OzBargain, TechCrunch, savings.com.au, hellopartner.com were all outside the session's allowed network domains). (2) The shared web-search budget ran out part-way through. So every "sourced" number below comes from search-result extracts of the cited page, not from my own reading of the page, and several questions were never searched at all. I mark each claim as **[S]** sourced via search extract tonight, **[B]** my background knowledge, not checked tonight, or **[I]** my inference or assumption. Treat [B] and [I] as leads to verify, not facts.

## 1. Bottom line

1. The market is large but that is not the constraint. Australians spent about A$82.6b online in 2025 (Australia Post) and somewhere around 40–85% of adults touch second-hand each year depending on the survey. The constraint is revenue per search.
2. Affiliate revenue per search is roughly A$0.01–0.06 on realistic assumptions, against a per-search cost of A$0.02–0.30. At the upper half of that cost range the consumer app loses money on every search under any affiliate-only model.
3. The founder's own category is one of the worst for affiliate income: BCF's Commission Factory listing shows 0.50% per sale with a 10-day cookie [S]. A A$300 rod-and-reel sale would pay about A$1.50.
4. The used side earns nothing when the sale happens on Facebook Marketplace or Gumtree. The only commission route on used goods is eBay Partner Network (reported at roughly 1–4% of sale with per-transaction caps; Australian rate card not verified).
5. The only used-side model I found with evidence of people paying real money is subscription alerts for resellers: Swoopa lists US$47–145 a month on the App Store [S]. That is a reseller tool, not the consumer app in the idea brief.
6. Paid user acquisition does not work on these numbers: lifetime affiliate revenue per install is about A$0.30 on my assumptions, and e-commerce apps keep about 3% of users at day 30 (Adjust, 2025) [S].
7. Comparable outcomes split cleanly. Winners either owned free distribution (Honey's extension, OzBargain's community, idealo/PriceRunner SEO) or sold to the supply side (Carsales, CarGurus). The best-funded Australian attempt, Little Birdie (A$30m from CBA), shut down in May 2024 [S].
8. Affiliate-funded shopping assistants are under scrutiny right now: Phia was suspended by Impact.com in July 2026 over cookie-stuffing allegations [S], following the 2024 Honey controversy. Any attribution trick is a company-ending risk.
9. My recommendation: this can be a small, real business (hundreds of thousands to low millions of dollars a year) if it starts web-first in one high-value, model-numbered category, keeps per-search cost under about A$0.05, and charges power users. It is not a venture-scale consumer app on the evidence I found.
10. A decision to build should be conditional on Track 5 showing a per-search cost at the low end of the range.

## 2. Findings

### 2.1 Market size

**Australia — online retail**

| Measure | Figure | Date | Source | Note |
|---|---|---|---|---|
| Online goods spend | A$82.6b | CY2025 | Australia Post eCommerce Report 2026 [S] | Growth reported as 14% in the report summary; one trade outlet says 19.9%. I could not open the PDF to settle it. |
| Households shopping online | 9.8m; 41% at least fortnightly | CY2025 | Australia Post [S] | |
| Online retail, NAB method | A$65.65b, +14.4% | 12 months to Aug 2025 | NAB Online Retail Sales Index [S] | Different method from Australia Post; do not add. |
| Online retail, NAB method | A$68.35b, about 15.1% of retail | to Dec 2025 (period not confirmed) | McGrathNicol citing NAB [S] | Secondary. |
| Basket size | Falling while total spend rises | 2025–Nov 2026 | Australia Post; CommBank Nov 2026 [S] | Consistent with value-seeking. |

ABS figures were not retrieved.

**Australia — second-hand**

| Measure | Figure | Date | Source | Note |
|---|---|---|---|---|
| "Circular economy" value | A$62b, up from A$48b in 2021 | 2022 report | Gumtree "Trading in the Circular Economy" via secondary coverage [S] | Earlier Gumtree reports (A$34b, A$40b) measured the value of unwanted items people could sell, not transactions. Treat A$62b as an upper bound, not GMV. No 2025/2026 edition found. |
| Bought or sold pre-loved in last 12 months | 84% | 2024 | eBay Recommerce Report (Australia) [S] | Buy-or-sell combined. |
| Bought second-hand in past year | 43% | undated | PayPal / Garage Sale Trail [S] | Lowest and most conservative figure. |
| Bought second-hand in past year | 72% | undated | Unnamed study via Inside Retail [S] | Low confidence. |
| Buying more second-hand due to cost of living | 24% (PayPal); 32% increased purchases, 70% citing lower cost (ShipStation) | undated | [S] | |
| Facebook users in Australia | 24.7m (88.5% of population) | Sept 2026 | NapoleonCat estimate [S] | Facebook overall. No Marketplace-specific Australian figure found. |

Inference [I]: with roughly 21m adults [B], 43–72% implies about 9–15m Australians buy something second-hand each year. Average transaction value and a reliable transaction-based market size were not found. Confidence on the size of the second-hand market: low. Confidence that it is large and growing with cost-of-living pressure: medium-high.

**Later expansion markets**

| Market | Online retail | Second-hand | Source |
|---|---|---|---|
| US | US$1,233.7b e-commerce in 2025, +5.4%, 16.4% of retail | Apparel resale US$30b in 2025, +13% (apparel only) | US Census; ThredUp 2026 Resale Report [S] |
| UK | Online was 28.1% of retail sales in Oct 2025; annual pound total not found | Not found | ONS [S] |
| Europe | B2C e-commerce €911b in 2025, +7%; EU-27 €715.8b | Not found | European E-commerce Report 2026 via secondary [S] |
| Global | — | Second-hand apparel forecast US$393b by 2030 | ThredUp [S] |

### 2.2 Revenue models

| Model | Typical rates found | Who uses it | Fit here |
|---|---|---|---|
| Affiliate commission, new goods | Commission Factory says its network average is 8–10% per sale [S], but that is fashion-heavy. BCF: 0.50%, 10-day tracking, 45-day validation [S]. The Good Guys discloses 0–6% paid to affiliates [S]. Amazon AU cut rates sharply from 15 June 2023, to 0% in one category [S]; current table not retrieved. | CamelCamelCamel, OzBargain, Honey, Phia | Core model for new goods, but hard-goods rates look like 0.5–4%, not 8–10%. |
| Affiliate, used goods | eBay Partner Network: percent of sale by category, about 1–4%, per-transaction caps (third-party reports cite US$100–550), new-buyer bonus removed [S]. Australian card not verified. | Used aggregators | Only works when the buyer ends up on eBay. |
| Cost per click from retailers | Not researched (search budget). [B]: PriceSpy, idealo and PriceRunner are mainly CPC-funded. | Classic comparison engines | Needs traffic scale before retailers will sign. |
| Sponsored placement | No rates found. | Trivago, comparison sites | Directly conflicts with a "best deal" verdict; ACCC guidance says operators should not take payment for preferred ranking [S]. |
| Subscription / freemium | Keepa Pro about €29/month, API from €49/month (2026 reviews) [S]. Swoopa Go US$47, Nitro US$88, Turbo US$144.99 per month [S]. ShopSavvy Pro US$2.99/month or US$29.99/year to remove ads (2024 snapshot) [S]. CamelCamelCamel: no paid tier [S]. Honey: free [B]. | Resellers and Amazon sellers pay; consumers barely do | Consumers pay US$3; people who make money from deals pay US$30–145. |
| Display advertising | OzBargain uses Publift; about 45m page views a month (Dec 2023) [S] | OzBargain, CamelCamelCamel | Only at large page-view scale. |
| Supply-side subscriptions and lead generation | CAR Group Australia: A$519m revenue, 66% EBITDA margin, FY26 [S]. CarGurus: US$907m revenue, 2025 [S]. | Carsales, CarGurus | Charge pawn shops, refurbishers and specialist used dealers for leads or listings. Unproven outside cars and property. |
| Data and insights | Nothing found tonight. | — | Used-price index by model is a plausible later product [I]. |
| Transaction fee / escrow | Nothing found tonight. | — | Would need payments licensing; not a first-year model [I]. |
| Cashback | Cashrewards bought Little Birdie in Aug 2024 to pair price search with cashback [S] | Cashrewards, ShopBack | Shares the same thin commission with the user. |

### 2.3 Monetising the used side

- Person-to-person sales on Facebook Marketplace and Gumtree pay no commission. I found no aggregator that earns per transaction there.
- What exists: eBay affiliate links on used listings; paid alert subscriptions for resellers (Swoopa); and, in vehicles, dealers paying for leads while private listings act as free content (Carsales, CarGurus [B] for the mechanism).
- A mechanism specific to this product [I]: the "is it worth it" comparison sends a share of used-intent shoppers to a new or refurbished purchase, which is commissionable. That is also exactly where the conflict of interest sits.
- Conflict of interest: the app earns when it says "buy new" and nothing when it says "buy that Marketplace listing". The ACCC's comparator website guidance (August 2015) asks operators to disclose commercial relationships even when they do not affect results, and not to accept payment for preferred treatment [S]. [B]: the Federal Court fined Trivago A$44.7m in 2022 for presenting paid-ranking results as best price. OzBargain's handling: merchants cannot pay to post or feature deals [S].
- Practical handling [I]: compute the verdict with no commission input, label every commissionable link, show when the used option wins, and take subscription revenue so income does not depend on the verdict.

### 2.4 Unit economics

All inputs below are my assumptions [I] unless marked. Formula for affiliate revenue per search:

click-out rate × purchase rate after click × order value × commission × share of sales actually tracked (0.8)

| Scenario | Click-out | Purchase | Order value | Commission | Revenue per search |
|---|---|---|---|---|---|
| Low | 25% | 3% | A$120 | 2% | 0.25 × 0.03 × 120 × 0.02 × 0.8 = **A$0.014** |
| Base | 35% | 4% | A$180 | 3% | 0.35 × 0.04 × 180 × 0.03 × 0.8 = **A$0.060** |
| High (camera-type category) | 50% | 6% | A$300 | 5% | 0.50 × 0.06 × 300 × 0.05 × 0.8 = **A$0.36** |
| Fishing at BCF's real rate | 35% | 4% | A$250 | 0.5% [S] | 0.35 × 0.04 × 250 × 0.005 × 0.8 = **A$0.014** |

Subscription, consumer tier at A$4.99/month, A$4.24 after a 15% store fee [B]:

| Share of monthly users paying | Revenue per monthly user | Per search at 3 searches a month |
|---|---|---|
| 1% | A$0.042 | A$0.014 |
| 2% | A$0.085 | A$0.028 |
| 4% | A$0.170 | A$0.057 |

Per active user per month, at 3 searches:

| Model | Revenue | Cost at A$0.02 | Cost at A$0.30 | Result |
|---|---|---|---|---|
| Affiliate base | A$0.18 | A$0.06 | A$0.90 | Profit only below A$0.06 per search |
| Affiliate base + 2% subscribers | A$0.27 | A$0.06 | A$0.90 | Break-even cost per search is 0.27 ÷ 3 = **A$0.09** |
| Reseller tier at A$39/month (about A$38 on web billing), 300 searches or alert checks a month | A$38 | A$6 | A$90 | Needs cost under about A$0.12 per check, or usage caps |

Scale needed for A$1m a year:

- Affiliate only: 1,000,000 ÷ 0.060 = 16.5m searches a year, 1.38m a month, about 460,000 monthly users at 3 searches each. That is about 5% of Australia's 9.8m online-shopping households.
- Affiliate plus consumer subscription: A$0.27 × 12 = A$3.24 per monthly user per year, so about 310,000 monthly users.
- Reseller subscriptions: 1,000,000 ÷ (38 × 12) = about 2,200 subscribers.

Paid acquisition check: assume 2 searches at install, then 8% of installs staying active at 3 searches a month for a year. Lifetime searches per install = 2 + (0.08 × 3 × 12) = 4.9. Revenue = 4.9 × 0.060 = about A$0.30 per install, before search costs of about A$0.25 at A$0.05 per search. I did not source an Australian cost per install, but any figure above about A$0.30 loses money, so growth has to be organic.

### 2.5 Comparable companies

| Company | Facts found | Status | What explains the outcome |
|---|---|---|---|
| Honey | PayPal paid about US$4b, closed Jan 2020 [S]. About 17m monthly users at the deal [B]. Dec 2024 MegaLag exposé on last-click commission capture; users reported falling from 20m to 17m [S]. | Operating, damaged | Free distribution via extension and creators; the same mechanism later became its liability. |
| PriceRunner / Klarna | Revenue SEK 460m in 12 months to Sept 2021; a 12% stake reported at SEK 1.06b, implying about SEK 8.8b for the whole, consistent with the €930m reported elsewhere [S, I] | Part of Klarna | SEO scale plus retailer CPC in markets with standardised products. |
| Little Birdie (AU) | A$30m from CBA in 2021 for a reported 23% stake; paused all operations May 2024; acquired by Cashrewards Aug 2024; relaunch not confirmed [S] | Failed as standalone | Money and a bank distribution deal did not create a habit. The closest Australian precedent. |
| Phia | US$35m Series A at US$185m valuation, Jan 2026; claims 1m+ users; Impact.com suspended it in July 2026 over alleged cookie stuffing, Awin reviewing [S] | Operating, under scrutiny; outcome of review not found | Celebrity distribution; affiliate-only revenue pushed it toward attribution abuse. |
| Daydream | US$50m seed June 2024; launched June 2025; no 2026 user data found [S] | Unknown traction | — |
| Beni | US$4m seed; iOS app Feb 2024; nothing found after that [S] | Unverified; possibly dormant | Resale-only affiliate income appears too thin. |
| Swoopa | Marketplace, Gumtree, eBay and other alerts; US$47–145/month; live App Store listing [S] | Operating | Sells speed to people who profit from it. |
| OzBargain | About 2.5m unique users and 45m page views in Dec 2023 (own wiki); display ads and affiliate links; no paid placement; founder full-time since 2011 [S]. A US$12.4m revenue figure from ZoomInfo is unverified. | Operating, lean | Community-generated content and trust; near-zero acquisition cost. |
| CAR Group (Carsales) | FY26 revenue A$1,253m; Australia A$519m at 66% EBITDA margin [S] | Thriving | Supply side pays; private listings are content. |
| CarGurus | 2025 revenue US$907m, +14% [S]. Built on a deal rating against estimated market value, paid for by dealers [B]. | Thriving | The clearest precedent for a "good deal / bad deal" verdict as the product, funded by sellers. |
| Keepa | About €29/month Pro, paid data API [S] | Operating | Sells history data to Amazon sellers. |
| CamelCamelCamel | Free since 2008, Amazon affiliate plus display ads; launched a Walmart tracker in 2026 [S] | Operating, tiny team [B] | Survives because costs are minimal. |
| ShopSavvy | Free with ads; Pro US$2.99/month [S]. Funding and users not retrieved. | Operating | — |
| idealo, PriceSpy/Schibsted | Not researched (search budget exhausted). | — | — |

Pattern: nobody in this list built a durable business on consumer affiliate revenue with paid acquisition. Survivors had free distribution, very low costs, or paying sellers and professionals.

### 2.6 Acquisition and retention

- Benchmarks: Adjust 2025 e-commerce apps, day 1 12.6%, day 7 6%, day 30 3%; "shopping" sub-category about 12% / 6% / 2% [S, via a secondary summary]. Older compilations cite 24.5% and 5.6% for day 1 and day 30. Either way, well over 90% of installs are gone in a month.
- Channels that worked for comparables: browser extension with creator sponsorship (Honey), community (OzBargain), SEO on product pages (PriceRunner, idealo [B]), price-drop alerts that bring users back (Keepa, CamelCamelCamel, Swoopa).
- Candidate habit triggers for this product [I]: (a) "share a Marketplace or Gumtree listing to the app and get a verdict", which matches the moment of doubt in the founder's story; (b) a watch on a specific model that alerts when a good used listing or a new-price drop appears; (c) shareable verdict pages ("Is A$180 a good price for a used Shimano Stradic 4000?") that rank in search and get posted in Facebook groups and on OzBargain.

### 2.7 Beachhead

Scores are my judgement [I], 1 (poor) to 5 (good). The only hard data point is BCF's 0.5%. Listing volumes per category were not measured.

| Category | Price level | New–used gap | Model identifiable from a listing | Monetisation (affiliate, eBay share) | Competition (5 = little) | Notes |
|---|---|---|---|---|---|---|
| Cameras and lenses | 5 | 4 | 5 | 4 | 3 | Exact model names, heavy eBay presence, buyers research hard. Specialist used dealers exist. |
| Power tools | 4 | 4 | 5 | 3 | 4 | Clear SKUs, trade buyers repeat. Stolen-goods and battery-condition issues. |
| Musical instruments | 4 | 4 | 4 | 3 | 3 | Reverb is an established used marketplace [B]. |
| Golf | 4 | 4 | 4 | 3 | 4 | Clear model years; strong trade-in culture. |
| Bikes | 5 | 4 | 2 | 2 | 3 | Model, year and size are often missing from listings. |
| Baby gear | 3 | 5 | 3 | 3 | 4 | Strong used culture, but safety and recall liability on a "buy it" verdict. |
| Phones and electronics | 4 | 3 | 5 | 2 | 1 | Most contested; lowest commissions. |
| Gaming | 3 | 2 | 5 | 2 | 2 | Small gaps, existing price trackers. |
| Furniture | 3 | 5 | 1 | 2 | 4 | Unbranded items cannot be matched to a new price. |
| Fishing and outdoor | 2 | 3 | 2 | 1 | 5 | Rod-and-reel combos are hard to match; BCF pays 0.5% [S]. |

Recommendation: start with **cameras and lenses**, with **power tools** as the second. Both have listings that name an exact model, a new price that is easy to find, a large price gap, and order values high enough for the high-revenue row in 2.4. Keep fishing as a personal test case, not the commercial beachhead. Confidence: medium-low until listing counts and affiliate rates are checked per category.

### 2.8 Distribution vehicle

Platform facts in this section are mostly [B] or [I]; the searches on assistant integrations did not run.

| Vehicle | For | Against |
|---|---|---|
| Web app with indexable verdict pages | No store fee, SEO compounding, easy sharing, fastest to test | Weaker push alerts |
| Mobile share-sheet target (a thin app) | Fits Marketplace, which is used mostly in the Facebook app; gives the product a verb | Still needs an install |
| Full standalone app first | Matches the idea brief | Retention near 3% at day 30; store fees on subscriptions; paid installs uneconomic |
| Browser extension | Honey's growth route | Desktop only; affiliate networks are policing extensions after Honey and Phia [S] |
| ChatGPT or other assistant app | Could be the cheapest reach if assistants become the first stop for shopping | Current Australian availability and commercial terms not verified tonight; the assistant owns the user |

Recommendation: web first, then a thin app whose main job is the share-sheet verdict and alerts. Do not lead with an extension.

## 3. Implications for the product

- Build the verdict, not the price table. CarGurus shows a deal rating can be the product; price tables are a commodity that Little Birdie could not sustain with A$30m.
- Design to a cost ceiling of about A$0.05 per search (cache new prices per model, compute live only for used listings). Above about A$0.09 the consumer model does not break even on my numbers.
- Plan for three income lines from the start: commission on new and refurbished, eBay affiliate on used, and a paid tier for alerts. Add a seller or dealer lead product only after there is traffic.
- Pick the beachhead on economics, not on the founder's fishing story.
- Make independence visible: disclosed links, verdict logic that ignores commission, no paid ranking. This is both an ACCC expectation and the brand.
- Avoid anything that claims affiliate credit the app did not earn. Networks are suspending accounts for it this year.
- Avoid paid install campaigns until lifetime revenue per install is measured.

## 4. Open questions

| Question | How to settle it |
|---|---|
| Actual Australian rate cards: eBay Partner Network, Amazon Associates AU, and Commission Factory rates for JB Hi-Fi, Kogan, Anaconda, Sydney Tools, Total Tools, camera retailers; whether Bunnings has any program | Open the three program sites directly (blocked tonight); apply for accounts |
| Australia Post 2025 growth: 14% or 19.9% | Read the report PDF |
| A transaction-based size for Australian second-hand, average value, and Marketplace's Australian user count | Gumtree and eBay report PDFs; Meta advertising tools; ABS |
| UK and EU second-hand market sizes; UK online retail in pounds | Not searched |
| idealo and PriceSpy revenue and model; ShopSavvy funding; Honey's revenue at acquisition; CPC rates Australian retailers pay | Not searched |
| State of assistant shopping integrations in Australia in late 2026 | Not searched |
| Whether Cashrewards relaunched Little Birdie; whether Beni still operates; outcome of the Impact.com and Awin reviews of Phia | Check each product's site and app listing |
| Real click-out and purchase rates, and willingness to pay for alerts | A two-week web prototype in one category with real affiliate links |
| Per-search cost | Track 5 |
| Listing volume by category on Marketplace, Gumtree and eBay | Manual counts in two cities |

## 5. Sources

All accessed via search extracts on 2026-11-17; none opened directly.

- Australia Post eCommerce reports: https://auspost.com.au/business/grow-your-business/ecommerce-reports
- Australia Post campaign page: https://auspost.com.au/campaign-corner/unboxing-australias-ecommerce-boom
- Post & Parcel on the Australia Post report: https://postandparcel.info/?p=162473
- CommBank, Nov 2026: https://www.commbank.com.au/articles/newsroom/2026/11/black-friday-sales-spending.html
- NAB Online Retail Sales Index, Aug 2025: https://business.nab.com.au/nab-online-retail-sales-index-august-2025
- McGrathNicol citing NAB: https://www.mcgrathnicol.com/insight/sentiment-slips-further-following-february-rate-hike/
- Gumtree report coverage: https://www.savings.com.au/news/gumtree-pre-loved-items-worth-small-fortune ; https://www.planetark.com/newsroom/news/new-report-values-australias-circular-trading-at-usd48-billion-and-its ; https://www.bandt.com.au/australias-second-hand-economy-now-worth-34-billion/
- PayPal / Garage Sale Trail: https://newsroom.au.paypal-corp.com/Second-hand_shopping_supports_Aussies_struggling_with_the_cost-of-living
- eBay Australia recommerce: https://insideretail.com.au/ir-pro/the-future-of-trading-in-the-past-ebays-role-in-australias-evolving-market-202505 ; https://www.ebayinc.com/stories/press-room/au/aussies-sitting-on-a-32-billion-goldmine-as-ebay-drops-selling-fees/
- Second-hand surveys: https://insideretail.com.au/sectors/fashion-accessories/the-rise-of-second-hand-shopping-in-australia-a-cultural-and-economic-shift-202502 ; https://ecommercenews.com.au/story/economic-pressures-lead-australians-to-embrace-secondhand-shopping ; https://ragtrader.com.au/news/86-of-australians-buy-second-hand-survey-reveals
- NapoleonCat Facebook users, Australia: https://stats.napoleoncat.com/facebook-users-in-australia/2026/06/
- US Census e-commerce: https://www.census.gov/retail/ecommerce.html
- ThredUp 2026 Resale Report: https://newsroom.thredup.com/news/thredup-14th-resale-report
- ONS retail sales, Oct 2025: https://www.ons.gov.uk/businessindustryandtrade/retailindustry/bulletins/retailsales/october2025
- European E-commerce Report: https://www.eurocommerce.eu/2025/09/new-growth-in-european-e-commerce-indicates-sectors-ability-to-adapt-and-reinvent ; https://handelsverband.swiss/?p=62881
- Commission Factory FAQ and BCF listing: https://www.commissionfactory.com/faq ; https://www.commissionfactory.com/my/advertiser-directory/bcf-affiliate-program/91580
- The Good Guys affiliate disclosure: https://commercial.thegoodguys.com.au/affiliates-commission-terms-and-conditions
- Amazon Associates AU schedule and 2023 cut: https://affiliate-program.amazon.com.au/help/node/topic/GRXPHT8U84RAYDXZ ; https://hellopartner.com/2023/06/13/amazon-drops-affiliate-commission-in-australia
- eBay Partner Network: https://ebaypartnernetwork.ebay.com/our-program/rate-card ; https://partnernetwork.ebay.com.au/resources/our-new-partner-platform ; https://www.authorityhacker.com/ebay-affiliate-program-review/
- Keepa pricing: https://revenuegeeks.com/keepa-pricing/
- Swoopa App Store listing: https://apps.apple.com/us/app/swoopa/id6475300269
- ShopSavvy: https://apps.apple.com/app/id338828953 ; https://shopsavvy.com/compare-prices
- CamelCamelCamel: https://softwareengineeringdaily.com/wp-content/uploads/2019/05/SED837-CamelCamelCamel.pdf
- ACCC comparator guidance: https://accc.gov.au/media-release/accc-releases-comparator-website-guidance ; https://www.accc.gov.au/system/files/CSBS%20-%20Comparator%20web%20sites%20project%20-%20Industry%20Guidance%20-%20final.pdf
- Honey: https://fortune.com/2024/12/23/honey-scam-browser-extension-mrbeast-mkbhd-linustechtips-megalag-expose-investigation-video/ ; https://www.moneymag.com.au/honey-browser-extension-accused-of-scamming-customers
- Klarna / PriceRunner: https://prnewswire.com/news-releases/klarna-acquires-pricerunner-to-strengthen-banking-offer-for-its-90m-global-consumers-301413788.html ; https://finextra.com/newsarticle/39130/klarna-acquires-price-comparison-site-pricerunner
- Little Birdie: https://techcrunch.com/2021/05/24/e-commerce-startup-little-birdie-lands-30m-aud-pre-launch-funding-from-australias-largest-bank ; https://www.startupdaily.net/topic/funding/fowl-play-cba-backed-ecommerce-site-little-birdie-shuts-down/
- Phia: https://www.globenewswire.com/news-release/2026/01/27/3226735/0/en/Phia-Raises-35M-Series-A-to-Build-the-AI-Alignment-Layer-for-Commerce.html ; https://techcrunch.com/2026/07/10/phia-accused-of-cookie-stuffing-taking-affiliate-credit-on-purchases-it-didnt-earn/ ; https://www.fmtc.co/affiliate-roundup-ebay-expands-affiliate-live-shopping-phia-suspended-google-labels-ai-ads-more/
- Daydream: https://techcrunch.com/2024/06/20/former-stitch-fix-coo-julie-bornstein-secures-50m-to-build-a-new-age-e-commerce-search-engine
- Beni: https://techcrunch.com/2022/12/13/beni-secondhand-shopping/ ; https://fashionunited.com/news/business/secondhand-browser-extension-beni-launches-ios-app-announces-new-partnerships/2024020658268
- OzBargain: https://www.ozbargain.com.au/wiki/help:stats_records ; https://www.ozbargain.com.au/wiki/help:advertise ; https://www.publift.com/case-studies/ozbargain
- CAR Group FY26: https://announcements.asx.com.au/asxpdf/20260810/pdf/072l1bhtmsqlrr.pdf ; https://cargroup.com/wp-content/uploads/2026/08/FY26-Annual-Report.pdf
- CarGurus FY2025: https://investors.cargurus.com/node/16966
- Adjust retention: https://www.adjust.com/blog/what-makes-a-good-retention-rate/ ; summary at https://www.getpanto.ai/blog/mobile-app-retention-statistics
