# Second pass — competitors (tracks 1, 2 and 8 §2.2)

Date read: 2026-11-17 for every source below. Pages were read directly with `curl` unless marked otherwise. Web searches used: 18 of 25.

Status labels: **confirmed** (read at the source), **corrected** (the source says something different), **unverified** (could not be read; reason given).

Limits that still apply:

- Nothing was installed or run. Every claim about what an app does comes from its own store listing or website, not from a test on an Australian listing.
- App Store prices are from the Australian store and are in AUD. Prices quoted from product websites are in USD.
- Four sites refused automated requests and were left alone: grabbit.app, producthunt.com, buywisely.com.au (all Cloudflare challenge) and help.openai.com / openai.com (HTTP 403).

---

## 1. What changed

**1. The central claim does not survive in its strict form.** The first pass said no verdict tool "was seen to compare against new retail prices". Two products do, by their own descriptions.

- **Deal Scout** (Chrome extension). On a specific Facebook Marketplace, Craigslist, OfferUp or eBay listing it shows a "BUY / CAUTION / AVOID verdict with score", a "Market comparison — sold avg, active listings, new retail price", and "Shows where to buy new if the used price isn't worth the risk". Free, no account. 36 users, 2 ratings, updated 15 October 2026. Australia is not mentioned; the benchmark is eBay sold prices and the retail cards are "Amazon, eBay, and more".
- **PriceSnap** (pricesnap.ai; Android app and web, iPhone "coming soon"). "Paste the listing link or describe the item, then type the asking price" and it returns Great / Good / Fair / Pricey, an offer and a walk-away price. Each result also has a "Where to buy" module of "current retail offers from distinct retailers ... cheapest first". It lists an AUD / Australia market. Google Play shows 1K+ downloads, updated 2 November 2026. Developer is AI Apps Limited, Isle of Man. For a used item the verdict is computed against used sold and asking prices; the retail offers are shown beside it, not used in it ("Retail offers are not comps and never feed the resale estimate").

What is still true: neither is an Australian product, neither names an Australian retailer or Gumtree, and neither has visible traction. Whether either returns correct Australian new prices for, say, a fishing reel is untested. The defensible wording is now: **no product with meaningful traction, and none built on Australian retailer prices, does this. The feature itself already exists.**

**2. One of the "US" verdict tools is from Sydney and serves Australia.** Spottable is "An app by Harbourside Apps", "Harbourside Apps Pty Ltd, Sydney, NSW", and its home page lists "US · UK · CA · AU · NZ · IE +more". It gives a deal verdict on Facebook Marketplace listings from "comparable Marketplace evidence" (other asking prices). It does not show a new retail price. Traction is small: 6 ratings (3.0) on the Australian App Store, 966 Chrome users.

**3. Australian stores already carry buyer-facing "is this used price fair" apps the first pass did not find.** All are tiny.

- **PriceVet** (Chrome): "Real-time price comparison for Facebook Marketplace. See how eBay AU prices compare. Built for NZ & AU buyers", with a "Deal Score from A (great deal) to F (overpriced)". No ratings.
- **Price Snap** by Adem Cilgin (iOS, a different product from PriceSnap above): Australian-localised listing, "See both the retail price and realistic secondhand value", aimed at people who have "scrolled Gumtree not knowing if a price is fair". Works from a photo, not a listing. No ratings shown in the Australian store.
- **PricePath** (iOS, in the Australian store): "Built for thoughtful buyers who want fair deals", which is the buy-to-keep positioning the first pass said nobody had taken. No ratings; last updated 29 May 2026.

**4. Nobody in this cluster has users.** Read at source: Grabbit's verified lifetime revenue on TrustMRR is US$30 with $0 monthly recurring revenue. YrdSale, PricePath and DealFlip AI have too few Australian ratings to display. Spottable has 6, Underpriced 2, Classifindr 2, Deal Scout 36 users. This strengthens the first pass's "opening or warning" point, and tilts it toward warning: the feature has been shipped at least a dozen times without finding an audience.

