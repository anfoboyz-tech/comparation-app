# Second pass — data access and legal

Read on 2026-11-17. Checks `research/findings/03-data-access-and-legal.md` and the cost rows of `research/findings/05-technical-architecture.md`. This is research, not legal advice; **[LAWYER]** marks points for a qualified Australian lawyer.

How pages were read: `curl` with a browser user-agent, or headless Chromium for pages that need JavaScript. `developer.ebay.com` returned 403 to this session, so the eBay documents were read on eBay's own second developer host, `www.edp.ebay.com`, which serves the same portal. 15 of the 25 allowed searches were used.

## 1. What changed

Most important first.

1. **eBay's Buy APIs (Browse included) are not open to a new entrant in production.** eBay's requirements page says: "The use of eBay's Buy APIs in production is intended for eBay partners only. You must apply for production access through the eBay Partner Network." It adds that applicants must "get approvals from eBay support organizations, and sign contracts with eBay", and "We advise you to complete the Production application process and obtain approval before you invest significantly in application development and testing." The first pass rated eBay "Open". It is gated: an eBay Partner Network account, a Buy API application with mock-ups and data flows, a reply within 10 business days, then a compliance review and contracts.
2. **The eBay licence clauses are real and were quoted correctly, and two more clauses matter as much.**
   - Storage and freshness: listing data shown may be no more than six hours older than eBay's site; copies must be deleted when no longer needed; content must be deleted once it is no longer public on eBay. So eBay prices cannot go into the app's long-term price history, which report 05 treats as the future fair-value dataset.
   - Training: eBay Content may not be used "to train algorithms, conduct machine learning ... train large learning models". Fitting any pricing or depreciation model on eBay data is barred. Passing a search result through an LLM at query time is not training, and the stricter "no ingestion into AI" rule applies only to Restricted APIs (see 3 below).
3. **A separate eBay section probably satisfies the co-mingling clause; the fair-price range is the harder problem.** The clause's own example is visual isolation "from third-party listings or other non-eBay information". The price clause bars using eBay Content "either alone or in combination with third-party information, to suggest or model prices for items listed on eBay Site". Read literally it is limited to items listed on eBay. A range for a Facebook Marketplace listing is outside the literal words; a verdict or suggested offer on an eBay listing the user brings is inside them. The section's opening words are broader ("in any way which may, directly or indirectly, undermine eBay's business interests"), and another item bars using eBay Content "to compete with eBay Services". Telling a shopper an eBay item is overpriced, or cheaper new at BCF, is the kind of use eBay could object to. This needs eBay's written answer, and the Buy API application is the place to ask. **[LAWYER]**
4. **Amazon Australia has restrictions the first pass missed.** Read on the Australian Associates site (policies updated 14 April 2026):
   - "Unless otherwise agreed by Amazon, your Site must not have price tracking and/or price alerting functionality."
   - A mobile app must be individually approved by Amazon, and it "must not emulate Amazon's own shopping app functionality".
   - No use of the API "for the purpose of aggregating, analyzing, extracting, or repurposing any Product Advertising Content" without written approval.
   - Non-image data may be cached for 24 hours at most, and "the client application may not store or cache" it.
   - The 10-sales threshold is confirmed for Australia: "Have at least 10 qualifying sales within the past 30 days".
5. **BCF's rate is confirmed, and the 0.5% figure is the lowest of three.** BCF's Commission Factory page shows 0.50% per sale as the headline, and "Split commission rate - 0.5% for coupon sites, 2% for content sites, 3% for loyalty/cashback sites", a 10-day tracking window, and "0% CPA for Clearance items". Which tier a price-check app falls in is BCF's decision. No product feed is mentioned on BCF's page.
6. **Most of the named retailers are not on Commission Factory.** A search of its public advertiser directory found BCF, Anaconda, Supercheap Auto, CameraPro and Camera House. It returned nothing for Tackle World, Sydney Tools, Total Tools, Bunnings, JB Hi-Fi, digiDirect, Ted's Cameras, Rebel, Macpac, Kogan, The Good Guys, Officeworks, Harvey Norman, Big W, Kmart, Target, Myer, Decathlon or Bing Lee. The first pass's assumption that Commission Factory covers most big Australian retailers is wrong; coverage is spread across several networks or absent.
7. **Gumtree's terms are stricter than assumed and were rewritten last month.** Effective 12 October 2026, users must not "scrape, crawl, copy, index, mirror or extract any part of the Platform or any Content by any means (manual or automated) ... without our express written consent", and the licence is "for your own personal use", not "to build, feed or operate a competing service". The manual-copying wording reaches further than Meta's and touches the user-shares-a-listing design. **[LAWYER]**
8. **Meta's terms close the logged-out gap.** Current text, effective 1 January 2025: "You may not access or collect data from our Products using automated means (without our prior permission) ... regardless of whether such automated access or collection is undertaken while logged-in to a Facebook account."
9. **Google v. SerpApi moved again on 9 November 2026.** The court dismissed Google's amended complaint, with leave to amend within 21 days, failing which the case is dismissed with prejudice. SerpApi's prices are as the first pass reported.
10. **The ACCC guide is still the 2015 one**, and a new consumer law starts on 1 July 2027 (see section 3).

