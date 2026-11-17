# Second pass — verification at the source

The first pass (reports 01–08 in `research/findings/`) could not open web pages and ran short of searches, so its claims rest on search-result summaries. Network access is now open. This pass reads the primary sources for the claims the build decision depends on.

## Rules
- Read `research/prompts/00-common-brief.md` for context and the general rules, then the first-pass report(s) named in your assignment, then `MORNING-BRIEF.md` to see which claims the decision rests on.
- The WebFetch tool may still fail in this session. To read a page, use `curl -sL` with an ordinary browser user-agent from Bash, one page per command, or the pre-installed Playwright (`require('playwright')`, `chromium.launch()`) for pages that need JavaScript. Save pages under your scratch directory, not the repository.
- Fetch only the specific pages you need to read. If a site refuses automated requests or asks for a login, do not try to get around it: note it as unreadable and move on.
- Web searches are rationed across all agents. Use at most 25, and spend them on finding the right page, not on re-running first-pass queries.
- Your job is to check, not to re-argue. For each claim: confirmed at source, corrected (say what the source actually says, with a short quote), or still unverified (say why).
- Do not edit the first-pass reports or any other file. Do not commit or push.

## Output
Write to the path given in your assignment:
1. **What changed** — the corrections and new facts that alter the build decision, most important first.
2. **Claim table** — claim, first-pass file, status (confirmed / corrected / unverified), what the source says, URL, date read.
3. **New findings** — anything material the first pass missed.
4. **Still open** — what could not be read and what would settle it.

Then reply with a summary of at most fifteen lines.