**5. Swoopa is no longer a general reseller tool.** Its Australian App Store listing now reads "Swoopa helps dealers find, evaluate, and acquire profitable private-party vehicles". General goods are a footnote. Plans are A$69 to A$229.99 a month (one in-app purchase is A$499). It is less likely to move into consumer fair-price checks than the first pass assumed.

**6. Meta: no buyer-facing price rating outside vehicles, and Muse is not in Australia.** Meta's own November 2025 post confirms price insights only for vehicle listings, as a test, in a post framed around the US and Canada. The March 2026 post is seller-side only. Muse is real (launched 8 September 2026, "rolling out in the US"; Singapore added 27 October 2026). Meta's launch post does not mention Marketplace at all, so the first-pass line that Muse "can watch Marketplace for a specific item" is not supported by Meta's own page.

**7. Google is live in Australia; the retailer list is not confirmed by Google.** Google's help pages confirm Gemini shopping in Australia and agentic checkout "only available in the US and Australia". The five retailer names come from one trade article dated 18 June 2026, which says the checkout "will soon launch with" them. No Google Australia post naming them was found.

**8. Little Birdie published no closure date and no reason.** Its site now shows only a goodbye notice. The 8 September 2025 date belongs to Cashrewards.

---

## 2. Claim table

### 2.1 Verdict tools

| Tool | Works on Australian listings? | Shows new retail price? | How the verdict is computed | Price | Ratings (AU store) | Last update | Status of first-pass claims |
|---|---|---|---|---|---|---|---|
| **Grabbit** | Not established. Search summary of its Product Hunt page says "currently available for US searches" | Not established | Not readable | Free; "Plus" tier | No app | Not readable | **Unverified.** grabbit.app and Product Hunt both returned a Cloudflare challenge. New fact, confirmed at TrustMRR: total verified revenue US$30, MRR $0 |
| **YrdSale** | App is in the Australian store. Marketplaces are US: "ShopGoodwill, eBay, Facebook Marketplace, Craigslist, Mercari, and OfferUp". No Gumtree | Not as a stated feature. Since v2.1 (12 June 2026) "Scout can now look up product specs, reviews, and real market prices — with tappable sources" | "Checks prices against comparable sales and tells you if you're looking at a deal, a fair price, or something overpriced". Source undisclosed | A$7.99 and A$14.99 in-app purchases | Too few to display | v2.9, 11 Oct 2026 | **Confirmed**, with the web-search addition |
| **Spottable** | **Yes, by its own claim**: "US · UK · CA · AU · NZ · IE +more". Facebook Marketplace only. Sydney developer | No. "typical price" is from other Marketplace listings | "Price conclusions require supplied Marketplace comparables. Spottable uses the middle half of those observed asking prices as the typical range ... It does not claim those items sold for that amount." Says nothing when comparables are too few. Score is 1–10 | Site: from US$4.99/month. AU store: A$7.99, A$22.99, A$49.99 monthly. Chrome: 3 free analyses a day | 6 ratings, 3.0 | v1.5.0, 20 Sept 2026 | **Corrected.** First pass: US-centred, "source not disclosed", about 198 Chrome users. Source: Sydney company, method published, 966 Chrome users (4.3 from 6 ratings) |
| **Underpriced** | Partly. Australian listing is localised ("Op Shop & Garage Sale Prices"); works from a screenshot, so any marketplace. "Comparable-listing availability varies by item, marketplace, region, and plan" | No | "Screenshot the listing. Underpriced identifies the item, checks what it sells for on eBay, and shows your profit after fees". Verdict is "Flip It, Potential Flip, or Pass" with a 0–100 score | A$14.99 to A$39.99 a month; site says from US$9.99 | 2 ratings, 5.0 | v2.0.28, about 15 Nov 2026 | **Confirmed** as reseller-focused and eBay-sold based. **Corrected** on labels (first pass: HOT DEAL / GOOD DEAL / FAIR / PASS) |
| **DealRater.ai** | Not stated. Chrome extension on Facebook Marketplace pages | No | "1-100 score"; "fair offer range based on mileage, age, and market comps". Examples are vehicles | Free 5 a month; US$9.99; US$29.99 | No mobile app | Not captured | **Confirmed** as existing; method detail is new |
| **PricePath** | In the Australian store. "Facebook Marketplace, Craigslist, OfferUp, and any peer-to-peer listing"; user pastes the listing | No mention | "A clear verdict — solid deal, worth negotiating, overpriced, or walk away"; "Target price and walkaway price based on real market value". Source undisclosed | A$22.99 a month, A$119.99 six months, A$199.99 a year, 10 analyses A$12.99 | Too few to display | v1.0.1, 29 May 2026 | First pass had it as "not checked". Now **confirmed** from the listing. Positioned at buyers, not flippers |
| **Swoopa** | Yes for alerts. Site: "instant Marketplace alerts from Facebook, Craigslist, OfferUp, Kijiji, Gumtree, Nextdoor, and eBay". Australian company (Market Sourcing Solutions Pty Ltd) | No. For vehicles it shows "retail, private-party, and trade-in pricing" | "AI Price Filter compares asking prices to estimated market values", hiding low-margin listings. Vehicle-focused | A$69, A$129, A$229.99 a month; one item at A$499 | 34 ratings, 4.6 (site claims "600 App Store Reviews") | v1.37.3, about 14 Nov 2026 | **Corrected.** First pass: general reseller alert tool. Source: now pitched at car dealers; general goods are an aside ("Swoopa alerts also work for anything") |
| **Classifindr** | Yes: "Gumtree AU and UK", Facebook Marketplace, eBay, Trade Me and others. Seller is Cloudridge Technologies Pty Ltd | No | No verdict. Alerts with keyword and "AI relevance" filters only | Free to start; unit-based paid plans; 7-day trial | 2 ratings, 5.0 | v1.1.7, 12 Sept 2026; v1.0 on 7 May 2026 | **Confirmed**, including the 2026 launch the first pass inferred |
| **DealFlip AI** | In the Australian store; user provides a listing | No | "fair market value based on pricing trends, condition, and comparable listings" | A$22.99, A$49.99, A$79.99 | Too few to display | v1.3, 14 July 2026 | First pass "not checked"; now **confirmed** from the listing |

