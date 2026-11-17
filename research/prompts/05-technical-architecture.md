# Track 5 — Technical architecture and cost

Output: `research/findings/05-technical-architecture.md`

## Goal
Work out how the system would actually be built in late 2026, what it would cost per search, and where the hard engineering problems are. The founder plans to start building tomorrow with an AI coding agent, as a solo or very small team, so favour architectures a small team can ship and run.

## Questions
1. **Query understanding.** Turning "fishing rod and reel combo around $200" or a pasted listing link or a photo into a canonical product or product class with attributes. Options: LLM extraction, product knowledge graphs, GTIN/barcode lookup, visual search. What works today and at what cost and latency?
2. **Retrieval design.** Live federated search at query time versus a pre-built index versus a hybrid; LLM agents with web search tools versus deterministic connectors; caching and freshness. What do current products appear to use? Compare on latency, cost, coverage, reliability and legal exposure.
3. **Product matching across sources.** The same item appears with different titles, bundles and variants, and used listings are noisy ("Shimano reel good cond"). What is the current best practical approach (embeddings plus LLM verification, multimodal matching), expected accuracy, and how do you handle near-matches and substitutes ("same rod, previous model year")?
4. **Used-condition normalisation and fair-value estimation.** How to turn listing text and photos into a condition grade, and how to estimate a fair used price for a general-goods item with thin data: sold comparables (eBay sold listings), depreciation priors by category, percent-of-new heuristics, LLM estimation with retrieved comps. How should uncertainty be expressed?
5. **Total cost of acquisition.** Modelling price plus shipping plus travel distance and time for pickup plus warranty and returns value plus risk discount for peer-to-peer. What inputs are available and what a defensible scoring formula looks like.
6. **Verdict generation.** Producing a buy / negotiate / wait / skip recommendation with reasons and a suggested offer price. How to keep it grounded in retrieved evidence and prevent invented prices; evaluation methods.
7. **Model and API costs.** Using current pricing as of November 2026 (look it up: Anthropic, OpenAI, Google model prices; web search tool prices; SERP and product-data API prices), estimate cost per search for two or three candidate designs, and the latency a user would experience. Show the arithmetic.
8. **Mobile stack.** React Native/Expo versus Flutter versus native for a two-platform launch by a small team in 2026; share-sheet extensions (receiving a Marketplace or Gumtree link from another app) on iOS and Android; push alerts; location; backend options (serverless, Supabase/Firebase, queues for long-running searches).
9. **Build sequence.** What a credible first version looks like that could be built in days to weeks, and what should be deferred.
10. **Hard problems.** Rank the technical risks by severity and say how each can be reduced.
