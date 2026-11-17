# Second pass — Track 4, academic literature

Date read: 2026-11-17 (every source below was read on this date). First-pass report checked: `research/findings/04-academic-literature.md`. Synthesis checked: `research/synthesis/literature-review.md`.

**How this pass worked.** arXiv (API and HTML full text), Crossref, EconPapers, the ACL Anthology, ACCC, NASC, European Commission, INFORMS, HBS and Which? pages were readable. Semantic Scholar and OpenAlex mostly refused requests (rate limits), and ScienceDirect, the Manchester repository and product.ai refused automated reading. I used 15 of the 25 web searches; most checking was done through the arXiv and Crossref search interfaces, which are not rationed. "Confirmed" below means confirmed against the abstract or bibliographic record at the publisher, arXiv or Crossref unless I say full text was read. Full text was read for the Xianyu paper (LLP), the ACCC comparator report (executive summary), the NASC 2025 report (relevant sections) and the EC study's summary page.

---

## 1. What changed

Most important first.

1. **Three of the first pass's "nothing found" gap claims are wrong as stated. The narrower gap survives.** The claims in the synthesis table (section 7) that the literature has "nothing" on new-versus-used choice outside vehicles, "nothing" on reference prices for used goods, and "nothing" on total cost as decision support do not hold:
   - *New versus used choice outside vehicles* has a literature: books (Ghose, Smith and Telang 2006), video games (Ishihara and Ching 2019), electronics and remanufactured goods (Guide and Li 2010; Abbey et al. 2017; Frota Neto, Bloemhof and Corbett 2016), and general products (Crosno and Cui 2018).
   - *Used price relative to new price* has been measured: Abbey et al. (2017) estimate "the ratio between wtp for a remanufactured product and wtp for a corresponding new product"; Solinas, Nunes and Ko (2025) study "a product's resale price expressed as a percentage of its original retail price" across four resale platforms plus four pre-registered experiments.
   - *Total cost as decision support* has experimental evidence for parts of it: life-cycle cost shown in a live online shop (Deutsch 2010), total cost of ownership information (Dumortier et al. 2015), shipping fees on eBay (Hossain and Morgan 2006), and partitioned versus all-in prices for new versus used goods (Crosno and Cui 2018).
   - **What is still not found:** a study of a tool that shows a buyer the current new price next to a specific used listing; a fair used-to-new ratio by category and condition for peer-to-peer listings of general goods; and a single figure combining price, shipping, pickup travel, time and risk. The product's research question still stands on these, but the synthesis should say "thin and scattered", not "nothing". Confidence that the narrower gap is real: medium. Solinas et al. themselves write that "little is known about what influence the value of secondhand products".

2. **Matching seller listings to catalogue products is not unstudied. eBay published on it in 2018.** Shah, Kopru and Ruvini (NAACL 2018 industry track, eBay) address "matching a seller listed item to an appropriate product". Kannan et al. (KDD 2011) match unstructured offers to structured products. eBay's eProduct (CVPR FGVC8 2021) is a 2.5-million-image benchmark for recognising the exact product from an image. Mercari has published visual search and embedding work on consumer-to-consumer listings (2025). What remains true: I found **no public benchmark** of second-hand classified listings (text plus photos) labelled with the canonical product and variant, and none in English or for Australia. So "no public benchmark" is confirmed; "unstudied" is wrong. The platforms have done this in-house with their own data, which makes it less of a moat than the first pass suggested.

3. **The Xianyu paper is real, and it is the best published evidence on how hard used-item pricing is.** arXiv 2510.09347, "LLP: LLM-Based Product Pricing in E-commerce" (Wang et al., Alibaba/Xianyu; v2 dated 31 Aug 2026). Full details are in section 3. The numbers that matter for the build decision:
   - With about 620,000 training listings and Xianyu's own 90-day pool of comparable listings, the system's price is within ±20% of the target for **54.6%** of test items (65.2% for standardised goods such as phones, 47.8% for non-standardised goods). On 611 categories it was not trained on: **42.9%**.
   - A language model with no retrieval of comparable listings: **17.4%**. Adding retrieval alone: 49.2%. Retrieval of comparables is what makes it work.
   - The "ground truth" is the **seller's listing price**, not a sale price ("we treat the seller-provided listing price as ground truth"). The paper says nothing about what items sell for.
   - Confidence filtering: on mobile phones, 78% within ±20% at 70% coverage; on the top ten categories, "over 80% pricing accuracy at 60% product coverage". Declining to price 30–40% of items is what buys the accuracy.
   - It is a seller-side tool. No buyer-side verdict is evaluated.
   - Consequence: an app without a large pool of recent comparable used listings should expect to be nearer the 17% end than the 55% end. The cross-track claim in `08-differentiation-and-moat.md` ("confidence filtering… much worse results for a plain language model without retrieval") is confirmed.

4. **A regulator-grade source now exists for how common buying-and-selling scams are in Australia.** The NASC 2025 report (full text read) says: "Buying or selling scams continued to be the most common scam type in Australia experienced by about 300,000 people" (ABS Personal Fraud, 2024–25). In Scamwatch data, shopping scams (online shopping plus classified scams) were the scam type with the most people reporting a loss: 12,248 people and A$10.8 million in 2025, up 22.2% from 10,022 in 2024. This confirms the first pass's inference that these scams are numerous and individually small (about A$880 per report with a loss).

