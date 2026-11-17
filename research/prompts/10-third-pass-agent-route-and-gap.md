# Third pass — the user's-own-agent route, the competitor gap, and the legwork problem

## Why this pass exists
The founder has pushed back on the first two passes, fairly. Two new directions:

1. **Permission.** "If I give the app permission to use my Facebook, my eBay and so on, the way Claude in Chrome can use my browser, does that make searching those sites feasible?" The earlier passes treated logged-in automation as off the table. This pass examines it properly.
2. **Legwork, not verdicts.** The founder's new example: needing a drive shaft for a car took four hours of searching sites, checking Marketplace and phoning wreckers. "Why can't an app do that in five minutes?" The product may be an agent that does the sourcing work, not a price checker.

The founder asked for loopholes. The useful reading of that is: find every route that is lawful or defensibly grey and durable, and say exactly where each one stops. Do not propose evading bot detection, bypassing access controls, or using other people's accounts; those end the company. Report bad news plainly.

## Rules
Follow the rules in `research/prompts/09-second-pass-verification.md` (how to read pages, search ration of 25, do not work around sites that refuse requests, do not edit other files, do not commit). Read `MORNING-BRIEF.md` and `research/synthesis/gap-analysis.md` first, plus the earlier reports named in your assignment. Cite URLs, label what you read at source versus search summary versus your own inference, and give confidence levels.

## Output
Write to the path in your assignment: bottom line (five to ten sentences); findings; what this means for the product; open questions; sources. Then reply with a summary of at most fifteen lines.

## Assignment A — the user's-own-agent route
Output: `research/findings/third-pass/A-user-agent-route.md`. Earlier reports: `research/findings/03-data-access-and-legal.md`, `research/findings/second-pass/03-data-and-legal.md`.

1. **Architectures.** Compare: (a) the app's servers logging in with the user's credentials or session; (b) an in-app browser on the phone where the user logs in and the app reads the pages loaded in that session; (c) a desktop browser extension acting in the user's session; (d) a general browser agent the user already has (Claude in Chrome, ChatGPT agent, Perplexity Comet, Gemini in Chrome) driven by a skill or instructions the product supplies; (e) an official OAuth or partner API where one exists. For each: what it can technically do on Facebook Marketplace, Gumtree, eBay and retailer sites; what breaks; who bears the risk.
2. **Law.** Read the Ninth Circuit's August 2026 decision in Amazon v. Perplexity and its later history; Meta v. BrandTotal (2022); Meta's and Gumtree's and eBay's current terms as they apply to a user's own agent (eBay's 2026 ban on "buy-for-me agents" and "LLM-driven bots" in its user agreement: what exactly does it prohibit, and does it cover read-only search?). Then Australian law: contract, the Criminal Code computer offences where the user themselves authorises access, privacy. What is the strongest honest statement of the position in Australia?
3. **What the browser-agent vendors do.** How do Anthropic, OpenAI, Perplexity and Google describe what their agents may do on logged-in sites, which sites block them, and what do Meta and eBay do about them in practice? Have user accounts been restricted for using agents?
4. **Platform rules.** Apple App Store and Google Play rules on in-app browsers that read third-party logged-in sessions; Chrome Web Store rules for extensions; whether iOS allows anything like a browser agent inside another app.
5. **Precedents.** Products that work this way today and have lasted: for example password managers, Plaid-style screen-scraping in banking before open banking, travel and shopping extensions (Honey, Capital One Shopping, Phia), Marketplace tools (Swoopa, Spottable, Deal Scout — how do they actually get data?), Australian examples. What happened to them?
6. **Verdict.** Rank the architectures from most to least defensible and durable. State what a careful founder could ship in Australia, what needs a lawyer's sign-off, and what would be reckless.

## Assignment B — competitor teardown and the gap
Output: `research/findings/third-pass/B-competitor-teardown-and-gap.md`. Earlier reports: `research/findings/02-competitors-used-and-cross-condition.md`, `research/findings/second-pass/01-02-competitors.md`, `research/findings/08-differentiation-and-moat.md`.

1. **Feature matrix.** For every product the earlier passes found (Deal Scout, PriceSnap, Spottable, PriceVet, Grabbit, YrdSale, Underpriced, DealRater, PricePath, Swoopa, Classifindr, Phia, Beni, Faircado, Zyft, BuyWisely, Google/Gemini shopping, ChatGPT shopping and agent, Meta AI in Marketplace) and any new ones: input method; sources searched; does it search for the user or only judge what the user found; new price; used comparables; verdict; total cost; location; alerts; contacts sellers; negotiates; phones or messages businesses; categories; Australia; platform; price; traction.
2. **What users say is wrong with them.** Read reviews on the app stores, Chrome Web Store, Product Hunt and any forum threads. Group the complaints.
3. **What none of them does.** From the matrix, list the capabilities with no or almost no coverage. Pay particular attention to: doing the search legwork end to end; reaching supply that is not listed online; contacting sellers or businesses on the user's behalf; handling parts, fitment and compatibility; a single answer across new, used, refurbished and wrecked; time-to-answer as the promise.
4. **Agents that do legwork.** Find products, anywhere, where an AI does hours of sourcing for a consumer: request-for-quote services, concierge shopping agents, AI that phones businesses (for example Google's call-a-business features), agentic search for used gear, parts-finding services. What do they do, where do they operate, how are they doing?
5. **Why the verdict tools have no users.** Form a view from the evidence: is it distribution, trust, frequency of need, or that a verdict is not the job people need done?
6. **The gap, stated precisely.** One paragraph, then three to five candidate product positions ranked by how open they are and how much pain they remove, each with what it would take and what could kill it.

## Assignment C — the car-parts sourcing problem in Australia
Output: `research/findings/third-pass/C-car-parts-sourcing.md`.

1. **How Australians find a used or new car part today.** Wreckers and auto recyclers, parts-locator and request-a-part services, eBay Motors, Facebook Marketplace and groups, Gumtree, dealers, aftermarket retailers (Repco, Supercheap Auto, Sparesbox and similar), specialist importers. How long does it take, and what do people complain about? Use forums and reviews.
2. **Existing locator services.** Find and assess every Australian parts-locator or wrecker-network service and the main overseas ones (for example Car-Part.com and similar in the US and UK). How they work, coverage, who pays, reviews, whether they are any good.
3. **Where the inventory lives.** What inventory systems do Australian wreckers use, are any searchable online or by API, and is there an industry body or data standard? How much stock is only discoverable by phone?
4. **Fitment data.** How a part is matched to a vehicle (VIN, part numbers, interchange data). Which fitment and interchange databases exist for Australian vehicles, who licenses them and at what cost?
5. **An agent that makes the enquiries.** Could an AI send the same parts request to many wreckers by web form, email, SMS or phone call and collect the replies? What exists already? What do Australian rules say about automated or AI-voiced calls and messages to businesses (ACMA, the Spam Act, Do Not Call Register, call-recording laws, any AI disclosure rules)?
6. **Market and money.** Size of the Australian used and aftermarket parts market, number of wreckers, typical part values, who would pay (consumer, mechanic, wrecker lead fee), and what comparable services charge.
7. **Competitors and threats.** Anything already doing "tell me the part, I find it" in Australia, including mechanic-facing trade tools.
8. **Other categories with the same shape.** Briefly: which other purchases take people hours of phoning and searching because supply is fragmented and partly offline (appliance spare parts, tyres, building materials, machinery parts, trades quotes)? Rank the top three by pain and reachability.
9. **Verdict.** Is car parts a better first market than second-hand general goods for a sourcing agent? What would a first version do, and what would stop it?
