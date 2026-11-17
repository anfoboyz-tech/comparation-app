# Track 3 — Data access and legal feasibility

Date: 2026-11-17. This is research, not legal advice. Points where a qualified Australian lawyer must be consulted are flagged **[LAWYER]**.

## Read this first: limits of tonight's research

This track was meant to check terms and API documentation at the source. That was only partly possible:

- **Direct page fetching was blocked** by the session's network policy (developer.ebay.com, affiliate-program.amazon.com and accc.gov.au were all refused). No terms-of-service page or API document was read in full tonight.
- **The web search budget ran out** after about 20 searches (the limit is shared by all eight agents). Searches on Australian privacy reform, every individual retailer's affiliate programme, Gumtree's terms, app store rules, and SERP-provider pricing did not run.

So every claim below carries one of three labels:

- **[S]** — supported by a search result retrieved tonight (a search-engine summary of the cited page, not my own reading of the full page).
- **[K]** — from my background knowledge (training data up to mid-2026), not re-checked tonight. Treat as a lead to confirm.
- **[I]** — my inference.

The legal framework and the big cases are solid. The retailer-by-retailer affiliate column is the weakest part of this document and needs about two hours of manual checking before anyone relies on it.

## 1. Bottom line

1. "Scan the entire internet" is not obtainable lawfully or reliably. What is obtainable is: eBay AU (official API), Amazon AU (official API, gated behind affiliate sales), retailers that publish affiliate product feeds, and Google Shopping results bought from a SERP vendor (legally grey, operationally fragile).
2. **Facebook Marketplace has no official route to listing data, and there is no sign one is coming to Australia.** The eBay–Meta arrangement runs the other way (eBay listings shown inside Marketplace) and is live only in the US, Germany and France [S]. Marketplace is the founder's own use case and the dominant local second-hand channel, so the app cannot search it server-side without scraping a hostile, litigious platform behind a login.
3. The durable way to include Marketplace is **user-assisted**: the shopper finds the listing in Facebook and hands it to the app (share sheet, pasted link, or screenshot read by a vision model). That turns the product from "we search everything for you" into "bring us any listing and we tell you if it is a good deal in ten seconds". This still removes the 50–100 minutes of the founder's story (checking new prices), though not the 20 minutes of searching Marketplace.
4. **eBay's API licence is more restrictive than expected.** Search results quoting the current agreement say eBay content may not be "co-mingled or combined with non-eBay Content" in a public display, may not be used "to suggest or model prices for items listed on eBay Sites", and needs written permission for anything that derives average selling prices [S]. Sold-price history (Marketplace Insights API) is a limited release for approved developers only [S]. A cross-site comparison list and a "what is this worth used" verdict both sit close to these clauses. This must be read at the source and cleared with eBay in writing before the design is fixed. **[LAWYER]**
5. Australian law has no decided case on scraping [S]. The practical risks are breach of website terms, the Criminal Code where an access control (a login) is bypassed, the Privacy Act where seller names, photos and locations are collected, and the Australian Consumer Law for how results are ranked and described. Facts such as prices are barely protected by copyright in Australia [K].
6. The US position on AI agents acting for a user improved in August 2026: the Ninth Circuit vacated Amazon's injunction against Perplexity's Comet and held that the user, not the agent's developer, is the one accessing the site [S]. That is a preliminary ruling under one US statute, it is being contested, and it does not bind Australian courts or override a platform's terms against the user. It lowers the risk of an "agent in the user's own session" design; it does not make it safe.
7. Realistic launch coverage, by my estimate (low confidence, no verified market-share data): official and affiliate routes can cover most big-retailer new prices in mainstream categories, but only a minority of second-hand listings (eBay only). The second-hand side depends on the user-assisted route.
8. The feasible version of this product is a **deal-verdict tool with strong new-price coverage and user-supplied second-hand listings**, not a universal second-hand search engine.

## 2. Findings

### 2.1 Source-by-source access table

Ratings: **Open** = official route available to a new entrant. **Gated** = official route exists but needs approval, sales history, or a contract. **Hostile** = no official route and terms or technical defences against automated access.

#### New goods, Australia