5. **Price accuracy in AI shopping answers has been measured, by consumer bodies and vendors, not by academics.** Which? (UK, October 2026 test, read at source): ChatGPT "correctly identified the lowest price and retailer for only eight products" of 25; "in 68% of cases, there was at least one issue". A Product.ai study (September 2026, read only via Tech.co because product.ai refused my request) reports conflicting or incorrect information in 86% of responses to 220 shopping questions across ChatGPT, Claude, Gemini and Perplexity, with a median error of US$300 when a price was wrong. ShoppingComp (arXiv 2511.22978) reports 17.76% for GPT-5.2 on hard, verifiable shopping tasks. I found no peer-reviewed study of price hallucination rates. This supports the design rule "never let the model state a price from memory", and it supports the claim that general assistants are beatable on price accuracy today. Neither test covered second-hand listings.

6. **Ronayne (2021) is stronger than the first pass and synthesis say.** The published abstract: "introducing any number of PCWs to a market increases prices for all consumers, both those who use the sites and those who do not." The first pass said comparison sites "can leave consumers worse off"; the synthesis said "can raise prices overall in theory". Within the model it is a general result, not a possibility.

7. **Bronnenberg, Kim and Mela (2016): one claim in the synthesis overstates the source, and one finding was left out.** The synthesis says shoppers searched "mostly within one brand or model". The source (INFORMS release) says "about 40 percent of consumers search only one brand and 20 percent only one model, while the average consumer will search about three brands and six models" — so most shoppers searched more than one brand. The paper's abstract also says "the first-time discovery of the chosen alternative usually takes place toward the end of the search sequence." People stay in a narrow attribute range from day one, but the exact product they buy is usually found late. This weakens the inference that the user "arrives with a listing in hand and only needs confirmation" and slightly strengthens the case that a tool can change which item is bought.

8. **All of the unverified leads in section 4 of the first pass check out** (38 of 38 looked up; table in section 2c). The ACCC 2014 report and the EC comparison tools study were both retrieved (section 2d). One new fact from the EC study bears on the product: 65% of comparison-tool users had experienced a problem, including "incorrect prices in 21% of the cases".

9. **Buy/wait advice exists as a research line, for airfares, not for used goods.** Etzioni et al. (KDD 2003, "To buy or not to buy: mining airfare data to minimize ticket purchase price") is the origin of Farecast-style advice; follow-ups exist (Cao and Xu, ICWS 2021). For used goods I found price forecasting (Buczyński et al., arXiv 2610.10727, second-hand electronics in Poland, 1–365 day horizons) but no evaluated buy/wait/skip advice to a buyer. The first pass's gap 4 is confirmed for used goods and should mention the airfare precedent.

---

## 2. Claim table

### 2a. Gap claims (priority 1)

