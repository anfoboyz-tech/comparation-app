# Third pass, Assignment A — the user's-own-agent route

Read on 2026-11-17. This is research, not legal advice. **[LAWYER]** marks points a qualified Australian lawyer must settle.

Labels used throughout:

- **[R]** read at the source today (page, court opinion, statute or policy text).
- **[S]** search-result summary only; the page was not read.
- **[K]** background knowledge, not re-checked today.
- **[I]** my inference.

24 of the 25 allowed searches were used. Nothing was installed or run: no agent was tested on Marketplace, Gumtree or eBay, and no account was used.

## 1. Bottom line

1. **The user's permission makes this technically feasible on a desktop computer, and it removes most of the hacking-law risk. It does not remove the contract problem**, because the permission that matters under each platform's terms is the platform's, and Meta, Gumtree and eBay each forbid automated access by their own users.
2. **It works today on desktop.** Products already do it: Spottable's Chrome extension, Deal Scout, and Reduck, which lets Claude or ChatGPT search Marketplace and draft seller messages inside the user's signed-in Chrome. All are small.
3. **It does not work as a phone app feature.** An in-app browser needs the user to type their Facebook password into your app, cannot run in the background on iOS, and runs against Apple guideline 5.2.2 and Google Play's webview rule. Marketplace buying happens mostly on phones, so this is the route's hardest limit.
4. **US law moved in favour of this route in 2026, on one point only.** The Ninth Circuit held on 4 August 2026 that when a locally running agent acts for a user, the user and not the agent's maker "accesses" the site under the anti-hacking statutes. Rehearing was denied in September. The court said in terms that the ruling "does not impair Amazon's ability to regulate access to Amazon.com via private terms of service for its users", and Amazon has since re-pleaded the case as interference with its user contracts.
5. **Australia is untested.** My best reading is that criminal exposure for a user driving a local agent in their own account is low, and that the live risks are contractual: the user's account can be restricted, and the developer can face a cease-and-desist, an inducing-breach claim, and removal from the app stores.
6. **Meta's record against user-side tools is the main reason for caution.** It banned the developer of the Unfollow Everything extension for life in 2021 and won on contract against BrandTotal's extension in 2022. I found no report of a Facebook account restricted for using Claude in Chrome, Comet or ChatGPT's agent, and no evidence that it is safe either.
7. **Ranking, most to least defensible:** official APIs and feeds; the user's own general agent using instructions you publish; a desktop extension that reads only the page the user is on; an extension that navigates and searches by itself; an in-app phone browser; your servers holding the user's login. The last is reckless.
8. **What this means for the drive-shaft example:** an agent can search Marketplace, Gumtree and eBay for a user in minutes on a desktop, at the user's own account risk. It cannot do so from a phone app, in the background, or at a scale and reliability a company can promise.

## 2. Findings

### 2.1 Architectures

What each can do is my technical assessment **[I]** except where a source is cited. Nothing was run.

| | (a) Your servers log in as the user | (b) In-app browser on the phone | (c) Desktop browser extension | (d) User's own general agent plus your instructions | (e) Official API |
|---|---|---|---|---|---|
| **Facebook Marketplace** | Possible until Meta's login checks trigger; a new device and a data-centre address invite checkpoints | Loads the mobile site after the user logs in again inside your app; your code can read the pages | Reads listing and results pages in the user's session; can also open tabs and run searches. Spottable and Reduck do this **[R]** | The agent searches, opens listings and drafts messages. Reduck's page says a click-through agent "is slow" **[R, vendor claim]** | None for reading listings **[R, earlier pass]** |
| **Gumtree** | Earlier pass reported bot protection rejecting data-centre sessions **[S]** | Same as Marketplace; search needs no login | Same; search pages are public | Same | None. Terms say "If we make an API available" **[R]** |
| **eBay** | Pointless: an API exists | Works, also pointless | Works. Deal Scout reads eBay listings **[R, second pass]** | Works for search; checkout is where eBay aims its ban | Browse API, approved partners only **[R, second pass]** |
| **Retailer sites** | Not needed, pages are public | Works | Works. Honey, Capital One Shopping and Phia are this model | Works; this is what the vendors advertise | Affiliate feeds for some retailers **[R, second pass]** |
| **What breaks** | Two-factor prompts, checkpoints, account locks | Second login inside your app; "Sign in with Google" is refused in embedded browsers **[K]**; no background running on iOS, so no alerts or monitoring; store review | Page redesigns; mobile, where extensions exist only in Safari on iOS and not in Chrome on Android **[K]** | Speed, cost of the agent subscription, the vendor's own blocks, regional availability, no control over quality | Approval, licence terms, coverage |
| **Who bears the risk** | You: you hold credentials, your machines make the access, and Meta's terms forbid collecting passwords | You and the user: your app is the tool and the store listing is the pressure point | User (account) and you (contract and inducement claims, store removal) | User (account) and the agent vendor (litigation). You bear inducement risk only | You, under a contract you signed |
| **Where it stops** | At the first serious legal letter | At app review or the first platform complaint | At scale: tolerated while small and passive | At the platform's detection and the vendor's policies | At the licence terms |