| Source | Official API or feed | Affiliate programme | Terms on automated access / enforcement | Rating | Confidence |
|---|---|---|---|---|---|
| eBay AU (new and used, live listings) | Browse API supports the AU marketplace; Feed API (beta) also lists AU [S]. Free. Default call limits apply, higher after an "Application Growth Check" [S]; the commonly cited default is 5,000 calls a day, which I could not confirm at the source. Licence restrictions on co-mingling, price modelling and AI use — see 2.2. | eBay Partner Network covers AU [K]. | API licence governs; scraping the site is prohibited by the user agreement [K]. | Open, with licence constraints that may conflict with the product | High on availability, medium on licence reading |
| Amazon AU | Product Advertising API 5.0 has been deprecated and replaced by the Creators API (OAuth 2.0; new credentials needed) [S]. Amazon's own pages gave 15 May 2026 for the PA-API retirement; third parties also cite 30 April 2026 [S]. Third-party sources say access needs 10 qualifying referred sales in the previous 30 days [S] — not confirmed on Amazon's pages, and not confirmed for the AU locale. API use is tied to the marketplace where you are an Associate [S]. | Amazon Associates Australia. Accounts without early sales are closed (three sales in 180 days, [K]). | Price shown must come from the API or an Amazon-served link, with a date/time stamp; comparison displays must show lowest new price and lowest used price where provided [S]. Site conditions of use prohibit robots and data mining [K]. Amazon has sued over an AI agent (see 2.5). | Gated (chicken-and-egg: need sales to get the API) | Medium |
| Kogan | No public product API known [K]. | Believed to run an affiliate programme with a feed [K, low]. | Standard anti-bot terms assumed; not read. | Gated | Low |
| Catch | Wesfarmers announced the closure of Catch in January 2025, with wind-down by mid-2025 [K]. A Commission Factory case study still names Catch as a merchant, but it is undated [S]. Treat as closed and remove from the list unless another track found otherwise. | — | — | Leave out | Medium |
| JB Hi-Fi, The Good Guys | No public API [K]. | Affiliate programmes believed to exist (Commission Factory or similar) [K, low]; search tonight did not confirm [S]. | Not read. | Gated, unconfirmed | Low |
| Harvey Norman, Officeworks, Bunnings | No public API [K]. | Not confirmed. I recall Bunnings and Officeworks having affiliate programmes; I cannot place Harvey Norman [K, low]. | Not read. | Unconfirmed | Low |
| BCF, Rebel, Supercheap Auto (Super Retail Group), Anaconda | No public API [K]. | I believe Super Retail Group brands and Anaconda are on Commission Factory [K, low]. BCF matters most for the founder's own example and should be checked first. | Not read. | Gated, unconfirmed | Low |
| Big W, Kmart, Target, Myer, David Jones, Decathlon AU | No public API [K]. | Most large Australian department and discount retailers run programmes through Commission Factory, Rakuten or Impact [K, low per retailer]. | Not read. | Gated, unconfirmed | Low |
| Shopify-based independents | Each store exposes `/products.json` by default and Schema.org product markup [K]. Shopify has been building a cross-merchant catalogue for AI shopping agents (2025–26) [K, medium]; access terms not checked. | Per store, often none. | Each store's own terms; Shopify platform terms. Low enforcement in practice [I]. | Open technically, permission varies per store | Medium |

How to confirm the affiliate column quickly: create a free publisher account on Commission Factory, Impact, Rakuten and Partnerize and search each merchant directory. Commission Factory exposes an affiliate API with a `GetDataFeeds` function returning XML or JSON, with rate limits [S], and reportedly requires merchants with ten or more products to supply a feed [S, third-party]. Commission Factory is owned by Awin [S]. Kelkoo runs comparison shopping on roughly 70 Awin and Commission Factory programmes including Bing Lee, Glassons and Gorman [S], which shows comparison publishers are accepted on the network.

Two cautions on affiliate feeds [K]:
- Each merchant approves each publisher individually and can refuse comparison or app publishers, or restrict feed use.
- Feeds are usually refreshed daily, so prices and stock can be stale. Displaying a stale lower price creates Australian Consumer Law exposure (2.4).

#### Used and peer-to-peer

| Source | Official route | Terms / enforcement | Rating | Confidence |
|---|---|---|---|---|
| Facebook Marketplace | None for reading listings. Meta's partner APIs let approved partners push listings into Marketplace [S, K]. | Terms ban collecting data by automated means without permission [S]. Login required for most use. Meta has sued scrapers repeatedly. See 2.3. | Hostile | High |
| Gumtree AU | No public API found [S]. | Third-party scraper listings report Akamai bot protection and rejection of datacentre sessions [S]. Terms not read; I expect a standard ban on robots and scraping [K]. A partnership or licensed feed is conceivable for a business of Gumtree's size and should be asked for directly [I]. | Hostile by default, possibly negotiable | Medium |
| eBay AU, used live listings | Browse API with condition filters [K]. | As above. | Open | High |
| eBay AU, sold listings | Marketplace Insights API returns up to 90 days of sales history, AU supported, but it is a limited release for developers approved by eBay business units [S]. The old Finding API route to completed listings was decommissioned in early 2025 [K]. | Deriving average selling prices needs eBay's written permission [S]. | Gated, unlikely for a new entrant | Medium–high |
| Cash Converters | No API known; webshop pages carry product markup [K]. | Not read. | Unconfirmed; small and approachable — ask [I] | Low |
| Carousell | Whether Carousell still operates in Australia was not verified. | — | Unverified | Low |
| Depop | No public buyer-side API [K]. | Not read. | Hostile / unconfirmed | Low |
| Reebelo, Back Market | Refurbished retailers with affiliate programmes and feeds [K, medium]. | — | Gated but obtainable | Medium |
| Grays, Lloyds Auctions | No API known [K]. Auction prices move, so feeds would mislead anyway [I]. | Not read. | Leave out at launch | Low |
| Local pawn and resale chains | None. | — | Leave out | Low |