Sources: https://apps.apple.com/au/app/yrdsale/id6759308082 · https://yrdsale.ai/ · https://apps.apple.com/au/app/id6758812746 · https://spottableapp.com/ · https://spottableapp.com/blog/ai-deal-scoring-explained/ · https://spottableapp.com/pricing/ · https://harboursideapps.com/ · https://chromewebstore.google.com/detail/spottable-ai/dbgjphnanjmmfjacahfhliahblokmpgh · https://apps.apple.com/au/app/underpriced/id6759008101 · https://www.underpriced.app/marketplace-analyzer · https://dealrater.ai/ · https://apps.apple.com/au/app/id6770200483 · https://apps.apple.com/au/app/swoopa/id6475300269 · https://getswoopa.com/ · https://getswoopa.com/pricing/ · https://apps.apple.com/au/app/classifindr/id6764547369 · https://classifindr.com/ · https://apps.apple.com/au/app/id6756501597 · https://trustmrr.com/founder/grabbitsearch

### 2.2 Other claims

| Claim | First-pass file | Status | What the source says | URL |
|---|---|---|---|---|
| No verdict tool compares against new retail prices | 02 (§1, Q3); morning brief | **Corrected** | Deal Scout: "Market comparison — sold avg, active listings, new retail price" and "Shows where to buy new if the used price isn't worth the risk". PriceSnap: retail offers shown "separately in the 'Where to buy' module, cheapest first" beside an asking-price verdict | https://chromewebstore.google.com/detail/mbkhagpggkmefaompfjkbbnbmmameapk · https://www.pricesnap.ai/is-this-a-good-deal · https://www.pricesnap.ai/how-pricesnap-works |
| None of the verdict tools was confirmed to serve Australia | 02 §1 | **Corrected** | Spottable lists AU and is built in Sydney. PriceVet is "Built for NZ & AU buyers". PriceSnap lists "AUD Australia" | https://spottableapp.com/ · https://chromewebstore.google.com/detail/ipaiccoeoohhpjbljjigldemjhcecblp · https://www.pricesnap.ai/compare-prices |
| Verdict tools are aimed at resellers | 02 Q3 | **Partly corrected** | True for Underpriced, Swoopa, DealFlip AI, ThriftCheck. Not true for PricePath ("thoughtful buyers who want fair deals, not lowball wars"), DealUp AI, Deal Scout, PriceSnap's deal checker ("Smart shoppers") | listings above |
| Verdict tools' methods are opaque | 02 Q3 | **Partly corrected** | Spottable and PriceSnap publish their method and their "can't judge" rules. YrdSale, PricePath, DealFlip AI do not | as above |
| Meta shows buyers AI price information on vehicle listings only, as a test | 02 Q3–Q4; 08 §2.2 | **Confirmed** | "we're beginning to test a new AI-powered feature designed to make buying cars easier ... When you visit a vehicle listing, you'll see AI-powered insights that can gather everything from engine options and safety ratings to ... reviews, and price insights". For other goods the only buyer feature is "Suggested questions to ask". The post cites US and Canada usage and gives no country list | https://about.fb.com/news/2025/11/facebook-marketplace-gets-a-glow-up/ |
| Meta AI suggests a price to sellers (March 2026) | 02 Q4; 08 | **Confirmed** | "suggesting a price based on similar items listed in your area". Nothing buyer-facing on price. Context given is "the US and Canada" | https://about.fb.com/news/2026/03/facebook-marketplace-new-meta-ai-tools-make-selling-faster-and-easier/ |
| Any buyer-facing price rating on non-vehicle Marketplace listings, anywhere | — | **Not found** | Neither Meta post describes one. One search of news coverage found none | as above |
| eBay listings appear inside Facebook Marketplace | 02 Q4 | **Confirmed for the US** | "Earlier this year, we began integrating eBay inventory into Marketplace followed by Poshmark". US figures only; Australia not mentioned | Nov 2025 post above |
| Muse launched in the US on 8 September 2026 | 08 §2.2 | **Confirmed** | Post dated September 8, 2026: "Muse is rolling out in the US on iOS, Android, and muse.ai" | https://about.fb.com/news/2026/09/introducing-muse-personal-ai-agent/ |
| Muse can watch Marketplace for a specific item | 08 §2.2 | **Not supported by Meta's post** | The launch post does not contain the word "Marketplace". It does say Muse can "negotiate on their behalf" and cites "selling a car for more" | same |
| Muse availability in Australia | 08 §2.2 | **Confirmed as not announced** | Only expansion post found is Singapore, 27 October 2026. No Australian post on the newsroom; secondary sources say no Australian date | https://about.fb.com/news/2026/10/muse-is-now-available-in-singapore-the-worlds-first-personal-ai-agent-built-for-everyone/ |
| Gemini shopping is available in Australia | 01 Q3; 02 Q4 | **Confirmed** | "Shopping with Gemini Apps is currently available in the following countries and regions: Argentina Australia Brazil Canada ..." | https://support.google.com/gemini/answer/16730149?hl=en-AU |
| Agentic checkout is live in Australia | 01 §1; 02 Q4; 08 | **Confirmed** | "This feature is currently only available in the US and Australia, in English and for selected merchants that accept Google Pay". Buy now, pay later is US only | https://support.google.com/googlepay/answer/16421147?hl=en-AU |
| ...with Bunnings, Kogan, THE ICONIC, Adore Beauty and Petbarn | 01 §1; 02 Q4; 08 | **Unverified at Google's own pages** | Trade press, 18 June 2026: "Google says a new checkout experience will soon launch with retailers including Adore Beauty, Bunnings, Kogan Group, Petbarn and THE ICONIC". Google's own posts say only that checkout "will roll out across Canada and Australia in the coming months". No Google Australia post naming retailers was found | https://www.channelnews.com.au/google-taps-aussie-retailers-for-ai-shopping-checkout-launch/ · https://blog.google/products-and-platforms/products/shopping/shopping-updates-google-marketing-live/ |
| Google shopping surfaces second-hand listings | 01 Q3; 02 Q4 | **Unverified** | The Gemini help page says it draws on "Google's Shopping Graph" and "eligible merchants". It says nothing about used or second-hand goods. Needs a hands-on test | Gemini help page above |
| ChatGPT shopping research is available in Australia | 01 Q3; 02 Q4; 08 | **Unverified** | OpenAI's help article and announcement both returned HTTP 403. A search summary of OpenAI's release notes says it launched 24 November 2025 for logged-in Free, Go, Plus and Pro users on web, iOS and Android, with no regional limit stated. That is a summary, not a reading | https://help.openai.com/en/articles/11128490-chatgpt-shopping-research |
| ChatGPT shopping research covers second-hand listings | 02 Q4; 08 | **Unverified** | Not readable; needs a hands-on test | — |
| Zyft is operating; 50,000+ retailers; 550,000 users | 01 §1, Q1 | **Confirmed, figure updated** | "700,000+ Aussies use Zyft to check prices across 50,000+ stores". 1.4K ratings, 4.5, No. 48 in Shopping, updated about 13 Nov 2026. Affiliate links disclosed. Now leads with a grocery list tracker. No mention of used goods | https://apps.apple.com/au/app/zyft-smart-price-checker/id1633382307 |
| BuyWisely is operating; 20,000+ retailers | 01 §1, Q1 | **Unverified** | buywisely.com.au returned a Cloudflare challenge. Its Chrome extension is listed but stale: 602 users, version 0.0.1, "Updated August 18, 2023" | https://chromewebstore.google.com/detail/buywisely-compare-track-p/clockgoljgonihmmbookebhmaokpfako |
| Little Birdie closed on 8 September 2025; no official reason | 01 §1, Q5 | **Corrected on the date** | Little Birdie's site gives no date and no reason: "It's with great sadness we announce that Little Birdie will no longer continue as a consumer product ... The extension and apps will continue to be available for the time being, but the experience will wind down as we decrease our data ingestion." The pause on 17 May 2024 is confirmed (Startup Daily). 8 September 2025 is the date Cashrewards announced its own closure | https://www.littlebirdie.com.au/ (rendered with Playwright) · https://www.startupdaily.net/topic/funding/fowl-play-cba-backed-ecommerce-site-little-birdie-shuts-down/ |
| Cashrewards closed 8 September 2025; no reason given | 01 Q5 | **Confirmed** | Dated Sep 8, 2025: "Cashrewards did not immediately provide a reason for the closure, but the closure reportedly arrives as part of a broader strategic review affecting the Big Four bank". Users had until 24 October to withdraw | https://www.smartcompany.com.au/startupsmart/cash-rewards-cashback-closure-announcement/ |
| Booko shows new and used prices | 01 Q1 | **Confirmed** | Page title: "Booko: Compare New and Used Book & DVD prices with Booko" | https://booko.info/ |
| Back Market and Reebelo operate in Australia and show a struck-through new price | 02 Q2 | **Partly confirmed** | Both operate Australian stores selling refurbished electronics from their own sellers. Marketing compares with new ("up to 70% less than new", "for up to 50% less than new"). A per-product new price was not confirmed; product pages need JavaScript and were not rendered | https://reebelo.com.au/ · https://www.backmarket.com.au/en-au |
| Amazon Australia shows new and used offers on one page | 02 Q2 | **Partly confirmed** | Amazon.com.au has an "Amazon Resale" store and an "Amazon Renewed" section. Whether a product page shows new and used side by side was not checked | https://www.amazon.com.au/resale |
| Phia is fashion-only | 01 Q3; 02 Q1 | **Confirmed** | Australian listing is titled "Phia: Fashion Deals & Rewards"; "Phia is built for people who care about what they wear". Compares "across 350 million items and 220,000+ sites, new and secondhand" | https://apps.apple.com/au/app/phia-shop-smarter-save-money/id6739351340 |
| Phia's Australian availability is not established | 01 Q3; 02 | **Corrected** | It is in the Australian App Store: 91 ratings, 4.8, updated 2 Nov 2026. Whether its retailer and resale coverage is Australian was not tested. One Australian review: "It's easier to google or ask AI to search" | same |
| Phia has a "worth the money" style verdict | 01 Q3 | **Confirmed** | "Should I Buy This? Tap it on any item while browsing Safari and Phia's AI instantly tells you if the price is fair, finds cheaper alternatives across retail and resale". It starts from a retail page, not a second-hand listing | same |
| Phia was suspended by Impact.com | assignment | **Confirmed (secondary source)** | TechCrunch, 10 July 2026: a Bloomberg investigation accused Phia of "cookie stuffing"; the report "led to Phia's suspension from Impact.com". Search summaries of later coverage say Impact called the suspension temporary and that Phia blamed a bug; those were not read at source | https://techcrunch.com/2026/07/10/phia-accused-of-cookie-stuffing-taking-affiliate-credit-on-purchases-it-didnt-earn/ |