Three points behind the table:

- **Architecture (a) is the one the terms name.** Meta: "You may not proxy, request, or collect Product usernames or passwords, or misappropriate access tokens", and users must "Not share your password, give access to your Facebook account to others" **[R]**. eBay Australia: users must not "share your sign-in credentials with any third parties" **[R]**.
- **The cloud-browser agents are closer to (a) than to (d).** OpenAI's help page describes a "virtual browser" in which the user signs in and "Cookies persist across sessions" **[R]**. The Ninth Circuit's reasoning rested on Comet running on the user's machine with Perplexity's servers "never directly access[ing]" Amazon **[R]**. Amazon's amended complaint reportedly alleges Perplexity's cloud servers used customers' authentication cookies directly for about two months **[S]**. A local agent and a hosted one are in different legal positions.
- **Architecture (e) does not grow with user permission.** A user's eBay sign-in does not unlock search beyond what the Browse API gives an approved app, and Meta offers no user-consent route to Marketplace listings **[I, from the earlier passes]**.

### 2.2 Law

#### Amazon v. Perplexity (Ninth Circuit, No. 26-1444, 4 August 2026) [R, opinion read in full]

- **Holding:** the preliminary injunction against Comet was vacated because Amazon was unlikely to show Perplexity "accessed" its computers. "It is the user who 'accesses' Amazon's computers, with the help of the Assistant to carry out specific acts on Amazon.com."
- **Facts it rests on:** Comet runs locally; the Assistant sends screenshots to Perplexity's servers and receives instructions; "Perplexity itself does not directly communicate with Amazon's servers."
- **Limits the court stated:**
  - "We do not establish a new legal regime governing agentic AI."
  - "We do not address whether in other contexts, including tort claims, Perplexity can avoid liability for the Assistant's actions."
  - "We do not address whether, on a different record or new facts, Perplexity may exercise control over the Assistant in such a way as to gain entry to Amazon's servers."
  - Footnote 5: "This outcome does not impair Amazon's ability to regulate access to Amazon.com via private terms of service for its users."
- **Unresolved fact:** the parties dispute whether Perplexity altered the agent's user-agent string after Amazon first blocked it. Disguising an agent is the conduct the founder's brief rules out, and it is the conduct Amazon is litigating.
- **Later history:**
  - Rehearing by the full court was denied; the docket date reported is 10 September 2026 **[S]**.
  - Amazon filed an amended complaint on 21 September adding a claim that Perplexity induces customers to breach Amazon's Conditions of Use **[S; the opening of one report was read, the rest was behind a sign-up]**.
  - Perplexity moved to dismiss on 13 October; no ruling was found **[S]**.

What it gives a founder: in the US, a locally running agent directed by the user is unlikely to be treated as the developer hacking the site. What it does not give: any protection against contract and interference claims, any application to hosted agents, or any authority in Australia.

#### Meta v. BrandTotal (N.D. Cal. 2022, 605 F. Supp. 3d 1218)

The opinion itself could not be read (three hosts refused or required a login). What follows is from the Ninth Circuit's description **[R]**, TechCrunch **[R]** and a search summary **[S]**.

- BrandTotal's UpVoice extension collected advertising data through the sessions of logged-in users who had installed it.
- The later version, which "passively logged ... data that users receive from Facebook through their normal use of the website", was held not to violate the anti-hacking statute, applying the rule of lenity **[R, as described by the Ninth Circuit]**.
- The court found BrandTotal breached the automated-collection clause of Facebook's terms and had not shown the terms unenforceable **[S; TechCrunch confirms the second half]**.
- It ended in October 2022 with a permanent injunction, deletion of the software and an undisclosed payment **[R, TechCrunch]**.

BrandTotal sold the collected data to advertisers and held Facebook accounts of its own. A tool that reads a page only to answer the user who is looking at it is a more sympathetic case. The contract clause is the same clause.

#### What the three platforms' terms say to a user running an agent

