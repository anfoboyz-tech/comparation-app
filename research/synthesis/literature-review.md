# Literature review

A synthesis of the academic track and the seven market tracks. The full review with tables, about 45 verified references and their links is in `research/findings/04-academic-literature.md`.

## Limits

The academic track verified references from abstracts and bibliographic records only; no full texts were read, and arXiv, RePEc and Crossref were unreachable. About 40 further works the reviewer recalled but could not confirm are listed in that file as leads and are not used here. Themes on fraud detection, used-item valuation and 2020–2026 consumer studies are thin. Each "nothing found" below is medium confidence at best.

## Second pass

A second reviewer, with network access, read abstracts and some full texts. All 38 unverified leads were confirmed, 14 references were spot-checked, and the gap claims were tested. Corrections are applied below; the detail is in `research/findings/second-pass/04-literature.md`. Three of the first pass's "nothing found" claims were wrong, and section 7 has been rewritten.

## 1. Why the founder's evening happened

Search theory has predicted it since Stigler (1961): looking for a better price costs effort, so people stop before finding the best one, and prices for the same item stay spread out. The internet did not remove this. Brynjolfsson and Smith (2000) measured 25–33% dispersion for identical books and CDs online. Baye, Morgan and Scholten (2004) followed four million prices on a comparison site and found no convergence to one price.

Two findings shape the product:

- **People search narrowly and settle early.** Bronnenberg, Kim and Mela (2016) found camera shoppers ran about 14 searches over about 15 days; about 40% searched a single brand and 20% a single model. Early search predicts the final purchase, though the item bought is usually first found late in the search. The user usually arrives with an item in mind, or a listing in hand.
- **People appear to decide how much to check, then check it.** De los Santos, Hortaçsu and Wildenbeest (2012) found this fits online book buying better than "keep looking until a good price appears". The implication is to deliver the whole sample at once and then say that further searching is unlikely to help.

The same evidence cuts against the size of the market. If most shoppers check little, most do not spend the founder's 100 minutes. The people who do are maximisers, who Schwartz and colleagues (2002) found report more regret. They are the likely early users.

## 2. Why price comparison alone is not the product

Comparison engines are 25 years old and the record is mixed.

- Retailers respond by making comparison harder: add-on fees, bait listings, retailer-exclusive model numbers (Ellison and Ellison, 2009).
- Ranking steers attention. Ursu (2018), using randomised rankings at Expedia, showed position determines what people look at.
- In Ronayne's (2021) model, commission-funded comparison sites raise prices for all consumers, though the UK competition regulator's 2017 market study found net benefit in the sectors it examined.
- The market tracks found the same in practice: new-goods comparison in Australia is free and crowded, and Little Birdie closed after A$30m of funding.

For this product, commission is the specific hazard. Retail purchases pay it and private second-hand sales do not, so an app funded by commission is paid to say "buy new". The verdict has to be computed without reference to who pays.

## 3. Why second-hand is harder, and where a tool can help

Akerlof (1970) explains the default condition: when buyers cannot see quality, they discount everything. Two mechanisms reduce the problem on eBay. Disclosure in the listing carries measurable price weight (Lewis, 2011), and established seller reputation was worth about 8% of the price in a field experiment (Resnick and colleagues, 2006), although feedback scores are inflated (Tadelis, 2016).

Facebook Marketplace and Gumtree offer weaker versions of both. A tool can substitute in part: note how much a listing discloses, and price the absence of warranty and returns explicitly instead of ignoring it.

Motivation is not only price. Guiot and Roux (2010) found distinct economic, recreational and anti-consumerist reasons for buying second-hand.

## 4. What "a good deal" means

Thaler (1985) separated the pleasure of a deal from the value of the item: people judge a price against a reference point. A reference supplied from outside shifts the buyer's own (Grewal, Monroe and Krishnan, 1998). The effect is easy to exploit. In outlet stores, each extra dollar of posted "original" price raised what shoppers paid by about 77 cents, most of all for the least informed (Ngwe, Harvard Business School).

So the core output of this product is an honest reference price: the real current new price and real used prices, with this listing placed between them. Retailers' "was" prices should never be shown as the reference. The least-informed benefit most, which favours categories people buy rarely.

## 5. How to present the answer

