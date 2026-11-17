# Common brief — read this before your track prompt

## The product being researched
A mobile app (iOS + Android), home market **Australia**, where a shopper enters an item, picks new / pre-owned / both, and the app searches across retailers and second-hand channels, finds the best deals, and tells them whether the purchase is worth it. It should handle local pickup versus shipped options. Full background: `docs/idea-brief.md`.

The founder's triggering experience: about 20 minutes on Facebook Marketplace finding a used fishing rod and reel, then 50–100 minutes checking new prices at BCF and other retailers to decide whether the used price was a good deal.

## Why this research exists
The founder will decide tomorrow morning whether and what to build. They need to know whether this has been done, whether it is feasible, where the real gap is, and how to build something people remember. The founder is commercially motivated and enthusiastic, so the most useful thing you can do is be accurate, including when the news is bad. A finding that kills a bad direction tonight is worth more than one that flatters the idea.

## Rules for every track
- Today's date is 2026-11-17. Search for current information; products in this space launch and die quickly. Check whether each product you name is still operating and say when you last saw evidence of it.
- Australia first, then global. A tool that exists in the US but not in Australia is relevant but is a different kind of finding — say which.
- Cite every factual claim with a URL. Separate what you verified from a source from what you are inferring. Give a confidence level (high / medium / low) on the claims that matter most.
- Prefer primary sources: the product's own site, app store listings, API documentation, terms of service, court documents, regulator pages, peer-reviewed papers. Use news and blogs to find things, then confirm at the source where you can.
- If you could not find or access something, say so. Do not fill gaps with plausible-sounding detail.
- Report numbers with their date and source. Do not invent statistics.
- Do not commit or push to git. Only write your one output file.

## Output
Write your findings as markdown to the output path given in your track prompt. Structure:

1. **Bottom line** — five to ten sentences. What the founder most needs to know from this track.
2. **Findings** — organised by the questions in your track prompt. Tables where you are comparing products or options across the same attributes.
3. **Implications for the product** — what this means for what to build, what to avoid, and where the opening is.
4. **Open questions** — what you could not settle and how it could be settled.
5. **Sources** — the URLs you used.

Then reply to the orchestrator with a summary of at most fifteen lines: the bottom line, the three findings most likely to change the product direction, and anything you could not verify.
