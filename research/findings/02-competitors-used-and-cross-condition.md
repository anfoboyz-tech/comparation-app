# Track 2 — Second-hand aggregators and new-versus-used comparison

Date of research: 2026-11-17.

## Read this first: limits of this track

Two constraints cut this track short, and they affect how much weight the conclusions can carry.

- **Page fetching was blocked.** Every direct page fetch (App Store, product sites) was refused by this session's network policy. Nothing below was confirmed by reading a primary page. Everything marked "search-verified" comes from search-result summaries of the cited URL.
- **The web search budget ran out.** The budget is shared by all eight agents and was exhausted after about 27 of my queries. Three planned queries never ran, and roughly a third of the checklist in the track prompt was not searched at all.

Each claim is therefore labelled one of three ways:

- **[S]** search-verified tonight, from a search summary of the cited URL.
- **[K]** from my background knowledge, not checked tonight. Treat as a lead, not a fact.
- **[N]** not checked.

The "absence" finding in question 5 rests on a limited set of searches. It is suggestive, not conclusive.

## 1. Bottom line

- **The exact product was not found.** I found no product that does new + used + local + shipped comparison with a buy verdict for general goods in Australia. Confidence: medium, because the search was cut short.
- **The gap is narrower than the founder probably assumes.** Since 2025 a cluster of small, mostly US, AI tools has appeared that score used general-goods listings as good deal / fair / overpriced: Grabbit (GrabScore), YrdSale, Spottable, Underpriced, DealFlip AI, PricePath and PriceScouter AI. Several cover Facebook Marketplace.
- **None of those tools was seen to compare against new retail prices.** They score against used comparables (other listings or eBay sold prices). None was confirmed to serve Australia.
- **Australian coverage of Facebook Marketplace and Gumtree does exist, but only in alert tools.** Swoopa (developer address in Brunswick, Victoria) and Classifindr monitor both and are aimed at resellers. They are not comparison or verdict products.
- **The best-funded new-plus-used product is fashion-only.** Phia raised a US$35.5M Series A in January 2026 and claims over 1.5M users. I found no evidence it covers general goods or Australia.
- **The verdict pattern is proven in vehicles.** Carsales Price Indicator and CarGurus deal ratings compare the asking price with a modelled market value. It works there because vehicles have a clean catalogue (make, model, year, odometer) and dense listing data, which fishing rods do not.
- **Platforms are moving on the seller side, not the buyer side.** Meta AI now suggests prices to sellers and is testing buyer-side AI insights with price information for vehicles only. I found no Gumtree or eBay Australia buyer-side price verdict.
- **The gap looks structural, not undiscovered.** The likely causes are data access (Facebook Marketplace and Gumtree have no public listings API that I know of), product matching for uncatalogued goods, and weak monetisation of local private sales. Whoever builds this has to solve those three, not just be first.

## 2. Findings

### Q1. Second-hand aggregators