## 2. Claim table

All rows read 2026-11-17. "03" and "05" are the first-pass files.

### eBay

| Claim | File | Status | What the source says | URL |
|---|---|---|---|---|
| Public displays may not co-mingle eBay and non-eBay content | 03 §2.2 | Confirmed | "(2) eBay Content in a Public Display may not be co-mingled or combined with non-eBay Content. For example, all eBay Content in a Public Display must be visually isolated from third-party listings or other non-eBay information" (the Public Display clause, cited in the agreement as Section 8.1(b)). Public Display is permitted "to promote eBay and enable Your Users to search and browse listings". | https://www.edp.ebay.com/join/api-license-agreement |
| eBay content may not be used to suggest or model prices | 03 §2.2 | Confirmed, scope clarified | Under "Restricted Activities": "Use eBay Content, either alone or in combination with third-party information, to suggest or model prices for items listed on eBay Site." Limited by its words to items listed on eBay. | same |
| Written permission needed to derive average selling prices | 03 §2.2 | Corrected (narrower) | Permission is needed for display "that enables derivation of ... Average selling price or gross merchandise sold for any eBay category", and site-wide statistics. It is category-level and about selling prices. A per-item range built from asking prices is not literally covered, though the list is "without limitation". | same |
| "Restricted APIs" data may not be fed to generative AI | 03 §2.2 | Confirmed, scope clarified | Restricted APIs are those "that provide information about market trends, pricing strategies, sales volumes, user behavior, or provide generated content ... Access is specially granted to select Developers." For those: no ingesting "into any artificial intelligence model, system, or tool ... not provided by or licensed from eBay without eBay's prior written consent". Pricing tools built on them need written consent and give eBay a licence to the tool. Browse is not named as restricted; Marketplace Insights fits the definition. | same |
| AI restrictions apply more generally | 03 §2.2 | Confirmed | For all eBay Content: no use "to train algorithms, conduct machine learning, develop synthetic data sets, train large learning models, and/or train artificial intelligence systems." | same |
| Developer must bind its own users | 03 §2.2 | Confirmed | "You will enter into a binding agreement with each of Your Users that includes ... (1) Your Users will be bound by this API License Agreement; (2) eBay will be a third-party beneficiary". | same |
| Agreement last updated 24 June 2025 | 03 §2.2 | Unverified | The page shows "Sept 3, 2025" at its foot and no "last updated" line in the text. | same |
| Browse API covers Australia | 03 §2.1 | Confirmed | "EBAY_AU - Australia (ebay.com.au)". The support table ticks Browse `item_summary` and `item`, and all Feed resources, for AU. Image search is supported in "US, DE, UK, and AU". | https://www.edp.ebay.com/api-docs/buy/static/ref-marketplace-supported.html |
| Browse default limit is 5,000 calls a day | 03 §2.1, 05 §2.2, §2.7 | Confirmed | "Browse API * All methods except getItems: 5000 API calls per day; getItems: 5000 API calls per day". Footnote: "* Buy APIs require an additional license." Higher limits follow the Application Growth Check. | https://www.edp.ebay.com/develop/api/buy/browse_api (call-limit table) |
| eBay AU is "Open" to a new entrant | 03 §2.1 | Corrected | Gated. See "What changed" item 1. Process: EPN account, Buy API application with "mocks and data flows", EPN reply "within 10 business days", then Developer Support review and contracts. | https://www.edp.ebay.com/api-docs/buy/static/buy-requirements.html |
| Marketplace Insights is a limited release for approved developers | 03 §2.1, 05 §2.2 | Confirmed in substance | Its documentation now sits behind a developer sign-in at a path named `marketplace-insights-private`, and it is absent from the public Buy API list (Browse, Charity, Deal, Feed, Marketing, Offer, Order). The "limited release" wording itself was seen only in search summaries; forum reports of refusals are undated. | https://www.edp.ebay.com/api-docs/buy/marketplace-insights/static/overview.html |
| eBay Partner Network covers Australia | 03 §2.1 | Confirmed | One global rate card; a note covers "qualifying sales through ebay.com.au". Rates: Sports and Musical Instruments 3%, Cameras & Photo and TV/Audio 2%, Computers 1.5%, Business & Industrial 2.5%, cap US$550 per sale in most categories. A sale counts if made "within 24 hours after clicking your affiliate link". | https://partnernetwork.ebay.com/our-program/rate-card |