| Claim | First-pass file | Status | What the sources say | URL |
|---|---|---|---|---|
| No work on a consumer choosing between new and used versions of the same product, outside vehicles | 04 §5 gap 1; synthesis §7 | **Corrected** | Ghose, Smith & Telang (2006): Amazon new and used books; "used books are poor substitutes for new books… only 16% of used-book sales at Amazon cannibalize new-book purchases". Ishihara & Ching (2019): "a new dynamic demand model for new and used durable goods" (Japanese video games). Guide & Li (2010): auctions measuring willingness to pay for new and remanufactured versions; "a clear difference in WTP". Crosno & Cui (2018): four experiments on "consumers' purchase decisions of new versus used products". Still not found: decision *support* for that choice. | https://doi.org/10.1287/isre.1050.0072 ; https://doi.org/10.1287/mksc.2018.1142 ; https://doi.org/10.1111/j.1540-5915.2010.00280.x ; https://doi.org/10.1108/JCM-02-2017-2091 |
| Nothing on how buyers form a reference price for a used item | 04 Theme 3 gap; §5 gap 2 | **Corrected (partly filled)** | Abbey, Kleber, Souza & Voigt (2017): "empirically estimates the magnitude and distribution of discount factors for remanufactured electronics products—the ratio between wtp for a remanufactured product and wtp for a corresponding new product". Solinas, Nunes & Ko (2025, EMAC proceedings): lower-priced products retain more of their original price on resale; "consumers infer higher margins for higher-priced products in the primary market… adjusting their willingness-to-pay down further"; five data sets from four resale platforms, four pre-registered lab studies. Kim, Rao, Kim & Rao (2011): preferences depend on "the ratio of the price of their used product to the price of the new product" (trade-ins). Kamins, Drèze & Folkes (2004): seller-supplied reference prices in internet auctions (title confirmed; abstract not readable). Malmendier & Lee (2011): "42 percent of auctions exceed the simultaneous fixed price" for the same item on the same page — buyers do not reliably use an available reference price. Huang & Liu (2021): reference-price effects in used-car retail (vehicles). Not found: fair used-to-new ratio by category and condition on peer-to-peer classifieds; effect of showing the new price beside a used listing. | https://doi.org/10.1111/poms.12628 ; https://proceedings.emac-online.org/pdfs/A2025-125270.pdf ; https://doi.org/10.1509/jmkr.48.1.157 ; https://doi.org/10.1086/380294 ; https://doi.org/10.1257/aer.101.2.749 ; https://doi.org/10.1007/s11129-021-09239-w |
| Total cost of acquisition not found as a consumer decision-support problem | 04 §5 gap 3 | **Corrected (components exist; the combined figure does not)** | Deutsch (2010): randomised field experiment in a live online shop showing life-cycle cost for washing machines, 2,065 clicks analysed. Dumortier et al. (2015): total-cost-of-ownership information and intent to buy hybrid/electric cars. Hossain & Morgan (2006): eBay field experiments; "charging a high shipping cost and starting the auction at a low opening price leads to… higher revenues" — buyers under-weight shipping. Crosno & Cui (2018): "consumers prefer partitioned pricing… for new products, whereas all-inclusive pricing is more preferred for used products". Blake et al. (2021) on hidden fees (confirmed lead). Not found: any study combining price, shipping, travel to pick up, time and risk allowance. | https://doi.org/10.1111/j.1530-9290.2009.00201.x ; https://doi.org/10.1016/j.tra.2014.12.005 ; https://doi.org/10.2202/1538-0637.1429 ; https://doi.org/10.1108/JCM-02-2017-2091 |
| No buy / wait / skip advice research | 04 §5 gap 4 | **Confirmed for used goods; corrected in general** | Etzioni, Tuchinda, Knoblock & Yates (KDD 2003) is buy-or-wait advice for airfares. Cao & Xu (ICWS 2021), "To Wait or To Buy". For used goods: price forecasting only (arXiv 2610.10727); reserve-price advice to sellers of used vehicles (arXiv 2611.18785). A web search for buyer-side deal-quality classification of used listings returned blogs and tools, no papers. | https://doi.org/10.1145/956750.956767 ; https://doi.org/10.1109/icws53863.2021.00031 ; https://arxiv.org/abs/2610.10727 |
| No study or benchmark on matching second-hand listings to canonical products, text or image | 04 Theme 6 gap; §5 gap 5; synthesis §6 | **Corrected: studied in industry; no public second-hand benchmark found** | Shah, Kopru & Ruvini (2018, eBay): "Matching a seller listed item to an appropriate product… with the exponential growth of individual and business sellers"; classification and siamese similarity models "outperform the baseline by more than 5%". Kannan, Givoni, Agrawal & Fuxman (KDD 2011): "Matching unstructured product offers to structured product specifications". eProduct (Yuan et al. 2021, eBay): 2.5 million images for "super fine-grained" product recognition. Mercari: zero-shot visual search on C2C listings "where listings are often unstructured and visually driven" (arXiv 2508.05661); the companion paper (2510.13359) uses one million image–title pairs. Xianyu: IPL (arXiv 2410.16977) extracts category, brand and condition from seller photos. None releases a labelled second-hand listing-to-product benchmark. | https://aclanthology.org/N18-3002/ ; https://doi.org/10.1145/2020408.2020474 ; https://arxiv.org/abs/2107.05856 ; https://arxiv.org/abs/2508.05661 ; https://arxiv.org/abs/2410.16977 |
| No second-hand tasks in LLM agent benchmarks | 04 §5 gap 6 | **Corrected (one now exists, on safety, not valuation)** | BazaarBench (arXiv 2610.06748, Oct 2026): "a simulated C2C marketplace… tracks ownership, item condition, and commitments"; inventories from a public eBay sample. FaMA (arXiv 2509.03890, Meta): an agentic assistant for Facebook Marketplace covering listing management and conversational search, "98% task success rate"; no price advice. Bargaining benchmarks exist (arXiv 2402.15813; 2509.06341). No benchmark for "is this used listing worth it". | https://arxiv.org/abs/2610.06748 ; https://arxiv.org/abs/2509.03890 |
| Second-hand price suggestion: Han et al. two-step design; Mercari has no peer-reviewed paper | 04 Theme 7 | **Confirmed, and extended** | Han et al. abstract confirms the classifier-then-regressor design ("determine whether the image and text… are qualified for reasonable price suggestion with a binary classification model"). Newer: LLP (section 3); Vedula et al. (Findings of ACL 2025), quantile regression with LLMs to "produce full predictive distributions" for prices; PhoneValue-Bench (arXiv 2611.00791) for trade-in valuation from photos. | https://arxiv.org/abs/2012.06008 ; https://arxiv.org/abs/2510.09347 ; https://arxiv.org/abs/2506.06657 ; https://arxiv.org/abs/2611.00791 |
| No treatment of search stopping in second-hand markets | 04 §5 gap 7 | **Unverified** | Not searched in this pass (lower priority). | — |

### 2b. Spot-check of the references the synthesis leans on (priority 4)