---

## 3. New findings

### 3.1 Products the first pass missed

| Product | What it is | Australia | New price shown? | Traction | Source |
|---|---|---|---|---|---|
| **Deal Scout** | Chrome extension. Opens automatically on a Facebook Marketplace, Craigslist, OfferUp or eBay listing. Verdict, eBay sold average, new retail price, where to buy new, counter-offer, negotiation messages. "COMPLETELY FREE. No subscription. No account required. No ads." | Not mentioned | **Yes** | 36 users, 2 ratings; v0.48.23, 15 Oct 2026; individual developer | https://chromewebstore.google.com/detail/mbkhagpggkmefaompfjkbbnbmmameapk |
| **PriceSnap** (pricesnap.ai) | Web and Android. Photo, barcode, description or pasted listing link plus the asking price. Verdict in five bands including "Can't judge this price · too few sales". Labels each price as reported sold, active listing, asking price or retail offer | AUD market listed; depth untested. Offers come from "Google Shopping and Amazon, where they cover your area" | **Yes**, as a separate "Where to buy" module | Google Play 1K+ downloads; updated 2 Nov 2026. Free tier 3 valuations a day; Pro US$9.99 a month. Carries ads | https://play.google.com/store/apps/details?id=ai.pricesnap.app · https://www.pricesnap.ai/is-this-a-good-deal |
| **PriceVet** | Chrome extension beside a Facebook Marketplace listing; compares with eBay AU; A–F deal score; user supplies own API keys | **Built for NZ and AU** | No | No ratings, no user count shown; v0.4.5, 28 Apr 2026 | https://chromewebstore.google.com/detail/ipaiccoeoohhpjbljjigldemjhcecblp |
| **Price Snap** (Adem Cilgin / AppUsta) | iOS. Photograph an item, get "new and used price ranges". Listing written for Australian op-shop and Gumtree users | Australian-localised listing, AUD | **Yes** (retail and second-hand ranges), from a photo, not a listing | Too few AU ratings to display (28 in the US store per search summary); v1.6, 15 June 2026 | https://apps.apple.com/au/app/price-snap-ai-price-scanner/id6749811323 |
| **DealUp AI** | iPhone, Android, web. Paste a listing link; score out of 100; buy / negotiate / verify first / pass; fair price "compared with similar private listings" | No Australian country option. Gumtree in its list sits beside UK sites | No | Play 1K+ downloads; claims "More than 10,000 buyers"; French developer | https://joindealup.com/ · https://play.google.com/store/apps/details?id=com.joindealup.app |
| **ThriftCheck** | iOS. Photo of an op-shop find; "BUY or SKIP"; resale prices from "eBay, Gumtree, Etsy & more" in the subtitle, "eBay, Mercari, Poshmark, and Etsy" in the body | Australian-localised listing | No | Too few ratings; A$14.99 a week | https://apps.apple.com/au/app/thriftcheck-vintage-resale-ai/id6762850899 |

