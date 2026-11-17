# Track 8 — Differentiation, product concepts and defensibility

Date of research: 2026-11-17.

**Read this first: evidence limits.** This track ran about 18 web searches before the session's shared search budget ran out, and every direct page fetch failed because the hosts are outside this session's network allowlist (openai.com, about.fb.com, techcrunch.com, help.carsales.com.au, arxiv.org, zillow.com, chromewebstore.google.com all refused). So:

- Claims marked **[S]** come from search-result summaries of the cited URL. I did not open the page itself.
- Claims marked **[M]** are from my own background knowledge and were not checked tonight. Treat them as low-to-medium confidence.
- Claims marked **[I]** are my inference.
- Kayak, Skyscanner, Shazam, GasBuddy, Trolley and the Farecast research were not searched at all. Section 1 says so row by row.

---

## 1. Bottom line

1. The founder's original framing, "search everything, new and used", is the concept most exposed to general assistants, and I would not build it as the core. New-retail comparison is already being absorbed: Google's AI shopping with in-chat checkout reportedly reached Australia in June 2026 with Kogan, Bunnings and The Iconic [S], and ChatGPT has had a shopping research mode since November 2025 [S].
2. Used and local is harder for assistants, but mostly for access reasons, not capability reasons, and access is not a durable gap. A reviewer already got ChatGPT Agent to log in to Facebook Marketplace and compile used-car listings (slowly) [S]. Meta launched its own agent, Muse, in the US on 8 September 2026, and it can reportedly watch Marketplace for a specific item [S].
3. The same walls that slow the assistants are higher for a startup. eBay banned third-party "buy-for-me agents" and "LLM-driven bots" in its user agreement in early 2026 [S], and Amazon sued Perplexity over agent access [S]. A small team cannot win on access. It can only win where the user brings the listing to it.
4. That points to the "check this listing" verdict, entered from the share sheet or a screenshot, as the wedge. It is cheap to build, needs no crawl of logged-in marketplaces, and answers the founder's actual 50–100 minute problem.
5. The verdict on its own is not a moat. At least nine small tools already do it for Facebook Marketplace (Spottable, DealRater.ai, DealScan, Peaky Dog, Deal Lens and others) [S]. The one whose numbers I saw has about 198 Chrome users [S]. Nobody has won, which is either an opening or a warning about demand.
6. The only assets I rate as both achievable and meaningful are: a region-and-condition dataset of observed used asking prices with reported outcomes, built from the exhaust of user checks; depth in a few categories; and a published accuracy record. All three are slow, and all three are weak in year one.
7. Meta is the single biggest risk. It already suggests prices to sellers "based on similar items in the area" (March 2026) and shows buyers AI price information on vehicle listings (November 2025) [S]. A buyer-facing "fair price" badge on general goods is a small step from there. I found no evidence it exists yet.
8. What Meta, eBay, Amazon and Google are structurally unlikely to do is tell a buyer "don't buy this, it is cheaper new at BCF this week" or "the same reel is on Gumtree for less". Cross-platform neutrality is the one position the platforms cannot occupy [I].
9. My recommendation is a narrow build: listing-check verdict plus new-price anchor, in two or three enthusiast categories, in Australia, with the data and track record designed in from day one. I rate it a reasonable small bet, not an obviously defensible business. Section 6 lists what would change that.

---

## 2. Findings

### 2.1 What made category-defining decision products work