| Reference and claim | Status | What the source says | URL |
|---|---|---|---|
| Bronnenberg, Kim & Mela (2016): 14 searches; ~15 days, six sessions; 40% one brand, 20% one model; early search predicts purchase | **Confirmed, with two corrections to how it is used** | Abstract: "14 searches on average prior to purchase… Early search is highly predictive of the characteristics of the camera eventually purchased… the first-time discovery of the chosen alternative usually takes place toward the end of the search sequence." INFORMS: "around 15 days and over six sessions… about 40 percent of consumers search only one brand and 20 percent only one model, while the average consumer will search about three brands and six models." The synthesis's "mostly within one brand or model" is wrong; the late-discovery finding was omitted. | https://doi.org/10.1287/mksc.2016.0977 ; INFORMS release (URL in first pass) |
| De los Santos, Hortaçsu & Wildenbeest (2012): sequential search rejected; fixed sample size fits better | **Confirmed** | "the benchmark model of sequential search with a known price distribution can be rejected… fixed sample size search provides a more accurate description". DOI the first pass lacked: 10.1257/aer.102.6.2955. | https://doi.org/10.1257/aer.102.6.2955 |
| Ronayne (2021): comparison sites "can" leave consumers worse off | **Corrected (stronger)** | "introducing any number of PCWs to a market increases prices for all consumers, both those who use the sites and those who do not." | https://doi.org/10.1111/iere.12504 |
| Resnick et al. (2006): 8.1% reputation premium; one or two negatives made no difference | **Confirmed** | "The difference in buyers' willingness-to-pay was 8.1% of the selling price… one or two negative feedbacks for our new sellers did not affect buyers' willingness-to-pay." Note the goods were vintage postcards sold by one dealer. | https://doi.org/10.1007/s10683-006-4309-2 |
| Ursu (2018): position affects search, not purchase given search; US$1.92 | **Confirmed** | "they affect what consumers search, but conditional on search, do not affect purchases… average position effect of $1.92". | https://doi.org/10.1287/mksc.2017.1072 |
| Peeters, Steiner & Bizer (2025): zero/few-shot LLMs match fine-tuned models; more robust to unseen entities | **Confirmed** | "the best LLMs require no or only a few training examples to perform comparably to PLMs that were fine-tuned using thousands of examples. LLM-based matchers further exhibit higher robustness to unseen entities." Also: "there is no single best prompt… the prompt needs to be tuned for each model/dataset combination" — a cost the first pass did not mention. | https://arxiv.org/abs/2310.11244 |
| WDC Products: 11,715 offers, 2,162 products; F1 0.64–0.89 | **Confirmed (counts); F1 range unverified** | Full text: "11,715 product offers describing in total 2,162 product entities". Abstract: "all matching systems struggle with unseen entities to varying degrees". I did not locate the 0.64–0.89 range. | https://arxiv.org/abs/2301.09521 |
| ShoppingBench: 3,310 instructions, 2.5M products, GPT-4.1 under 50% | **Confirmed** | "even state-of-the-art language agents (such as GPT-4.1) achieve absolute success rates under 50%"; "3,310 user instructions"; AAAI 2026 oral. | https://arxiv.org/abs/2508.04266 |
| Allouah et al. (2025): position bias, sponsored-tag penalty, concentration, seller tweaks | **Confirmed; title has changed** | Current title (v3): "What Is Your AI Agent Buying? Evaluation, Biases, Model Dependence, & Emerging Implications for Agentic E-Commerce". Abstract matches every first-pass point and adds: "these preferences are unstable: model updates can drastically reshuffle market shares". | https://arxiv.org/abs/2508.02630 |
| Ngwe outlet study: US$1 of "original" price → 77 cents | **Confirmed; paper identified** | HBS Working Knowledge: "for every $1 increase in the posted 'original price' for an item, consumers were willing to pay, on average, an extra 77 cents". The working paper is named there: Ngwe, "Fake Discounts Drive Real Revenues in Retail". The data are from one US clothing and accessories brand's outlet stores. I did not open the working paper itself. | https://www.library.hbs.edu/working-knowledge/bargain-hunters-beware-a-store-s-original-price-might-not-be-after-all |
| Staelin, Urbany & Ngwe (2023) | **Confirmed; citation completed** | *Journal of Marketing* 87(6), 826–846. "disclosure of the true normal price charged may be the only solution"; "a laboratory study of 900 consumers". | https://doi.org/10.1177/00222429231164640 |
| Dietvorst follow-up (adjustable algorithms), marked "reportedly… not separately verified" in synthesis | **Confirmed** | Dietvorst, Simmons & Massey (2018), *Management Science* 64(3), 1155–1170: "Participants were considerably more likely to choose to use an imperfect algorithm when they could modify its forecasts… even when participants were severely restricted in the modifications they could make." The tasks were incentivised forecasting, not shopping. | https://doi.org/10.1287/mnsc.2016.2643 |
| WebShop: 29% vs 59% | **Confirmed** | "task success rate of 29%… far lower than human expert performance (59%)". | https://arxiv.org/abs/2207.01206 |
| Nosko & Tadelis, authors unconfirmed | **Confirmed; now published** | NBER w20830 (2015), authors Nosko and Tadelis; published in *Quantitative Marketing and Economics* 24(1), 2026. | https://doi.org/10.1007/s11129-026-09313-1 |
| Bibliographic loose ends | **Confirmed** | Thaler (1985) DOI 10.1287/mksc.4.3.199. Guiot & Roux pages 355–371. Iyengar & Lepper *JPSP* 79(6), 995–1006, DOI 10.1037/0022-3514.79.6.995. Scheibehenne et al. *JCR* 37(3), 409–425, DOI 10.1086/651235. Dietvorst et al. (2015) DOI 10.1037/xge0000033. WebMall accepted at SIGIR 2026; ShopGym at NeurIPS 2026; ShopSimulator reports "less than 40% full-success rate". | Crossref / arXiv records |

### 2c. Unverified leads from first-pass section 4 (priority 3)

All confirmed to exist with the stated authors and venue. None struck. "Read" is the Crossref, arXiv or EconPapers record; findings were not checked unless quoted elsewhere in this report.