| Product | Sources covered | FB Marketplace / Gumtree | Countries | Categories | Platform | Traction / model | Status |
|---|---|---|---|---|---|---|---|
| **Phia** | Retail plus resale sites; "nearly 10,000 retail brand partners" as of June 2026 [S] | Not seen [S] | US-centred [K] | Fashion (contemporary, resale, luxury); no evidence of electronics or furniture [S] | iOS app and mobile browser extension [S] | US$35.5M Series A in Jan 2026 at a US$185M valuation, US$43.5M total; over 1.5M users by June 2026 (company claims) [S]. Affiliate model [K] | Active 2026 [S] |
| **Beni** | 40+ resale marketplaces including Poshmark, ThredUp, Patagonia Worn Wear [S] | No [K] | US [K] | Fashion [S] | Chrome and Safari extension since 2021; iOS app Feb 2024 [S] | Claimed "nearly 80% of online resale listings" in Feb 2024 (vendor claim) [S] | Current status not checked [N] |
| **Gem** | "All resale sites and stores" for vintage and second-hand clothing [S] | Not seen | Not checked [N] | Vintage and second-hand clothing [S] | iOS app (Gem Search, LLC) [S] | No funding information found [S] | App Store listing exists [S] |
| **Faircado** | 70 partners, 10M+ products (vendor claim) [S] | Not seen | Europe-centred; top traffic Germany, US, UK, France, Netherlands [S] | General "pre-owned"; category detail unconfirmed [S] | Desktop extension for Chrome, Firefox, Edge, Safari [S] | Free; affiliate model [K] | Active; v3.8.12 released 23 Apr 2026 [S] |
| **Encore** | Poshmark, The RealReal, Grailed, Etsy, eBay [S] | No FB Marketplace listed [S] | US [K] | Mostly fashion and vintage [S] | Web; app was "in the works" in late 2024 [S] | Y Combinator Fall 2024; about US$500K reported, sources conflict [S] | 2026 status not checked [N] |
| **Croissant** | Guaranteed resale price on new items from 100+ retailers [S] | No | US [K] | Fashion | App and extension [S] | A different model (buy-back value), not an aggregator [S] | Not checked [N] |
| **Grabbit** | Facebook Marketplace, Craigslist, OfferUp, Depop, Mercari [S] | FB Marketplace yes; Gumtree not listed [S] | US mix of sources; Australia not seen [S] | General goods [S] | Web; native apps on the roadmap [S] | Indie founder (listed on TrustMRR); launch date unconfirmed [S] | Appears active [S] |
| **YrdSale** | ShopGoodwill, eBay, FB Marketplace, Craigslist, Mercari, OfferUp [S] | FB Marketplace yes; Gumtree no [S] | US sources [S] | General goods [S] | iOS [S] | Deal / fair / overpriced verdict; "Scout" assistant; downloads unknown [S] | Listed 2026 [S] |
| **FlowMarket** | eBay, Vinted, Wallapop, FB Marketplace and others [S] | FB Marketplace yes; Gumtree not listed [S] | 29 countries (own claim); Australia unconfirmed [S] | General [S] | Web [S] | Unknown | Appears active [S] |
| **GlobalSecondHand** | "Gumtree, eBay and more together" on its Australia guide page [S] | Gumtree claimed; FB Marketplace unknown [S] | Multi-country [S] | General | Web [S] | Operator unknown; may only link out [S] | Unknown |
| **Yarni.ai** | eBay, Etsy, partner sellers [S] | No [S] | Australia [S] | Fashion [S] | Web [S] | Unknown | Active 2026 (published a 2026 guide) [S] |
| **Swoopa** | FB Marketplace, Craigslist, OfferUp, Kijiji, Gumtree, Nextdoor, eBay [S] | Both claimed [S] | Multi-country; developer Market Sourcing Solutions, Brunswick VIC [S] | General, aimed at resellers [S] | iOS app [S] | Paid subscription; one reviewer cites about US$145 a month; reviews complain of alert delays [S] | Active [S] |
| **Classifindr** | FB Marketplace, Gumtree (AU and UK), Craigslist, Trade Me, Kijiji, OfferUp [S] | Both; states it reads public listing pages only [S] | AU, UK, NZ, US, CA [S] | Cars, tools, furniture, electronics, rentals [S] | iOS and web push [S] | Free listing; alerts by push, email, Discord, Telegram [S] | New; a high App Store ID suggests a 2026 launch (inference) |
| **Marketplace Monitor**, **DealScout**, **FlipSumo** | Marketplace alert tools [S] | FB Marketplace | Unknown | General | Apps | Reseller tools; detail not checked [N] | — |
| **Secondhand MCP** | FB Marketplace, eBay, Depop, Poshmark [S] | FB Marketplace yes, with a warning that it "may break if Facebook changes their frontend" [S] | eBay defaults to the US site [S] | General | Open-source developer tool for AI assistants [S] | Not a consumer product | Active on GitHub [S] |
| **Bountye** | "Search all secondhand sites in one place" plus its own marketplace [S] | Unknown | Australia [S] | General | App [S] | Founded 2015 by a former eBay director; about A$1.2M raised; 4.9% commission [S] | No recent evidence found; likely defunct (inference) |
| **SearchTempest** | Craigslist plus optional eBay [S] | Not a source [S] | US-centred | General | Web | Long-running; ads [K] | Active [S] |
| **PicClick** | eBay only, visual search [K] | No | Multi-country | General | Web | eBay affiliate [K] | Not checked [N] |
| **Bidbud, Lykdat, Used.com.au-style sites** | — | — | — | — | — | — | Not checked [N] |

Patterns across the table:

- **Funded aggregators are fashion.** Phia, Beni, Gem, Encore, Croissant and Yarni are all fashion or vintage clothing. Confidence: high.
- **Fashion is structurally easier.** Those products draw on marketplaces that offer affiliate feeds and shipped inventory (Poshmark, ThredUp, The RealReal, eBay). That is why they avoid Facebook Marketplace.
- **Facebook Marketplace coverage sits with small tools.** It appears in indie or reseller tools (Grabbit, YrdSale, Swoopa, Classifindr, Spottable, Secondhand MCP), apparently by reading public pages. Classifindr and Secondhand MCP say as much.
- **Gumtree Australia coverage was seen in three places only:** Swoopa, Classifindr and GlobalSecondHand's claim.
- **There is one failed Australian precedent.** Bountye pitched "search all secondhand sites in one place" in 2015. Why it faded was not established tonight.

### Q2. New versus used in one view

| Product | Shows new price beside used? | Scope | Notes |
|---|---|---|---|
| **Phia** | Yes. Its "price check" compares the item being viewed with real-time retail and second-hand prices [S] | Fashion, US | The closest existing product to the founder's concept, in a different vertical |
| **Beni, Faircado** | Partly. They show second-hand alternatives while the user browses a new item on a retail site [S] | Fashion (Beni); broader, Europe (Faircado) | The new price is the page the user is already on |
| **Croissant** | Shows a guaranteed future resale value on a new item [S] | Fashion | The inverse framing: what the new item will be worth later |
| **Carsales / RedBook** | Used valuation against a modelled market, including RedBook residual values [S] | Vehicles, Australia | See question 3 |
| **Reverb Price Guide** | No. Used and vintage sold prices only [S] | Music gear | Estimated range and average sale price by exact model and condition |
| **Swappa** | Publishes blog comparisons (used runs "30 to 60% below new retail") and average sale prices [S] | Phones and tech, US | New price is not a live part of the product, as far as seen |
| **Bicycle Blue Book** | Trade-in and market value from a machine-learning model over "millions of transactions" [S] | Bikes, US | Says it cannot value rare or vintage bikes |
| **Amazon "new & used" offers** | Yes, on the same product page [K] | Catalogue goods | Depth of used offers on Amazon Australia not checked [N] |
| **Back Market, Reebelo** | Refurbished price shown against a struck-through new price [K] | Electronics; both operate in Australia [K] | Not checked tonight [N] |
| **StockX, Chrono24, PriceCharting, camera price guides, Cash Converters, BikeExchange, Google Shopping used filter** | — | — | Not checked [N]. A search on Google's AI shopping in Australia returned nothing about a used-condition filter [S] |

Two points follow:

- **New-beside-used exists where there is a catalogue.** Phones, sneakers, vehicles, music gear and fashion SKUs all have a stable identifier to match on.
- **No general-goods example was found.** I saw nothing that does this for uncatalogued goods sold locally.

### Q3. Fair-price and verdict tools

| Product | Verdict | How computed | Scope |
|---|---|---|---|
| **Carsales Price Indicator** | Around / Below / Well Below Market Price; no tag means above average [S] | Listed price against the market average of similar cars on Carsales, using RedBook LiveMarket data and live listings [S] | Cars under 15 years old, priced $5,000–$70,000; excludes write-offs and hail damage; ignores options, condition and service history; exact thresholds unpublished [S] |
| **RedBook Real Time Valuation** | Retail and wholesale values [S] | Adjusted for kilometres, margin and condition (As New to Poor) [S] | Business API |
| **CarGurus** | Great / Good / Fair / High / Overpriced [S] | Asking price against Instant Market Value, modelled from comparable current and past listings, plus dealer reputation; statistical outliers flagged [S] | Not in Australia [K]. Based on asking prices, not sold prices [S] |
| **Grabbit GrabScore** | 0–100 plus Great Deal / Good / Fair / Poor [S] | Compares similar products across supported marketplaces, matching on model, storage and condition; warns that niche items have less data [S] | Used general goods, US sources |
| **YrdSale** | Deal / fair price / overpriced [S] | "Comparable sales"; data source not disclosed [S] | Six US marketplaces; can analyse a listing shared from Safari or Facebook [S] |
| **Spottable** | Deal score 1–10, suggested fair price, scam flags [S] | "Market comps"; source not disclosed [S] | FB Marketplace; iOS and Chrome extension. From US$4.99 a month. The extension has about 198 users and 6 ratings [S] |
| **Underpriced** | HOT DEAL / GOOD DEAL / FAIR / PASS [S] | Photo identification plus eBay sold listings [S] | Reseller-focused; has a "Facebook Marketplace Analyzer for Flippers" [S] |
| **PricePath, PriceScouter AI, DealFlip AI, AI Thrift, Snag AI** | Similar verdict labels [S] | Not checked [N] | Small indie apps, 2025–26 |
| **Apify "Facebook Marketplace AI Deal Finder"** | Flags underpriced listings [S] | FB Marketplace price against eBay sold prices [S] | Developer tool; rated 1.1 from 2 reviews [S] |
| **Facebook Marketplace** | Price suggestion to sellers "based on similar items in the area" (March 2026); buyer-side AI insights with price information being tested on vehicle listings (Nov 2025) [S] | Meta's own listing data | No buyer-side verdict found for non-vehicle goods [S] |
| **Gumtree Australia** | Launched a mobile-phone price checker in 2014 based on average asking prices [S] | Its own ads | 2026 news is an AI customer-support agent only [S] |
| **eBay** | Seller research tools show average sold price, range and trends by condition [S] | eBay sold data | Its AI shopping agent launched May 2025 for a small share of US users [S] |
| **WorthPoint, Flipsy, Decluttr, Mercari and Depop suggestions** | — | — | Not checked [N] |