- **Few options, compared side by side.** Häubl and Trifts (2000) showed a recommendation agent plus a comparison table cut effort and improved decisions. Choice overload is conditional (Scheibehenne and colleagues, 2010; Chernev and colleagues, 2015), and the conditions that trigger it, complex options and uncertain preferences, describe new-versus-used well.
- **Show confidence and evidence.** People abandon an algorithm after seeing it err, even when it beats humans (Dietvorst, Simmons and Massey, 2015). A wrong verdict costs more than a withheld one.
- **Let users adjust the assumptions.** A follow-up by the same authors found that being able to adjust an algorithm's output increases its use.

The market research points the same way: one Australian survey, whose research firm and sample size were not seen, found 3% of shoppers would buy on an AI recommendation alone.

## 6. What machines can and cannot yet do

- **Matching retail offers is feasible.** Current models match product offers with few or no training examples about as well as models trained on thousands (Peeters, Steiner and Bizer, 2025). Benchmark accuracy ranges from 0.64 to 0.89 (F1) by difficulty, and drops sharply on products not seen before (Peeters, Der and Bizer, 2024).
- **Matching second-hand listings is done inside platforms.** eBay (Shah and colleagues, 2018), Mercari and Xianyu have published on it. No public benchmark was found for classified listings, so accuracy on a listing like "rod and reel, barely used, pick up Frankston" has to be measured.
- **Pricing used items is hard even for the platform.** Xianyu's 2025 system retrieves comparable listings from its own 90-day pool and withholds low-confidence suggestions. It lands within 20% of the seller's asking price 54.6% of the time overall, 78% for phones when it answers 70% of cases, and 17.4% for a model without comparables.
- **Assistants get current prices wrong.** Which? found in October 2026 that ChatGPT gave the correct lowest price and retailer for 8 of 25 products. No peer-reviewed study of this was found.
- **Valuation research supports ranges and refusals.** Han and colleagues (2020) built second-hand price suggestion as two steps: decide whether the listing can be priced at all, then price it.
- **Shopping agents are not reliable alone.** The best agents succeed on under half of realistic tasks (ShoppingBench, Wang and colleagues, 2026) and are swayed by position and listing wording (Allouah and colleagues, 2025).

The design consequence is the one the architecture track reached independently: use models to read, match and explain; compute prices and verdicts in code from retrieved data.

## 7. Gaps

Three things the first pass called unstudied have a literature:

- **Choosing between new and used.** Studied for books (Ghose, Smith and Telang, 2006), video games (Ishihara and Ching, 2019) and remanufactured goods (Guide and Li, 2010).
- **Used-to-new price ratios.** Measured for remanufactured electronics (Abbey and colleagues, 2017) and for resale price as a share of original retail (Solinas, Nunes and Ko, 2025).
- **Total-cost information.** Field experiments show that how shipping is presented changes what people pay (Hossain and Morgan, 2006).

What was still not found, at medium confidence:

| Gap | In the literature | In the market |
|---|---|---|
| Decision support for a specific used listing of a general-goods item | Not found; price-suggestion systems are seller-side | Small tools exist, with undisclosed accuracy and few users |
| A fair used-to-new ratio by category and condition on classifieds | Not found | Not seen |
| One figure combining price, shipping, travel, time and risk | Not found | Not seen in any product |
| Buy, negotiate, wait or skip advice for used goods outside vehicles | Only price forecasting; buy/wait advice exists for airfares (Etzioni and colleagues, 2003) | Vehicles; small verdict tools |
| A public benchmark for matching classified listings to products | Not found | — |
| Second-hand tasks in shopping-agent benchmarks | None include condition, negotiation or pickup | — |
| Measurement of scams on Facebook Marketplace or Gumtree | Craigslist-era studies only | Official figures do not isolate either platform |
| Australian evidence | Regulator reports only | — |

The remaining gap is narrower than first claimed: a trustworthy fair-value judgement on a specific used listing, with total cost, for general goods. That is the basis of the research question in `research-question.md`.

## 8. Questions the product could answer that nobody has

These come from the academic track and could be run inside the product once it has users.

1. What used-to-new price ratio do buyers treat as fair, by category and condition?
2. Does a "you have seen the realistic range" signal cut search time and regret without raising the price paid?
3. How accurately can current models identify the product and variant in Australian classified listings? This would be the first public benchmark of its kind.
4. Does showing one total-cost figure change the choice between used-local, used-shipped and new?
5. Do verdicts with evidence, confidence and adjustable assumptions keep users' trust after a visible error?