The Australian App Store's "You Might Also Like" rails on these pages list a further dozen Marketplace alert apps (Pacto, JDMarket, Pouncify, FlipDar, GrailHound, Outpost Alerts, DealHawkHQ, Flipify, Flipinator, BuyHub). They were not opened. By name and subtitle they are alert tools.

### 3.2 What the gap actually is now

Reading the listings side by side, the pieces of the founder's product are each shipped by someone:

| Piece | Who already has it |
|---|---|
| Verdict on a specific listing the user brings | Spottable, PricePath, DealUp AI, Deal Scout, DealRater, YrdSale, PriceSnap |
| New retail price beside the verdict | Deal Scout, PriceSnap; Price Snap (from a photo) |
| Works on Australian Facebook Marketplace listings, by own claim | Spottable, PriceVet, Classifindr and Swoopa (alerts) |
| Published method with "not enough data" behaviour | Spottable, PriceSnap |
| Buy-to-keep positioning | PricePath, DealUp AI, PriceSnap |
| Australian retailer prices (BCF, Anaconda, Bunnings and similar) as the new-price source | **Nobody found** |
| Gumtree listing as an input | **Nobody found** among verdict tools (alert tools only) |
| Mobile share-sheet flow plus new price | **Nobody found** (Deal Scout is desktop Chrome; PriceSnap has no iPhone app) |
| Drive distance or total cost in the verdict | **Nobody found** |
| Evidence of users | **Nobody** |