What the verdict tools have in common:

- **They are a 2025–26 development.** Large language models have made "paste a listing, get a verdict" cheap to build, which is why so many have appeared at once.
- **They are aimed at resellers.** Most answer "can I flip this for profit?", not "should I buy this to keep?".
- **They compare used against used.** None was seen to use the new retail price as an input.
- **Their methods are opaque and traction is tiny.** No independent accuracy test was found for any of them.

### Q4. Marketplace-side moves, 2025–2026

**Meta**
- Nov 2025: Marketplace refresh with collaborative buying, Meta AI suggested questions for buyers, and a test of AI vehicle insights that include price information [S].
- March 2026: Meta AI drafts listings, suggests a price from similar local items, and auto-replies to buyers [S].
- The effort is aimed at sellers. Nothing was found comparing against new retail prices.

**eBay and Meta**
- A pilot shows selected eBay listings inside Facebook Marketplace in the US, Germany and France, with checkout on eBay [S]. It began in January 2025 as part of Meta's EU antitrust remedy [K].
- No report of an Australian rollout was found [S]. The follow-up search on expansion did not run [N].

**eBay**
- A May 2026 article reports eBay Australia dropped selling fees for casual sellers, framed as a response to Facebook Marketplace [S].
- eBay Live launched in Australia [S].
- eBay reportedly banned third-party autonomous AI buying agents in February 2026 [S]. That matters to any product that wants to transact on eBay on a user's behalf.

**Gumtree Australia**
- ASX-listed as GUM with a market capitalisation of about A$58M [S].
- 2026 news is limited to an AI help agent [S]. It is a small company with limited capacity to close this gap itself (inference).

**Google and OpenAI**
- Gemini shopping and agentic checkout are live in Australia with Bunnings, Kogan, Petbarn, The Iconic and Adore Beauty [S].
- ChatGPT shopping research launched in November 2025 [S].
- Both cover new retail. Neither was seen to include Facebook Marketplace or Gumtree listings [S].
- The implication is that the new-price half of the founder's product is being absorbed by general AI assistants, while the local-used half is not.

**Others**
- Vinted launched in Australia with an Australia Post arrangement [S]. That adds another used-goods source, in fashion.
- Amazon Australia was not checked [N].

### Q5. Is there a general-goods product doing new + used + local + shipped + verdict?

Not found. The nearest neighbours each miss part of it:

| Nearest neighbour | What it has | What it lacks |
|---|---|---|
| Phia | New + used + price check; funded; mobile | General goods, local pickup, Australia |
| Grabbit, YrdSale | Used aggregation across FB Marketplace and others, general goods, verdict | New retail comparison, Australia and Gumtree; Grabbit has no native app |
| Swoopa, Classifindr | FB Marketplace + Gumtree Australia coverage, general goods | Comparison, new prices, verdict (Swoopa has some AI price filters) |
| Carsales | Verdict against market in Australia | Anything beyond vehicles |
| Gemini, ChatGPT shopping | New retail comparison in Australia, conversational | Local second-hand listings |

**Searches that ran** (all on 2026-11-17):

