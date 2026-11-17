# Track 4 — Academic literature review

Date of research: 2026-11-17. Home market: Australia.

## Read this first: how complete this review is

This review is **partial**, and the reader should weigh it accordingly.

- The web-search allowance for tonight's run is shared by all eight agents and ran out after I had completed 38 searches. Ten further searches were refused.
- Direct fetching of bibliographic sources (arXiv, RePEc/EconPapers, Crossref) is blocked by this session's network settings, so I could not verify references by another route.
- Every work in the numbered **Verified references** list was confirmed tonight against at least one bibliographic record (publisher page, RePEc/EconPapers, arXiv, NeurIPS/AAAI proceedings, or a regulator's own site). Findings attributed to them come from abstracts and bibliographic records, not from reading full texts.
- Works I know of but could not confirm tonight are kept out of the argument and listed separately in section 4 as **unverified leads**. They are not citations. Do not quote them until someone has checked them.
- Coverage is strongest for themes 1, 3, 4, 5, 6 and 8. It is thin for theme 2 (regulator studies), theme 7 (valuation) and theme 9 (fraud), and for 2020–2026 work in the economics and consumer-behaviour themes.

Markers used below: **[V]** = verified tonight from a source; **[I]** = my inference; **[B]** = background knowledge not verified tonight.

---

## 1. Bottom line

1. The founder's 70–120 minute experience is what sixty years of search theory predicts: search is costly, so people stop early, and prices for identical goods stay dispersed. Online price dispersion of 25–33% for identical books and CDs was measured in 2000 [1], and a comparison site with four million price observations found no convergence to one price [2]. Comparison engines did not remove the problem (confidence: high).
2. Retailers respond to comparison engines by making comparison harder (obfuscation: add-ons, bait listings, incompatible product variants) [3]. A comparison app is in an arms race with the sellers it lists, and "total cost" comparison is the part sellers fight hardest (confidence: high on the mechanism, medium on how strongly it applies to Australian retail in 2026).
3. People search far less than the app's premise assumes. In camera purchases, shoppers ran about 14 searches over about 15 days but stayed in a narrow part of the product space, and what they bought was close to what they found on day one [5]. The product should shorten and confirm a decision the user has largely made, not present a wide exploration (confidence: medium-high).
4. Whoever controls the ranking controls what gets looked at. A randomised experiment at Expedia showed rank position drives what users inspect, by lowering search cost, though not what they buy once they have inspected it [6]. A deal app's ranking is its main power and its main conflict of interest. Theory shows commission-funded comparison sites can raise prices overall [8], and the UK regulator found benefits alongside concerns about contracts that stop suppliers offering lower prices elsewhere [7].
5. Second-hand markets work when sellers disclose and buyers can verify. Voluntary disclosure (photos, text) carries measurable price weight on eBay Motors [11]; established seller reputation is worth roughly 8% of the selling price in a controlled field experiment [12]. Facebook Marketplace and Gumtree offer much weaker versions of both, which is where an app can add value (confidence: medium; the evidence is from eBay, not from Australian classifieds).
6. "Is this a good deal?" is a reference-price question, and the literature is clear that the feeling of a deal (transaction utility) is separate from the value of the item [14][15][16]. It is also easy to manipulate: inflated "original" prices raise what people pay [17][18]. An app that supplies an honest reference price (real new price, real recent used prices) addresses the documented mechanism directly.
7. The machine-learning parts are feasible for new goods and unproven for used goods. LLMs now match product offers about as well as models fine-tuned on thousands of examples, with few or no training examples [27]. But the benchmarks are retailer offers with structured titles; all matchers degrade on products they have not seen [26], and I found no benchmark for matching messy second-hand listings to a canonical product.
8. LLM shopping agents are not reliable enough to act unsupervised. The best agents succeed on under half of realistic shopping tasks in the latest benchmark [34], and vision-language shopping agents show position bias and concentrate choices on a few products [37]. Use the LLM to extract, match and explain; compute prices and verdicts from retrieved data.
9. I found no academic work on unified new-versus-used decision support for general goods, nor on total-cost-of-acquisition comparison across shipping, pickup travel, risk and time. Within the limits of tonight's search that is a real gap, and it is the product's opening (confidence: medium; absence of evidence from a truncated search).

---

## 2. Findings

### Theme 1 — Consumer search and search costs

**Foundational works**

| Work | What it established | Status |
|---|---|---|
| Stigler (1961) [0] | Price dispersion is a consequence of costly search; buyers search until the expected saving no longer covers the cost | [V] |
| Brynjolfsson & Smith (2000) [1] | 8,500+ price observations, 41 internet and conventional outlets, 15 months. Online prices for identical books differed by an average of 33%, CDs 25%. Brand and trust still differentiated sellers | [V] |
| Baye, Morgan & Scholten (2004) [2] | Four million daily prices, 1,000+ consumer electronics products on Shopper.com. Little support for convergence to one price. Gap between the two lowest prices averaged 22% with two sellers listed, 3.5% with seventeen | [V] |
| Ellison & Ellison (2009) [3] | With a price search engine dominant, demand becomes very price-sensitive for some products; retailers respond with obfuscation that frustrates search and protects markups | [V] |
| De los Santos, Hortaçsu & Wildenbeest (2012) [4] | Browsing and purchase data for online bookstores reject the textbook sequential-search model; fixed-sample-size search (decide how many places to check, then check them) fits better. Authors caution it may not generalise | [V] |
| Bronnenberg, Kim & Mela (2016) [5] | Camera shoppers: 14 searches on average before purchase; about 15 days and six sessions; about 40% searched one brand only and 20% one model only; early search strongly predicts the final purchase | [V] (session/brand figures are from the INFORMS press release, not the paper text) |
| Ursu (2018) [6] | Randomised rankings at Expedia: position affects what is searched, not purchase conditional on search; estimated position effect US$1.92; rankings work by lowering search cost | [V] |

**Consensus.** Search costs are real and large enough to sustain dispersion for identical goods even where comparison is one click away [0][1][2]. Shoppers examine few options and settle early [5]. Sellers adapt to transparency [3].

**Live disagreements.** Whether people search sequentially (stop when a good-enough price appears) or pick a sample size up front [4]. This matters for design: a sequential searcher wants a "stop now" signal; a fixed-sample searcher wants the whole sample delivered at once. The evidence in [4] favours the second for books, with an explicit caveat about other settings.

**What I could not verify tonight.** Measured time and money left on the table by search in the 2020s, drip-pricing experiments, and work on price beliefs. Leads are in section 4.

**Design implication.**
- Deliver the full sample in one step (new prices at the main retailers plus recent used prices) because that matches how people appear to search [4] and removes the 50–100 minute phase the founder described. [I]
- Then give an explicit stopping signal ("you have seen the realistic range; further search is unlikely to save more than $X"). The value of the product is permission to stop. [I]
- Expect narrow intent: the user usually arrives with a specific item or a listing in hand [5]. Build listing-first entry (paste or share a Marketplace listing) ahead of open-ended browsing. [I]
- Report dispersion itself ("new price ranges from $A to $B across 6 retailers"). The literature says the spread is real and persistent, and it is the direct evidence that checking was worthwhile. [I]

### Theme 2 — Price comparison engines

**Verified sources**

| Source | Finding | Status |
|---|---|---|
| UK CMA, Digital comparison tools market study, final report, 26 Sept 2017 [7] | Covered comparison sites and apps, notably car and home insurance, energy, broadband, flights and credit cards. Found comparison tools help people shop around and switch, which can strengthen competition. Raised concern about contract terms that limit suppliers' ability to offer lower prices on other channels | [V] (headline findings only; I did not retrieve the recommendations) |
| Ronayne (2021) [8] | Theoretical model: because suppliers pay comparison sites fees that are passed through to prices, the existence of comparison sites can leave consumers worse off, and more competing sites can worsen it | [V] (findings taken from the working-paper version and university press coverage) |
| Ellison & Ellison (2009) [3] | Retailers on a price search engine obfuscate to defeat ranking by price | [V] |
| Ursu (2018) [6] | Ranking position causally directs attention | [V] |
| ACCC Digital Platform Services Inquiry, report on general online retail marketplaces (dated March 2022, released April 2022) [9] | Examined Amazon Australia, Catch, eBay Australia and Kogan; raised a range of consumer and seller concerns, including how marketplace algorithms are used | [V] (via ACCC page and trade-press reports) |
| ACCC Digital Platform Services Inquiry, final report (dated March 2025, released June 2025) [10] | Identifies manipulative design practices, fake reviews and product-safety issues as common features of online retail marketplaces | [V] (via ACCC page and law-firm summaries) |

**Consensus.** Comparison tools lower search costs and, on balance, help consumers who use them [7]. Their commercial model (fees, commissions, paid placement) creates incentives that work against those consumers [8], and ranking is where the incentive bites because position steers attention [6].

**Live disagreements.** Whether comparison intermediaries lower or raise average market prices once their fees are counted. [8] shows the price-raising case is theoretically coherent; the CMA [7] found net benefit in the sectors it studied.

**Not verified tonight.** The ACCC's 2014 report on comparator websites in Australia; the European Commission's 2014 study of comparison tools; empirical work on sponsored placement and rate-parity clauses. The search for the ACCC report returned nothing and my follow-up was cut off by the search limit. Leads in section 4.

**Design implication.**
- Decide the revenue model before the ranking algorithm. If affiliate commission funds the app, used listings from Marketplace and Gumtree pay nothing and new retail pays something, which biases the "worth it?" verdict toward buying new. The verdict must be computed independently of who pays. [I]
- Disclose how results are ordered and mark anything paid. This is both the regulator's direction of travel [7][10] and a differentiator. [I]
- Build for obfuscation from day one: bundles, model-number variants exclusive to one retailer, shipping revealed late. Total-cost normalisation is the defence. [I from 3]

### Theme 3 — Second-hand markets

**Verified sources**

| Work | Finding | Status |
|---|---|---|
| Akerlof (1970) [11a] | When buyers cannot observe quality, low-quality goods drive out high-quality ones and the market can shrink or fail | [V] |
| Lewis (2011) [11] | eBay Motors: sellers voluntarily disclose private information in the listing; the listing acts as a contract to deliver the car shown; online disclosures are important price determinants, and the cost of disclosing affects both disclosure and price | [V] |
| Resnick, Zeckhauser, Swanson & Lockwood (2006) [12] | Randomised field experiment on eBay: an established high-reputation identity earned about 8.1% more willingness-to-pay than new identities selling matched items (7.6% in the working-paper version). One or two negatives on a new seller made no detectable difference | [V] |
| Tadelis (2016) [13] | Review of reputation and feedback systems on platforms, including evidence that feedback is biased upward | [V] |
| "The Limits of Reputation in Platform Markets: An Empirical Analysis and Field Experiment", NBER Working Paper 20830 [13a] | Title and NBER number verified; authors as I recall them are Nosko and Tadelis [B] | [V] title only |
| Guiot & Roux (2010) [13b] | Second-hand shopper motivation scale from two French samples (708 subjects): eight factors under three headings — critical (distance from the conventional retail system), economic, and recreational. Four shopper segments | [V] (page range differs between indexes; check before quoting pages) |

**Consensus.** Adverse selection is the default condition of used-goods markets [11a]. It is mitigated, not removed, by disclosure that binds the seller [11] and by reputation that has measurable monetary value [12]. Feedback scores are inflated and carry less information than they appear to [13]. Motivation to buy used is not only price; treasure-hunting and anti-consumerist motives are distinct and measurable [13b].

**Live disagreements.** How much reputation systems really discipline sellers given inflated feedback [13][13a]. Whether sustainability is a real driver of used purchases or a stated-preference artefact — I could not retrieve the 2020–2026 recommerce literature tonight to settle this.

**Gap found.** I found nothing on **how buyers form a reference price for a used item**. The reference-price literature (theme 4) is about new retail goods. The founder's behaviour — using the new price at BCF as the anchor for a used rod — is plausible and consistent with theory, but I have no study that measures it. Confidence that this is a true gap: medium.

**Design implication.**
- Classified platforms such as Facebook Marketplace lack eBay's binding listing contract and structured feedback. The app can partly substitute: score how much a listing discloses (photo count, model number present, stated faults, age), because disclosure is what carried price information in [11]. [I]
- Treat seller-profile signals as weak evidence. One or two negatives did not move prices in [12], and positive feedback is inflated [13]. [I]
- Price the risk explicitly. A used item with no warranty and no return right is worth less than the same item with them; the roughly 8% reputation premium in [12] is one calibration point for how much buyers discount uncertainty. [I]
- Serve more than the bargain hunter. The recreational motive in [13b] suggests a "find" framing may engage a segment that a pure savings calculator will not. [I]

### Theme 4 — Reference prices, anchoring and deal evaluation

**Verified sources**

| Work | Finding | Status |
|---|---|---|
| Thaler (1985) [14] | Introduced transaction utility: the satisfaction of a purchase depends on the price paid relative to a reference price, separately from the value of the good itself | [V] (DOI for the 1985 original inferred from the RePEc link; the 2008 reprint DOI is confirmed) |
| Grewal, Monroe & Krishnan (1998) [15] | Advertised reference prices shift buyers' internal reference price; perceived transaction value feeds acquisition value, which drives purchase and search intentions | [V] |
| Mazumdar, Raj & Sinha (2005) [16] | Integrative review of how reference prices are formed, retrieved and used; sets out open questions | [V] |
| Ngwe, HBS research on outlet "original" prices [17] | For each US$1 increase in the posted original price, consumers paid about 77 cents more on average. Frequent repeat shoppers were least swayed; shoppers with the least brand knowledge paid more | [V] via Harvard Business School Working Knowledge; I could not confirm the working paper's exact title and year |
| Staelin, Urbany & Ngwe (2023) [18] | Journal of Marketing article on fictitious (inflated reference) pricing and its regulation; associated coverage recommends disclosing a "true normal price" | [V] existence and topic; details from press coverage |

**Consensus.** People judge a deal against a reference point, not against intrinsic value [14][16]. An external reference price supplied by the seller moves the internal one [15]. Inflated reference prices work on real shoppers and work best on the least informed [17].

**Live disagreements.** How internal reference prices are formed (memory of past prices versus prices visible at the point of purchase) and how to regulate fictitious pricing [16][18].

**Not verified tonight.** Regret and purchase-confidence studies; anchoring experiments; Australian was/now enforcement cases. Leads in section 4.

**Design implication.**
- The app's core output is a trustworthy external reference price. For a used listing: the lowest current new price, the typical recent used price, and where this listing sits between them. [I]
- Never display a retailer's "was" price as the reference. Compute the reference from observed price history, in the spirit of the "true normal price" remedy [18]. This is a concrete trust feature. [I]
- The least informed benefit most [17]. Categories where buyers shop rarely and lack price knowledge (fishing gear, tools, baby equipment, appliances) are better beachheads than phones, where price knowledge is widespread. [I]
- Separate the two judgments on screen: "is it a good price?" (transaction) and "is it worth having at this price?" (acquisition). The literature treats them as distinct [14][15]; an app that merges them will endorse cheap things nobody needed. [I]

### Theme 5 — Choice overload and decision support

**Verified sources**

| Work | Finding | Status |
|---|---|---|
| Iyengar & Lepper (2000) [19] | The jam study: large assortments attracted attention but depressed purchase | [V] existence; details from secondary accounts |
| Scheibehenne, Greifeneder & Todd (2010) [20] | Meta-analysis of 50 experiments (63 conditions, N = 5,036): mean choice-overload effect virtually zero, large variance, evidence of publication bias | [V] |
| Chernev, Böckenholt & Goodman (2015) [21] | Meta-analysis of 99 observations: overload appears reliably under four conditions — complex choice sets, difficult tasks, uncertain preferences, and a goal of minimising effort | [V] |
| Schwartz et al. (2002) [22] | Maximisers (who seek the best option) report less happiness and more regret than satisficers across seven samples | [V] |
| Häubl & Trifts (2000) [23] | Controlled experiment: a recommendation agent and a comparison matrix each reduced search effort, shrank consideration sets while raising their quality, and improved decision quality | [V] |
| Dietvorst, Simmons & Massey (2015) [24] | People abandon an algorithm after seeing it err, even when it outperforms humans. A follow-up by the same authors found that letting users adjust the algorithm's output increases use | [V] (follow-up noted in search results; not separately verified) |
| Logg, Minson & Moore (2019) [25] | People often weight algorithmic advice more than human advice; the effect weakens when the alternative is their own judgment | [V] |

**Consensus.** Choice overload is conditional, not universal [20][21]. The conditions that trigger it — complex options, hard trade-offs, uncertain preferences — describe a new-versus-used comparison well [I from 21]. Screening plus side-by-side comparison improves decisions and reduces effort [23].

**Live disagreements.** Algorithm aversion versus appreciation [24][25]. The reconciliation suggested by the two papers together is that people accept algorithmic advice until they see it fail, and then over-correct.

**Design implication.**
- Show few options. Three or so candidate deals with a named best, plus a comparison table, is the configuration that the experimental evidence supports [23][21]. [I]
- The founder is describing maximiser behaviour (100 minutes to be sure). Maximisers suffer regret [22]. Design for them: show what was checked and how many sources were covered, so the user can believe the search was exhaustive without doing it. [I]
- A visibly wrong verdict is costly out of proportion [24]. Show confidence, show the evidence behind each verdict, and prefer "not enough data to judge" over a guess. [I]
- Let users adjust inputs (condition, how far they will drive, what their time is worth). Adjustability raised uptake of imperfect algorithms in the follow-up to [24]. [I]

### Theme 6 — Product matching and entity resolution

**Verified sources**

| Work | Finding | Status |
|---|---|---|
| Mudgal et al. (2018), DeepMatcher [26a] | Deep learning does not beat classical methods on clean structured records but clearly beats them on textual and dirty records | [V] |
| Li et al. (2020/21), Ditto [26b] | Fine-tuned pre-trained language models beat previous best by up to 29% F1 on benchmarks (one arXiv version says 19%); matched prior results with half the labelled data; 96.5% F1 on a large company-matching task | [V] |
| Narayan et al. (2022) [26c] | Entity matching posed as a prompt to a large language model; the largest GPT-3 model matched or beat prior methods zero- and few-shot | [V] |
| Peeters, Der & Bizer (2024), WDC Products [26] | Benchmark of 11,715 product offers for 2,162 products from real web shops, varying corner-case share, unseen products, and training-set size. F1 from 0.64 to 0.89 depending on variant. Every matcher drops sharply on unseen products | [V] |
| Peeters, Steiner & Bizer (2025) [27] | Best LLMs need zero or few examples to match models fine-tuned on thousands; LLMs are more robust to unseen products; GPT-4 can produce structured explanations of match decisions | [V] |

**Consensus.** Matching the same product across retailer offers is a well-studied problem with a clear trajectory: classical similarity features, then fine-tuned transformers [26a][26b], now general LLMs with little or no task-specific training [26c][27]. Hard cases are near-identical variants (the corner cases in [26]).

**Live disagreements.** Cost versus accuracy of LLM matching at scale, and whether fine-tuned small models still win when plenty of labels exist. [B]

**Gap found.** Every benchmark I verified uses retailer offers, which have titles, brands and often identifiers. I found no benchmark and no study on matching **second-hand listings** — "fishing rod and reel, barely used, pick up Frankston" with three photos — to a canonical product. I also could not complete a search on image-based matching. Confidence that the text gap is real: medium.

**Design implication.**
- New-goods matching can be built with current LLMs and no training data [27]. This part of the product is low technical risk. [I]
- Used-listing identification is the research problem and the technical moat. Do not assume retailer-benchmark accuracy transfers; [26] shows accuracy falls on unseen products even within retailer data. [I]
- Variant confusion (the 7 ft versus 9 ft rod, the 2500 versus 4000 reel) is the corner case that most damages a price verdict. When the model cannot resolve the variant, ask the user or show a price range across variants. [I]
- Use the explanation capability in [27] in the interface: "matched to Shimano X because the listing says …". It supports the trust requirements in theme 5. [I]

### Theme 7 — Used-item valuation

**Verified sources**

| Work | Finding | Status |
|---|---|---|
| Rosen (1974) [28] | Hedonic pricing: a product's price decomposes into implicit prices of its attributes. The theoretical basis for attribute-based valuation | [V] |
| Han et al. (2020), text + images [29] | Second-hand price suggestion built as two models: a classifier that first decides whether the listing's images and text are good enough to price at all, then a regression that predicts the price | [V] (arXiv 2012.06008; the search summary gives the venue as ACM Multimedia 2020, which I did not confirm separately) |
| Han et al. (2020), vision-based [30] | Companion paper pricing second-hand items mainly from images, adding brand, category and specification attributes | [V] (arXiv 2012.06009) |
| Yamaura et al. (2019) [31] | Multi-modal deep learning (images plus attributes) for resale price of second-hand jewellery | [V] (arXiv 1907.00661) |
| Mercari Price Suggestion Challenge (Kaggle) [32] | Public competition, 2,384 teams, US$100,000 prize, predicting listing prices from title, description, category, brand and condition | [V] as a competition. I found **no peer-reviewed paper** on it — only competitor write-ups and a student thesis |

**Consensus.** Price prediction from listing text, category, brand and stated condition is tractable enough to have been run as a mass competition [32]. Multimodal models exist [29][30][31]. The most transferable design idea is in [29]: decide first whether an item can be priced, and decline when it cannot.

**Not verified tonight.** Depreciation-curve studies, used-vehicle and used-phone price prediction, automated condition grading from photos, and uncertainty methods such as conformal prediction. The one search I ran for 2022–2024 multimodal work returned only 2019–2020 papers.

**Design implication.**
- Output a range and a confidence, never a single number. Adopt the "can this be priced?" gate from [29]. [I]
- Prefer comparables over a learned model at launch: recent sold or listed prices for the same matched product, adjusted for condition. It needs no training data and is explainable. A hedonic model [28] becomes useful once the app has its own data. [I]
- The practical obstacle in Australia is data: sold prices on Facebook Marketplace and Gumtree are not observable; eBay sold listings are the nearest proxy. This is a question for the data-access track, not the literature. [I]

### Theme 8 — LLM shopping agents

**Verified sources**

| Benchmark / study | What it measures | Headline result | Status |
|---|---|---|---|
| WebShop, Yao et al., NeurIPS 2022 [33] | Simulated shop, over one million products, 12,087 instructions | Best model 29% task success versus 59% for expert humans | [V] |
| Shopping MMLU, Jin et al., NeurIPS 2024 [33a] | 57 tasks, 20,799 questions from Amazon data on shopping knowledge and reasoning | General-benchmark performance strongly predicts shopping performance | [V] |
| ShoppingBench, Wang et al., AAAI 2026 [34] | 3,310 instructions over 2.5M real products; finding products, knowledge questions, multi-seller orders, coupons and budgets | Leading agents including GPT-4.1 under 50% absolute success | [V] |
| DeepShop, Lyu et al., arXiv 2506.02839 [35] | Shopping queries with layered attributes, filters and sorting, on live sites | Exists; I did not retrieve results | [V] existence |
| WebMall, arXiv 2508.13024 [36] | Comparison shopping across four simulated shops | Exists; I did not retrieve results | [V] existence |
| Allouah et al., "What Is Your AI Agent Buying?", arXiv 2508.02630 [37] | Randomised mock marketplace testing vision-language shopping agents | Strong position bias that differs by model; agents penalise sponsored tags and reward platform endorsements; price and rating sensitivity varies sharply by model; demand concentrates on a few products; small seller-side description tweaks shift market share | [V] |
| ShopSimulator (arXiv 2601.18225), ShopGym (arXiv 2605.16116), ComboShoppingBench (arXiv 2608.09282) [38] | Newer 2026 benchmarks | Exist per search results; not examined | [V] existence only |

**Consensus.** Agents have improved but still fail on more than half of realistic multi-step shopping tasks [33][34]. Their choices are sensitive to presentation and manipulable by sellers [37].

**Live disagreements.** Whether benchmark sandboxes predict real-site performance; [33] reports that performance transferred to Amazon and eBay, but that was a 2022 result with far weaker models. [B for the caveat]

**Gap found.** None of the benchmarks I verified includes second-hand listings, condition, negotiation or pickup logistics. I could not complete searches on price hallucination rates or consumer trust in AI shopping advice.

**Design implication.**
- Do not let a model state a price from its own knowledge. Every price shown must come from a retrieved, timestamped, linked source. [I]
- Use LLMs where the benchmarks show strength (understanding products and attributes [33a], matching [27]) and keep arithmetic, ranking and the verdict in ordinary code. [I]
- Seller-side manipulation of agent choices [37] will reach marketplace listings. Rank on verified fields (price, matched model, distance), not on persuasive description text. [I]
- The under-50% result [34] is a moat argument as well as a caution: a narrow, well-instrumented pipeline for one task (is this used item worth it?) can beat a general agent for some time. [I]

### Theme 9 — Fraud and safety in peer-to-peer marketplaces

**Verified sources**

| Source | Finding | Status |
|---|---|---|
| National Anti-Scam Centre, Targeting Scams report on 2024 [39] | Combined reported scam losses A$2.03 billion in 2024, down 25.9% on 2023. Scamwatch alone: 249,448 reports and A$318.8m in losses, down from 301,778 reports and A$476.8m in 2023. Largest categories by loss: investment A$945.0m, romance A$156.8m, payment redirection A$152.6m, remote access A$106.0m, phishing A$84.5m | [V] |
| National Anti-Scam Centre, Targeting Scams report on 2025 (released March 2026) [40] | Combined reported losses A$2.18 billion in 2025, up 7.8% | [V] |
| ACCC Digital Platform Services Inquiry final report [10] | Fake reviews and product-safety issues common on online retail marketplaces | [V] |

**What I could not establish.** The loss and report figures for **buying and selling scams** and for classified/marketplace scams specifically. The search results did not include that breakdown and I could not open the report. I also could not run searches on fraud-detection methods or on which listing signals predict fraud. Theme 9 is the weakest part of this review.

**Consensus (limited).** Scam losses in Australia are large and rose again in 2025 [39][40]. Buying-and-selling scams are not in the top five categories by loss [39], which suggests they are numerous but individually small — [I], and I could not confirm report counts.

**Design implication.**
- A safety layer is defensible on the headline figures alone, but the specific signals to use need the fraud literature this review did not reach. [I]
- Price far below the app's own reference range is a signal the app is uniquely placed to compute. "Too cheap for a real listing" is the mirror image of "good deal", and a deal finder that cannot tell them apart will send users to scams. [I]
- Do not claim scam detection in marketing until it is validated. Theme 5 shows visible errors destroy trust in algorithmic advice [24]. [I]

---

## 3. Implications for the product

**What the literature supports building**

1. **A reference-price engine for used listings.** Input: a second-hand listing. Output: matched product, current new-price range across Australian retailers, typical used price, and where this listing sits. This addresses the documented mechanism (deal judgment is reference-dependent [14][15][16]) in the place where I found no academic or regulator work (reference prices for used goods).
2. **A stopping signal.** Search theory says the user's problem is not finding prices but knowing when to stop [0][4][5]. "You have seen the realistic range" is the product.
3. **A short, explained answer.** Few options, a comparison table, a verdict with its evidence and confidence [21][23][24][27].
4. **Total cost, not sticker price.** Sellers obfuscate through add-ons and shipping [3]; pickup adds travel and time. Normalising these is the direct counter.
5. **Honest history instead of "was" prices** [17][18].

**What to avoid**

1. An autonomous agent that browses and decides. Current agents fail more often than they succeed on realistic tasks [34] and are steerable by listing text [37].
2. Commission-ordered rankings. Theory [8] and regulators [7][10] both point at this as the way comparison tools turn against users, and it would bias the app toward new goods.
3. A single predicted "fair price" without a range. Valuation research itself gates on whether an item is priceable [29].
4. A wide catalogue browsing experience. Shoppers stay narrow and decide early [5].
5. Trusting seller ratings on classifieds as a strong signal [12][13].

**Where the opening is**

- Categories bought rarely by people without price knowledge, where inflated reference prices bite hardest [17] and where used supply is deep: outdoor and fishing gear, tools, baby goods, furniture, appliances, bikes.
- The used-listing-to-product matching problem. It is unbenchmarked as far as I could find, which makes it both the main technical risk and the hardest part for a competitor to copy.
- The maximiser segment [22]: people who currently spend an hour checking. They are the ones with a felt problem and a reason to pay or return.

**Bad news stated plainly**

- Comparison engines have existed for 25 years and the academic record is that they did not eliminate dispersion and did provoke seller counter-measures [2][3]. New-goods price comparison alone is not a new idea and the literature gives no reason to expect a newcomer to win there.
- The evidence that people search little [5] cuts against the size of the market: most shoppers may not feel the founder's pain because they do not do the founder's checking.
- The used-goods valuation and fraud evidence I could verify is thin. The parts of the product that depend on them rest on inference, not on literature.

---

## 4. Open questions

**Questions the review could not settle**

| Question | Why open | How to settle |
|---|---|---|
| How much time and money do Australian shoppers lose to incomplete search in 2026? | I verified no study after 2018 on measured search effort, and none for Australia | Search the 2020–2026 marketing-science literature; or run a 200-person survey with a timed shopping task |
| How do buyers form a reference price for a used item? | Nothing found | Targeted search; if still nothing, this is a publishable study the app could run |
| How well do current LLMs match classified listings to products? | No benchmark found | Hand-label 300–500 Australian Marketplace/Gumtree listings in two categories and test |
| What share of Australian scam reports and losses are buying-and-selling scams on classifieds? | Breakdown not retrieved | Read Appendix tables of the NASC reports [39][40] and Scamwatch statistics |
| What listing signals predict fraud? | Searches not run | Literature search on classified-ad fraud detection |
| What did the ACCC conclude about comparator websites? | Search returned nothing; follow-up blocked | Retrieve the ACCC's comparator website report and guidance from accc.gov.au |
| Does sustainability really drive used purchases? | 2020–2026 recommerce literature not retrieved | Literature search; check for behavioural rather than stated-preference studies |
| Depreciation curves by category | Not retrieved | Literature search; or estimate from eBay sold listings |

**Unverified leads — recalled from memory, NOT confirmed tonight, not to be cited until checked**

These are works I believe exist and are relevant. I could not check authors, years, venues or findings tonight, so details may be wrong. Each needs to be looked up before use.

- Theme 1: Weitzman (1979), optimal sequential search, *Econometrica*. Diamond (1971), a model of price adjustment. Varian (1980), "A Model of Sales". Baye & Morgan (2001), information gatekeepers, *AER*. Dinerstein, Einav, Levin & Sundaresan (2018), consumer price search and platform design (eBay), *AER*. Blake, Moshary, Sweeney & Tadelis (2021), price salience (StubHub fees), *Marketing Science*. Honka (2014), search and switching costs in auto insurance, *RAND Journal*. Gorodnichenko, Sheremirov & Talavera (2018), price setting in online markets.
- Theme 2: ACCC (2014), the comparator website industry in Australia. European Commission (2014), study of comparison tools. Edelman & Wright (2015), price coherence and excessive intermediation, *QJE*. Hunold, Kesler & Laitenberger (2020), online travel agent rankings, *Marketing Science*. Armstrong, Vickers & Zhou (2009), prominence and consumer search.
- Theme 3: Cabral & Hortaçsu (2010), dynamics of seller reputation on eBay. Jin & Kato (2006), price, quality and reputation field experiment. Ghose, Smith & Telang (2006), internet exchanges for used books. Einav, Farronato & Levin (2016), peer-to-peer markets. Backus, Blake, Larsen & Tadelis (2020), sequential bargaining on eBay Best Offer. Styvén & Mariani (2020) and Padmavathy, Swapana & Paul (2019) on online second-hand shopping motivations.
- Theme 4: Urbany, Bearden & Weilbaker (1988), advertised reference prices. Kalyanaram & Winer (1995), empirical generalisations from reference price research. Simonson (1992), anticipated regret in purchase decisions. Tversky & Kahneman (1974), anchoring.
- Theme 5: Xiao & Benbasat (2007), e-commerce recommendation agents review, *MIS Quarterly*. Diehl (2005), searching too much in ordered environments. Castelo, Bos & Lehmann (2019), task-dependent algorithm aversion. Longoni & Cian (2022), AI recommendations in utilitarian versus hedonic contexts.
- Theme 6: Fellegi & Sunter (1969), a theory for record linkage. Köpcke, Thor & Rahm (2010), evaluation of entity resolution on real-world problems. Primpeli, Peeters & Bizer (2019), the WDC training set for large-scale product matching.
- Theme 7: Angelopoulos & Bates, introduction to conformal prediction (for calibrated price ranges).
- Theme 8: Zhou et al. (2023), WebArena. Deng et al. (2023), Mind2Web. Kumar & Lakkaraju (2024), manipulating LLMs to increase product visibility. Aggarwal et al. (2024), generative engine optimisation.
- Theme 9: Park et al. (2014), "Scambaiter", on Craigslist scams, NDSS.

**Access limits that should be fixed before a second pass**

- Raise the web-search allowance (the shared limit was 200 searches across all agents).
- Allow `arxiv.org`, `export.arxiv.org`, `api.crossref.org` and `econpapers.repec.org` in the session's network settings so references can be verified directly.

---

## 5. Gaps in the literature

Stated with the caveat that tonight's search was cut short; each "not found" is medium confidence at best.

1. **Unified new-versus-used decision support for general goods.** Not found. The search literature studies new goods at retailers [1][2][5]; the second-hand literature studies trust and motivation within used markets [11][12][13b]. I found nothing that studies a consumer choosing between a new and a used instance of the same product, outside vehicles.
2. **Reference-price formation for used goods.** Not found. Reference-price theory [14][15][16] was built on new retail goods with advertised prices. How a buyer anchors on a new price to judge a used one, and what discount they treat as fair by category and condition, appears unmeasured.
3. **Total cost of acquisition.** Not found as a consumer decision-support problem. Obfuscation research covers add-on fees [3], but I found nothing combining price, shipping, travel to pick up, time, and the expected cost of risk (no warranty, no returns, fraud) into one comparable figure.
4. **Buy / wait / skip advice across conditions.** Not found. Deal evaluation research explains how consumers feel about a price [14][15]; none of what I verified evaluates advice that also considers waiting for a better used listing or a retail sale.
5. **Matching unstructured second-hand listings to canonical products.** Benchmarks cover retailer offers only [26][27]. No classified-listing benchmark found, in text or images.
6. **Second-hand tasks in LLM agent benchmarks.** None of the verified shopping benchmarks include condition, negotiation or pickup [33][34][35][36].
7. **Search stopping in second-hand markets.** Stopping rules are studied for posted-price retail [4]. Used listings arrive and disappear over time, which changes the problem; I found no treatment.
8. **Australian evidence.** Apart from regulator reports [9][10][39][40], everything verified here is US, UK, European or Chinese. Australian retail has different concentration, shipping distances and classifieds habits.

### Candidate research questions the product could be built to answer

1. **RQ1 — Reference prices for used goods.** When shown the current new price and the typical used price for a matched product, how does a buyer's willingness to pay for a used listing change, and what used-to-new price ratio do buyers treat as fair, by category and condition? Testable in-app by randomising which references are shown.
2. **RQ2 — Stopping.** Does a "you have seen the realistic range" signal reduce search time and post-purchase regret without increasing the price paid? Outcome measures: time to decision, price relative to the best available, and a regret question two weeks later. Maximiser/satisficer scores [22] as a moderator.
3. **RQ3 — Listing identification.** How accurately can current LLMs, with text and photos, match Australian classified listings to a canonical product and variant, and how does verdict accuracy degrade with variant ambiguity? Produces the first benchmark of its kind.
4. **RQ4 — Total cost.** Does presenting a single total-cost-of-acquisition figure (price, shipping, travel, time, risk allowance) change choices between pickup-used, shipped-used and new, compared with presenting sticker prices? Which component moves decisions most?
5. **RQ5 — Trust in the verdict.** Do evidence-backed verdicts with stated confidence and adjustable assumptions sustain trust after a visible error better than a bare verdict [24][25]?

---

## 6. Sources

### Verified references

[0] Stigler, G. J. (1961). The Economics of Information. *Journal of Political Economy*, 69(3), 213–225. https://doi.org/10.1086/258464 — record: https://econpapers.repec.org/RePEc:ucp:jpolec:v:69:y:1961:p:213

[1] Brynjolfsson, E., & Smith, M. D. (2000). Frictionless Commerce? A Comparison of Internet and Conventional Retailers. *Management Science*, 46(4), 563–585. https://doi.org/10.1287/mnsc.46.4.563.12061 — record: https://econpapers.repec.org/RePEc:inm:ormnsc:v:46:y:2000:i:4:p:563-585

[2] Baye, M. R., Morgan, J., & Scholten, P. (2004). Price Dispersion in the Small and in the Large: Evidence from an Internet Price Comparison Site. *Journal of Industrial Economics*, 52(4), 463–496. https://ideas.repec.org/a/bla/jindec/v52y2004i4p463-496.html — author copy: https://faculty.haas.berkeley.edu/rjmorgan/Small&Large.pdf

[3] Ellison, G., & Ellison, S. F. (2009). Search, Obfuscation, and Price Elasticities on the Internet. *Econometrica*, 77(2), 427–452. https://doi.org/10.3982/ECTA5708 — https://www.econometricsociety.org/publications/econometrica/2009/03/01/search-obfuscation-and-price-elasticities-internet

[4] De los Santos, B., Hortaçsu, A., & Wildenbeest, M. R. (2012). Testing Models of Consumer Search Using Data on Web Browsing and Purchasing Behavior. *American Economic Review*, 102(6), 2955–2980. https://econpapers.repec.org/RePEc:aea:aecrev:v:102:y:2012:i:6:p:2955-80

[5] Bronnenberg, B. J., Kim, J. B., & Mela, C. F. (2016). Zooming In on Choice: How Do Consumers Search for Cameras Online? *Marketing Science*, 35(5), 693–712. https://doi.org/10.1287/mksc.2016.0977 — press release: https://www.informs.org/News-Room/INFORMS-Releases/News-Releases/Consumers-may-search-online-for-30-days-but-buy-close-to-what-they-found-on-the-first-day

[6] Ursu, R. M. (2018). The Power of Rankings: Quantifying the Effect of Rankings on Online Consumer Search and Purchase Decisions. *Marketing Science*, 37(4), 530–552. https://doi.org/10.1287/mksc.2017.1072 — record: https://econpapers.repec.org/RePEc:inm:ormksc:v:37:y:2018:i:4:p:530-552

[7] Competition and Markets Authority (UK) (2017). Digital comparison tools market study: final report. 26 September 2017. https://www.gov.uk/cma-cases/digital-comparison-tools-market-study — report: https://assets.publishing.service.gov.uk/media/59c93546e5274a77468120d6/digital-comparison-tools-market-study-final-report.pdf — FCA response: https://www.fca.org.uk/news/statements/response-cmas-final-report-dct-market-study

[8] Ronayne, D. (2021). Price Comparison Websites. *International Economic Review*, 62(3), 1081–1110. https://doi.org/10.1111/iere.12504 — record: https://econpapers.repec.org/RePEc:wly:iecrev:v:62:y:2021:i:3:p:1081-1110 — press: https://warwick.ac.uk/news/pressreleases/we_could_all/

[9] ACCC (2022). Digital Platform Services Inquiry, March 2022 interim report (general online retail marketplaces). https://www.accc.gov.au/inquiries-and-consultations/finalised-inquiries-and-monitoring/digital-platform-services-inquiry-2020-25/march-2022-interim-report — coverage: https://www.itnews.com.au/news/accc-targets-algorithm-misuse-by-online-retail-giants-579314

[10] ACCC (2025). Digital Platform Services Inquiry, March 2025 final report. https://www.accc.gov.au/inquiries-and-consultations/finalised-inquiries/digital-platform-services-inquiry-2020-25/march-2025-final-report — summary: https://jws.com.au/what-we-think/accc-calls-for-increased-regulation-in-digital-platforms-services-inquiry-final-report/

[11a] Akerlof, G. A. (1970). The Market for "Lemons": Quality Uncertainty and the Market Mechanism. *Quarterly Journal of Economics*, 84(3), 488–500. https://doi.org/10.2307/1879431

[11] Lewis, G. (2011). Asymmetric Information, Adverse Selection and Online Disclosure: The Case of eBay Motors. *American Economic Review*, 101(4), 1535–1546. https://doi.org/10.1257/aer.101.4.1535 — record: https://ideas.repec.org/a/aea/aecrev/v101y2011i4p1535-46.html

[12] Resnick, P., Zeckhauser, R., Swanson, J., & Lockwood, K. (2006). The Value of Reputation on eBay: A Controlled Experiment. *Experimental Economics*, 9(2), 79–101. https://doi.org/10.1007/s10683-006-4309-2 — https://www.cambridge.org/core/journals/experimental-economics/article/abs/value-of-reputation-on-ebay-a-controlled-experiment/610EA11BA19583907061AFB677BE4338

[13] Tadelis, S. (2016). Reputation and Feedback Systems in Online Platform Markets. *Annual Review of Economics*, 8, 321–340. https://doi.org/10.1146/annurev-economics-080315-015325 — record: https://ideas.repec.org/a/anr/reveco/v8y2016p321-340.html

[13a] The Limits of Reputation in Platform Markets: An Empirical Analysis and Field Experiment. NBER Working Paper 20830. https://www.nber.org/papers/w20830 (title and number verified; authors not confirmed tonight)

[13b] Guiot, D., & Roux, D. (2010). A Second-hand Shoppers' Motivation Scale: Antecedents, Consequences, and Implications for Retailers. *Journal of Retailing*, 86(4), 355–371 (one catalogue lists 383–399). https://doi.org/10.1016/j.jretai.2010.08.002 — record: https://ideas.repec.org/a/eee/jouret/v86y2010i4p355-371.html

[14] Thaler, R. (1985). Mental Accounting and Consumer Choice. *Marketing Science*, 4(3), 199–214. https://econpapers.repec.org/RePEc:inm:ormksc:v:4:y:1985:i:3:p:199-214 — 2008 reprint: https://doi.org/10.1287/mksc.1070.0330

[15] Grewal, D., Monroe, K. B., & Krishnan, R. (1998). The Effects of Price-Comparison Advertising on Buyers' Perceptions of Acquisition Value, Transaction Value, and Behavioral Intentions. *Journal of Marketing*, 62(2), 46–59. https://doi.org/10.2307/1252160

[16] Mazumdar, T., Raj, S. P., & Sinha, I. (2005). Reference Price Research: Review and Propositions. *Journal of Marketing*, 69(4), 84–102. https://doi.org/10.1509/jmkg.2005.69.4.84

[17] Harvard Business School Working Knowledge, on research by Donald Ngwe into "original" prices at outlet retailers. https://www.library.hbs.edu/working-knowledge/bargain-hunters-beware-a-store-s-original-price-might-not-be-after-all (underlying working paper not retrieved)

[18] Staelin, R., Urbany, J. E., & Ngwe, D. (2023). Competition and the Regulation of Fictitious Pricing. *Journal of Marketing*. Coverage: https://www.ama.org/2023/05/02/battling-deceptive-pricing-how-revealing-the-true-normal-price-can-protect-consumers (volume, pages and DOI not confirmed tonight)

[19] Iyengar, S. S., & Lepper, M. R. (2000). When Choice is Demotivating: Can One Desire Too Much of a Good Thing? *Journal of Personality and Social Psychology*. Confirmed through secondary sources including [20]; volume and pages not confirmed tonight.

[20] Scheibehenne, B., Greifeneder, R., & Todd, P. M. (2010). Can There Ever Be Too Many Options? A Meta-Analytic Review of Choice Overload. *Journal of Consumer Research*, 37(3). https://abcwest.cogs.indiana.edu/pmwiki/pdf/scheibehenne.options.2010.pdf

[21] Chernev, A., Böckenholt, U., & Goodman, J. (2015). Choice Overload: A Conceptual Review and Meta-Analysis. *Journal of Consumer Psychology*, 25(2), 333–358. https://doi.org/10.1016/j.jcps.2014.08.002

[22] Schwartz, B., Ward, A., Monterosso, J., Lyubomirsky, S., White, K., & Lehman, D. R. (2002). Maximizing Versus Satisficing: Happiness Is a Matter of Choice. *Journal of Personality and Social Psychology*, 83(5), 1178–1197. https://doi.org/10.1037/0022-3514.83.5.1178 — https://works.swarthmore.edu/fac-psychology/101

[23] Häubl, G., & Trifts, V. (2000). Consumer Decision Making in Online Shopping Environments: The Effects of Interactive Decision Aids. *Marketing Science*, 19(1), 4–21. https://doi.org/10.1287/mksc.19.1.4.15178

[24] Dietvorst, B. J., Simmons, J. P., & Massey, C. (2015). Algorithm Aversion: People Erroneously Avoid Algorithms After Seeing Them Err. *Journal of Experimental Psychology: General*, 144(1), 114–126. https://faculty.wharton.upenn.edu/wp-content/uploads/2016/11/20-Dietvorst-Simmons-Massey-2015.pdf

[25] Logg, J. M., Minson, J. A., & Moore, D. A. (2019). Algorithm Appreciation: People Prefer Algorithmic to Human Judgment. *Organizational Behavior and Human Decision Processes*, 151, 90–103. https://doi.org/10.1016/j.obhdp.2018.12.005

[26a] Mudgal, S., Li, H., Rekatsinas, T., Doan, A., Park, Y., Krishnan, G., Deep, R., Arcaute, E., & Raghavendra, V. (2018). Deep Learning for Entity Matching: A Design Space Exploration. *SIGMOD 2018*. https://doi.org/10.1145/3183713.3196926 — report: https://pages.cs.wisc.edu/~anhai/papers1/deepmatcher-tr.pdf

[26b] Li, Y., Li, J., Suhara, Y., Doan, A., & Tan, W.-C. (2020). Deep Entity Matching with Pre-Trained Language Models. *PVLDB*, 14(1), 50–60. https://doi.org/10.14778/3421424.3421431 — https://arxiv.org/abs/2004.00584

[26c] Narayan, A., Chami, I., Orr, L., & Ré, C. (2022). Can Foundation Models Wrangle Your Data? *PVLDB*, 16(4), 738–746. https://doi.org/10.14778/3574245.3574258 — https://arxiv.org/abs/2205.09911

[26] Peeters, R., Der, R. C., & Bizer, C. (2024). WDC Products: A Multi-Dimensional Entity Matching Benchmark. *EDBT 2024*. https://arxiv.org/abs/2301.09521

[27] Peeters, R., Steiner, A., & Bizer, C. (2025). Entity Matching using Large Language Models. *EDBT 2025*, 529–541. https://doi.org/10.48786/edbt.2025.42 — https://arxiv.org/abs/2310.11244

[28] Rosen, S. (1974). Hedonic Prices and Implicit Markets: Product Differentiation in Pure Competition. *Journal of Political Economy*, 82(1), 34–55. https://doi.org/10.1086/260169

[29] Han, L., et al. (2020). Price Suggestion for Online Second-hand Items with Texts and Images. arXiv:2012.06008. https://arxiv.org/abs/2012.06008

[30] Han, L., et al. (2020). Vision-based Price Suggestion for Online Second-hand Items. arXiv:2012.06009. https://arxiv.org/pdf/2012.06009

[31] Yamaura, Y., et al. (2019). The Resale Price Prediction of Secondhand Jewelry Items Using a Multi-modal Deep Learning. arXiv:1907.00661. https://arxiv.org/pdf/1907.00661

[32] Mercari Price Suggestion Challenge (Kaggle competition). Competitor write-up: https://medium.com/unstructured/how-i-lost-a-silver-medal-in-kaggles-mercari-price-suggestion-challenge-using-cnns-and-tensorflow-4013660fcded (no peer-reviewed paper found)

[33] Yao, S., Chen, H., Yang, J., & Narasimhan, K. (2022). WebShop: Towards Scalable Real-World Web Interaction with Grounded Language Agents. *NeurIPS 2022*. https://arxiv.org/abs/2207.01206 — https://neurips.cc/virtual/2022/poster/52872

[33a] Jin, Y., et al. (2024). Shopping MMLU: A Massive Multi-Task Online Shopping Benchmark for Large Language Models. *NeurIPS 2024 Datasets and Benchmarks*. https://proceedings.neurips.cc/paper_files/paper/2024/hash/2049d75dd13db049897562bcf7d59da8-Abstract.html — https://arxiv.org/abs/2410.20745

[34] Wang, J., Xiao, K., et al. (2026). ShoppingBench: A Real-World Intent-Grounded Shopping Benchmark for LLM-based Agents. *AAAI 2026*. https://ojs.aaai.org/index.php/AAAI/article/view/40640 — https://arxiv.org/abs/2508.04266

[35] Lyu et al. (2025). DeepShop: A Benchmark for Deep Research Shopping Agents. arXiv:2506.02839. https://arxiv.org/abs/2506.02839

[36] WebMall — A Multi-Shop Benchmark for Evaluating Web Agents (2025). arXiv:2508.13024. https://arxiv.org/html/2508.13024v1

[37] Allouah, A., Besbes, O., Figueroa, J. D., Kanoria, Y., & Kumar, A. (2025). What Is Your AI Agent Buying? Evaluation, Implications and Emerging Questions for Agentic E-Commerce. arXiv:2508.02630. https://arxiv.org/html/2508.02630v3

[38] ShopSimulator, arXiv:2601.18225, https://arxiv.org/html/2601.18225.pdf ; ShopGym, arXiv:2605.16116, https://arxiv.org/pdf/2605.16116 ; ComboShoppingBench, arXiv:2608.09282, https://arxiv.org/pdf/2608.09282 (existence only)

[39] National Anti-Scam Centre / ACCC. Targeting scams: report on scams data and activity 2024. https://www.scamwatch.gov.au/research-and-resources/targeting-scams-report — ministerial release: https://ministers.treasury.gov.au/ministers/stephen-jones-2022/media-releases/scam-losses-slashed-over-1-billion-under-labors-anti

[40] National Anti-Scam Centre. Targeting scams report 2025. https://www.nasc.gov.au/system/files/targeting-scams-report-2025.pdf — ACCC release: https://www.accc.gov.au/media-release/continued-action-critical-to-combat-fraud-as-annual-scam-losses-exceed-2-billion

### Method note

All sources above were located through web search on 2026-11-17. Figures are taken from abstracts, bibliographic records, press releases and search-result summaries; no full paper text was read. Where indexes disagreed (page ranges for [13b], the F1 gain in [26b], the release date of [9], the revenue figure in [12]) both values are reported.
