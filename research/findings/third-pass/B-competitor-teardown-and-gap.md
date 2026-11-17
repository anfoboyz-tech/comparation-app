# Third pass, Assignment B — competitor teardown and the gap

Date of research: 2026-11-17. Web searches used: 24 of 25.

**Evidence labels**

- **[R]** read at the source today (page fetched with `curl`, or Apple's public review and lookup feeds).
- **[P2]** read at the source by the second pass (`research/findings/second-pass/01-02-competitors.md`); not re-read today.
- **[S]** from a search-result summary only.
- **[K]** my background knowledge, unchecked today.
- **[I]** my inference.

**Limits**

- Nothing was installed or run. Every statement about what a product does is the vendor's own description unless a review or press test is cited.
- Refused automated requests and left alone: Product Hunt, Reddit, Indie Hackers, Trustpilot, GeekWire, grabbit.app, buywisely.com.au, shopbeni.com, OpenAI's help pages. So the "what users say" section rests on the App Store, the Chrome Web Store and press tests.
- Google Play pages loaded but showed no review text for PriceSnap or DealUp AI.
- Car-parts locators are Assignment C's subject. I cover them only far enough to place them in the matrix.

---

## 1. Bottom line

1. Thirteen tools now give a verdict on a second-hand listing the user has already found. I could find written user feedback for only five of them, and the Australian App Store shows zero ratings for six. The feature has been shipped repeatedly and nobody has come back to say anything about it.
2. No product in the matrix does the finding for a buyer across new, used and unlisted supply. The verdict tools judge; the alert tools watch one or two classifieds sites for resellers; the aggregators are fashion-only; the assistants cover new retail.
3. No product found contacts a private seller for the user. Several draft a message for the user to send. Meta's Muse advertises that it messages sellers and negotiates, and in CNN's test it said it could not and drafted a message instead [R].
4. The products with real traction are the ones that go and collect answers from many suppliers for a costly or urgent purchase. CarEdge reports 163,096 AI negotiation sessions with car dealers since July 2025 [R]. 1st Choice Spares in the UK, which broadcasts a parts request to breakers, has about 26,000 Trustpilot reviews [S]. hipages earned A$90.6m in FY26 collecting trades quotes [S].
5. My reading of why the verdict tools have no users: a verdict is not the job. It serves someone who has already done the searching, at a moment that comes a few times a year, with a number they have no reason to trust, usually for a monthly fee. Poor distribution is real but is a consequence of that, not the cause. Confidence: medium.
6. The gap, stated so it can be defended: **no product found, in Australia or elsewhere, takes a specific need, makes the enquiries itself across online listings and suppliers who have to be asked, and returns one ranked answer across new, used, refurbished and wrecked within a stated time.** Each piece exists somewhere. The combination does not, and no consumer product found makes outbound enquiries to Australian businesses at all.
7. "Five minutes" is not supported by the evidence for supply that has to be asked. CarEdge's dealers take 18.4 hours on average to reply and 35% never do [R]. Meta's internal tests reportedly found human callers succeeded 95–98% of the time and AI-only calls did worse [S]. An honest promise is minutes for what is listed online and hours for what needs a phone call.
8. The morning brief's "suspiciously cheap" flag is not an opening. PriceSnap, Deal Scout, PriceVet and Spottable all already flag it [R, P2].

---

## 2. Findings

### 2.1 Feature matrix

Key: **Y** yes, **N** no, **P** partial, **D** drafts text for the user to send, **?** not established. "Searches for you" means the product goes and finds candidate items, as opposed to judging one the user brings.

**Table A — what each product does**

| Product | Input | Sources it draws on | Searches for you | New price | Used comparables | Verdict | Total cost | Location | Alerts | Contacts sellers | Negotiates | Phones or messages businesses |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| **Deal Scout** | Opens on a listing page | eBay sold and active; "Amazon, eBay, and more" for new | N | Y | Y (eBay sold) | Buy / Caution / Avoid | N | N | N | D | D (counter-offer) | N |
| **PriceSnap** (pricesnap.ai) | Photo, barcode, description or pasted link, plus asking price | Google Shopping, Amazon, sold and asking prices | P (retail offers only; filter new / used / refurbished) | Y | Y | Great / Good / Fair / Pricey / can't judge | P (delivery and tax where shown; no travel) | P (market-level) | ? | N | P (offer and walk-away price) | N |
| **Spottable** | Listing in Chrome; search and alerts in the iPhone app | Facebook Marketplace only | P (Marketplace only) | N | Y (other asking prices) | Score 1–10 | N | Y (Marketplace's) | Y | D | N | N |
| **PriceVet** | Sits beside a Marketplace listing | eBay AU | N | N | Y (eBay AU low / median / high) | A–F, risk flags | N | N | N | N | N | N |
| **Grabbit** | Search box | Marketplace, Craigslist, OfferUp, Depop, Mercari [S] | Y (US sources) [S] | ? | Y | GrabScore 0–100 | ? | ? | ? | N | N | N |
| **YrdSale** | Search, or share a listing | ShopGoodwill, eBay, Marketplace, Craigslist, Mercari, OfferUp | Y (US sources) | P (assistant looks up "real market prices") | Y | Deal / fair / overpriced | N | ? | ? | N | N | N |
| **Underpriced** | Screenshot or photo | eBay sold | N | N | Y | Flip / Potential / Pass, profit after fees | P (selling fees, not buying costs) | N | N | N | N | N |
| **DealRater.ai** | Marketplace listing in Chrome | "Market comps" | N | N | Y | Score 1–100, offer range | N | N | N | N | P (offer range) | N |
| **PricePath** | Pasted listing | Undisclosed | N | N | ? | Solid / negotiate / overpriced / walk away | N | N | N | N | P (target and walk-away price) | N |
| **DealUp AI** | Pasted or shared listing link | "Similar private listings" | N | N | Y | Buy / negotiate / verify first / pass | N | N | N | D (re-scores when the user pastes the seller's reply) | D (plan and offer range) | N |
| **DealFlip AI** | Listing | Undisclosed | N | N | Y | Fair market value | N | N | N | N | N | N |
| **Price Snap** (A. Cilgin) | Photo of an item | Undisclosed | N | Y (range) | Y (range) | None; two ranges | N | N | N | N | N | N |
| **ThriftCheck** | Photo of an item | eBay, Mercari, Poshmark, Etsy | N | N | Y | Buy / Skip | N | N | N | N | N | N |
| **Swoopa** | Saved searches | Marketplace, Gumtree, eBay, Craigslist, OfferUp, Kijiji, Nextdoor | Y (monitoring) | N (vehicle retail / private / trade values) | P (vehicle values) | Price filter | N | Y | Y | P (links out to the platform) | N | N |
| **Classifindr** | Saved searches | Gumtree AU and UK, Marketplace, eBay, Trade Me and others | Y (monitoring) | N | N | N | N | Y | Y | N | N | N |
| **Scout: Marketplace Alerts** (new to this research) | Saved searches | Facebook Marketplace | Y (monitoring, multi-location) | N | N | N | N | Y | Y | N | N | N |
| **Flipify**, **Marketplace Monitor** | Saved searches | Marketplace, eBay, Craigslist, OfferUp | Y (monitoring) | N | N | P (Flipify rates listings [S]) | N | Y | Y | N | N | N |
| **Phia** | Retail page, link or photo | "220,000+ sites, new and secondhand" | Y | Y | Y (resale listings) | "Should I buy this?" | N | N | Y (price) | N | N | N |
| **Beni** | Retail page being browsed | 40+ resale sites [S] | Y | P (the page you are on) | Y | N | N | N | ? | N | N | N |
| **Faircado** | Retail page or search | Partner second-hand marketplaces | Y | P | Y | N | N | N | ? | N | N | N |
| **Zyft** | Search, barcode, Safari extension | "50,000+" Australian stores | Y (new only) | Y | N | N | N | P (in-store filter) | Y (price drop) | N | N | N |
| **BuyWisely** | Search | Australian retailers [S] | Y (new only) | Y | ? | N | ? | ? | Y | N | N | N |
| **Google (Gemini, AI Mode)** | Conversation | Shopping Graph; phone calls to stores (US) | Y (new retail) | Y | ? | N | P | Y | Y (price target) | N | N | **Y, US only**: "Let Google Call" phones nearby stores about stock and price [R] |
| **ChatGPT (shopping research, agent)** | Conversation; agent drives a browser | Retail product data [S]; agent can open sites the user logs in to [K] | Y (new retail); P for classifieds via the agent, slowly [S] | Y | ? | Opinion on request | N | P | N | N | N | N |
| **Meta AI in Marketplace; Muse** | Marketplace itself; Muse by chat | Meta's own listings | P (Muse; a Tom's Guide Marketplace search returned nothing usable [R]) | N | Y (seller price suggestion; vehicle price insights) | N for non-vehicles | N | Y | ? | **Claimed**; in CNN's test it drafted only [R] | Claimed | P (Muse calling beta, US, September 2026 [S]) |

**Table B — scope, price and traction**

| Product | Categories | Australia | Platform | Price | Traction (date read 2026-11-17) |
|---|---|---|---|---|---|
| Deal Scout | General | Not mentioned | Chrome | Free | 36 users, 2 ratings [R] |
| PriceSnap | General | AUD market listed; depth untested | Web, Android | Free 3 a day; Pro US$9.99/month | Google Play 1K+ downloads [R] |
| Spottable | General | Yes; Sydney developer | iOS, Chrome | A$7.99–49.99/month | 966 Chrome users, 6 Chrome ratings; App Store 6 ratings (AU), 2 (US) [R] |
| PriceVet | General | Built for NZ and AU | Chrome | Free; user supplies API keys | No ratings, no user count [R] |
| Grabbit | General | US only [S] | Web | Free; Plus tier | US$30 lifetime verified revenue [P2] |
| YrdSale | General | In the store; US marketplaces | iOS | A$7.99 and A$14.99 | 0 ratings AU, 1 US [R] |
| Underpriced | General, for resellers | Localised listing | iOS, Chrome | A$14.99–39.99/month | 2 ratings AU, 14 US [R] |
| DealRater.ai | Mostly vehicles | Not stated | Chrome | Free 5 a month; US$9.99; US$29.99 | 31 users, 1 rating [R] |
| PricePath | General | In the store | iOS | A$22.99/month | 0 ratings AU and US; last update two days after its May 2026 release [R] |
| DealUp AI | Property, cars, electronics, watches, other | No Australian country option [P2] | iOS, Android, web | Subscription for full reports | Play 1K+ downloads; 0 App Store ratings AU [R] |
| DealFlip AI | General, for flippers | In the store | iOS | A$22.99–79.99 | 0 ratings AU, 1 US [R] |
| Price Snap (Cilgin) | General | Localised listing | iOS | Free with purchases | 0 ratings AU, 31 US [R] |
| ThriftCheck | Op-shop finds | Localised listing | iOS | A$14.99/week | 0 ratings AU, 8 US [R] |
| Swoopa | Vehicles for dealers; "anything" as an aside | Yes; Melbourne company | iOS | A$69–229.99/month | 34 ratings AU, 560 US [R] |
| Classifindr | General | Yes | iOS, web | Free to start | 2 ratings AU, 0 US [R] |
| Scout: Marketplace Alerts | General | Yes; Matten Pty Ltd | iOS | Subscription with trial | 47 ratings AU, 4.4 [R] |
| Flipify / Marketplace Monitor | General, for resellers | In the store | iOS | Subscription | 7 ratings (2.7) / 14 ratings (3.6) AU [R] |
| Phia | Fashion | In the store; coverage untested | iOS, Safari extension | Free; affiliate | 91 ratings AU, 22,800 US [R] |
| Beni | Fashion | No [K] | Extension, iOS | Free; affiliate | Not readable today |
| Faircado | Fashion-led, general | No; Europe | Extension, app | Free; affiliate | Site live [R]; numbers not checked |
| Zyft | New goods, groceries | Yes | iOS, Android, extension | Free; affiliate | 1,416 ratings AU, 4.5 [R]; claims 700,000 users [P2] |
| BuyWisely | New goods | Yes | Web | Free | Not readable |
| Google | New retail | Shopping and checkout yes [P2]; phone calling is US only [R] | Search, Gemini | Free | Mass market |
| ChatGPT | New retail | Unverified [P2] | App, web | Free and paid | Mass market |
| Meta AI / Muse | Marketplace | Marketplace yes; Muse not in Australia [P2] | Facebook, Muse app | Not checked | Mass market |

Sources: App Store rating counts and dates from Apple's lookup feed for the AU and US stores [R]; Chrome Web Store pages [R]; second-pass report for the rest.

**Corrections and additions to the earlier passes**

- **Scout: Marketplace Alerts** was missed. It is an Australian-company alert app with more Australian ratings (47) than Swoopa (34). Alerts only, no verdict. https://apps.apple.com/au/app/id6738621889 [R]
- **Swoopa's real market is the US.** 560 US ratings against 34 Australian [R].
- **PricePath looks abandoned**: released 27 May 2026, last updated 29 May 2026, no ratings in either store [R].
- **Deal Scout's two reviews are weak evidence.** One describes "finding discounts and promotions online" and "deals from a wide range of categories", which is not what the extension does [R].
- **Spottable's only Australian App Store "review"** is a five-star entry whose text is a question to a seller about a Shimano Curado reel, evidently typed into the wrong box [R]. It is not a review.
- **Scam and too-cheap flags exist already**: PriceSnap ("A price far below the rest is flagged, not called a bargain") [R], PriceVet ("Risk flags for suspicious listings") [R], Deal Scout (a reviewer: "even if the seller is potentially shady") [R], Spottable [P2].

### 2.2 What users say is wrong with them

The first finding is the absence. Of the thirteen verdict tools, only Spottable, Underpriced, Deal Scout, DealRater and DealFlip AI have any written review I could read, and they total about twenty. Complaints about the verdict being wrong barely exist because almost nobody has used one. The grouped complaints below therefore come mostly from the neighbours that do have users: Swoopa (55 reviews read), Phia (53), Zyft (50) and Pine (44).

| Complaint | Where | Representative quotes [R] |
|---|---|---|
| **"I can do this myself, free"** | Swoopa, Phia, Spottable | "This app doesn't do anything more than you can do yourself by logging into Facebook." (Swoopa, US, Sept 2026). "It's easier to google or ask AI to search." (Phia, AU, July 2026). "By the time it loads i could have compared prices myself" (Phia, AU). "Why would I pay monthly to see less ads for the things I'm searching for?" (Spottable, US, Oct 2026) |
| **Misses listings, or is late** | Swoopa, Spottable | "Some of the deals I find don't ever show up on swoopa." "I get alerted ... 10-30 minutes sometimes more after an item is posted." "It can't sync all the fb marketplace relative recent items because of fb algorithms prevents it" (AU). "Can not find relevant listings that I can currently see on marketplace." (Spottable) |
| **Wrong item matched** | Phia, Zyft, Swoopa | "I searched for laptops and desktop computers... I got bags for laptops" (Swoopa). "Phia will happily tell me it found a better price on completely different shoes". "comparing prices with similar but not matching products... it must be a comparison of the exact same model" (Zyft) |
| **Valuation not believed** | Swoopa, Phia | "The value estimator doesn't seem to be based on any reality" (Swoopa). "Just kept getting 'this price is typical' so deleted" (Phia) |
| **Price, paywall, trial, cancelling** | Swoopa, Spottable, Pine | "Not free, requires an account to use, and no way to try it without spending at least $5. 20 cents per search." (Spottable; the most-upvoted review on its Chrome page). "for an individual searching for a car the subscription rates are too high to make it worthwhile" (Swoopa). Charged during the "free" trial; cancel button leads nowhere (Swoopa, Pine) |
| **Permissions and privacy** | Phia, Zyft | "you are forced to allow always access to every website". "Safari warned me that the access the extension required would give this app access to sensitive information such as my passwords and credit card details. Big no from me!" (Zyft, AU). This is the most frequent one-star theme for both apps |
| **Conflicted business model** | Phia, Zyft | "steals commissions from small creators" (Phia). "the filter isn't showing multiple websites, but sponsors that have that item" (Zyft, AU) |
| **Scam and spam listings pass through** | Swoopa | "more scam/spam car listings showing up than actual cars for sale" |
| **The agent leaves the work with me** | Pine | "it also had me do most of the work"; "it does require some handholding"; one reviewer says a task was reported complete and charged for when it was not |

What satisfied users say is as informative. Every positive Underpriced review is from a reseller ("for anyone into reselling or thrifting"). Swoopa's are from flippers and dealers ("I'm buying 3-5 cars a week"; "Your first deal essentially will pay for the subscription"). I found no positive review of any of these tools from someone buying one item to keep, other than three short Spottable reviews from March 2026.

Two points bear on Assignment A. The permission that a browser extension or in-app browser needs is itself the top complaint for Phia and Zyft. And reviewers know the alert tools scrape: "Scraping Facebook's marketplace/API seems to be some sort of legal Gray zone so maybe we are just paying to cover an eventual lawsuit."

### 2.3 What none of them does

| Capability | Coverage in the matrix | Confidence that it is open |
|---|---|---|
| **Search legwork end to end** (retailers, classifieds, eBay and offline suppliers, for one need) | None. Verdict tools do not search. Alert tools watch classifieds only. Aggregators are fashion. Assistants cover new retail | High |
| **Supply that is not listed online** | None of the shopping products. Only Google's store-calling (US; toys, health and beauty, electronics at launch [R]) and parts request networks reach it | High for Australia |
| **Contacting private sellers for the user** | None sends. Deal Scout, DealUp AI and Spottable draft. Muse claims it and did not do it when tested [R] | High |
| **Phoning or messaging businesses for the user** | Google, Muse, Pine and small apps such as Tripo, all US. CarEdge by email and SMS, US car dealers. None found serving Australian consumers | Medium-high (Pine is listed in the Australian App Store with one rating; whether it calls Australian numbers was not established) |
| **Parts, fitment, compatibility** | None of the 25 products. Sits entirely with parts specialists (Assignment C) | High |
| **One answer across new, used, refurbished and wrecked** | PriceSnap filters retail offers by new / used / refurbished from Google Shopping and Amazon. Phia does new and resale in fashion. Nobody joins local classifieds, wreckers and new retail | High |
| **Time-to-answer as the promise** | Tripo: "reports back in minutes" [R]. PartsClub: quotes "usually within 1 hour" [R]. No verdict, alert or aggregator tool states a time for a complete answer | Medium |
| **Total cost including the trip** | None. PriceSnap adds delivery and tax only | High |
| **Gumtree listing as buyer input** | None among verdict tools | Medium (unchanged from second pass) |
| **Recorded outcomes or a published accuracy record** | None | High |

Not gaps, despite earlier reports: a verdict; a new price beside it; a too-cheap flag; a suggested offer; a drafted seller message; alerts.

### 2.4 Agents that do legwork

| Product | What it does for the consumer | Where | How it is doing | Evidence |
|---|---|---|---|---|
| **Google "Let Google Call" / business calling** | Phones nearby stores to ask about stock, price and promotions, then emails or texts a summary with other local inventory. Launched for services (January 2025 test; all US users July 2025), products (November 2025), and inside AI Mode (May 2026). Calls announce they are automated and from Google; businesses can opt out | US only. The product post says "in the U.S." | Free, built into Search. No usage figures published | Google blog [R]; TechCrunch 16 July 2025 [R]; Localogy 7 May 2026 [R] |
| **CarEdge AI negotiator** | Emails and texts car dealers from anonymous addresses, collects out-the-door prices, negotiates in rounds. About US$40 [S] | US | **163,096 sessions** July 2025 to 10 November 2026; 1,925 in the last seven days; 65% of sessions get any dealer response; **average response 18.4 hours**, first out-the-door price 37.1 hours; 9.4 agent messages per negotiation. Savings figures are self-reported | caredge.com/report [R] |
| **Pine** | Phones customer-service lines, negotiates bills, cancels subscriptions | US | US$25m Series A, December 2025 [S]. 148 US App Store ratings, 4.4 [R]. Reviews complain of pricing, hand-holding and one false completion [R] | App Store feed [R] |
| **Meta Muse calling** | Phones US businesses for bookings, stock checks, billing | US beta from 16 September 2026 [S] | Reuters: Meta tested human contractors placing the calls; internal posts put human success at 95–98% and AI-only lower; rolled back as "a miss" on disclosure [S; iTnews copy of the Reuters lead read, rest paywalled] | Layer3 Labs comparison [R]; Reuters via syndication [S] |
| **Tripo**, Reqly, Callio | Small apps that phone up to five local businesses at once and compare answers | US | No traction evidence. Tripo was featured on BetaList in February 2026 | BetaList [R]; others [S] |
| **PartsClub** | Posts a parts request to "100+ verified wreckers" who reply with quotes; also 100,000+ listed parts synced from wreckers' eBay stores. Free to buyers, no commission | **Australia** | Calls itself "Australia's newest parts marketplace". No independent reviews found | partsclub.com.au [R] |
| **1st Choice Spares** | Same broadcast-a-request model to UK breakers | UK | About 26,000 Trustpilot reviews, score 3.9. Complaints are non-delivery and warranty disputes with the breaker, not the locating | [S]; Trustpilot refused the fetch |
| **hipages; Airtasker** | Post a job, receive quotes from trades or taskers | Australia | hipages FY26 revenue A$90.6m, 36,400 subscribing trade businesses. Airtasker FY26 revenue A$57.8m on A$240m of marketplace volume | [S], from results announcements |
| **Kwibal; Fetchlist** | Adjacent: browse local second-hand items and the company confirms with the seller, collects and delivers | US cities | Small. Fetchlist's founder runs it with AI bots that contact sellers [S] | kwibal.com [R]; GeekWire [S] |
| **Cavela, Alibaba Accio** | Agents that find suppliers and negotiate, for businesses | Global | Accio claims 10 million monthly users (March 2026) | [S] |
| Yard-side agents | The reverse: AI that answers a wrecker's phone or WhatsApp and quotes from stock | US, some Australian trade coverage | Vendor marketing only. A US recyclers' group told members in 2026 to expect customers' agents to deal with yards' agents | [S]; URG post [R] |

Three things stand out.

1. **I found no working consumer product that phones or messages salvage yards to find a part.** A search for exactly that returned vendor tools for the yard's side and one speculative blog post. Confidence: medium; Assignment C should confirm.
2. **Every outbound-enquiry agent found operates in the US.** For Australia I found the opt-in request boards (PartsClub, hipages, Airtasker), where the supplier must already have joined and must choose to answer.
3. **Response is the constraint, not capability.** CarEdge's own numbers show a third of dealers never answer and the rest take most of a day. Meta's reported internal result is that people on the phone still beat the AI.

### 2.5 Why the verdict tools have no users

The four candidate explanations, with the evidence for each.

**Distribution.** Real, but not sufficient.
- For: all thirteen are solo or tiny developers. Several are desktop Chrome extensions for a mobile activity. Six have no Australian ratings.
- Against: Spottable is marked "Featured" on the Chrome Web Store and has 966 users after eight months [R]. PriceSnap reached 1K+ installs and stalled. In the same stores, reseller tools gather hundreds of ratings (Swoopa 560) and a funded fashion tool 22,800. Distribution is available when the product gives people a reason to return or to tell others.

**Trust.** Contributes.
- Every verdict rests on asking prices or eBay sold prices; none has outcomes [P2]. The one valuation feature with many users is called "not based on any reality" [R].
- An unexplained score asks for more trust than a list of comparables the buyer can check, and the Australian survey in the second pass put willingness to buy on an AI recommendation alone at 3%.

**Frequency.** Strong.
- A person buying to keep meets this question a handful of times a year. That is too rare to form a habit, to justify A$8–50 a month, or to produce word of mouth. The most-upvoted Spottable review is about being asked to pay before trying it [R].
- The only satisfied reviewers are people who do it daily for profit. This matches the first pass's inference and is now supported by the reviews.

**Wrong job.** Strongest, in my view.
- A verdict tool starts work after the user has found the listing. In both of the founder's stories the hours went on finding: 50–100 minutes locating new prices, four hours locating a drive shaft. The verdict addresses the last minute of that.
- Where forum users did ask "is this fair?", they had answers within the hour for free, often "just buy new" [second pass].
- The complaint that recurs across Swoopa, Phia and Spottable is "I can do this myself". Nobody says that about CarEdge contacting nine dealers.
- The products with traction in section 2.4 all do the collecting: they go to many suppliers and come back with answers.

**View.** In order of weight: the verdict is not the job; the need is too infrequent for a subscription or a habit; the number cannot be trusted enough to act on; and weak distribution follows from those three. Confidence: medium. This is a pattern across a small set of products, read from store pages and reviews, and survivors are easier to see than failures. It would be wrong if a verdict tool with good distribution and a free tier were shown to retain keep-buyers; none has been tried on those terms that I could find.

One caution against over-reading. The legwork products that work share two further properties the founder's general-goods case lacks: the purchase is expensive or urgent (a car, a gearbox, a bathroom), and the suppliers are businesses that want the enquiry. A A$60 fishing reel from a private seller has neither.

### 2.6 The gap, stated precisely

No product found, in Australia or overseas, accepts a specific need from a consumer, makes the enquiries itself across online listings and across suppliers whose stock is only discoverable by asking, and returns a single ranked answer spanning new, used, refurbished and wrecked options, with total cost, inside a stated time. The pieces exist separately: Google phones retail stores about stock in the US; CarEdge emails and texts US car dealers; PartsClub and its UK equivalents pass a parts request to wreckers who have signed up and wait for them to reply; thirteen tools grade a listing the user has already found. Nobody joins active outbound enquiry to online search and a cross-condition ranking, and no consumer product found makes outbound enquiries to Australian businesses at all. This is a statement of what 24 searches and about 45 pages turned up on one day; small products in this area launch monthly, and the parts-specific half of the claim depends on Assignment C.

**Candidate positions, most open and most painful first**

| # | Position | How open | Pain removed | What it would take | What could kill it |
|---|---|---|---|---|---|
| 1 | **Sourcing agent for one fragmented, partly offline category, car parts first.** The user gives the vehicle and the part. The agent searches the sources it may lawfully search, sends the same enquiry to wreckers and suppliers by web form, email and SMS, phones those that do not answer, and returns ranked options with price, condition, warranty and distance | High. No outbound-enquiry product found for Australia; PartsClub waits on about 100 opted-in wreckers | High. Hours of calls, often with a car off the road | A supplier directory with contact routes; enough fitment knowledge to ask the right question; outbound messaging and calling that complies with Australian rules (Assignment C); reply handling; a person as fallback for calls; a promise in hours, not minutes; a charge per successful find or a supplier lead fee | Wreckers ignoring or refusing automated enquiries; replies too slow to beat ringing round; cost per request above what a buyer will pay; PartsClub or an inventory vendor adding the same thing; Google bringing store-calling to Australia |
| 2 | **The same engine for other ask-around purchases** (tyres, appliance spares, building materials, machinery parts) | Medium-high in Australia; Google's version is US only and limited to chosen retail categories | Varies by category; lower urgency than a car | Position 1 working first; a directory and question script per category | Google's calling arriving here; hipages and Airtasker already own trades quotes; thin margins per job |
| 3 | **"Find it for me" for considered second-hand purchases in a few hobby categories**, returning a shortlist across Marketplace, Gumtree, eBay and new retail with total cost. Marketplace reached only through the user's own session (Assignment A) or by hand | Medium. Nobody does it for general goods in Australia, but it is what Muse and browser agents are aimed at | Medium. The founder's rod-and-reel hour and a half | A lawful access route; category catalogues for matching; a concierge period run by hand to learn what a good answer is | Platform terms and blocking; Muse launching in Australia; the frequency problem from section 2.5; sellers are private individuals who cannot be phoned |
| 4 | **The supplier's side**: make small wreckers' stock answerable, by handling their inbound enquiries or publishing their inventory | Unknown in Australia; vendors exist in the US | The supplier's, not the consumer's | Sales to several hundred small businesses | A different company from the one the founder described; slow sales. Worth knowing because it is where position 1's lasting advantage would come from |
| 5 | **Fair-price check on a listing the user brings** (the morning brief's version) | Low. Thirteen tools, no users | Low | Little | The evidence in section 2.5. Keep it as the last line of a sourcing answer, not as the product |

---

## 3. What this means for the product

- **Stop treating the verdict as the product.** The teardown gives no support for a fourteenth listing checker, however well localised. The four openings the second pass identified (Australian retailers, Gumtree, phone-first, travel cost) are improvements to something nobody uses.
- **The opening is doing the asking.** It is the one capability with no coverage in Australia and with paying users elsewhere.
- **Pick a category where suppliers are businesses and the purchase is urgent or costly.** That is where the working examples are, and where the people being contacted want the enquiry. Car parts fits; a used fishing reel from a private seller does not.
- **Promise hours and beat them.** Minutes for listed stock, a stated number of business hours for anything that needs a reply. The CarEdge and Meta figures are the best available guide to what outbound enquiry actually achieves.
- **Plan for a person in the loop on calls at first.** Meta's reported internal numbers favour it, and its mistake was hiding it, not doing it.
- **Charge per job or per successful find.** A monthly fee for an occasional need is the most consistent pricing complaint in the reviews.
- **Avoid an extension that asks for access to every site** unless Assignment A shows there is no other route. It is the leading one-star theme for the two largest apps read.
- **Do not present the too-cheap flag or a drafted seller message as differentiators.** Both are common.
- **Test before building.** Take twenty real parts requests, make the enquiries by hand by email, SMS and phone, and record response rate, time to first usable quote, and whether the result beat what the person would have found alone. That measures the one thing the desk research cannot.

---

## 4. Open questions

1. **Will Australian wreckers and small suppliers answer an automated or AI-voiced enquiry, and how fast?** Nothing found measures this. The manual test above settles it.
2. **Does any Australian parts locator already make outbound enquiries, or publish live wrecker stock?** Assignment C. PartsClub is the only one I read.
3. **Is Google's store-calling coming to Australia?** Google's posts name only the US. Duplex made limited calls to Australian businesses in 2020 [S], so the capability has been here before. Watch Google's Australian blog.
4. **Does Pine place calls to Australian numbers?** It is in the Australian App Store with one rating. Install and try.
5. **How good is PartsClub in practice?** No independent reviews found. Post one real request and time the quotes.
6. **Do Deal Scout, PriceSnap and Spottable work on Australian listings?** Still untested by anyone in this research. Ten minutes each.
7. **What do Product Hunt and Reddit say about the verdict tools?** Both refused automated requests. Read by hand: Spottable's and Grabbit's Product Hunt pages, and r/Flipping.
8. **What does an enquiry cost to make?** No figures gathered for AI voice minutes, SMS or human fallback per request. Needed before pricing.
9. **Would a keep-buyer return to a free verdict tool with good distribution?** Untested by the market; it is the one condition under which section 2.5 would be wrong.

---

## 5. Sources

All read or searched 2026-11-17.

**Read at source today**
- Deal Scout reviews: https://chromewebstore.google.com/detail/mbkhagpggkmefaompfjkbbnbmmameapk/reviews
- Spottable reviews: https://chromewebstore.google.com/detail/spottable-ai/dbgjphnanjmmfjacahfhliahblokmpgh/reviews
- DealRater.ai reviews: https://chromewebstore.google.com/detail/mcoiofhpiamkkfdnjondgcplkkdljfjl/reviews
- PriceVet: https://chromewebstore.google.com/detail/ipaiccoeoohhpjbljjigldemjhcecblp
- PriceSnap on Google Play: https://play.google.com/store/apps/details?id=ai.pricesnap.app&hl=en_AU&gl=AU
- DealUp AI on Google Play: https://play.google.com/store/apps/details?id=com.joindealup.app&hl=en_AU&gl=AU
- Scout: Marketplace Alerts: https://apps.apple.com/au/app/id6738621889
- Flipify: https://apps.apple.com/au/app/id6504143452
- App Store customer-review feeds, AU and US stores, of the form `https://itunes.apple.com/{au|us}/rss/customerreviews/page=1/id={app id}/sortBy=mostRecent/json`, for Swoopa (6475300269), Spottable (6758812746), YrdSale (6759308082), Underpriced (6759008101), Classifindr (6764547369), PricePath (6770200483), DealFlip AI (6756501597), Phia (6739351340), Zyft (1633382307), Pine (6746403769)
- App Store rating counts and release dates: `https://itunes.apple.com/lookup?id={ids}&country={au|us}`
- Google, "Let Google Call" and agentic checkout: https://blog.google/products-and-platforms/products/shopping/agentic-checkout-holiday-ai-shopping/
- TechCrunch on Google business calling, 16 July 2025: https://techcrunch.com/2025/07/16/google-rolls-out-ai-powered-business-calling-feature-brings-gemini-2-5-pro-to-ai-mode
- Localogy, 7 May 2026: https://www.localogy.com/2026/05/google-ai-mode-can-now-find-local-products-in-stock/
- CarEdge report: https://caredge.com/report
- CNN test of Muse, 23 September 2026 (syndicated): https://keyt.com/news/money-and-business/cnn-business-consumer/2026/09/23/meta-says-its-muse-ai-agent-can-do-things-for-you-i-put-it-to-the-test/
- Tom's Guide test of Muse, 26 September 2026: https://www.tomsguide.com/ai/i-tried-turning-metas-muse-ai-into-my-personal-shopper-only-3-of-7-prompts-actually-worked
- Layer3 Labs comparison of calling assistants, updated 25 October 2026: https://www.layer3labs.io/comparisons/ai-assistants-that-make-phone-calls
- iTnews copy of the Reuters report on Muse's human concierge (lead paragraph only): https://www.itnews.com.au/news/meta-testing-a-human-concierge-for-its-new-personal-ai-agent-muse-629106
- PartsClub: https://partsclub.com.au/how-it-works
- Kwibal: https://kwibal.com/
- Tripo on BetaList: https://betalist.com/startups/tripo
- Faircado: https://faircado.com/
- United Recyclers Group post on agents: https://u-r-g.com/the-ai-agents-are-coming-the-ai-agents-are-coming/

**Search summaries only**
- CarEdge price and launch: https://fortune.com/2025/09/10/this-30-year-old-ceo-says-his-ai-negotiator-can-successfully-haggle-down-the-price-of-a-car-by-thousands-of-dollars/
- Pine funding: https://www.businesswire.com/news/home/20251203384902/en · https://siliconangle.com/2026/05/06/pine-ai-aims-consumer-ai-agent-complex-customer-service-interactions/
- Reuters on Muse's human concierge, 22 September 2026: https://www.bnnbloomberg.ca/business/artificial-intelligence/2026/09/22/meta-testing-a-human-concierge-for-its-new-personal-ai-agent-muse-reuters-exclusive/
- 1st Choice Spares on Trustpilot: https://www.trustpilot.com/review/1stchoice.co.uk
- hipages FY26: https://www.marketindex.com.au/asx/hpg/announcements/fy26-full-year-results-announcement-2A1691277
- Airtasker FY26: https://quartr.com/events/airtasker-limited-art-h2-2026_FYV08Y8U
- Fetchlist: https://www.geekwire.com/2026/the-100-a-month-workforce-how-an-entrepreneur-bootstrapped-a-portland-delivery-startup-with-ai-bots/
- Duplex in Australia, 2020: https://venturebeat.com/2020/04/08/google-quietly-expands-duplex-to-the-u-k-australia-and-canada/
- Yard-side AI tools: https://eitserv.tech/en/ai-for-salvage-yards · https://autorecyclingworld.com/how-ai-is-helping-auto-recyclers-improve-efficiency-and-scale-operations/
- Business sourcing agents: https://techcrunch.com/2025/11/19/cavela-lands-6-6m-to-help-brands-beat-pre-tariff-manufacturing-costs/ · https://www.technologyreview.com/2026/04/06/1135118/ai-online-seller-alibaba-accio/amp/
- ChatGPT shopping research: https://help.openai.com/en/articles/11128490-using-shopping-research-in-chatgpt
- Flipify description: https://www.capterra.com.au/software/1105903/Flipify
- Second-hand participation in Australia: https://ragtrader.com.au/news/86-of-australians-buy-second-hand-survey-reveals

**Earlier reports relied on**
- `research/findings/second-pass/01-02-competitors.md` for every [P2] item
- `research/findings/second-pass/06-07-demand-and-market.md` for the forum and survey evidence
- `research/findings/02-competitors-used-and-cross-condition.md` and `research/findings/08-differentiation-and-moat.md`

**Refused automated requests; not read**
- producthunt.com, reddit.com, indiehackers.com, trustpilot.com, geekwire.com, grabbit.app, buywisely.com.au, shopbeni.com, help.openai.com