- app search Facebook Marketplace Gumtree eBay at once Australia second hand aggregator
- Beni Phia Gem Faircado Croissant Encore comparison 2026
- Swoopa app Facebook Marketplace Gumtree alerts Australia
- app compares new price vs used listings "is it a good deal" second hand general goods AI
- eBay listings on Facebook Marketplace partnership Australia 2025 2026
- Grabbit / GrabScore
- YrdSale
- Classifindr
- Phia funding and categories beyond fashion
- Gem vintage search
- Faircado 2026
- Bountye Australia
- Spottable deal score
- Facebook Marketplace Meta AI 2026 price insights
- Gumtree Australia 2026 AI price guide
- eBay AI shopping agent, sold comparison, new vs used
- Google Shopping used filter Australia / Gemini
- ChatGPT shopping research used listings
- Carsales Price Indicator / RedBook
- CarGurus Instant Market Value
- Underpriced AI Facebook Marketplace analyser Australia
- SearchTempest / PicClick / Bidbud / Lykdat / Encore
- Encore funding
- Australian startup compare second hand prices Gumtree Facebook Marketplace eBay "one search" 2025–2026 (extended mode)
- used.com.au / second-hand price guide Australia
- Reverb / Swappa / Bicycle Blue Book

**Searches that did not run** because the budget was exhausted:

- Back Market / Reebelo "vs new"
- Amazon Australia used and Renewed
- eBay–Facebook pilot expansion
- App Store and Google Play Australia keyword searches
- StockX, Chrono24, PriceCharting, camera price guides, Cash Converters, BikeExchange
- WorthPoint, Flipsy, Decluttr, Mercari and Depop pricing
- Product Hunt and Reddit sweeps for Australian indie launches
- Japanese and European equivalents

The absence is credible for a funded, visible product: one would have surfaced in the Australia-specific extended search. It is not credible for an indie app launched in the last few months. This space is producing new small apps monthly.

### Q6. Why the gap exists (inference from the evidence)

1. **Data access is the main barrier.**
   - Facebook Marketplace and Gumtree offer no public listings API [K].
   - Every tool seen covering them reads public pages. Classifindr says so, and Secondhand MCP warns it breaks when Facebook changes its front end [S].
   - Funded companies avoid that risk. Fashion aggregators use affiliate feeds from marketplaces that want traffic.
   - Confidence: medium-high.
2. **Product matching is hard without a catalogue.**
   - Verdicts work where a catalogue exists: vehicles (Carsales, RedBook), phones (Swappa), music gear (Reverb), bikes (Bicycle Blue Book).
   - These tools exclude or warn on thin data: Carsales skips older and unusual cars, Bicycle Blue Book skips vintage bikes, GrabScore warns on niche categories [S].
   - A "used Shimano rod and reel combo" with a vague title and no model number is the hard case.
   - Confidence: high.
3. **Monetisation is weak for local used goods.**
   - A cash pickup on Facebook Marketplace or Gumtree pays no affiliate commission.
   - The tools that do cover Facebook Marketplace charge resellers a subscription (Swoopa, Spottable) because resellers have a profit motive.
   - A consumer buying one fishing rod does not have that motive.
   - Confidence: medium.
4. **The buy-to-keep consumer use is infrequent.** Every verdict tool found targets flippers, who use it daily. That suggests builders have not found consumer retention. Confidence: low-medium (inference only).
5. **The market is small.** A dedicated Australian product has a small addressable market compared with the US, and the one prior local attempt (Bountye, 2015) faded.

## 3. Implications for the product

**Positioning**
- "Nobody has done this" is not a safe pitch. The accurate claim is narrower: nobody has combined used aggregation, a new-price baseline and a verdict for general goods in Australia.
- Expect any of Grabbit, YrdSale, Spottable or Swoopa to add the missing piece quickly. The parts are cheap to build.
- The defensible assets are Australian data: Gumtree and Facebook Marketplace coverage, and Australian retailer prices from BCF, Anaconda, Bunnings and similar.

**What to build first**
- The new-price baseline is the least contested piece. No used-deal tool seen uses it, and it is the founder's actual pain (the 50–100 minutes).
- "Paste or share a listing, get the new price, typical used price and a verdict" avoids the hardest data-access problem. The user brings the listing; the app does not need to crawl Marketplace.
- YrdSale and Spottable already use this share-a-listing pattern [S].
- Full cross-marketplace search is the risky part. It depends on reading Facebook Marketplace pages, which is fragile, and its legal position belongs to another track.