| Platform | Text | Read-only search covered? |
|---|---|---|
| **Meta** (terms effective 1 January 2025) **[R]** | "You may not access or collect data from our Products using automated means (without our prior permission) ... regardless of whether such automated access or collection is undertaken while logged-in to a Facebook account." | Yes. "Access" is enough; no purchase or message is needed. |
| **Meta, Automated Data Collection Terms** (7 October 2024) **[R]** | "You will not engage in Automated Data Collection without first obtaining Meta's express written permission". The terms claim to bind anyone who "otherwise engage[s] in Automated Data Collection". | Yes. Permitted uses are search engines and link previews. |
| **Gumtree** (effective 12 October 2026; in force for existing users since 12 November) **[R]** | Clause 8: must not "use any bot, script, macro, browser automation or similar tool to post, respond to or interact with Listings or other Users, unless we provide that tool". Clause 3.6: no "bots or other automated tools to post Listings or send messages". Clause 11.3: no copying "by any means (manual or automated)". Clause 11.1: no use "to build, feed or operate a competing service". | Yes. "Browser automation" that "interact[s] with Listings" describes a browser agent almost exactly. This is the most explicit of the three. |
| **eBay Australia** (posted 9 October 2026, effective 11 November 2026) **[R]** | Clause 15: "you will not use any robot, spider, scraper or other automated means to access the eBay services for any purpose without our express written permission." | Yes: "for any purpose". |
| **eBay US** **[R]** | Users may not "use any robot, spider, scraper, data mining tools, data gathering and extraction tools, or other automated means (including, without limitation buy-for-me agents, LLM-driven bots, or any end-to-end flow that attempts to place orders without human review) to access our Services for any purpose, except with the prior express permission of eBay". | Yes: the agent wording is a list of examples inside a ban on automated access "for any purpose". |

On eBay specifically:

- **Correction to the assignment's premise.** The "buy-for-me agents" and "LLM-driven bots" wording is in the US user agreement. It is **not** in the Australian user agreement in force today, which has only the general ban **[R]**. The wording does appear in the comment header of eBay Australia's robots.txt (version "v28.1_AU_August_2026") **[R]**.
- **The agreement's words cover read-only search; eBay's signals point at checkout.** The robots.txt policy is headed "Checkouts are strictly for human users" **[R]**.
- **eBay.com treats user-triggered agents differently from crawlers.** Its robots.txt blocks training crawlers (ClaudeBot, GPTBot, PerplexityBot and others) from the whole site, but gives `ChatGPT-User`, `Claude-User`, `OAI-SearchBot` and `Claude-SearchBot` a group with `Allow: /sch/`, the search path that is disallowed for everyone else **[R]**.
- **eBay.com.au has no such group.** Those agents fall under the general rules, where `/sch/` is disallowed **[R]**.
- A robots.txt line is not the "express written permission" the agreement requires **[I]**. My reading is that eBay tolerates named vendors' user-triggered search on its US site and has not extended that to Australia. Confidence: medium on the facts, low on eBay's intent.

#### Australia

**Contract. [I, LAWYER]**

- A user with an account has accepted the terms, so the earlier doubt about whether a contract forms does not arise.
- Using an agent on any of the three sites is a breach by the user on the words quoted above.
- The platform's practical remedy is to restrict or close the account. Damages against one shopper would be trivial.
- The developer is not a party to the user's contract. The routes to the developer are:
  - the developer's own account, if it has one (BrandTotal did);
  - the tort of inducing breach of contract, which needs knowledge of the contract and an intention to procure the breach **[K]**. A product built to automate these sites, by a founder who has read this report, has the knowledge. This is the theory Amazon is now running in the US **[S]**;
  - copyright, if listing photos or descriptions are copied to a server **[K]**.
- An unfair-contract-terms argument against a blanket anti-automation clause is conceivable and untested; a platform would point to security and scam prevention as its legitimate interest **[I]**.

**Criminal Code (Cth), Part 10.7. [R for the text; I for the application; LAWYER]**

- Section 478.1 makes it an offence to cause "unauthorised access to ... restricted data", intending the access and knowing it is unauthorised. Penalty: 2 years. Restricted data is data "to which access is restricted by an access control system". Pages behind a login qualify.
- Section 476.2(1): access is unauthorised "if the person is not entitled to cause that access".
- Section 476.2(2): access "is not unauthorised merely because he or she has an ulterior purpose for causing it".
- Section 476.2(3): "a person causes any such unauthorised access ... if the person's conduct substantially contributes to it."
- Application:
  - A user reading listings their own account is entitled to see is hard to describe as "not entitled to cause that access". Whether breaching a term about the *manner* of access removes the entitlement has not been decided for a website.
  - New South Wales authority on the equivalent state offence (*Salter v DPP*, 2011, a police officer using a police database) is reported as turning on what the person was entitled to access, with later cases confirming purpose is not an element **[S, the judgment was not read]**. I do not know how a court would apply that to a consumer's own account.
  - The Ninth Circuit's answer, that the user and not the developer "accesses", does not transfer cleanly. The Australian test is whether conduct "substantially contributes" to the access, which could reach a developer. The developer's protection in Australia is therefore that the access is authorised, not that someone else did it.
  - Architecture (a) is the weakest: your machines make the access with credentials the platform told the user not to share.