### Amazon Australia

| Claim | File | Status | What the source says | URL |
|---|---|---|---|---|
| Creators API needs 10 qualifying sales in 30 days | 03 §2.1 | Confirmed for AU | "Have at least 10 qualifying sales within the past 30 days to access the PA API through the Creators API". Also: "Be enrolled in the Amazon Associates program for your target marketplace". | https://affiliate-program.amazon.com.au/creatorsapi/docs/en-us/introduction |
| PA-API 5.0 is retired | 03 §2.1 | Confirmed | "has been deprecated and is being replaced by the Creators API"; calls return "HTTP 403 Forbidden". No retirement date is given on the page. | https://affiliate-program.amazon.com.au/creatorsapi/docs/en-us/paapiv5-deprecation |
| Prices only from the API or Amazon-served links, with a time stamp | 03 §2.1 | Confirmed | "your Site may only show prices and availability if: (a) we serve the link ... or (b) you obtain Product pricing and availability data via Creators API or PA API". A date/time stamp is required if data is refreshed "less frequently than hourly", with a set disclaimer. | https://affiliate-program.amazon.com.au/help/operating/policies |
| Comparison displays must show lowest new and lowest used price | 03 §2.1 | Confirmed | "in any 'comparison' format (including through the use of any price-comparison tool or engine) ... you must display both the lowest 'new' price and, if we provide it to you, the lowest 'used' price". | same |
| Accounts closed without three sales in 180 days | 03 §2.1 | Unverified | Not found in the Australian operating agreement (updated 15 October 2025) or policies. Registration says sign-up is "available only to associates who have referred qualified sales and have been accepted into the program". | https://affiliate-program.amazon.com.au/help/operating/agreement |
| Commission rates (not in first pass) | — | New | Tools & Hardware 10%; Sports & Outdoors, Camera & Photo, Electronics 5%; Computers 2%; all other 2%. Session window 24 hours. | https://affiliate-program.amazon.com.au/help/node/topic/GRXPHT8U84RAYDXZ |

### Affiliate programmes

| Retailer | Network | Rate | Tracking window | Feed | Restrictions noted | Status | URL |
|---|---|---|---|---|---|---|---|
| BCF | Commission Factory | 0.50% headline; 0.5% coupon / 2% content / 3% loyalty-cashback | 10 days | Not mentioned | 0% on clearance | Confirmed | https://www.commissionfactory.com/advertiser-directory/bcf-affiliate-program/91580 |
| Anaconda | Commission Factory | Header 2.00%; body text "Up to 5% Base Commission Rate" | Header 14 days; body "7 Day Cookie Window" | "Data Feed available" | None stated | Confirmed listed; page contradicts itself | https://www.commissionfactory.com/advertiser-directory/anaconda-affiliate-program/76675 |
| Supercheap Auto | Commission Factory | Header 1.00%; "Tiered category commission rates from 1% - 7%" | Header 10 days; body "30 day" | "Product datafeed" | Clearance, tyres, gift cards and several brands earn nothing | Confirmed (new) | https://www.commissionfactory.com/advertiser-directory/supercheap-auto-affiliate-program/89312 |
| CameraPro | Commission Factory | 2.00% | 2 days | Not mentioned | None stated | Confirmed | https://www.commissionfactory.com/advertiser-directory/camerapro-affiliate-program/55797 |
| Camera House | Commission Factory | 1.90% header; "2%" in body | 30 days | "Full product datafeed available" | "Open to all promotional methods" | Confirmed (new) | https://www.commissionfactory.com/advertiser-directory/camera-house-affiliate-program/21198 |
| digiDirect | impact.com and FlexOffers, per a third-party directory; left Commission Factory November 2025 (its old page now returns 404) | Not read | Not read | Not read | Not read | Network from secondary source only | https://www.affilitizer.com/programs/digidirect.com.au |
| JB Hi-Fi | Partnerize since April 2026, per a third-party directory | Not read | Not read | Not read | Not read | Network from secondary source only; terms need a Partnerize login | https://www.affilitizer.com/programs/jbhifi.com.au |
| Ted's Cameras | None found | — | — | — | — | Not on Commission Factory; no affiliate link on its home page; FlexOffers says it does not currently offer the programme (search summary) | — |
| Tackle World | None found | — | — | — | — | Not on Commission Factory; no affiliate link on its home page | — |
| Sydney Tools | None found | — | — | — | — | Not on Commission Factory; one search found nothing | — |
| Total Tools | None found | — | — | — | — | Not on Commission Factory; one search found nothing; its site refused the request | — |
| Bunnings | None found | — | — | — | — | Not on Commission Factory; its site refused the request. A ShopBack blog calls Bunnings a partner, apparently for gift cards (search summary, unverified) | — |
| Amazon Australia | Own programme (Associates) | See Amazon table | 24 hours | Creators API after 10 sales | App approval; no price tracking or alerts; see "What changed" 4 | Confirmed | above |
| eBay Australia | Own programme (EPN) | See eBay table | 24 hours | Buy and Feed APIs after approval | Licence clauses above | Confirmed | above |