**How to compute the verdict**
- Copy the vehicle pattern. Carsales and CarGurus publish a label, a market reference and explicit exclusions where data is thin.
- Say "not enough data" when that is true, as they do.
- Start in categories with model numbers (power tools, electronics, fishing reels with model names, bikes), where matching is tractable.

**Revenue**
- Affiliate commission on the "buy new instead" outcome is the obvious revenue line. The used side pays nothing.
- That creates an incentive to steer users towards new. The verdict's credibility depends on resisting it.

**Competitive pressure**
- General AI assistants (Gemini with Australian retailers, ChatGPT shopping) will commoditise new-price lookup. The lasting value has to be in the local-used side and the verdict.
- Do not target resellers. That segment is crowded with subscription tools.

## 4. Open questions

1. **Is there an Australian indie app already doing this?** App Store and Google Play Australia keyword searches were not run. Settle it by searching both stores for "compare second hand prices", "used price checker", "marketplace search all" and "is it a good deal".
2. **Do Grabbit, YrdSale, Spottable or Underpriced work on Australian listings today?** Do any show a new retail price? Settle it by installing each and testing with a Gumtree or Facebook Marketplace Australia listing.
3. **What can Swoopa's AI price filters actually do, and what does it cost in AUD?** It is the most likely local competitor to extend into this. Check its site and the Australian App Store listing.
4. **Has the eBay-in-Facebook-Marketplace pilot expanded beyond the US, Germany and France?** Check eBay and Meta newsroom posts.
5. **Why did Bountye fail?** Look for a founder post-mortem or ask Asim Brown directly.
6. **What is the status of the unchecked items?** This covers Beni, Encore and Croissant's current state, and Bidbud, Lykdat, PicClick, Back Market, Reebelo, StockX, Chrono24, PriceCharting, Cash Converters, WorthPoint, Flipsy, Decluttr, Amazon Australia used offers and the Google Shopping used filter.
7. **How accurate are the AI deal scores?** No independent test was found. A 20-listing hand test would show how high the bar is.

Open questions 1 to 3 can be settled in about an hour with a phone. They should be done before a build decision.

## 5. Sources

All accessed through search summaries on 2026-11-17. Pages were not fetched directly.

**Aggregators and resale search**
- Grabbit: https://www.grabbit.app/about · https://grabbit.app/grabscore · https://trustmrr.com/founder/grabbitsearch · https://www.producthunt.com/products/grabbit-3
- YrdSale: https://mwm.ai/apps/yrdsale/6759308082
- Phia: https://apps.apple.com/us/app/phia-shop-smarter-save-money/id6739351340 · https://www.globenewswire.com/news-release/2026/01/27/3226735/0/en/Phia-Raises-35M-Series-A-to-Build-the-AI-Alignment-Layer-for-Commerce.html · https://pulse2.com/phia-35-million-series-a/ · https://parsers.vc/news/260702-phia-s-ai-shopping-revolution--celebrity/ · https://www.trendhunter.com/trends/phia-app
- Beni: https://prnewswire.com/news-releases/first-of-its-kind-beni-dominates-resale-marketplace-with-innovative-app-and-new-partnerships-with-poshmark-patagonia-wornwear-thredup-and-treet-302054761.html · https://www.retailtouchpoints.com/topics/digital-commerce/resale-aggregator-platform-beni-debuts-ios-app-adds-poshmark-thredup-and-more
- Gem: https://apps.apple.com/us/app/-/id1459900557
- Faircado: https://faircado.com/tssh · https://faircado.com/tz7w · https://addons.mozilla.org/en-US/firefox/addon/faircado-second-hand-first
- Encore: https://techcrunch.com/2024/11/10/encore-is-an-ai-powered-search-engine-for-your-thrifting-needs · https://www.ycombinator.com/launches/MDc-encore-the-perplexity-for-online-shopping · https://www.vcbacked.co/company/encore-san-francisco
- Croissant: https://businessoffashion.com/articles/technology/croissant-resale-fintech/
- Fashion aggregator overview: https://circularfashionnews.substack.com/p/search-engines-for-secondhand-fashion
- FlowMarket: https://flow-market.org/
- GlobalSecondHand: https://www.globalsecondhand.com/guide/secondhand-australia
- Yarni: https://yarni.ai/blog/best-second-hand-fashion-marketplaces-australia
- Secondhand MCP: https://github.com/jlsookiki/secondhand-mcp · https://mcpservers.org/servers/jlsookiki/secondhand-mcp
- Bountye: https://www.ellaslist.com.au/sydney/directory/services/bountye-search-all-secondhand-sites-in-one-place · https://www.smartcompany.com.au/startupsmart/bountye-brings-the-op-shop-into-the-digital-age/ · https://www.tweaktown.com/pressrelease/9382/aussies-buy-better-bountye/index.html
- SearchTempest: https://alternativeto.net/software/searchtempest