**A local precedent: bank screen-scraping. [R, Treasury discussion paper, August 2023]**

- For years Australian fintechs collected bank data by having customers hand over internet-banking logins, against bank terms that "customers must not share their login details".
- Treasury's paper treats it as a practice to regulate, lists consumer risks, and notes the Commonwealth Bank "takes steps to warn the customer". It does not describe it as an offence.
- The Government asked for advice on a ban where the Consumer Data Right is a workable substitute; no start date was found **[S]**.
- What this shows: consent-based access against the site's terms was tolerated in Australia for a long time. What it does not show: banking had a regulator building an official replacement, and banks did not sue. Marketplaces have neither feature.

**Privacy Act. [K and S, LAWYER]**

- Listing pages carry sellers' names, photos and suburbs, and message threads carry more. An agent that screenshots pages sends that to an AI vendor.
- The September 2026 exposure draft reportedly leaves the small-business exemption (turnover under A$3 million) in place **[S, law-firm summaries]**. The exemption does not cover businesses that trade in personal information **[K]**.
- Design response: process on the device or transiently, keep item facts only, and never keep seller identity.

**Strongest honest statement of the Australian position:**

> No Australian court has decided whether a person may use an AI agent in their own logged-in account against a website's terms, or whether the maker of that agent is liable. The user is very probably in breach of contract and can lose the account. Criminal liability for a user-directed agent running on the user's own device is unlikely on the statute's wording but has not been ruled out by any court. A developer who stays off the platform's servers, holds no credentials, does not disguise the agent and stores no personal information has a defensible position and no precedent to rely on. The US ruling that helps is persuasive at most, is confined to one statute, and expressly preserves the contract claim.

Confidence: medium. A lawyer could move this in either direction.

### 2.3 What the browser-agent vendors do

| Vendor | What it says about logged-in sites | Blocks | Who is responsible | Australia |
|---|---|---|---|---|
| **Anthropic, Claude in Chrome** **[R]** | "allows Claude to interact directly with websites on your behalf"; it works in the user's own Chrome session. Recommends not using it on sensitive sites and suggests a separate browser profile. | Cannot access adult or pirated-content sites; "asks for permission before accessing financial sites". Prohibited from "Bypassing captchas" and "Gathering or scraping facial images". | Consumer terms: "You are responsible for all Inputs you submit to our Services and all Actions"; third-party services are used "subject to any terms ... applicable" to them. | Paid plans; desktop Chrome. No regional limit seen on the page. |
| **OpenAI** **[R]** | "ChatGPT agent is no longer available. Use ChatGPT Work"; browser work is in a cloud browser. The user signs in by taking over a "virtual browser"; cookies persist. | "may not be able to visit certain websites. This blocklist applies across both the virtual browser and apps." The list is not published. | Not stated on the page read. | The retired agent was offered in all supported countries. Atlas is reported retired on 9 August 2026 **[S]**. |
| **Google, Gemini in Chrome auto browse** **[R]** | Can "Compare products, search for deals, and add items to your cart"; can sign in using Google Password Manager with permission. | Asks the user to take over for sensitive steps; reported to include accepting terms of service **[S]**. | "You're responsible for Gemini's actions during a task, including mistakes and unexpected results like purchases." | **Not available.** "Be 18 or over and in the US." Not on iPhone or iPad. |
| **Perplexity, Comet** **[R, company statement of 4 November 2025]** | "User agents are exactly that: agents of the user. They're distinct from crawlers, scrapers, or bots." Credentials "stored securely only in your device". | None stated. | Position is that the user acts. | An iPhone version launched in March 2026 **[S]**. |

What Meta and eBay do about agents in practice:

- **Meta** disallows the vendors' crawlers (ClaudeBot, GPTBot, PerplexityBot and others) across facebook.com in robots.txt **[R]**. That does not reach an agent working inside the user's own Chrome, which presents as the user's browser. Meta's tools there are behaviour detection, checkpoints and account restriction **[I]**.
- **eBay** is described above: a contractual ban with a permission gate, crawler blocks, and a search allowance for named user-triggered agents on the US site only.
- **Amazon** sued, and blocks agents it can identify **[R, opinion]**. Banks reportedly block agents from customer accounts **[S]**.