| Lead | Status | Citation / DOI |
|---|---|---|
| Weitzman (1979) | Confirmed | "Optimal Search for the Best Alternative", *Econometrica* 47(3), 641. 10.2307/1910412 |
| Diamond (1971) | Confirmed | "A model of price adjustment", *J. Economic Theory* 3(2), 156–168. 10.1016/0022-0531(71)90013-5 |
| Varian (1980) | Confirmed | "A Model of Sales", *AER* 70(4), 651–59. https://econpapers.repec.org/RePEc:aea:aecrev:v:70:y:1980:i:4:p:651-59 (no DOI) |
| Baye & Morgan (2001) | Confirmed | *AER* 91(3), 454–474. 10.1257/aer.91.3.454 |
| Dinerstein, Einav, Levin & Sundaresan (2018) | Confirmed | *AER* 108(7), 1820–1859. 10.1257/aer.20171218 |
| Blake, Moshary, Sweeney & Tadelis (2021) | Confirmed | "Price Salience and Product Choice", *Marketing Science* 40(4), 619–636. 10.1287/mksc.2020.1261 |
| Honka (2014) | Confirmed | *RAND J. Economics* 45(4), 847–884. 10.1111/1756-2171.12073 |
| Gorodnichenko, Sheremirov & Talavera (2018) | Confirmed | "Price Setting in Online Markets: Does IT Click?", *JEEA* 16(6), 1764–1811. 10.1093/jeea/jvx050 |
| ACCC (2014) comparator report | Confirmed, read | See 2d |
| European Commission comparison tools study | Confirmed, summary read | See 2d |
| Edelman & Wright (2015) | Confirmed | *QJE* 130(3), 1283–1328. 10.1093/qje/qjv018 |
| Hunold, Kesler & Laitenberger (2020) | Confirmed | *Marketing Science* 39(1), 92–116. 10.1287/mksc.2019.1167 |
| Armstrong, Vickers & Zhou (2009) | Confirmed | *RAND J. Economics* 40(2), 209–233. 10.1111/j.1756-2171.2009.00062.x |
| Cabral & Hortaçsu (2010) | Confirmed | *J. Industrial Economics* 58(1), 54–78. 10.1111/j.1467-6451.2010.00405.x |
| Jin & Kato (2006) | Confirmed | *RAND J. Economics* 37(4), 983–1005. 10.1111/j.1756-2171.2006.tb00067.x |
| Ghose, Smith & Telang (2006) | Confirmed, abstract read | *Information Systems Research* 17(1), 3–19. 10.1287/isre.1050.0072 |
| Einav, Farronato & Levin (2016) | Confirmed | *Annual Review of Economics* 8, 615–635. 10.1146/annurev-economics-080315-015334 |
| Backus, Blake, Larsen & Tadelis (2020) | Confirmed | *QJE* 135(3), 1319–1361. 10.1093/qje/qjaa003 |
| Styvén & Mariani (2020) | Confirmed | Ek Styvén & Mariani, *Psychology & Marketing* 37(5), 724–739. 10.1002/mar.21334 |
| Padmavathy, Swapana & Paul (2019) | Confirmed | *J. Retailing and Consumer Services* 51, 19–32. 10.1016/j.jretconser.2019.05.014 |
| Urbany, Bearden & Weilbaker (1988) | Confirmed | *J. Consumer Research* 15(1), 95. 10.1086/209148 |
| Kalyanaram & Winer (1995) | Confirmed | *Marketing Science* 14(3 supp.), G161–G169. 10.1287/mksc.14.3.g161 |
| Simonson (1992) | Confirmed | *J. Consumer Research* 19(1), 105. 10.1086/209290 |
| Tversky & Kahneman (1974) | Confirmed | *Science* 185(4157), 1124–1131. 10.1126/science.185.4157.1124 |
| Xiao & Benbasat (2007) | Confirmed | *MIS Quarterly* 31(1), 137–209. 10.2307/25148784 |
| Diehl (2005) | Confirmed | *J. Marketing Research* 42(3), 313–322. 10.1509/jmkr.2005.42.3.313 |
| Castelo, Bos & Lehmann (2019) | Confirmed | *J. Marketing Research* 56(5), 809–825. 10.1177/0022243719851788 |
| Longoni & Cian | Confirmed; date note | *J. Marketing* 86(1), 91–108; online 2020, issue 2022. 10.1177/0022242920957347 |
| Fellegi & Sunter (1969) | Confirmed | *JASA* 64(328), 1183–1210. 10.1080/01621459.1969.10501049 |
| Köpcke, Thor & Rahm (2010) | Confirmed | *PVLDB* 3(1–2), 484–493. 10.14778/1920841.1920904 |
| Primpeli, Peeters & Bizer (2019) | Confirmed | WWW '19 Companion, 381–386. 10.1145/3308560.3316609 |
| Angelopoulos & Bates | Confirmed | "Conformal Prediction: A Gentle Introduction", *Foundations and Trends in ML* 16(4), 494–591 (2023). 10.1561/2200000101 |
| Zhou et al. (2023) WebArena | Confirmed | arXiv 2307.13854. Best GPT-4 agent 14.41% vs human 78.24% |
| Deng et al. (2023) Mind2Web | Confirmed | arXiv 2306.06070; NeurIPS 2023 |
| Kumar & Lakkaraju (2024) | Confirmed | arXiv 2404.07981. A "strategic text sequence" on a product page raises its chance of being the LLM's top recommendation |
| Aggarwal et al. (2024) GEO | Confirmed | arXiv 2311.09735; KDD 2024 |
| Park et al. (2014) Scambaiter | Confirmed | Park, Jones, McCoy, Shi & Jakobsson, NDSS 2014. 10.14722/ndss.2014.23284 |
| Dietvorst follow-up | Confirmed | See 2b |