| Product | Memorable interaction | Asset that was hard to copy | Lesson for this product | Evidence |
|---|---|---|---|---|
| carsales / RedBook (AU) | A tag on every listing: Around, Below or Well Below Market Price | RedBook valuation data plus live carsales listings; the comparison adjusts for features and mileage | The label is generated independently and sellers cannot buy it. It is withheld for cars under $5,000 or over $70,000, so they decline to rate where data is thin | [S] carsales help and editorial pages |
| CarGurus (US) | Five-level deal rating (Great, Good, Fair, High, Overpriced) on every listing | Instant Market Value built from current and past comparable listings, recalculated daily | They state the rating covers price only, not condition, and give no rating when comparables are insufficient. Exact thresholds are not published | [S] CarGurus help pages |
| Autotrader UK | Good / Great price flag | Own valuation from its listing base | Cars priced above market get no flag. The verdict is only shown when it flatters the listing, which protects seller relationships | [S] Autotrader help |
| Zillow Zestimate | One number for any home | Listing and transaction data at national scale | Reported median error is about 1.8% for on-market homes and 7.2% for off-market homes (August 2026 refresh), and up to 12.7% in thin states. Accuracy is much better when there is an asking price to anchor on. Zillow Offers, which traded on the forecasts, was shut in November 2021 with a write-down of about $340 million in one quarter | [S] Boston.com, HomeLight, news reports |
| Hopper | "Wait" or "buy now" | Historical fare data | The "95% accurate" claim is self-reported. I found no independent verification, and anecdotal tests were unfavourable. A headline accuracy number that nobody can audit becomes a liability | [S] several secondary sources, none strong |
| Honey | Coupon applied automatically at checkout | Distribution (peak of over 20 million Chrome users) | Affiliate incentives collided with user and creator interests. After the December 2024 exposé it reportedly fell to 12–14 million users, and Google changed Chrome extension affiliate rules in March 2025 | [S] 9to5Google, ppc.land |
| Yuka | Scan a barcode, get a score out of 100 | Independence: no advertising, no sponsored rankings, revenue from premium subscriptions | Reported 80–85 million users (company figures). Neutrality was the product, and it was funded by users, not by the things being rated | [S] BBC via The Star, App Store listing |
| Vivino | Photograph a label, get a rating | User-generated ratings: 77 million users and 3.5 billion label scans (company figures) | The scan is both the utility and the data collection. Headcount estimated down 23% since 2023, so a large dataset has not guaranteed a strong business | [S] Vivino about page, Revelio Labs estimate |
| OzBargain (AU) | Community-voted deals | Community and habit: 2.5 million unique users and 14 million sessions in December 2023 (own Google Analytics figures) | Owns "new-item deals" in Australia. Do not compete there. It is weak on used goods and on "is this specific listing fair" [I] | [S] OzBargain advertising page |
| PetrolSpy (AU) | Map of prices near you | Crowdsourced price entries plus government feeds where states mandate reporting; daily $25 fuel-card draw for contributors | Crowdsourcing works when contributing takes seconds and the contributor benefits from others doing the same | [S] Choice, Savings.com.au |
| Frugl (AU) | Grocery price comparison | Scraped supermarket prices | Uptake declined consistently and the app was handed to an outside developer in April 2023. Current status not verified | [S] The Sentiment |
| Keepa / camelcamelcamel | Price-history chart on the product page | Years of accumulated price history that cannot be recreated after the fact | The clearest example of "time in market" as a moat. Catalogue-size figures online conflict, so I give none | [S] vendor blogs only; weak |
| Kayak, Skyscanner, Shazam, GasBuddy, Trolley, Farecast | Not researched | Not researched | Search budget ran out before these were covered | None |

Patterns that recur across the ones I could check:

- **The verdict lives on the object the user is already looking at.** carsales, CarGurus, Yuka and Vivino all attach a judgement to a specific item. None asks the user to start a new search.
- **The winners decline to answer when data is thin.** carsales and CarGurus both withhold ratings. An academic system for second-hand pricing on Xianyu (China) reports the same design: confidence filtering to reject unreliable suggestions, and much worse results for a plain language model without retrieval of comparable items [S, arXiv 2510.09347].
- **The data asset is time or contribution, never cleverness.** Price history, listing history and user scans all had to be collected as they happened.
- **Unauditable accuracy claims and conflicted revenue both end badly.** Hopper, Zillow Offers and Honey are the three cautionary cases.

### 2.2 The general-assistant threat

What I could establish about each, as of November 2026:

| Assistant | New-retail shopping | Used and local | Australia status | Evidence |
|---|---|---|---|---|
| ChatGPT | Shopping research mode since 24 November 2025; asks clarifying questions and builds a buyer's guide. OpenAI itself warns prices and availability may be wrong. Instant Checkout was scaled back in March 2026 and moved into apps | No sign that shopping research covers second-hand listings. ChatGPT Agent has logged in to Facebook Marketplace and listed used cars in a reviewer's test, slowly and with a manual verification step | Conflicting reports on whether the full shopping research interface is live in Australia | [S] |
| Google (Search, AI Mode, Gemini) | Comparison tables, price tracking with a target price, agentic checkout, AI that phones stores (US, November 2025) | Not established | AI shopping with checkout reportedly rolled out in Australia in June 2026 (Kogan, Bunnings, Adore Beauty, Petbarn, The Iconic). Rests on one trade report | [S] |
| Meta (Meta AI, Muse) | Not its focus | Owns the Marketplace data. Seller price suggestions from nearby similar items (March 2026). Buyer-side AI insights including price information on vehicle listings (November 2025). Muse agent can reportedly watch Marketplace for an item | Muse launched in the US only on 8 September 2026. Australian availability of any of these not verified | [S] |
| Amazon | Rufus retired into "Alexa for Shopping" (May 2026, US), with 365-day price history and Buy for Me on other retailers' sites | None | Alexa+ early access began in Australia in August 2026. Alexa for Shopping not confirmed here | [S] |
| Perplexity | Shopping with PayPal "Instant Buy" (US). Comet browser agent | Not established | Comet is available worldwide; Instant Buy appears US-only | [S] |
| Claude | Not researched tonight | Not researched | Not researched | None |

Where they fall down, and whether the weakness will last:

| Weakness | Structural or temporary | Reasoning |
|---|---|---|
| Finding local second-hand listings behind a login | **Temporary for the assistants, permanent for a startup.** | Browser agents already do it badly [S]. A Ninth Circuit panel vacated the injunction against Perplexity's Amazon agent in August 2026, reasoning that the user, not Perplexity, accessed the site [S]. That case is not finished. Meta needs no permission on its own marketplace. |
| Cross-platform comparison | **Structural for platform-owned assistants.** | eBay bans third-party agents and blocked Muse [S]. Meta has no reason to send a buyer to Gumtree. Independent assistants (ChatGPT, Perplexity) are not bound by this, but face the walls above. |
| Sold-price and outcome history for used goods | **Structural for everyone outside the platform.** | Nobody but the marketplace sees the sale. The only outside routes are observing listings disappear over time and asking users what they paid [I]. |
| Calibrated verdict, with accountability | **Partly structural.** | General assistants give an opinion without a track record, and OpenAI disclaims price accuracy [S]. A specialist can publish hit rates. But a specialist only earns this with data it does not have on day one. |
| Alerts over days | **Temporary.** | Google tracks prices to a target and Muse watches Marketplace [S]. This is already a commodity feature. |
| Australian retailer and category knowledge | **Temporary, twelve to twenty-four months** [I]. | Google's Australian rollout already includes Bunnings and Kogan [S]. |
| Neutrality | **Structural.** | Each large player sells ads, takes checkout fees or owns a marketplace. Honey shows how an affiliate-funded "helper" loses trust [S]. |

Hard-nosed reading: within twelve months I expect a general assistant to answer "find me the best new or used deal on X in Brisbane" passably in the US, and somewhat later in Australia [I, medium confidence]. I expect "is this specific Marketplace listing fairly priced" to be answered by Meta itself inside Marketplace at some point, with timing unknown [I, low confidence on timing]. What I do not expect either to offer is a neutral, cross-platform verdict with a published accuracy record and regional used-price data. That is a narrower opening than the founder's vision.

### 2.3 Defensible assets