Have accounts been restricted for using agents?

- **Not found for Facebook, Marketplace or eBay.** Two searches found no report tying a restriction to Claude in Chrome, Comet, Atlas or ChatGPT's agent. Absence of reports is weak evidence: the products are new and Meta gives no reasons for restrictions.
- **Reported, unverified, for neighbouring cases.** Vendor blogs and forum posts describe Meta ad accounts closed after AI agents were connected, Marketplace restrictions on automated posting tools, and a sharp rise in LinkedIn restrictions on extension-driven automation in early 2026 **[S, low-quality sources]**.
- **Verified for developers.** See Unfollow Everything and the NYU researchers in 2.5.

### 2.4 Platform rules

**Apple App Store [R, guidelines read today]**

- 5.2.2: "If your app uses, accesses, monetizes access to, or displays content from a third-party service, ensure that you are specifically permitted to do so under the service's terms of use. Authorization must be provided upon request." Meta's and Gumtree's terms withhold that permission, so a complaint from either is enough to remove the app.
- 2.5.6: apps that browse the web must use WebKit. Nothing in the guidelines forbids an in-app browser or reading a page the user has loaded.
- 4.4 permits Safari web extensions shipped inside an app.
- 5.1.2(i): disclose and obtain explicit permission before sharing personal data "with third-party AI". Screenshots of a logged-in Facebook page sent to a model fall under this.
- A browser agent inside an iPhone app is allowed in principle: Comet for iOS is on the App Store **[S]**. That is a browser whose maker is fighting the litigation that goes with it. It is not a precedent for a shopping app that opens Facebook in a panel and harvests it.

**Google Play [R]**

- "We don't allow apps whose primary purpose is to drive affiliate traffic to a website or provide a webview of a website without permission from the website owner or administrator."

**Chrome Web Store [R]**

- Reading pages in the user's session is allowed if disclosed: "Collection and use of web browsing activity is prohibited, except to the extent required for a user-facing feature described prominently".
- Single purpose, narrowest permissions, and limited use of data, including "scraped content or otherwise automatically gathered user data".
- "Do not facilitate unauthorized access to content on websites, such as circumventing paywalls or login restrictions." Reading what the signed-in user can already see is not circumvention on my reading **[I]**.
- Affiliate links only with "related user action" and a "direct and transparent user benefit". This is the rule tightened after Honey.
- No remotely hosted logic: "Building an interpreter to run complex commands fetched from a remote source, even if those commands are fetched as data" is a violation, with exemptions for the Debugger and User Scripts APIs. An extension whose steps are chosen by a model on your server has to be built inside those exemptions.

### 2.5 Precedents

| Product | How it gets data | What happened |
|---|---|---|
| **Password managers** **[K]** | Fill forms in the user's session; take no site data | Universally tolerated. They act for the user without extracting anything, which is why they are not a useful precedent for search. |
| **Bank screen-scraping in Australia** (Yodlee, illion, Basiq and others) **[R, Treasury]** | Customer's banking login, used by the provider's servers | Ran for many years against bank terms; now being replaced by the Consumer Data Right, with a ban under consideration. |
| **Honey, Capital One Shopping** **[S; K]** | Extension reads retailer pages in the user's session | Tolerated by retailers because they are paid affiliates. Honey's trouble came from affiliate attribution: a creator class action survived a motion to dismiss on 22 June 2026, and its Chrome listing is reported at 12 million users, down from over 20 million **[S]**. |
| **Phia** **[R, TechCrunch 10 July 2026]** | Extension reads the product page | Accused of overriding other affiliates' codes in background tabs; suspended from Impact.com; says it has fixed it. |
| **BrandTotal UpVoice** **[R, S]** | Extension in panel members' logged-in Facebook sessions | Lost on contract; permanent injunction and payment, October 2022. |
| **Unfollow Everything** **[S, consistent across several outlets]** | Free extension automating actions in the user's own Facebook account | 2021: cease-and-desist from Meta's lawyers, developer's Facebook and Instagram accounts "permanently disabled", extension withdrawn. |
| **NYU Ad Observer** **[S]** | Opt-in extension collecting ads users saw | August 2021: Meta disabled the researchers' accounts and platform access. |
| **Power Ventures** **[R, as described by the Ninth Circuit]** | Users gave an aggregator access to their Facebook accounts | Liable under the anti-hacking statute for continuing after a cease-and-desist letter. The Ninth Circuit distinguished it without overruling it. |
| **Perplexity Comet** **[R, S]** | Local agent browser in the user's session | Sued by Amazon; won the appeal on the hacking statutes; contract-interference claim pending. |
| **Spottable** (Sydney) **[R]** | iPhone app: server-side, "No Facebook password", reading public Marketplace. Chrome extension: "Checks listings while you browse", with batch analysis of results pages | Operating. 966 Chrome users and 6 Australian ratings per the second pass. |
| **Deal Scout** **[R, second pass]** | Chrome extension that opens on Marketplace, eBay and other listing pages | Operating; 36 users. |
| **Reduck** **[R, page updated 6 November 2026]** | Extension scripts that "run in your own Chrome, where you are already signed in", exposed to Claude or ChatGPT as tools: search, open listings, read seller profiles, type a message that "stays unsent until you say so" | Operating; says it raised US$3 million. The closest live example of architectures (c) and (d) combined. |
| **Swoopa** (Melbourne) | Not disclosed; says it is not a scraper **[S, first pass]** | Operating after about three years, now aimed at car dealers **[R, second pass]**. Its site refused today's request. |