### 2d. Regulator studies (priority 5)

| Claim | Status | What the source says | URL |
|---|---|---|---|
| ACCC report on comparator websites could not be retrieved | **Retrieved and read (executive summary)** | "The comparator website industry in Australia", ACCC, November 2014 (released 28 Nov 2014, MR 287/14). Scope was mainly private health insurance, energy and telecommunications, not retail goods. Benefits: sites "can reduce search costs" and there is "preliminary anecdotal evidence" of downward pressure on prices. Use is "predominantly for research rather than purchasing, with purchases… held back by a lack of consumer trust in the motivations of… comparator websites". Concerns: representations about market coverage, savings, being "unbiased, impartial or independent", value rankings, and "undisclosed commercial relationships affecting recommendations to consumers". Most sales happen through call centres ("up to 90 per cent in some cases"). Prior penalties: EnergyWatch over A$2 million; Compare the Market A$10,200 infringement notice. Industry guidance followed in August 2015. | https://www.accc.gov.au/system/files/926_Comparator%20website%20industry%20in%20Australia%20report_FA.pdf ; https://www.accc.gov.au/media-release/comparing-apples-with-apples-accc-report-on-the-comparator-website-industry-in-australia |
| European Commission comparison tools study could not be retrieved | **Summary page read; full PDF located, not read** | "Study on the coverage, functioning and consumer use of comparison tools and third-party verification schemes for such tools", finalised end of 2014. Commission summary: 1,042 tools mapped (910 websites, 132 apps); "74% of EU consumers have used a comparison tools and 40% are using them at least once a month"; "65% of consumers surveyed had experienced a problem… (e.g. unavailability of the product in 54% of the case, incorrect prices in 21% of the cases)"; "Less than half of the comparison tools mapped were willing to disclose details on their supplier relationship, description of business model or the sourcing of their price and product data"; ranking changes choice. | https://commission.europa.eu/publications/comparison-tools-and-third-party-verification-schemes_en |

### 2e. Other first-pass claims touched

| Claim | Status | Source | URL |
|---|---|---|---|
| NASC 2025: A$2.18 billion combined losses, up 7.8% | Confirmed (full text) | "totalling $2.18 billion in 2025, an increase of 7.8% from 2024"; 481,523 combined reports (494,732 in 2024). | https://www.nasc.gov.au/system/files/targeting-scams-report-2025.pdf |
| Buying-and-selling scams "numerous but individually small" (first-pass inference) | Confirmed | See item 4 in section 1. | same |
| Han et al. venue "ACM Multimedia 2020" | Unverified | arXiv record gives no venue. | https://arxiv.org/abs/2012.06008 |

---

## 3. New findings

### 3a. The Xianyu paper in full (arXiv 2510.09347v2, full HTML text read)

**Citation.** Wang, You, Zhang, Xie, Han, Wu, Huang and Chen, "LLP: LLM-Based Product Pricing in E-commerce". First posted 10 Oct 2025; v2 31 Aug 2026. No venue stated on the arXiv record.

**Problem.** Suggesting a price to an individual seller listing a second-hand item on Xianyu.

**Method.**
1. *Retrieve comparables.* A pool of the platform's listings from the 90 days before the target listing, with "off-platform trades, clickbait, and counterfeits" removed and only high-engagement listings kept. Retrieval uses multimodal "Semantic IDs".
2. *Reason over them with a small fine-tuned LLM.* Base model Qwen2.5-7B-Instruct. Training: supervised fine-tuning on about 580,000 examples whose rationales were written by a larger teacher model, then reinforcement learning (GRPO) on the rest of about 620,000. The reasoning step uses text only; the authors list not using images as a limitation.
3. *Filter by confidence.* "We use next-token entropy as a proxy for model confidence… we estimate its confidence by averaging the entropy across the corresponding generation steps." Suggestions above an entropy threshold are withheld. Listings missing brand or model, and unreleased products with no comparables, produce high entropy and are filtered automatically.

**Ground truth.** "We treat the seller-provided listing price as ground truth." Online, accuracy is measured against the seller's final submitted price. Sale prices are not used.

**Offline results** (72,561 test listings, top 55 categories; SAR = share within ±20% of the target price):

| Method | SAR standardised | SAR non-standardised | SAR overall |
|---|---|---|---|
| Text nearest-neighbour average | 36.7% | 19.0% | 25.9% |
| Previous production method (attribute clusters) | 43.3% | 30.6% | 36.6% |
| LLM alone | 19.7% | 15.8% | 17.4% |
| LLM + retrieval | 61.0% | 41.7% | 49.2% |
| LLP (retrieval + both training stages) | 65.2% | 47.8% | 54.6% |

On 611 unseen categories (210,267 listings): LLP 42.9%; LLM + retrieval 34.6%; fine-tuned LLM without retrieval 6%.

**Confidence filtering results.** Mobile phones: "a high precision of 78% at 70% product coverage"; AUC 0.77. Top ten categories: "over 80% pricing accuracy at 60% product coverage… Even under full coverage… near 70%". Handbags: near 100% at 20% coverage.

**Online results** (10-day A/B test, 20% of traffic each arm). Sellers who submitted the suggested price unchanged: 6% → 17%. Online SAR: 40% → 72%. GMV +0.7%. The v2 abstract adds: "Under the same 30% product coverage, it raises the static adoption rate (SAR) from 40% to 72%, and maintains a strong SAR of 47% even at 90% recall." Served on 20 NVIDIA L20 GPUs at 25 queries per second, about 790 ms end to end.