So the opening is narrower than "nobody shows the new price". It is Australian retailer coverage, Gumtree, a phone-first flow and total cost. All four are execution details a competitor could add, and Spottable is a Sydney team already holding the Australian Marketplace side.

### 3.3 Other points

- **Spottable publishes a page on "Marketplace API providers" and offers an integration for AI assistants** ("Use Spottable with ChatGPT or Claude Code"). It reads public Marketplace listings without the user's login ("The iPhone app searches public Marketplace listings"). That is the access route the legal track flagged as risky; Spottable is taking that risk today in Australia.
- **Underpriced states the limit plainly**: "Values come from eBay sold listings, because Marketplace doesn't publish what things sold for." Every verdict tool read uses either eBay sold prices or other asking prices. None has outcome data.
- **Zyft has moved toward groceries.** Its listing now opens with a grocery list tracker. It has not moved toward used goods.

---

## 4. Still open

| Question | Why it is open | What would settle it |
|---|---|---|
| Does Deal Scout or PriceSnap return a correct Australian new price for a real Australian listing? | Nothing was installed or run | Ten minutes: install Deal Scout in Chrome, open three Australian Marketplace listings; run the same three through pricesnap.ai with the market set to Australia |
| Does Spottable's verdict work on Australian listings in practice? | Own claim only | Chrome extension gives 3 free analyses a day; test on the same three listings |
| Grabbit: coverage, method, Australia | grabbit.app and Product Hunt refuse automated requests | Open grabbit.app in a browser |
| Is ChatGPT shopping research live in Australia, and does it or Gemini surface second-hand listings? | OpenAI pages return 403; Google's page is silent on used goods | The Phase 0 assistant test already planned: ask both about a specific used item from an Australian account |
| Which Australian retailers are actually live in Google's agentic checkout | No Google page naming them was found | Try a purchase flow in Gemini from an Australian account, or find Google Australia's own announcement |
| BuyWisely's current state and coverage | Site refuses automated requests | Open buywisely.com.au in a browser |
| Do Back Market, Reebelo and Amazon Australia show a new price on each product page? | Product pages were not rendered | Open one product page on each |
| Is there an Australian app found only through in-store search? | Store search pages were not read; discovery relied on three web searches restricted to the store domains | Search the App Store and Google Play on an Australian phone for "used price checker", "is it a good deal", "marketplace deal checker", "second hand price guide" |
| Is any Meta buyer-side price feature visible in Australia? | Meta's posts give no country list | Open a vehicle listing on Marketplace from an Australian account and look for AI insights |