The pattern:

- **Tools that read retailer pages last**, because retailers are paid for the sales they send.
- **Tools on Meta's properties last while they are small.** The ones Meta noticed (BrandTotal, Unfollow Everything, NYU) were stopped by contract claims and account bans, and none of them needed a hacking-law win.
- **No product found has scaled on logged-in Marketplace access.**

### 2.6 Verdict

Ranked from most to least defensible and durable.

| Rank | Route | Defensible? | Durable? | Stops at |
|---|---|---|---|---|
| 1 | **(e) Official API or feed** | Yes | Yes, within the licence | eBay and some retailers only. Nothing for Marketplace or Gumtree. |
| 2 | **(d) The user's own general agent, with instructions you publish** | Best of the session routes. You touch no platform and hold nothing. | Medium. Depends on vendors and on platforms not blocking them. | Desktop only in practice; minutes per task; Gemini's version is US-only; the user carries the account risk; you carry inducement risk if your instructions direct the breach. |
| 3 | **(c) Extension, passive**: reads the page the user is viewing, on the user's click, processed transiently | Grey but occupied. Same contract clause as BrandTotal, far more sympathetic facts. | Medium on desktop while small | Desktop and iOS Safari only. It judges what the user found; it does not search. |
| 4 | **(c) Extension, active**: opens tabs, runs searches, pages through results, drafts messages | Grey, leaning against you. This is "browser automation" in Gumtree's words and "automated means" in Meta's and eBay's. | Low to medium | The first cease-and-desist; the user's account. |
| 5 | **(b) In-app phone browser** | Poor. Same legal position as 4, plus store rules, plus asking for a Facebook password inside your app. | Low | App review, or one complaint under 5.2.2. No background running. |
| 6 | **(a) Your servers with the user's login** | No | No | Meta's password clause; the weakest position under the Criminal Code; Power Ventures. |

**A careful founder could ship in Australia:**

- Official sources: eBay through the partner programme if approved, and retailer feeds.
- The user-brings-a-listing flow from the earlier passes.
- A desktop extension limited to rank 3: one page, on a click, nothing kept but item facts, plainly disclosed.
- A published instruction pack, and a tool server that supplies only what you lawfully hold (retail prices, the verdict logic, travel cost), for people who already use Claude in Chrome or a similar agent. Your server never touches Marketplace, Gumtree or eBay; the user's agent does, on the user's decision.

**Needs a lawyer's sign-off before shipping:**

- Any extension feature that navigates, searches or pages through results by itself.
- Anything on Gumtree, including the passive extension, given clause 8 and the "manual or automated" copying clause.
- Whether instructions that tell an agent to search Marketplace amount to inducing breach, and how to word them.
- Drafting or sending messages to sellers.
- Keeping any listing data on your servers.
- What the product may say about coverage and permission. "Searches Marketplace for you" is a claim about something the platform forbids.

**Reckless:**

- Collecting or storing users' passwords, cookies or tokens for any of these sites.
- Running users' sessions on your servers.
- Building the phone app around a Facebook web panel.
- Background monitoring or alerts through users' sessions.
- Disguising automation, rotating addresses, or defeating checkpoints and captchas.
- Buying Marketplace data from a scraping vendor.

## 3. What this means for the product