Other affiliate claims:

| Claim | File | Status | What the source says | URL |
|---|---|---|---|---|
| Commission Factory requires merchants with ten or more products to supply a feed | 03 §2.1 | Corrected | It is a recommendation: "If you have more than 10 items onsite we would recommend having a data feed." | https://help.commissionfactory.com/what-is-a-datafeed-and-how-do-affiliates-use-them |
| Comparison publishers are accepted on the network | 03 §2.1 | Confirmed | Feed users listed first: "Price comparison sites and apps", then deal aggregators and comparison shopping services. Each merchant still approves each publisher. | same |
| Commission Factory has a `GetDataFeeds` API and belongs to Awin | 03 §2.1 | Confirmed | "Retrieves an array of data feeds"; rate-limited (429 error). Site footer: "Part of the Awin Group". | https://dev.commissionfactory.com/V1/Affiliate/Functions/GetDataFeeds/ |
| Most large Australian retailers run programmes through Commission Factory, Rakuten or Impact | 03 §2.1 | Corrected for Commission Factory | See "What changed" 6. Rakuten, Impact and Partnerize directories need a login and were not checked. | https://www.commissionfactory.com/advertiser-directory |

### Meta, Gumtree, ACCC

| Claim | File | Status | What the source says | URL |
|---|---|---|---|---|
| Meta bans automated collection without permission | 03 §2.3 | Confirmed | Quoted in "What changed" 8. Terms "Effective January 1, 2025". | https://www.facebook.com/legal/terms |
| The ban now applies whether or not logged in | 03 §2.3 | Confirmed at source | Same sentence. Also: "you may not sell, license, or purchase any data obtained from us or our services, regardless of whether such data was obtained while logged-in". Buying Marketplace data from a scraping vendor is therefore itself a breach by an account holder. | same |
| Gumtree: standard ban on robots and scraping expected | 03 §2.1 | Confirmed and stronger | Gumtree AU Pty Ltd, "Effective: 12 October 2026". Clause 11.3 quoted in "What changed" 7. A second clause bars scraping "by any automated means, including for the purpose of training any artificial intelligence". Clause 11.1 limits use to "your own personal use". | https://help.gumtree.com.au/articles/en_US/KB_Article/Gumtree-Terms-of-Use-AU |
| Gumtree has no public API | 03 §2.1 | Unverified, with a lead | Clause 11.4: "If we make an API available, your use of the API is subject to these Terms". No API was found; the wording leaves room to ask. | same |
| ACCC guide has three principles | 03 §2.4 | Confirmed | "Principle 1: Facilitate honest, like-for-like comparisons. Principle 2: Be transparent about commercial relationships. Principle 3: Clearly disclose who and what is being compared." Published 3 August 2015. | https://www.accc.gov.au/about-us/publications/a-guide-to-comparator-websites-for-website-operators-and-suppliers |
| Whether anything newer than 2015 exists | 03 §2.4 | Answered | No newer guide. The 2015 guide is still the listed publication. The ACCC's "Selling online" page (search listing dated 21 July 2026) has a short "Comparison websites and apps" section stating they "must not mislead consumers". | https://www.accc.gov.au/business/selling-products-and-services/selling-online |

