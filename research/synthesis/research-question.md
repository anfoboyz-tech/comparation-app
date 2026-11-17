# Research question

Revised after the third pass. The earlier question, about a fair-price check on a listing the user had already found, is kept at the end as a component.

## The question

> For an Australian who needs a specific item sold through fragmented, partly offline supply, starting with a car part, can an agent using only lawful routes cut hours of searching and phoning to under five minutes of the user's own time, and return within a working day a ranked, fitment-checked set of options at least as good as the user would have found alone?

- **"Lawful routes"** means official APIs and feeds the product is approved for, stock that suppliers publish, existing request networks, and enquiries sent to businesses by web form, email, SMS or phone. Marketplace search through the user's own desktop browser agent is an optional extra at the user's own risk, not something the product depends on.
- **"Five minutes of the user's time"** is the promise. A five-minute result is possible only for stock already listed online.

## Sub-questions and what would count as an answer

The thresholds are proposals to make each question decidable. They are judgement calls. Change them before the experiments start, not after.

| # | Sub-question | Measure | Pass | Stop and rethink |
|---|---|---|---|---|
| 1 | Do the existing locators already solve it? | 20 real part requests, including the founder's drive shaft, put through Findapart, Hollander Parts, PartsClub and WrecKonnect. Share that get a suitable, correctly fitting quote; time to first quote | Under half get a suitable quote within 4 hours | 70% or more get a suitable quote within 2 hours. Then the four hours were a discovery problem and the product is a signpost |
| 2 | Is there supply the locators miss? | For the same requests, search eBay, new-part retailers and phone yards by hand. Share of requests where the best option came from outside the locators | 30% or more | Under 10% |
| 3 | Will suppliers answer an agent? | Reply rate and time by channel (web form, email, SMS, phone) for enquiries sent on a buyer's behalf, first by hand, then by the agent with disclosure | 40% or more reply within one working day on at least one channel | Under 20% on every channel |
| 4 | Can it get the part right? | Share of requests where the agent's fitment questions and matching identify the correct part, checked against a mechanic or parts interchange data | 90% or more | Under 75%; a wrong part costs the user more than no answer |
| 5 | Is the answer as good as doing it by hand? | Best total cost found by the agent against the best found by a person spending the usual hours | Within 10% on 80% of requests | Worse on more than a third |
| 6 | Does it keep the time promise? | User's own time per request; elapsed time to a usable answer | Under 5 minutes of user time; a usable answer within one working day on 80% of requests | Over 15 minutes of user time |
| 7 | Is it lawful and tolerated? | A lawyer's view on AI enquiries to businesses under the telemarketing and spam rules; complaints from suppliers during the trial | Clearance for the enquiry wording; no more than isolated complaints | A lawyer advises against, or suppliers object in numbers |
| 8 | Who needs it often enough to pay? | Repeat requests within 30 days, by consumers and by mechanics; payments made | A segment where one in three return and some pay real money | No segment returns |
| 9 | Can it pay for itself? | Cost per request; revenue per completed purchase from referral fees, a finder's fee or subscription | Revenue per request above cost in at least one segment | No revenue line clears cost |

Sub-questions 1 and 2 need no software and should be answered first. Sub-question 1 is the one most likely to stop the project.

## Hypotheses

- **H1.** The existing locators work for common parts on common cars and fail for uncommon parts, older vehicles and phone-only yards. That tail is where the four hours go.
- **H2.** Suppliers answer a clear, specific enquiry from an agent about as often as one from a person, provided it says who it is acting for and asks for nothing but the part.
- **H3.** Getting fitment right up front, by asking the questions a wrecker would ask, removes most of the back-and-forth that makes phoning slow.
- **H4.** Mechanics return; consumers mostly do not.

## Component question: the fair-price check

The earlier question remains as the last stage of the pipeline, where the agent tells the user which option is the better buy.

> For a specific second-hand listing or quote, can a tool return the current new price, a fair used range and a buy / negotiate / skip verdict that is accurate enough to trust and that beats asking a general AI assistant?

Its measures still apply inside the larger product: new price found within 2% on 80% of items; match tier right on 80% of listings; verdict agreement of 80% with hand research; no figure that does not trace to retrieved evidence. As a standalone product it has weak evidence of demand: thirteen tools do it and none has found users.

## Out of scope for this question

- Searching Facebook Marketplace or Gumtree from the product's own servers.
- A phone app that drives the user's logged-in sessions.
- A general new-goods price comparison engine.
- Buying or paying on the user's behalf.
- Markets outside Australia.