1. **The honest answer to the founder's question is "yes for you, not yet for a company".** A person with Claude in Chrome can have it search Marketplace, Gumtree and eBay in their own browser today. Turning that into a product means either owning the tool that does the access (ranks 3 to 6, with rising risk) or standing behind someone else's agent (rank 2, with little control).
2. **The phone is the binding constraint, more than the law.** No route puts an agent inside the Facebook app. Any session route is a desktop product in a category that is used on phones.
3. **Rank 2 is cheap to test and should be tested before anything is built.** Write the instructions, run them in Claude in Chrome on ten real searches including the drive-shaft case, and record time taken, completeness, and whether Facebook interrupts. That converts most of this report's inferences into observations in a day.
4. **If rank 2 works, the product is the part the agent lacks, not the browsing.** That is Australian retail prices, fitment or model matching, total cost, a verdict, and for parts the enquiries to wreckers covered by Assignment C. Those are assets you can hold lawfully.
5. **Do not make the business depend on a session route for Marketplace.** Every precedent on Meta's properties ends with the tool small or stopped. Treat it as an optional accelerator for desktop users that the product survives losing.
6. **eBay is the platform most likely to say yes.** It has a permission gate, a partner programme and a visible distinction between agents that read and agents that buy. Ask for permission in the Buy API application already recommended.
7. **Gumtree is the platform most likely to say no in writing**, and the one whose new terms name the technique. Ask for a licensed feed; do not automate it.

## 4. Open questions

| Question | How to settle it |
|---|---|
| Does a browser agent complete a Marketplace, Gumtree and eBay search in Australia today, how long does it take, and does Facebook interrupt? | Run it: ten searches with Claude in Chrome on a personal account, timed. Nothing in this report was tested. |
| Does breach of a website's automation clause make a user's access "unauthorised" under section 478.1, and can a developer "substantially contribute"? | Lawyer; read *Salter v DPP* and any later authority. |
| Would published instructions for a third-party agent amount to inducing breach of contract in Australia? | Lawyer. Watch the ruling on Perplexity's motion to dismiss in the Northern District of California for the US answer. |
| Will eBay permit a user-triggered agent to search ebay.com.au, as its US robots.txt appears to for named vendors? | Ask eBay in writing with the Buy API application. |
| Does Meta restrict accounts that use browser agents on Marketplace? | No reports found. Only testing over weeks, or a statement from Meta, would show it. |
| What exactly did the BrandTotal court hold on contract and on the earlier extension versions? | Read 605 F. Supp. 3d 1218 through a legal database; three hosts refused today. |
| Where did Australia's screen-scraping ban end up? | Treasury and ASIC pages for 2025–26; not found today. |
| Does Comet's iPhone app act inside logged-in sites, and did Apple impose conditions? | Install it; not verified. |
| How do Swoopa and Classifindr obtain Marketplace and Gumtree data? | Swoopa's site refused the request. Ask them, or inspect the apps' network behaviour on your own device. |
| Is the small-business exemption staying in the final privacy bill? | Attorney-General's Department; the exposure draft itself was not read. |

## 5. Sources

Read at the source today:

- Ninth Circuit opinion, *Amazon.com Services LLC v. Perplexity AI, Inc.*, No. 26-1444: https://cdn.ca9.uscourts.gov/datastore/opinions/2026/08/04/26-1444.pdf
- Meta Terms of Service: https://www.facebook.com/legal/terms
- Meta Automated Data Collection Terms: https://www.facebook.com/legal/automated_data_collection_terms
- https://www.facebook.com/robots.txt
- Gumtree Terms of Use: https://help.gumtree.com.au/articles/en_US/KB_Article/Gumtree-Terms-of-Use-AU
- https://www.gumtree.com.au/robots.txt
- eBay Australia User Agreement: https://www.ebay.com.au/help/policies/member-behaviour-policies/user-agreement?id=4259
- eBay US User Agreement: https://www.ebay.com/help/policies/member-behaviour-policies/user-agreement?id=4259
- https://www.ebay.com.au/robots.txt and https://www.ebay.com/robots.txt
- Criminal Code Act 1995 (Cth), compilation of 18 February 2026, volume 3, sections 476.1, 476.2, 478.1: https://www.legislation.gov.au/C2004A04868/2026-02-18/2026-02-18/text/original/pdf/3
- Treasury, "Screen scraping – policy and regulatory implications": https://treasury.gov.au/consultation/c2023-436961 and https://treasury.gov.au/sites/default/files/2023-08/c2023-436961-dp.pdf
- Anthropic, "Use Claude in Chrome safely": https://support.claude.com/en/articles/12902428-using-claude-in-chrome-safely
- Anthropic Consumer Terms: https://www.anthropic.com/legal/consumer-terms
- OpenAI, "ChatGPT agent": https://help.openai.com/en/articles/11752874-chatgpt-agent
- Google, auto browse in Gemini in Chrome: https://support.google.com/chrome/answer/16821166?hl=en
- Perplexity, "Bullying is not innovation": https://www.perplexity.ai/hub/blog/bullying-is-not-innovation
- Apple App Review Guidelines: https://developer.apple.com/app-store/review/guidelines/
- Google Play spam policy: https://support.google.com/googleplay/android-developer/answer/9899034?hl=en
- Chrome Web Store Program Policies: https://developer.chrome.com/docs/webstore/program-policies/policies
- Spottable: https://spottableapp.com/ , https://spottableapp.com/extension/ , https://spottableapp.com/facebook-marketplace-api/ , https://spottableapp.com/faq/
- Reduck: https://reduck.ai/use-cases/facebook-marketplace-mcp
- TechCrunch on the BrandTotal settlement: https://techcrunch.com/2022/10/03/meta-settles-lawsuit-for-significant-sum-against-businesses-scraping-facebook-and-instagram-data/
- TechCrunch on Phia: https://techcrunch.com/2026/07/10/phia-accused-of-cookie-stuffing-taking-affiliate-credit-on-purchases-it-didnt-earn/
- The Fashion Law on Amazon's amended complaint (opening paragraphs only): https://www.thefashionlaw.com/amazon-perplexity-case-is-becoming-a-test-of-who-controls-ai-commerce/