#### Aggregated feeds and data vendors

| Source | What it actually is | Usable? | Confidence |
|---|---|---|---|
| Google Merchant Center / Content API / Merchant API | A way for **merchants** to upload their own products. The Content API for Shopping was sunset on 18 August 2026 and replaced by the Merchant API [S]. Neither lets a third party query Google's Shopping index [S, K]. | No | High |
| Google Shopping product search API | None for third parties. The old Search API for Shopping was retired in 2013 [K]. Google's agent-commerce protocols announced in 2026 are for agents transacting with merchants, not an open price index [K, medium]. | No | Medium–high |
| Bing Shopping | The Bing Search APIs were retired in August 2025 [K]. No public shopping API. | No | Medium–high |
| Affiliate networks (Commission Factory, Awin, Impact, Rakuten, Partnerize, CJ) | Product datafeeds per approved merchant. Commission Factory API confirmed [S]. | Yes — the main lawful source for Australian retail prices | Medium |
| SERP providers (SerpApi, DataForSEO, Oxylabs, Bright Data, Zyte, PriceAPI) | They scrape Google Shopping, Amazon, eBay and others and resell structured results; Australian localisation is generally offered [K]. Prices not checked tonight; roughly US$1–15 per thousand queries depending on vendor and speed [K, low]. | Technically yes. Legally the scraping risk sits mostly with the vendor, but you are still displaying data taken against the source's terms. Supply is fragile: Google sued SerpApi in December 2025; the court dismissed Google's DMCA claims on 20 July 2026 with a path to amend, and the case was still moving in late August [S]. Reddit's separate suit continues [S]. | Medium |
| Schema.org product markup | Most retailers publish price, availability and identifiers in page markup because Google requires it [K]. Reading it still means crawling each retailer's site, which their terms and bot defences usually prohibit [I]. | Only with permission, or for user-initiated single-page reads | Medium |

### 2.2 eBay licence — the clauses that matter

Search results tonight quote the current eBay API License Agreement (updated 24 June 2025) [S]:

- "eBay Content in a Public Display may not be co-mingled or combined with non-eBay Content. For example, all eBay Content in a Public Display must be visually isolated from third-party listings or other non-eBay information."
- You may not "use eBay Content, either alone or in combination with third-party information, to suggest or model prices for items listed on eBay Sites."
- "You must have eBay's express prior written permission to use or display eBay Content in any way that enables derivation of" statistics such as average selling prices.
- "Restricted APIs" are those that "provide information about market trends, pricing strategies, sales volumes, user behavior, or provide generated content"; data from them may not be fed into generative AI tools without eBay's consent. The June 2025 update added AI restrictions more generally.
- The developer is responsible for binding its own users to the agreement.

What this means [I]:
- A single ranked list mixing eBay, Amazon and BCF offers is, on its face, co-mingling. A separate, visually isolated "eBay" section may comply. Developers on eBay's forum have asked exactly this for comparison apps and I found no official answer [S].
- A verdict such as "this used reel is worth about $140 based on eBay" is close to the price-modelling and average-price clauses, and passing eBay data through an LLM may engage the AI clauses.
- Comparison sites do show eBay offers, so permissions exist through eBay Partner Network arrangements [K]. The route is to apply to EPN and ask eBay in writing about the exact display.

**[LAWYER]** and a written answer from eBay are needed before building on eBay data. I could not open the agreement itself tonight.

### 2.3 Facebook Marketplace in depth

**Official routes.** None for reading listings [K, high]. Meta's Marketplace partner programme is inbound: partners use a Meta-built API to place and update their own listings on Marketplace [S]. The eBay–Meta pilot from January 2025 shows selected eBay listings on Marketplace in the US, Germany and France, with checkout on eBay; it was offered in response to EU antitrust charges and later widened to other EU classifieds businesses [S]. I found no extension to Australia [S]. Nothing in it gives outsiders Marketplace data.

**Meta's terms.** The Terms of Service say users "may not access or collect data from our Products using automated means (without our prior permission)" (section 3.2.3) [S, via secondary sources]. Meta revised its terms effective 1 January 2025 with clarified misuse wording, and a clause-tracking site reports the ban now applies whether or not the visitor is logged in [S, secondary; not read at source].

**Cases.**
- *Meta v. BrandTotal* (N.D. Cal., 2022): a browser extension that collected data through logged-in users' sessions was found to breach section 3.2.3 [S]. This is the closest precedent for a user-side extension that harvests Marketplace data.
- *Meta v. Bright Data* (N.D. Cal., 23 January 2024): summary judgment for Bright Data. Meta's terms as then written bound logged-in users and did not reach logged-out scraping of public data; Meta could not bind Bright Data after it closed its accounts. Meta dropped its remaining claim in February 2024 and waived appeal [S]. The court did not address scraping behind a login, and the ruling interprets only Meta's then-current terms [S].
- Why Bright Data does not rescue a Marketplace scraper [I]: (a) Marketplace search, especially local results, largely needs a login, and reports on logged-out access are inconsistent [S]; (b) Meta has since reworded its terms; (c) it is a single US district court decision on US contract law; (d) technical blocking makes such a scraper unreliable regardless of legality.