### Costs and litigation (report 05)

| Claim | File | Status | What the source says | URL |
|---|---|---|---|---|
| SerpApi: $25 / 1,000, $75 / 5,000, $150 / 15,000, $275 / 30,000 searches a month | 05 §2.2, §2.7 | Confirmed | Starter $25 (1,000, 200 an hour), Developer $75 (5,000), Production $150 (15,000), Big Data $275 (30,000). Google Shopping is among the covered APIs. | https://serpapi.com/pricing |
| DataForSEO Google Shopping about $0.001–$0.002 a page; standard queue up to 45 minutes; live price unknown | 05 §2.2 | Confirmed and completed | Products: "Standard queue ... Up to 45 minutes ... $0.001"; "Priority queue ... Up to 1 minute ... $0.002", per page of 40 products. There is no live mode for product search, so the fastest route can take up to a minute, which does not fit a ten-second verdict. | https://dataforseo.com/pricing/merchant/google-shopping-api |
| Google v. SerpApi: claims dismissed 20 July 2026; amended complaint status uncertain | 03 §2.1, 05 §2.2 | Updated | "On November 9, Chief Judge Yvonne Gonzalez Rogers ... granted SerpApi's motion to dismiss Google's amended complaint." It is "with leave to amend"; "Google has 21 days to file a new complaint. If it does not ... it will dismiss the case with prejudice." This is SerpApi's own account; the order was not read. Only the anti-circumvention claims have been tested. | https://serpapi.com/blog/court-dismisses-googles-amended-complaint-against-serpapi/ |

## 3. New findings

1. **eBay data cannot feed the app's own price history or models.** The licence allows "limited intermediate copies ... deleted when they are no longer required", requires listings to be no more than six hours stale, and bars storing eBay Content "other than for the purposes allowed". Report 05's plan to "store every observation with a timestamp" must exclude eBay-sourced observations unless eBay agrees otherwise.
2. **eBay reserves a general veto.** The agreement says eBay may suspend access if it believes the developer is "using the Developer Tools in any way that undermines eBay's business interests", and it owns "any content created or derived" from eBay Content. A product whose common answer is "buy it elsewhere" depends on eBay's tolerance.
3. **Amazon's rules collide with the planned product in three places**: app approval before any Amazon link may appear in a mobile app; no price tracking or alerts (report 05's "wait" verdict and any later price-drop alert); and no analysis or repurposing of Amazon data without written approval. Amazon data also cannot be used to "develop or improve large language or multimodal models, machine learning models".
4. **Gumtree's terms now cover manual copying and competing services.** A user sharing a screenshot is acting under Gumtree's licence to the user; the app never accepts Gumtree's terms. Whether Gumtree could act against the app for inducing breach is a question for a lawyer. The October 2026 rewrite also shows Gumtree is actively tightening. **[LAWYER]**
5. **The ACCC guide has specific points that apply directly.** Operators should "avoid making absolute statements such as 'widest range' ... and 'best deals available', unless such claims can be substantiated"; disclose market coverage "before consumers use the comparison service"; not show a supplier's logo if its products are not compared; "not manipulate algorithms to display results based on their commercial relationships"; and keep prices current, where "disclosure ... about when the product information was last updated may also assist". An operator is responsible for supplier information it "adopts or endorses".
6. **A general ban on unfair trading practices starts on 1 July 2027.** According to Clayton Utz, the Competition and Consumer Amendment (Unfair Trading Practices) Act 2026 received assent on 6 July 2026. It prohibits conduct that "manipulates the consumer or unreasonably distorts the environment in which the consumer makes ... a decision" and causes detriment, and requires mandatory transaction charges to be shown with the base price. Relevant to how verdicts and total-cost figures are presented. Read from a law-firm summary, not the Act. https://www.claytonutz.com/insights/2026/october/dark-patterns-drip-pricing-and-dodgy-subscriptions-australia-s-new-unfair-trading-practices-act-explained
7. **Retailers that do have programmes pay little and exclude clearance stock.** BCF and Supercheap Auto both pay nothing on clearance items, which are the items a deal-checking app will most often surface. Tracking windows are short: 2 days at CameraPro, 24 hours at Amazon and eBay.
8. **SerpApi sells a "Facebook Marketplace API"** (listed on its pricing page). Using it would breach Meta's terms as quoted above; noted only because it will come up as a tempting shortcut.