**Alert and reseller tools**
- Swoopa: https://apps.apple.com/us/app/swoopa/id6475300269 · https://getswoopa.com/tools-to-automate-facebook-marketplace-alerts
- Classifindr: https://apps.apple.com/app/classifindr/id6764547369 · https://startupa.ge/classifindr
- Marketplace Monitor: https://apps.apple.com/us/app/-/id6491068401

**Verdict tools**
- Spottable: https://apps.apple.com/app/id6758812746 · https://chromewebstore.google.com/detail/dbgjphnanjmmfjacahfhliahblokmpgh · https://spottable-lp.pages.dev/blog/ai-deal-scoring-explained
- Underpriced: https://apps.apple.com/us/app/underpriced/id6759008101 · https://www.underpriced.app/marketplace-analyzer · https://www.underpricedai.com/
- DealFlip AI: https://apps.apple.com/us/app/id6756501597
- PriceScouter AI: https://www.producthunt.com/p/pricescouter-ai/pricescouter-ai-2
- Apify deal finder: https://apify.com/webdatalabs/facebook-marketplace-deal-finder
- Carsales: https://help.carsales.com.au/hc/en-gb/articles/360015482932-carsales-Price-Indicators-FAQs · https://www.carsales.com.au/editorial/details/carsales-price-indicator-gives-car-buyers-confidence-115213 · https://business.carsales.com.au/news-room/introducing-real-time-used-car-valuations/
- CarGurus: https://cargurus.helpscoutdocs.com/article/10-what-is-imv · https://www.cargurus.com/Cars/developers/docs/InstantMarketValue.html · https://www.cargurus.com/about/how-cargurus-works
- Reverb: https://reverb.com/news/how-to-use-the-reverb-price-guide
- Swappa: https://swappa.com/blog/new-vs-used-electronics-savings/
- Bicycle Blue Book: https://www.bicyclebluebook.com/article/about-value-guide/
- Gumtree phone price checker (2014): https://www.bandt.com.au/gumtree-australia-launches-mobile-phone-price-checker-tool/

**Marketplace and platform moves**
- Meta: https://about.fb.com/news/2025/11/facebook-marketplace-gets-a-glow-up/amp/ · https://about.fb.com/news/2026/03/facebook-marketplace-new-meta-ai-tools-make-selling-faster-and-easier/amp/ · https://techcrunch.com/2025/11/13/facebook-marketplace-gets-new-collaborative-and-social-features-meta-ai-integrations · https://techcrunch.com/2026/03/12/facebook-marketplace-now-lets-meta-ai-respond-to-buyers-messages · https://www.pymnts.com/meta/2026/meta-ai-writes-listings-and-sets-prices-for-facebook-marketplace-sellers/
- eBay and Meta pilot: https://valueaddedresource.net/ebay-facebook-marketplace-partnership · https://thenightly.com.au/society/technology/meta-tries-letting-facebook-marketplace-users-view-ebay-listings-as-way-to-resolve-eu-charges-c-17348083
- eBay Australia fees: https://eftm.com/2026/05/ebay-australia-has-dropped-fees-for-casual-sellers-clean-out-and-clean-up-without-any-fees-275988
- eBay agent: https://www.fortune.com/2025/05/06/ebay-ai-agent · https://blog.vendoo.co/ebay-price-guide
- Gumtree: https://smartcompany.com.au/partner-content/gumtree-turns-to-ai-agent-to-answer-customer-questions-around-the-clock · https://simplywall.st/stocks/au/media/asx-mkt/market-shares/valuation
- Google: https://www.channelnews.com.au/google-taps-aussie-retailers-for-ai-shopping-checkout-launch/ · https://support.google.com/gemini/answer/16730149
- ChatGPT shopping research: https://help.openai.com/en/articles/11128490-chatgpt-shopping-research · https://www.modernretail.co/technology/openais-new-chatgpt-shopping-tool-promises-in-depth-research-just-not-for-amazon-products/
- Vinted Australia: https://www.just-style.com/news/vinted-australia-launch-secondhand/