**How others do it.**
- *Swoopa* (publisher Market Sourcing Solutions Pty Ltd, apparently Australian; on the App Store as of tonight's search): sends alerts for new listings on Facebook Marketplace, Gumtree, eBay and others. It says it "isn't a scraper" and is "fully compliant", without explaining how; its own blog publishes a guide to scraping Marketplace [S]. I found no report of Meta acting against it [S]. My inference is that it relies on automated access that Meta's terms prohibit and survives because it is small. That is evidence the approach works for a while, not that it is lawful or durable.
- *Phia* (US, fashion): a browser and Safari extension reads the product page the user is already on, sends details to Phia's servers, and returns matches from resale sites such as eBay, Poshmark, The RealReal and Depop; revenue is affiliate commission [S]. How it sources each resale site (API, affiliate feed or scraping) is not public [S]. In 2025 researchers reported the extension captured full page HTML, including a banking login URL, and Bloomberg reported hidden background tabs injecting affiliate links at checkout [S]. Phia does not cover Facebook Marketplace as far as I found.
- *Beni*: not checked tonight; status unknown.
- Scraping vendors sell Marketplace scrapers and datasets [K]; buying from them does not change the terms position for an app that displays the data.

**Options, rated.**

| Option | How it works | Lawful? | Durable? |
|---|---|---|---|
| Server-side scraping (own or bought) | Bots query Marketplace, usually with accounts | Breaches Meta's terms; login bypass raises Criminal Code questions in Australia; collects seller personal information | No. Blocks, bans, legal letters. |
| User pastes link or uses share sheet | User shares a listing URL from the Facebook app; the app receives the URL | Yes for receiving the URL. Fetching the page server-side is automated access, small in scale and similar to link-preview fetching, but still within the terms' wording and often met by a login wall [I] | High for the hand-off; low for the server fetch |
| Screenshot plus vision model | User screenshots the listing; the app extracts title, price, condition, location | Yes. No access to Meta's systems. Privacy: avoid storing seller names and faces | High. Best single option. |
| In-app browser with the user's own login | User logs into Facebook inside the app's web view; the app reads the pages the user views | Grey. The user is bound by 3.2.3; BrandTotal went against this pattern; the Ninth Circuit's Perplexity ruling points the other way on a different statute. Handling Facebook credentials or sessions is a serious trust and app-review risk | Low–medium. Meta can detect web views and block them; user accounts can be restricted. |
| User-side browser extension | Reads the Marketplace page in the user's desktop browser | Same grey zone; safest if it processes only the page in view, on the user's command, and does not build a server-side database of listings | Medium on desktop; Marketplace use is mostly mobile, where extensions are limited to Safari |
| Agentic "search Marketplace for me" using the user's session | An AI agent drives the user's logged-in session | Greyest. See 2.5 | Low |

Lawful and durable: share sheet, pasted link, screenshot. Fragile: everything that automates a logged-in session. Not viable: server-side scraping.

### 2.4 Law

**Australia**

- **Contract (terms of service).** Whether scraping in breach of website terms is actionable has not been judicially considered in Australia; breach of contract is plausible where terms expressly prohibit commercial scraping, with doubt over whether a contract forms when no human accepts terms [S, King & Wood Mallesons]. Logging in or holding an API key removes that doubt [I]. **[LAWYER]**
- **Copyright and databases.** Australia has no separate database right. After *IceTV v Nine Network* (High Court, 2009) and *Telstra v Phone Directories* (Full Federal Court, 2010), factual compilations get little or no copyright protection [K]. Prices, model names and availability are facts. Listing photos and seller-written descriptions are copyright works, and copying a substantial part without authority may infringe [S, K]. Practical rule: show facts and link out; use images only under an API or affiliate licence. **[LAWYER]**
- **Criminal Code (Cth), Part 10.7.** Section 478.1 covers unauthorised access to "restricted data", meaning data protected by an access control system [K]. Public pages are unlikely to qualify; data behind a login can. Using fake or borrowed accounts to scrape Marketplace is the scenario to avoid. Commentary puts criminal exposure mainly on bypassing security or entering restricted areas [S]. **[LAWYER]**
- **Privacy Act 1988.** Second-hand listings contain seller names, profile photos, suburbs and sometimes phone numbers, all personal information [K]. Points to check, none verified tonight because the search did not run:
  - The small-business exemption (turnover of $3 million or less) does not apply to businesses that trade in personal information [K].
  - The Privacy and Other Legislation Amendment Act 2024 created a statutory tort for serious invasions of privacy (in force June 2025), stronger regulator powers, and transparency duties for automated decisions due to start in December 2026 [K, medium]. Whether the second round of reforms (removing the small-business exemption, a "fair and reasonable" test) has been legislated is unknown to me.
  - The privacy regulator's Clearview AI determination (2021) treated scraping of publicly available personal data as collection by unfair means, and regulators issued joint statements on scraping in 2023 and 2024 [K].
  - Design response: never store seller identity; keep only item facts; process screenshots without retaining faces or names. **[LAWYER]**
- **Australian Consumer Law and the regulator's comparison-site guidance.** The ACCC's 2015 guide for comparator websites sets three principles: accurate like-for-like comparisons, transparency about commercial relationships, and clarity about who and what is compared [S]. Operators should disclose commercial relationships even where they do not affect results, label sponsored or promoted results, and not claim impartiality if ranking reflects preferential deals [S]. I did not check for an update since 2015. Enforcement shows the stakes: Trivago was penalised $44.7 million in 2022 for presenting paid-ranking results as the best prices, and iSelect $8.5 million in 2020 [K]. For this app:
  - Do not say "searches the whole internet", "every retailer" or "best price" unless true. State which sources are covered.
  - If ranking or inclusion depends on affiliate commission, say so prominently. Better, rank by total price and disclose that some links earn commission.
  - "Worth it" verdicts are representations. State the basis and the data date. An AI verdict presented confidently on stale or thin data is the main exposure.
  - Show a time stamp on prices (Amazon requires it in any case [S]).
- **Spam Act 2003.** Bans harvesting email addresses and governs marketing messages; relevant only if contact details were collected from listings, which the design should avoid [K].
- **Consumer Data Right.** Covers banking and energy, not retail product data [K]. Not relevant.

**United States and European Union reference points** (all [K] unless marked)

- *Van Buren v. United States* (2021): the federal computer-crime statute is about entering areas that are off-limits ("gates up or down"), not misusing permitted access.
- *hiQ v. LinkedIn*: the Ninth Circuit (2019, reaffirmed 2022) held scraping public pages probably does not violate that statute; hiQ then lost on breach of contract and the case ended in 2022 with a judgment against it. Not criminal, still a contract breach.
- *Meta v. Bright Data* (2024): see 2.3 [S].
- *X Corp v. Bright Data* (N.D. Cal., May 2024): claims over scraping public posts dismissed, largely as pre-empted by copyright law; later history not checked.
- *Google v. SerpApi* (2025–26): attempt to use anti-circumvention law against search scraping failed at the first stage [S].
- *Ryanair v PR Aviation* (EU Court of Justice, 2015): where a database is not protected by copyright or the database right, the owner is free to restrict use by contract. In the EU, terms can bite harder on unprotected data.
- EU Database Directive: a separate right against extracting substantial parts of a database built with substantial investment. Classifieds and marketplace databases plausibly qualify. No Australian or US equivalent. Matters for EU expansion.
- GDPR: scraping personal data needs a lawful basis; regulators have fined scrapers. Seller data in EU listings would need the same exclusion as proposed for Australia.

Overall [I]: US law has moved in scrapers' favour on public, logged-out data, and platforms still win where there is a login, an account or a clear contract. Australia is untested and has a stricter privacy regulator stance. None of the favourable US rulings covers logged-in Marketplace data.

### 2.5 AI agents acting for a user

- Amazon sued Perplexity in November 2025 over the Comet browser's shopping agent [K]. The district court granted a preliminary injunction in March 2026; the Ninth Circuit stayed it and on 4 August 2026 vacated it in *Amazon.com Services LLC v. Perplexity AI, Inc.*, No. 26-1444, holding that when a user directs the assistant to act on Amazon.com, the user, not Perplexity, is accessing Amazon's computers, so Amazon was unlikely to succeed on its computer-fraud claims [S]. Amazon petitioned for rehearing by the full court on 18 August 2026 [S]. One outlet reports the petition was denied; I could not confirm that [S].
- Limits [I]: a preliminary-stage ruling; it concerns computer-access statutes, not Amazon's contract claims; it is being contested; it is US law. In Australia the equivalent questions are open.
- Platforms set their own rules and block technically. Commentary in 2026 describes platforms with leverage writing agent rules unilaterally [S]. Amazon blocks most third-party shopping agents [K].
- Effect on risk [I]: an agent running on the user's device, in the user's session, at the user's instruction, is now easier to defend in the US than a server-side scraper. It remains exposed to terms claims against the user and the developer (BrandTotal), to blocking, and to app-store review. It is a reasonable later-stage option for retailer sites that tolerate it. It is not a foundation for launch, and not for Facebook.

### 2.6 App store policy

Not checked at the source tonight (apps.apple.com and policy pages were unreachable and the search budget was spent). All [K]; confirm against the current App Review Guidelines and Google Play Developer Program Policies before submission.

- **Apple 5.2.2 (third-party sites and services):** an app that uses or displays content from a third-party service must be permitted to do so under that service's terms, and Apple can ask for proof of authorisation. A scraper-backed app can be rejected or removed on a complaint from Meta or a retailer.
- **Apple 5.2.1 and trademarks:** retailer names may be used to identify sources; do not use logos or imply endorsement without permission. Affiliate programmes usually license logos.
- **Apple 4.2 and 4.2.2:** apps that are mainly web clippings, content aggregators or collections of links can be rejected for minimum functionality. The verdict and comparison logic need to be visibly native.
- **Apple 3.1.3(e):** physical goods are bought outside in-app purchase, so affiliate links out to retailers are allowed. Subscriptions for premium features must use in-app purchase.
- **Apple 5.1.1 and 5.1.2(i):** disclose data collection; since late 2025 apps must disclose and get permission before sending personal data to third-party AI services. Relevant to screenshots sent to a vision model.
- **In-app browsers:** allowed with the system web engine. Injecting scripts into a third-party logged-in session to extract data is the kind of behaviour that draws review and platform complaints. Phia's extension episode shows the reputational cost [S].
- **Google Play:** the spam policy prohibits apps whose main purpose is to drive affiliate traffic to a site, or to wrap a site in a web view without permission. The AI-generated content policy requires a way for users to report problematic generated output. The user-data policy requires prominent disclosure. Impersonation and intellectual-property policies cover third-party marks.
- **AI advice:** neither store bans AI purchase advice. The risk is misleading claims, which is a consumer-law matter (2.4).

### 2.7 Recommended data strategy

**Tier 1 — launch, official and affiliate routes**

| Source | Route | Blocking dependency |
|---|---|---|
| Australian retailers with affiliate feeds | Commission Factory first, then Impact, Rakuten, Partnerize, Awin | Per-merchant approval; confirm BCF, Anaconda, JB Hi-Fi, Bunnings, Officeworks, Kmart, Big W are present |
| eBay AU, new and used live listings | Browse API plus eBay Partner Network | Written clarity from eBay on co-mingling and price-verdict use |
| Amazon AU | Associates links from day one; Creators API once the sales threshold is met | Sales threshold; until then, link out to Amazon search without showing a price |
| Refurbished specialists (Reebelo, Back Market) | Affiliate feeds | Approval |
| Shopify independents | Opt-in or per-store permission; published feeds | Outreach |

**Tier 2 — user-assisted**

| Source | Route |
|---|---|
| Facebook Marketplace | Share sheet, pasted link, screenshot with vision extraction. The user does the searching in Facebook; the app does the valuing and comparing. |
| Gumtree | Same at launch; ask Gumtree for a licensed feed or partnership in parallel |
| Any retailer not in Tier 1 | The user shares a product page; the app reads that one page's product markup on the user's request. Low volume, user-initiated, defensible; confirm with a lawyer |
| Later option | On-device agent in the user's session for tolerant sites, once the law and platform positions settle |

**Tier 3 — leave out or treat with caution**

- Server-side scraping of Facebook Marketplace, Gumtree, Depop, Carousell.
- eBay sold-price data, unless eBay grants Marketplace Insights access.
- Auction houses and local pawn chains at launch.
- SERP-vendor Google Shopping data as a production dependency. It is acceptable for prototyping and for filling gaps where no feed exists, with eyes open: the upstream source objects, supply can break, and the co-mingled display and "best price" claims carry consumer-law risk if the data is wrong.

**Coverage estimate.** I found no verified market-share data tonight, so these are reasoned guesses. Track 1 or 2 may have real figures; use theirs over mine.

| Tier | Share of relevant listings for a typical shopper | Reasoning | Confidence |
|---|---|---|---|
| Tier 1, new goods | Perhaps 50–70% of the offers a shopper would check for mainstream categories (electronics, appliances, outdoor, sport) | Large chains dominate Australian retail, and most appear to run affiliate programmes. Falls sharply if key chains (Bunnings, Harvey Norman, JB Hi-Fi) refuse feed access or have no programme. Niche categories such as fishing tackle depend on BCF, Anaconda and specialists being reachable. | Low |
| Tier 1, used goods | Perhaps 10–25% | eBay is the only official source. Local-pickup second-hand trade in Australia is mostly Facebook Marketplace and Gumtree. | Low |
| Tier 2, used goods | Potentially most of the rest, but only for listings the user finds personally | Coverage becomes whatever the user brings. The app cannot say "there is a better one two suburbs away" on Marketplace. | Medium on the logic |
| Tier 3 | The remainder | Not obtainable durably. | — |

## 3. Implications for the product

1. **Change the promise.** "We search everywhere" cannot be delivered honestly and would be a misleading claim under consumer law. "Show us any listing and we tell you in seconds whether it is a good deal, and where to get it cheaper new" can be delivered, and it matches the larger part of the founder's own pain.
2. **Make the hand-off from Facebook effortless.** Share-sheet target, screenshot recognition, and paste detection are the core of the experience. That is where product quality will be judged.
3. **The used-price reference is the hard part.** Without eBay sold data, the "is this used price fair" judgement must come from the new price (Tier 1), live eBay asking prices (if eBay permits that use), and the app's own record of listings users submit. That record, built only from item facts, becomes a proprietary asset that grows with use and that no competitor can scrape from the app. Early verdicts will be weaker than later ones; say so in the product.
4. **Secure eBay and Commission Factory before writing much code.** Two applications and two emails decide whether Tier 1 exists. Ask eBay specifically about a mixed comparison list and a price verdict.
5. **Solve the Amazon cold start.** Launch with Amazon affiliate links without displayed prices, earn the qualifying sales, then switch on the API.
6. **Design for privacy from the start.** Store item, price, condition, suburb-level location and date. Do not store seller names, faces or profile links.
7. **Build disclosure into the interface.** Source list, price time stamps, commission disclosure and the basis of every verdict. Cheap to do, and it is what the regulator's guidance asks for.
8. **Avoid logged-in Facebook automation.** It is the tempting shortcut and the one that can end the company: account bans for users, removal from the app stores under Apple's 5.2.2, and a plaintiff with a record of suing.
9. **Opening.** The big comparison engines have feeds but ignore second-hand; the Marketplace alert tools scrape and do not value. A lawful deal-verdict tool between them is feasible. Its ceiling is set by how much searching the user will still do personally.

## 4. Open questions

| Question | How to settle it |
|---|---|
| Exact current wording of eBay's API licence on co-mingling, price modelling, AI use, and whether Browse is a "Restricted API"; Browse daily call limit | Read developer.ebay.com/join/api-license-agreement and the call-limits page; email eBay developer support with a mock-up; lawyer review |
| Creators API eligibility for Amazon Australia (sales threshold, mobile-app approval, caching limits, AI restrictions) | Read affiliate-program.amazon.com.au operating agreement and Creators API documentation |
| Which Australian retailers have affiliate programmes with product feeds, and whether they accept comparison apps | Publisher accounts on Commission Factory, Impact, Rakuten, Partnerize; search directories; apply |
| Gumtree's terms and appetite for a licensed feed | Read the terms; contact Gumtree business development |
| Whether Meta's 2025 terms close the logged-out gap from *Bright Data* | Read Meta's current Terms of Service section 3.2.3 |
| Status of Amazon's rehearing petition in *Amazon v. Perplexity*; status of *Google v. SerpApi* after August 2026 | Court dockets or legal news |
| Status of Australian Privacy Act second-round reforms; whether the small-business exemption still exists | Privacy regulator and Attorney-General's Department pages; lawyer |
| Whether a single user-initiated read of a retailer page or link preview breaches terms in a way that matters | Lawyer |
| Current Apple and Google Play wording | Read the guidelines at the source |
| SERP-vendor pricing and Australian Google Shopping coverage quality | Vendor pricing pages; a one-day trial on 50 real queries, including fishing gear |
| Whether Catch, Carousell AU and Beni still operate | Their sites and app-store listings |
| Real share of second-hand listings by platform in Australia | Other tracks; platform reports |

To redo this track properly, the session needs outbound access to at least: developer.ebay.com, affiliate-program.amazon.com.au, affiliate-program.amazon.com, www.accc.gov.au, www.oaic.gov.au, www.facebook.com (terms pages), developers.facebook.com, www.gumtree.com.au, developer.apple.com, support.google.com, dev.commissionfactory.com — plus a fresh search allowance.

## 5. Sources

Retrieved through search tonight (summaries, not full-page reads):

eBay
- https://developer.ebay.com/join/api-license-agreement
- https://developer.ebay.com/cms/files/api_license_2017-05-25_final.pdf
- https://developer.ebay.com/develop/get-started/api-call-limits
- https://www.developer.ebay.com/api-docs/buy/ref-marketplace-supported.html
- https://www.developer.ebay.com/api-docs/buy/marketplace-insights/overview.html
- https://developer.ebay.com/develop/buying-apps/research-apis
- https://community.ebay.com/forum/ebay-developers-program-57950/topic/policy-clarification-private-filament-price-comparison-app-using-the-browse-api-483314/
- https://community.ebay.com/t5/eBay-APIs-Talk-to-your-fellow/Questions-about-the-API-license-agreement/td-p/34247390
- https://www.ecommercebytes.com/2025/07/18/ebay-restricts-developers-from-using-its-data-to-train-ai/
- https://github.com/BoPeng/ai-marketplace-monitor/issues/483

Amazon
- https://affiliate-program.amazon.com/creatorsapi/docs/en-us/paapiv5-deprecation
- https://affiliate-program.amazon.in/creatorsapi/docs/en-us/migrating-to-creatorsapi-from-paapi
- https://affiliate-program.amazon.com/gp/associates/help/operating/linking/
- https://dev.to/th3nate/amazon-pa-api-v5-is-shutting-down-april-30-2026-here-is-what-changes-at-the-auth-layer-22ek
- https://affiliatexblocks.com/docs/amazon-creators-api/
- https://affiliate-program.amazon.com.au/help

Meta and Facebook Marketplace
- https://techcrunch.com/2024/02/26/meta-drops-lawsuit-against-web-scraping-firm-bright-data-that-sold-millions-of-instagram-records/
- https://www.quinnemanuel.com/the-firm/news-events/client-alert-meta-v-bright-data-significant-decision-for-web-scraping-industry/
- https://blog.ericgoldman.org/archives/2024/01/game-on-bright-data-scores-major-victory-in-web-scraping-dispute-with-meta-guest-blog-post.htm
- https://www.mediapost.com/publications/article/392920/bright-data-didnt-violate-metas-terms-by-scrapin.html
- https://www.courthousenews.com/judge-rules-brandtotals-data-harvesting-violates-metas-terms-of-use-and-anti-hacking-laws/
- https://www.socialmediatoday.com/news/metas-updating-its-terms-of-service-with-clarified-wording-around-misuse/732577/
- https://conductatlas.com/platform/meta/meta-terms-of-service/automated-data-collection-restrictions/
- https://about.fb.com/news/2023/01/leading-the-fight-against-scraping-for-hire/
- https://www.ebay.com/help/selling/listings/ebay-listings-facebook-marketplace?id=5559
- https://valueaddedresource.net/ebay-facebook-marketplace-partnership
- https://www.valueaddedresource.net/meta-expands-eu-facebook-marketplace-partnership/
- https://thenightly.com.au/society/technology/meta-tries-letting-facebook-marketplace-users-view-ebay-listings-as-way-to-resolve-eu-charges-c-17348083
- https://www.howtogeek.com/887438/you-can-browse-facebook-marketplace-without-an-account/
- https://fastcompany.com/91629388/ai-agents-have-no-rules-so-meta-wrote-its-own

Comparable tools
- https://apps.apple.com/us/app/swoopa/id6475300269
- https://getswoopa.com/tools-to-automate-facebook-marketplace-alerts
- https://getswoopa.com/how-to-scrape-facebook-marketplace/
- https://www.digitalcommerce360.com/2025/04/28/phia-ecommerce-startup-phoebe-gates/
- https://chromewebstore.google.com/detail/phia-best-price-in-one-cl/ehoknmhmadiboejdbinglmbnlghnbldc
- https://www.nowsecure.com/blog/2025/11/19/inside-a-mobile-apps-data-overreach-what-our-phia-safari-extension-analysis-reveals/

AI agents and scraping litigation
- https://www.wsgrdataadvisor.com/2026/08/ninth-circuit-addresses-cfaa-and-agentic-ai-tools-in-groundbreaking-decision/
- https://blog.ericgoldman.org/archives/2026/08/ninth-circuit-lifts-restrictions-on-agentic-ai-accessing-amazon.htm
- https://www.americanbar.org/groups/litigation/resources/newsletters/privacy-data-security/ninth-circuit-holds-human-user-not-developer-ai-agent-responsible-websites-accessed/
- https://www.courthousenews.com/ninth-circuit-lifts-block-on-ai-powered-shopping-assistant/
- https://www.ballardspahr.com/insights/alerts-and-articles/2026/08/ninth-circuit-opines-on-agentic-ai-in-e-commerce
- https://paymentexpert.com/2026/03/19/amazon-secures-injunction-perplexity/
- https://searchengineland.com/google-loses-key-dmca-claims-against-serpapi-in-scraping-lawsuit-483185
- https://serpapi.com/blog/google-v-serpapi-the-court-granted-our-motion-to-dismiss/
- https://ppc.land/google-faces-21-day-deadline-to-save-its-dmca-case-against-serpapi/

Google
- https://developers.google.com/shopping-content/guides/deprecation-and-sunset
- https://developers.google.com/merchant/api/latest-updates

Affiliate networks
- https://dev.commissionfactory.com/V1/Affiliate/Functions/GetDataFeeds/
- https://help.commissionfactory.com/what-is-a-datafeed-and-how-do-affiliates-use-them
- https://www.commissionfactory.com/market-insights/affiliate-marketing/case-study-kelkoo-optimising-datafeeds-for-comparison-shopping
- https://mulwi.com/commission-factory-feed/

Gumtree
- https://apify.com/abotapi/gumtree-au-scraper.md
- https://apify.com/muhammadafzal/gumtree-scraper-au-uk-nz-za

Australian law and regulator guidance
- https://www.mallesons.com/au/en/insights/latest-thinking/screen-scraping.html
- https://sprintlaw.com.au/articles/web-scraping-essential-australian-legal-guidelines/
- https://legalvision.com.au/scrape-data/
- https://www.accc.gov.au/publications/comparator-websites-a-guide-for-comparator-website-operators-and-suppliers
- https://www.accc.gov.au/system/files/CSBS%20-%20Comparator%20web%20sites%20project%20-%20Industry%20Guidance%20-%20final.pdf
- https://accc.gov.au/media-release/accc-releases-comparator-website-guidance
- https://www.brightlaw.com.au/guide-for-comparator-website-operators-and-suppliers/

Not sourced tonight (background knowledge, labelled [K] in the text): hiQ v. LinkedIn, Van Buren, X Corp v. Bright Data, Ryanair v PR Aviation, the EU Database Directive, GDPR, IceTV, Telstra v Phone Directories, Criminal Code Part 10.7, the Privacy Act and its 2024 amendments, the Clearview AI determination, the Trivago and iSelect penalties, the Spam Act, Apple and Google Play policy clauses, individual retailer affiliate memberships, the Catch closure, and SERP-vendor pricing.