## 4. Still open

| Item | Why | What would settle it |
|---|---|---|
| Whether eBay will approve this app, a separate-section display, and use of asking prices in a fair range | Depends on eBay's discretion | Apply to EPN and submit the Buy API application with the actual mock-up; ask the three questions in writing |
| Whether Browse counts as a Restricted API | The definition is functional, not a list | Same written question to eBay |
| Rates, cookie length, feeds and publisher rules for JB Hi-Fi (Partnerize) and digiDirect (impact.com, FlexOffers) | Network pages need a publisher login | Free publisher accounts on Partnerize and impact.com |
| Whether Bunnings, Total Tools, Sydney Tools, Tackle World and Ted's Cameras have any programme | Nothing found; two sites refused the request; Rakuten, Impact and Partnerize directories not searchable without login | Publisher accounts on those networks; email each retailer |
| Which BCF tier a price-check app gets, and whether BCF supplies a feed | Decided by BCF on application | Apply through Commission Factory |
| Anaconda's actual rate and window | Its page states two different sets | Apply, or ask Commission Factory |
| Amazon's "three sales in 180 days" rule for Australia | Not in the documents read | Associates Central help after sign-up |
| Whether Amazon would approve this app, and waive the price-tracking rule | Amazon's discretion | Apply as an Associate and submit the app for approval |
| Whether Google refiles against SerpApi by about 30 November 2026 | Pending | SerpApi blog or the docket (No. 4:25-cv-10826-YGR) |
| Text of the Unfair Trading Practices Act 2026 | Only a law-firm summary was read | legislation.gov.au; lawyer |
| Australian Google Shopping coverage of BCF, Anaconda and similar retailers through SerpApi or DataForSEO | Not tested; needs paid calls | A one-day trial on 30–50 real items |

## Sources read

- https://www.edp.ebay.com/join/api-license-agreement
- https://www.edp.ebay.com/api-docs/buy/static/buy-requirements.html
- https://www.edp.ebay.com/api-docs/buy/static/ref-marketplace-supported.html
- https://www.edp.ebay.com/develop/api/buy/browse_api
- https://www.edp.ebay.com/develop/get-started/api-call-limits
- https://www.edp.ebay.com/api-docs/buy/marketplace-insights/static/overview.html (redirects to sign-in)
- https://partnernetwork.ebay.com/our-program/rate-card and its rate card PDF
- https://affiliate-program.amazon.com.au/creatorsapi/docs/en-us/introduction
- https://affiliate-program.amazon.com.au/creatorsapi/docs/en-us/onboarding/register-for-creators-api
- https://affiliate-program.amazon.com.au/creatorsapi/docs/en-us/paapiv5-deprecation
- https://affiliate-program.amazon.com.au/help/operating/policies
- https://affiliate-program.amazon.com.au/help/operating/agreement
- https://affiliate-program.amazon.com.au/help/node/topic/GRXPHT8U84RAYDXZ
- https://www.commissionfactory.com/advertiser-directory and the five programme pages in the table
- https://help.commissionfactory.com/what-is-a-datafeed-and-how-do-affiliates-use-them
- https://dev.commissionfactory.com/V1/Affiliate/Functions/GetDataFeeds/
- https://www.affilitizer.com/programs/jbhifi.com.au and https://www.affilitizer.com/programs/digidirect.com.au (third-party directory)
- https://www.facebook.com/legal/terms
- https://help.gumtree.com.au/articles/en_US/KB_Article/Gumtree-Terms-of-Use-AU
- https://www.accc.gov.au/about-us/publications/a-guide-to-comparator-websites-for-website-operators-and-suppliers and the guide PDF
- https://www.accc.gov.au/business/selling-products-and-services/selling-online
- https://www.claytonutz.com/insights/2026/october/dark-patterns-drip-pricing-and-dodgy-subscriptions-australia-s-new-unfair-trading-practices-act-explained
- https://serpapi.com/pricing
- https://serpapi.com/blog/court-dismisses-googles-amended-complaint-against-serpapi/
- https://dataforseo.com/pricing/merchant/google-shopping-api

Refused or unreadable: developer.ebay.com (403), www.gumtree.com.au (browser challenge; the help-centre copy of the terms was read instead), www.bunnings.com.au, www.totaltools.com.au and www.thegoodguys.com.au (403).
