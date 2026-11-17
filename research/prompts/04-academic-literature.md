# Track 4 — Academic literature review

Output: `research/findings/04-academic-literature.md`

## Goal
A real literature review that grounds the product in what is known about how people search for prices, why they stop searching, how they judge used goods, and how machines match products and estimate value. The founder wants thesis-level rigour used for practical ends: every theme should finish with what it implies for the product.

## Themes
For each theme: the foundational works, the most relevant work from 2020–2026, the consensus, the live disagreements, and the design implication. Give full references (authors, year, title, venue, DOI or URL). Only cite papers you have confirmed exist; if you are unsure of a detail, say so rather than guessing.

1. **Consumer search and search costs.** Stigler (1961) onward: sequential versus fixed-sample search, price dispersion online (Brynjolfsson and Smith; Baye, Morgan and Scholten), why dispersion persists despite comparison engines, obfuscation (Ellison and Ellison), measured time and effort consumers spend on search, and how much they leave on the table.
2. **Price comparison engines.** Effects on prices, consumer welfare and retailer behaviour; trust in and bias of comparison sites; ranking and sponsored-placement effects; regulator studies (ACCC, UK CMA digital comparison tools market study, EU studies).
3. **Second-hand markets.** Information asymmetry and adverse selection (Akerlof), reputation and trust mechanisms in peer-to-peer markets, consumer motivations and barriers for buying used (price, sustainability, risk, effort), the recommerce literature, and evidence on how buyers form reference prices for used goods.
4. **Reference prices, anchoring and deal evaluation.** Transaction utility (Thaler), internal and external reference prices, how consumers judge "a good deal", fake discounts and was/now pricing, regret and purchase confidence.
5. **Choice overload and decision support.** Evidence for and against choice overload, satisficers versus maximisers (Schwartz), recommendation agents and decision aids (Häubl and Trifts), explanation and trust in algorithmic advice, algorithm aversion and appreciation.
6. **Product matching and entity resolution.** Matching the same product across sources: classical methods, deep learning (DeepMatcher, Ditto), the WDC product matching benchmarks, LLM-based matching (2023–2026), and matching unstructured, noisy second-hand listings to canonical products including from images.
7. **Used-item valuation.** Hedonic pricing, depreciation curves, price prediction for second-hand goods (vehicles, phones, general marketplace listings such as the Mercari price suggestion work), condition assessment from text and images, and uncertainty estimation.
8. **LLM shopping agents.** Benchmarks and studies of LLM agents for shopping and web tasks (WebShop, Shopping MMLU, ShoppingBench and newer), reliability and hallucination of prices, bias in AI product recommendations, and consumer trust in AI shopping advice.
9. **Fraud and safety in peer-to-peer marketplaces.** Scam prevalence (ACCC Scamwatch and equivalents), detection methods, and what signals predict a fraudulent listing.

## Synthesis required
Finish with a section titled **Gaps in the literature** that states what has not been studied or solved — in particular anything on unified new-versus-used decision support for general goods, total-cost-of-acquisition comparison (price plus shipping plus travel plus risk plus time), and buy/wait/skip advice across conditions. Then list three to five candidate research questions the product could be built to answer.