| Asset | Achievable for a small team | Moat strength if achieved | Notes |
|---|---|---|---|
| Observed used asking prices by region, model and condition, collected from user-submitted listings | Medium. Needs volume; each check adds one data point | Medium. Meta has far more, but will not share it or use it neutrally | Starts empty. Useful in a category only after hundreds of checks per popular model [I] |
| Outcome prices (what the user actually paid, or that the listing vanished) | Low to medium. Depends on users answering a follow-up | High. Nobody outside the platforms has this | The follow-up prompt ("Did you buy it? For how much?") must be designed in from the first release |
| New-price history for Australian retailers in chosen categories | Medium. Has to be collected over time | Medium in niche categories, low in mainstream ones that Google covers | "BCF had this at $229 in June" is the kind of fact assistants lack. Feasibility belongs to the data-access track |
| Verdict accuracy track record, published | Medium. Needs outcomes first | Medium. Cheap to claim, expensive to earn | Publish by category, with misses. Do not publish one headline number (Hopper) |
| Category depth (model variants, what wears out, what to inspect) | High. One enthusiast founder can do fishing gear | Low to medium. Assistants know much of this already | Makes the verdict feel expert. Good wedge, weak wall |
| Community | Low. OzBargain took many years | High | Do not plan on it |
| Trust and neutrality positioning | High to claim, medium to keep | Medium | Requires a revenue model that does not depend on steering purchases |
| Seller-side relationships | Low | Low | Would also undermine neutrality |

### 2.4 Product concepts

**(a) Search everything.** Promise: one search for the best deal, new or used, near you.
- Interaction: type an item, choose new, used or both, get a ranked list.
- Data: live retailer prices plus live listings from Marketplace, Gumtree and eBay.
- Memorable: only if coverage is complete, which is the hard part.
- Moat: none that I can identify.
- Main risk: head-on with Google and ChatGPT for new, and dependent on marketplace access for used.
- Build difficulty: very high.
- Assessment: do not lead with this.

**(b) Check this listing.** Promise: share any second-hand listing and get a fair-price verdict in ten seconds.
- Interaction: share sheet or screenshot from Marketplace or Gumtree. The app identifies the item, shows a fair range, the current new price, an offer to make, and what to inspect.
- Data: the shared listing, current new prices, comparable used asking prices, and over time its own history.
- Memorable: one tap, one answer, on the thing you are already looking at.
- Moat: weak at launch; grows through the dataset and track record in 2.3.
- Main risk: Meta ships a fair-price badge; existing small tools show the feature alone does not pull users.
- Build difficulty: low to medium. A language model with vision can read a screenshot today [M].
- Assessment: the wedge.

**(c) Cheapest way to own X.** Promise: every way to get this item, ranked by real total cost.
- Interaction: name an item, see new, refurbished, used-shipped and used-local options ranked after shipping, travel, warranty value and expected resale value.
- Data: everything in (a), plus resale estimates.
- Memorable: "net cost to own" is a number nobody else shows.
- Moat: the resale curves, which come from the same dataset as (b).
- Main risk: inherits the access problem of (a).
- Build difficulty: high.
- Assessment: a later layer on (b), limited to categories where the data exists.

**(d) Watch-and-alert hunter.** Promise: tell it what you want and your price, and it tells you when a good one appears.
- Interaction: set a target, get a push notification with a verdict attached.
- Data: continuous monitoring of marketplaces.
- Memorable: the notification that saves $200.
- Moat: none. Muse and Google price tracking already do versions of this [S].
- Main risk: continuous monitoring of logged-in marketplaces is exactly what the platforms prohibit.
- Build difficulty: high, and legally the most exposed.
- Assessment: avoid as a core. Alerts on new-retail price drops in chosen categories are a safe subset.

**(e) My addition: a public fair-price guide for chosen categories.** Promise: a page for every popular model saying what it is worth used in Australia, and when used stops being worth it.
- Interaction: a web page per model (for example a specific reel) showing lowest recent new price, typical used asking range by condition, and a "used is only worth it below $X" line.
- Data: the exhaust from (b), plus new-price history.
- Memorable: it becomes the reference people quote in haggling, as RedBook is for cars.
- Moat: pages are indexable, so they earn search traffic and are the kind of source assistants cite. The product becomes an input to the assistants instead of a rival [I].
- Main risk: thin data makes pages wrong, and wrong public numbers damage trust faster than private ones.
- Build difficulty: medium, but only after (b) has volume.
- Assessment: this is how (b) turns into something defensible.

