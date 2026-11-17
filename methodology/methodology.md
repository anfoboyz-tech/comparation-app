# Methodology

Revised after the third pass. How to get from the research to a validated product, in stages, with a decision at the end of each. It answers the research question in `research/synthesis/research-question.md`, where the pass and stop thresholds are defined.

## Product definition this methodology tests

**Tell it what you need. It does the searching and the asking, and comes back with one ranked answer.**

- First market to test: car parts in Australia. The founder spent four hours finding a drive shaft across websites, Marketplace and phone calls to wreckers.
- The agent pins down the exact part, searches stock that is listed online, lodges requests with the existing parts networks, sends enquiries to yards that have to be asked, chases the ones that do not reply, and ranks the options by total cost.
- The promise is five minutes of the user's time, with a first answer in minutes and a fuller one within a working day.
- The fair-price check from the earlier design is the last step: it tells the user which option is the better buy, including against a new part.

Why this shape, and why not a verdict tool or "search everything", is in `research/synthesis/gap-analysis.md`.

## Principles

1. **Lawful routes only.** Official APIs the product is approved for, stock that suppliers publish, existing request networks, and enquiries to businesses. No marketplace access from the product's servers and no user passwords.
2. **An enquiry is only an enquiry.** It says it is an assistant acting for a buyer, asks for price, condition and availability, and never promotes the product to the supplier.
3. **Get the part right before asking anyone.** The agent asks the fitment questions first and says so when it cannot confirm a fit.
4. **The model never produces a number.** Code computes prices, totals and rankings from what was retrieved.
5. **Promise the user's time, not the clock.** Suppliers answer in hours. The product says so.
6. **The user decides and pays.** The agent drafts and recommends; it does not commit or buy.
7. **Every request leaves data behind:** which suppliers answer, how fast, on which channel, and what parts cost.
8. **Measure before building more.** Each phase ends with numbers against the thresholds.

## Phases

### Phase 0 — Find out whether the problem is already solved (week 1; the founder, no software)

| Check | Method | Stop or change if |
|---|---|---|
| Existing locators | Put 20 real part requests, starting with the drive shaft, through Findapart, Hollander Parts, PartsClub and WrecKonnect. Mix common and uncommon parts, newer and older vehicles. Record whether a suitable quote arrives, how fast, and at what price | 70% or more get a suitable quote within 2 hours. Then the product is at most a signpost to them |
| Supply the locators miss | For the same requests, search eBay and new-part retailers and phone five yards each. Record where the best option came from | Under 10% of best options come from outside the locators |
| Will yards answer | While phoning, note which yards answer, which prefer a text or email, and what they ask you | Almost none answer on any channel |
| Browser-agent trial | Run ten searches, including the drive shaft, with Claude in Chrome on your own account and time them. This shows what the optional desktop route can do | Does not stop anything; informs stage 4d of the pipeline |
| Mechanics | Ask five mechanics how they source used parts, what they use, and what goes wrong | They are fully served by trade tools |
| Second-hand goods comparison | Run five real listings through Deal Scout, PriceSnap, Spottable and PriceVet | Informs whether the fair-price step needs building or can be simple |

Start in parallel:

- **Lawyer.** Ask about AI-voiced and automated enquiries to businesses under the telemarketing, spam and call-recording rules; what disclosure is needed; and the Gumtree and Meta terms for the optional desktop route.
- **eBay Partner Network** application, for the parts listings on eBay.
- **Approach one locator**, PartsClub or Hollander, about access to their stock search. They are a competitor and a possible partner.

**Decision at the end of Phase 0:** build the sourcing agent for parts, change market, or stop.

### Phase 1 — Do it by hand for real people (weeks 2–3)

A concierge test: take real requests and fulfil them manually, following the pipeline as a checklist. This answers sub-questions 2, 3, 5 and part of 8 before any agent exists.

- **Recruit** 20–30 requests from car forums, Facebook groups and two or three mechanics.
- **For each,** record the fitment questions needed, every source tried, each supplier's channel and response time, the options found, and what the person bought.
- **Measure** supplier reply rate by channel, time to a usable answer, the person's own time, and whether they would use it again or pay.

The record of which yards answer and how is the first version of the supplier-response map.

**Decision:** which stages are worth automating, and whether consumers or mechanics are the user.

### Phase 2 — Build the agent without an app (weeks 3–6)

Build the pipeline in `methodology/pipeline.md` as a tool the founder operates.

- **Order of build:** fitment questions; listed-stock search; request-network lodging; email and SMS enquiries; reply reading and matching; ranking with total cost. Voice calls last, and only after the lawyer's view.
- **Test set:** the Phase 0 and Phase 1 requests, with their known outcomes.
- **Measures:** fitment accuracy against a mechanic's judgement; best total cost against the by-hand result; supplier reply rate to agent enquiries against the by-hand rate; cost per request; any complaint from a supplier.
- **Regression rule:** the test set is re-run on every change to prompts or models.

**Decision:** build a user-facing version only if sub-questions 3, 4 and 5 pass.

### Phase 3 — First user-facing version (2–3 weeks)

One flow: state the need, answer the fitment questions, get a first answer from listed stock, get notified as better options arrive, pick one.

- **Web first or app first** is still the founder's decision. Notifications over hours favour a phone app; a web version is quicker to test and can take real payments. A workable order is web with SMS or email notifications for the field study, then the app.
- Recommended stack from the architecture track: TypeScript throughout, Supabase, a durable job runner for requests that last hours, a small model for reading and matching and a stronger one for conversation; Expo for the app.
- Not in this version: buying on the user's behalf, marketplace search inside the app, more than one category.

### Phase 4 — Field study (4 weeks)

Answers sub-questions 6, 8 and 9. With 30–50 users this shows direction, not precise rates.

- **Participants:** consumers from Phase 1 channels and at least five mechanics.
- **Instrumented use:** user time per request, time to first and to best answer, options found, purchases completed, repeat requests within 30 days.
- **Payment:** a real charge, tested as a finder's fee on a completed purchase for consumers and a monthly fee for mechanics.
- **Supplier side:** reply rates over time, complaints, and whether any yard asks to be listed or to be left alone.

**Decision:** launch in car parts, move to the mechanic segment only, change category, or stop.

### Phase 5 — Widen, only on evidence

1. **Adjacent categories with the same shape:** truck and machinery parts, tyres, appliance spare parts, building materials. One track ranks truck and machinery parts first, on judgement only.
2. **Second-hand hobby goods:** "find it for me" for a specific rod, tool or lens, using the same engine and the fair-price check.
3. **Supplier side:** a paid listing or lead product for yards, once there is buyer volume. It must stay separate from the ranking.
4. **Desktop companion** for users with their own browser agent, if the lawyer's view allows.

## Evaluation summary

| Phase | Sub-questions | Main measure | Who does it |
|---|---|---|---|
| 0 | 1, 2 | Whether existing locators already solve it | Founder |
| 1 | 2, 3, 5, 8 | By-hand fulfilment of real requests | Founder |
| 2 | 3, 4, 5, 9 | Agent against the by-hand results | Coding agent; founder; a mechanic for fitment |
| 3 | — | Working product | Coding agent |
| 4 | 6, 8, 9 | Time saved, repeat use, payment | Founder with users |

## What this methodology does not establish

- **Market size.** A 50-person study shows whether the behaviour exists, not how many share it.
- **How suppliers react at scale.** Twenty enquiries a week is not two thousand.
- **Legal clearance.** The lawyer's view is an input the experiments cannot supply.
- **Durability against Google or the locators** adding the same agent. That depends on speed and on the supplier-response data.