**Failure analysis.** About 40% of failures were seller subjectivity (urgent sellers price low, patient ones high); 20% missing information in the listing; 20% poor retrieval; 20% reasoning errors or hallucinated conclusions.

**Other notes.** More retrieved comparables help up to a point, then hurt (performance drops at 100). Off-the-shelf large models with the same retrieved items were competitive; the fine-tuned 7B model beat them at far lower serving cost.

**What it means for this product.** (My inference.) The accuracy comes from a dense pool of recent comparable used listings that only a marketplace has. The target is an asking price, so even a perfect copy tells a buyer what sellers ask, not what a fair price is. Withholding a verdict on a third or more of listings is normal practice at the best-resourced operator. The headline "72%" applies at 30% coverage.

### 3b. Used-item valuation (thin theme)

- **Uncertainty methods now exist for price prediction.** Vedula et al. (Findings of ACL 2025, arXiv 2506.06657): a fine-tuned Mistral-7B with quantile heads produces "full predictive distributions" for prices from text and beats point-estimate approaches on calibration; datasets are public. ProbSAINT (arXiv 2403.03812): probabilistic used-car pricing with "the ability to flag predictions that the model is unsure about". Hjort et al. (arXiv 2312.06531): conformal prediction for house-price valuation models, with a correction for uneven coverage across areas. Nothing found applying conformal prediction to second-hand consumer goods.
- **Condition grading from photos exists for phones only.** Mohandas, Southern, Fitzpatrick & Hayes (2025), *Journal of Remanufacturing* 15(1), 65–95 (https://doi.org/10.1007/s13243-024-00147-2): detection and severity grading of screen scratches and cracks; notes that manual grading is "subjective". PhoneValue-Bench (arXiv 2611.00791, Oct 2026): over twenty thousand trade-in orders with multi-view photos and diagnostic screenshots; the reference pipeline fills appearance fields at 97.0 but staff-inspection fields at only 54.1 — photos recover cosmetic condition much better than functional condition. Surface defects in recycled books: arXiv 2409.04958. Nothing found for furniture, tools, outdoor gear or other general goods; one search was run.
- **Depreciation and price paths.** Buczyński et al. (arXiv 2610.10727): daily listing prices for 100+ phone and laptop models on Polish marketplaces, January 2022 to March 2025; best model error 8.51% at 365 days; at 1–7 days "the naive baseline remains competitive" (today's price is the best short-term forecast). Solinas, Nunes & Ko (2025): cheaper goods retain a larger share of original price. Frota Neto, Bloemhof & Corbett (2016), *IJPE* 171, 371–380 (https://doi.org/10.1016/j.ijpe.2015.02.006) compares new, used and remanufactured prices on eBay; title confirmed, abstract not readable. Ghose (2009), *MIS Quarterly* 33(2): on Amazon's used market for PDAs, cameras, audio players and laptops, "price declines are larger for more unreliable products".
- **Price sanity checking.** Sartipi et al. (arXiv 2603.20636): an LLM pipeline that flags price outliers by comparing against similar products, "over 75% agreement with human auditors". Relevant to the "too cheap to be real" signal.
- **Listing-price behaviour on classifieds.** Reichel & Schindl (2025; arXiv 2411.07808): on Austria's main second-hand platform, sellers using rounded price endings list higher.

### 3c. Fraud in peer-to-peer marketplaces (thin theme)

- **Prevalence, Australia.** See section 1 item 4. Also: 71.0% of people who experienced a scam notified an authority (ABS, via NASC), so Scamwatch counts are a floor. Jan–Sep 2025: shopping scams had 9,628 loss reports and A$8.6 million, "an increase of 19 per cent in reported losses" (ACCC, https://www.accc.gov.au/media-release/australians-report-nearly-260m-in-losses-as-shopping-scams-surge). The NASC category merges online shopping (fake stores) with classified scams, so the classifieds-only share is still not published.
- **Measurement studies are about Craigslist and are a decade old.** Park et al. (NDSS 2014, Scambaiter); Park, McCoy & Shi (2017), "Understanding Craigslist Rental Scams", Financial Cryptography (https://doi.org/10.1007/978-3-662-54970-4_1); Garg & Nilizadeh (2013), IEEE S&P Workshops (https://doi.org/10.1109/spw.2013.21); Alsaleh & Zhou (2018), "A Heuristic Method for Identifying Scam Ads on Craigslist", EISIC (https://doi.org/10.1109/eisic.2018.00019). Existence confirmed; I did not read their findings, so the specific listing signals they use are still unverified.
- **Platform-side detection uses data an outside app does not have.** Kodate et al. (arXiv 1906.07974): fraud detection on a C2C marketplace from the buyer–seller transaction network. Li et al. (CIKM 2019, arXiv 1908.10679): graph-based spam detection at Xianyu. Both rely on platform-internal graphs.
- **Mitigation.** Burton & Gundur (2026), anti-fraud messaging and trust mechanisms on C2C platforms, *European Journal on Criminal Policy and Research* (https://doi.org/10.1007/s10610-025-09651-y). Title only.
- **No academic measurement of scam listings on Facebook Marketplace or Gumtree was found.** A search summary noted ProPublica's reporting that platforms do not disclose fraudulent-listing data; I did not open that article.
- Consequence: the first pass's caution stands. Listing-level scam detection by a third-party app has no published evidence base; the one signal the app can compute itself is price far below its own reference range.

### 3d. Trust in AI shopping advice and price accuracy, 2020–2026 (thin theme)

- **Price accuracy.** Section 1 item 5. The Which? piece also records OpenAI's response: "Prices in its initial product listings may not be the lowest available."
- **Grounding helps and is measurable.** Zeng et al. (arXiv 2503.04830, Amazon): adding citations to a shopping assistant's answers improved grounding by 13.83% and online engagement by 3–10%.
- **Agents and sponsorship.** Wadi & Ma (arXiv 2609.17989): agents acting for a consumer penalise sponsored listings, but naming a platform as the agent's principal "significantly attenuates this sponsorship penalty without instructions to favor advertisers". Wadi & Ma (arXiv 2609.28372): when information is costly to fetch and the goal is vague, LLM shoppers skip the attributes needed to compute unit price.
- **Consumer trust.** Pre-LLM academic work is confirmed (Longoni & Cian; Castelo et al.; Dietvorst et al. 2018). For LLM-era shopping advice I found only industry surveys in search summaries (not opened, not cited) and one journal article by title: Meng & Xiao (2026), consumer satisfaction with ChatGPT product advice, *J. Retailing and Consumer Services* 88 (https://doi.org/10.1016/j.jretconser.2025.104496). I found no peer-reviewed experiment on whether shoppers follow LLM price or deal advice. That is a gap.

### 3e. Smaller points

- The Peeters et al. (2025) abstract says prompts must be tuned per model and dataset; "no training data" does not mean "no tuning effort".
- Nosko & Tadelis's published abstract adds a mechanism relevant to an app issuing verdicts: "buyers may generalize from individual transactions to the platform as a whole". One bad experience attributed to the app's verdict may be held against the whole app.
- Li & Sundararajan (arXiv 2405.09023) model brand-run resale channels; evidence that manufacturers are entering resale.

---

## 4. Still open

| Item | Why open | What would settle it |
|---|---|---|
| Frota Neto, Bloemhof & Corbett (2016): actual used-to-new price ratios on eBay | ScienceDirect and the Manchester repository copy refused automated reading (403) | Open the DOI in a browser; this is the closest published measurement of used versus new prices for the same items |
| Kamins, Drèze & Folkes (2004); Huang & Liu (2021); Etzioni et al. (2003): findings | Abstracts not exposed by Crossref; Semantic Scholar withholds them | Read at publisher pages by hand |
| Solinas, Nunes & Ko (2025): the retained-value percentages by price tier | Only the abstract page of the proceedings PDF was read | Read the full proceedings paper; check for a journal version |
| Ngwe working paper text | Only the HBS summary read | HBS working paper 18-113 (number from memory, not verified) |
| Product.ai AI-shopping accuracy study | product.ai returned 403; figures come from Tech.co and differ between outlets (86% "factual conflict" versus price-specific rates) | Read the study page in a browser before quoting any figure other than Which?'s |
| WDC Products F1 range 0.64–0.89 | Not located in the text I searched | Check the results tables in arXiv 2301.09521 |
| Han et al. (2020) venue | Not on arXiv record | Check ACM Digital Library |
| Craigslist scam papers: which listing signals predict fraud | Existence confirmed only | Read Park et al. (2014, 2017) and Alsaleh & Zhou (2018) |
| Classifieds-only share of Australian shopping scams | NASC merges online shopping and classified scams | Scamwatch statistics page by category, or ABS Personal Fraud tables |
| Search stopping when listings arrive and disappear (first-pass gap 7) | Not searched | Targeted search in operations research and economics (dynamic search, secretary-type problems with posted prices) |
| Whether sustainability really drives used purchases | Not searched; lower priority | Behavioural, not stated-preference, studies in the 2020–2026 recommerce literature |
| Peer-reviewed evidence on consumer trust in LLM shopping or price advice | Two searches found only industry surveys | Search SSRN and the 2025–2026 issues of *J. Marketing*, *JMR*, *JCR*, *Marketing Science* directly |
| Full EC comparison tools report | Summary page read; PDF located | https://commission.europa.eu/document/download/93ad0e7a-af93-49fe-880b-9bcffbf5035f_en?filename=final-report-study-on-comparison-tools_en.pdf |
| A public benchmark for used-listing-to-product matching | Not found in arXiv, Crossref or two web searches; absence is not proof | Ask the WDC group (Bizer) and check Hugging Face and Kaggle dataset listings |

### Suggested edits to the synthesis (for whoever owns it; I have not edited any file)

1. Section 7 gap table: replace "Nothing" in the first three rows with "Scattered work on parts; no study of decision support for a specific used listing", and cite Ghose et al. (2006), Ishihara & Ching (2019), Abbey et al. (2017), Solinas et al. (2025), Crosno & Cui (2018), Deutsch (2010).
2. Section 7, matching row: "No public benchmark for second-hand listings; eBay and Mercari have published in-house methods."
3. Section 1: change "mostly within one brand or model" to "about 40% within one brand and 20% within one model", and add that the purchased item is usually first found late in the search.
4. Section 2: Ronayne's result is that comparison sites raise prices for all consumers in the model, not that they "can".
5. Section 6: add the Xianyu figures (17% without comparables, 55% with, at ±20% of asking price) and the Which? result (8 of 25 correct).
6. Section 5: the Dietvorst follow-up is now verified.