**(f) Feature, not a concept: the offer.** Every verdict ends with a number to offer and a message to send. Spottable already drafts seller messages [S], so this is table stakes.

### 2.5 Positioning signals

- **Taken in Australia:** fair price for cars (carsales and RedBook), deals on new goods (OzBargain), fuel (PetrolSpy) [S].
- **Appears unclaimed:** "a fair-price check for anything second-hand" and "the RedBook for everything else". The listing-check tools I found look US-built, and most are desktop Chrome extensions, while Marketplace use is mainly mobile [I]. I could not check Gumtree's or eBay Australia's own price-guide features, or Australian app store listings, before the search budget ran out. Confidence that the position is open: medium-low until that check is done.
- **Strongest framing I can support:** the independent second opinion. "We don't sell anything, so we can tell you not to buy."

### 2.6 Recommendation

Back (b), restricted to two or three categories the founder knows (fishing gear is the obvious first), with the new-price anchor from (c), built so that every check feeds the dataset behind (e). Charge users directly or keep it free at first; do not fund it with affiliate links on the items being judged.

Evidence that would change my mind:

- **Toward not building:** Meta showing a buyer-facing price rating on general Marketplace listings in any market; or a test this week in which ChatGPT or Gemini, given a screenshot of a real Australian listing, returns a verdict the founder would have trusted.
- **Toward not building:** fewer than roughly one in three test users checking a second listing within a fortnight. A verdict tool used once is a feature.
- **Toward building bigger:** users voluntarily reporting what they paid at a rate that makes the outcome dataset real; or one category reaching enough checks that the public price pages are accurate.

---

## 3. Implications for the product

- Build for the moment the founder described: a listing is already on screen and the question is "is this fair?" Do not build a search engine.
- Treat the user as the access layer. Share sheet and screenshot input avoids the scraping fight that eBay, Amazon and Meta are escalating.
- Always show the new price beside the used verdict. This is the cross-platform fact the marketplace's own assistant has least reason to show.
- Give a range and a confidence level, and say "not enough data" when that is true. carsales and CarGurus both do.
- Ask for the outcome after every check. This is the only route to data others lack.
- Stay narrow. A trusted verdict on reels beats an unreliable one on everything.
- Expect the standalone app to be one of several front doors. The same verdict could be offered inside ChatGPT or other assistants as an app [M]; I did not verify current terms.

## 4. Open questions

1. Does Meta already show buyers a price rating on non-vehicle listings anywhere, and are Muse or the Marketplace AI features live in Australia? Settle by checking Meta's newsroom and an Australian account.
2. How good are ChatGPT, Gemini and Meta AI today at judging a real Australian listing from a screenshot? Settle with a one-hour test on twenty real listings, scored against the founder's own research.
3. Do Gumtree or eBay Australia offer buyers a price guide? Not checked.
4. Is there an Australian-built listing checker with traction? The competitor track should answer; I found only small, apparently US tools.
5. What does sharing a Marketplace listing from the mobile app actually hand to another app (link only, or text and image)? This decides between share sheet and screenshot. Settle with a ten-minute device test.
6. Will users report what they paid? Only a prototype can answer.
7. Kayak, Skyscanner, Shazam, GasBuddy, Trolley and Hopper's academic record were not researched.

## 5. Sources

All accessed 2026-11-17 through search-result summaries only; the pages themselves could not be opened from this session.