Search summaries only:

- Rehearing denied: https://www.courthousenews.com/no-9th-circuit-rehearing-in-amazon-perplexity-case/ ; https://dockets.justia.com/docket/circuit-courts/ca9/26-1444
- Amended complaint and motion to dismiss: https://www.mlex.com/mlex/artificial-intelligence/articles/2527900 ; https://www.mlex.com/mlex/artificial-intelligence/articles/2537838
- BrandTotal ruling: https://www.courthousenews.com/judge-rules-brandtotals-data-harvesting-violates-metas-terms-of-use-and-anti-hacking-laws/ ; https://leagle.com/decision/infdco20220607c73
- eBay's agent ban: https://www.valueaddedresource.net/ebay-bans-ai-agents-updates-arbitration-user-agreement-feb-2026/ ; https://www.ecommercebytes.com/2026/01/21/ebay-bans-ai-shopping-agents-updates-arbitration-provision/ ; https://www.mediapost.com/publications/article/412276/ebay-blocks-3rd-party-agents-eyes-new-attribution.html
- Unfollow Everything: https://gizmodo.com/facebook-banned-the-creator-of-unfollow-everything-and-1847826505 ; https://yro.slashdot.org/story/21/10/08/178224/facebook-bans-developer-behind-unfollow-everything-tool
- NYU Ad Observer: https://about.fb.com/news/2021/08/research-cannot-be-the-justification-for-compromising-peoples-privacy ; https://article19.org/resources/open-letter-facebook-withdraw-cease-desist-to-nyu
- Honey: https://ppc.land/honey-loses-7-000-merchants-as-judge-lets-creator-lawsuit-proceed/ ; https://news.bloomberglaw.com/litigation/paypal-cant-shed-content-creators-affiliate-hijacking-claims
- *Salter v DPP* commentary: https://www.mondaq.com/australia/crime/1113738/criminal-prosecution-of-accessing-restricted-data-in-new-south-wales
- Privacy reform: https://www.hsfkramer.com/en_US/insights/2026-09/the-draft-tranche-2-privacy-act-reforms-whats-there-whats-new-and-whats-missing ; https://www.sparke.com.au/insights/a-new-era-for-privacy-in-australia-implications-of-privacy-act-reform-tranche-2/
- Screen-scraping ban direction: https://www.mallesons.com/au/en/insights/latest-thinking/the-government-announces-its-plans-for-the-cdr.html
- Agents blocked by sites; account restrictions (low-quality sources): https://bambooflags.com/blog/websites-blocking-ai-agents.html ; https://tofuads.com/resources/ai-agent-ad-account-ban-meta-google ; https://autolander.ai/guide/facebook-marketplace-automation/ ; https://linkedinsider.blog/linkedin-automation-crackdown-2026
- Comet for iOS; Atlas retirement: https://www.iphoneincanada.ca/2026/03/19/perplexity-launches-comet-browser-for-ios/ ; https://dev.to/jay_elsheikh_59b14ad67922/comet-and-atlas-why-the-ai-browser-bet-is-failing-47l3
- Open-source Marketplace monitors that log in as the user: https://github.com/BoPeng/ai-marketplace-monitor

Refused or unreadable today: getswoopa.com (browser challenge), www.fastcompany.com (403), www.courthousenews.com (403), leagle.com (login), law.justia.com (browser challenge), courtlistener.com API (needs a key), AustLII (403), rm.coe.int (403), www.mallesons.com screen-scraping article (redirected to an index page).