General assistants and platforms
- https://openai.com/index/chatgpt-shopping-research
- https://ecommercenews.com.au/story/chatgpt-s-checkout-retreat-an-opportunity-for-aussie-retailers
- https://www.channelnews.com.au/chatgpt-launches-dedicated-shopping-assistant-powered-by-gpt-5-mini/
- https://www.androidauthority.com/chatgpt-agent-review-3583538/
- https://blog.google/products-and-platforms/products/shopping/agentic-checkout-holiday-ai-shopping/
- https://www.shopifreaks.com/google-launches-its-ai-shopping-tool-in-australia-with-retailers-like-kogan-and-bunnings-its-first-such-rollout-in-asia-pacific/
- https://cfotech.com.au/story/google-launches-universal-cart-for-agent-led-shopping
- https://about.fb.com/news/2026/03/facebook-marketplace-new-meta-ai-tools-make-selling-faster-and-easier/amp/
- https://techcrunch.com/2025/11/13/facebook-marketplace-gets-new-collaborative-and-social-features-meta-ai-integrations
- https://www.pymnts.com/meta/2026/meta-ai-writes-listings-and-sets-prices-for-facebook-marketplace-sellers/
- https://www.techrepublic.com/article/news-meta-ai-facebook-marketplace-buyer-seller-address/
- https://mikareyes.com/ai/7-things-to-do-with-meta-muse
- https://thepaypers.com/payments/news/ebay-restricts-third-party-ai-agents-including-metas-muse
- https://www.ecommercebytes.com/2026/01/21/ebay-bans-ai-shopping-agents-updates-arbitration-provision/
- https://www.theregister.com/2026/01/22/ebay_updates_legalese_to_ban/
- https://geekwire.com/2026/judge-blocks-perplexitys-ai-bot-from-shopping-on-amazon-in-early-test-of-agentic-commerce/
- https://www.retail-insight-network.com/newsletters/us-court-overturns-amazon-injunction-perplexity
- https://ecommercenews.com.au/story/amazon-rolls-out-alexa-in-australia-via-early-access
- https://www.digitalcommerce360.com/2026/05/13/amazon-launches-ai-agent-alexa-for-shopping/
- https://ppc.land/amazon-merges-rufus-and-alexa-into-one-shopping-assistant/
- https://newsroom.au.paypal-corp.com/paypal-perplexity-comet-early-access-australia

Existing listing-check tools
- https://apps.apple.com/us/app/id6758812746 (Spottable)
- https://chromewebstore.google.com/detail/dbgjphnanjmmfjacahfhliahblokmpgh (Spottable extension)
- https://chromewebstore.google.com/detail/mcoiofhpiamkkfdnjondgcplkkdljfjl (DealRater.ai)
- https://chromewebstore.google.com/detail/dnidpjpakkallbhniigeiageaecnodck (DealScan)
- https://chromewebstore.google.com/detail/mhhcifhkedliejmbdocomajmdfbnkifj (Peaky Dog)
- https://chromewebstore.google.com/detail/deal-lens/ndojllleemkjjelapmjdgapoeincbiol (Deal Lens)

Decision products
- https://help.carsales.com.au/hc/en-gb/articles/360015482932-Price-Indicators
- https://www.carsales.com.au/editorial/details/carsales-price-indicator-gives-car-buyers-confidence-115213
- https://cargurus.helpscoutdocs.com/article/10-what-is-imv
- https://www.cargurus.com/about/how-cargurus-works
- https://help.autotrader.co.uk/hc/en-gb/articles/9831718888733-What-does-Good-price-mean
- https://www.boston.com/real-estate/home-buying/2026/10/21/home-value-estimates-zillow-redfin/
- https://www.homelight.com/blog/buyer-most-accurate-home-value-website/
- https://incidentdatabase.ai/reports/1501
- https://camli.com/is-hopper-price-prediction-accurate
- https://techcrunch.com/2017/10/25/hopper-expands-its-price-prediction-technology-to-hotels-initially-in-nyc
- https://9to5google.com/2025/03/13/honey-affiliate-update/
- https://ppc.land/honey-drops-to-14-million-chrome-users-amid-ongoing-affiliate-scandal/
- https://www.the-star.co.ke/news/world/2026-07-15-is-tracking-your-food-purchases-good-for-your-health
- https://apps.apple.com/app/1092799236 (Yuka)
- https://www.vivino.com/ja/about
- https://www.reveliolabs.com/companies/vivino/employees
- https://www.ozbargain.com.au/wiki/help:advertise
- https://choice.com.au/transport/cars/general/articles/cheap-fuel-apps-review
- https://www.savings.com.au/car-loans/what-are-the-top-fuel-finder-apps
- https://thesentiment.com.au/frugl-restructures-business-after-seeing-low-returns-for-its-grocery-price-tracking-app
- https://arxiv.org/abs/2510.09347v1
