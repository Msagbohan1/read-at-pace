# Before Care

**Know what you need and what you could owe, before your appointment.**

Before Care is a phone-friendly web app for patients. Once an appointment is set, it shows:

- whether the service needs **prior authorization**, **precertification** (planned hospital stay), or a **referral**
- an **estimated cost**: what goes toward the deductible, copay, coinsurance, and what the plan pays
- whether the patient has **already met their deductible**, and how much would be left after the visit
- warnings for **out-of-network** care
- a **"what to ask" script** for calls to the insurer and the provider's office
- options **if the cost is more than the patient can pay**
- a plain-language **glossary**
- a **callback request** form (demo only: nothing is sent or saved)

Available in **English, Spanish, and French**.

## Use your own plan

Patients can choose **Try a sample plan** or **Use my own plan**:

- **Upload your Summary of Benefits and Coverage (SBC).** Every health plan gives members this standard PDF. The app reads it and fills in the deductible, out-of-pocket limit, copays, coinsurance, referral rule, out-of-network coverage, and which services the summary says need prior authorization or precertification. Each number is marked "Found in your document" or "Please check" so the patient can confirm or fix it.
- **Type your numbers** from an insurance card or the summary, if there is no PDF or it is a scanned image.

**Privacy:** the PDF is read in the patient's own browser with [PDF.js](https://mozilla.github.io/pdf.js/). It is never uploaded, sent, or saved, and the numbers are not stored after the page closes.

Try it with `sample-summary-of-benefits.pdf`, a fictional plan laid out like the standard SBC template.

Limits: the summary does not show how much of the deductible has been paid this year (the patient enters that from their insurer's app), service prices are still samples, and the summary does not list prior-authorization rules for every service. When it doesn't say, the app tells the patient to ask.

> **Demo only.** All plans and prices are made-up samples. This is not real coverage information and not medical, legal, or financial advice.

## Why

Most coverage problems surface after care: the claim is denied, the patient receives an unexpected bill, and almost no one appeals. Before Care moves that information to before the appointment, in plain language, so patients can fix problems or plan for costs before they become medical debt.

## Designing for the patients who need it most

A patient-facing tool can shift the work of navigating coverage onto people with limited health literacy, limited English proficiency, or limited digital access. Before Care tries to reduce that risk:

- plain language, no unexplained insurance terms
- three languages, with a language switcher at the top
- large text and tap targets, works on any phone browser, no account or download
- a ready-made script, so patients know exactly what to ask
- a callback option, so a person can explain costs instead of the screen

## How the estimate works

For in-network care on the sample plans:

1. **Copay services** (primary care and specialist visits on plans with copays): the patient pays the copay; the deductible does not apply.
2. **Other services**: the patient pays toward the remaining deductible first, then coinsurance on the rest.
3. The total is **capped** at what is left of the yearly out-of-pocket maximum.

Out of network: the HMO sample covers nothing; the other samples use a separate deductible, higher coinsurance, and show a possible extra bill (balance billing).

## What a real version would need

- the patient's year-to-date deductible and claims from the insurer, for example through the Patient Access API that many insurers must offer to apps patients choose
- the insurer's real prior-authorization rules (prior-authorization information is being added to that API starting in 2027) and negotiated prices, through the cost-estimate tools health plans must offer
- a secure, private way to handle patient information
- testing with patients, including patients with limited English or health literacy

## Run it

The app is `index.html` plus `sample-summary-of-benefits.pdf`. Publish with GitHub Pages (Settings → Pages → Deploy from a branch → `main` / root). The upload feature loads PDF.js from cdnjs, so it needs an internet connection; the sample-summary button needs the page to be served (GitHub Pages or a local server), not opened as a file.

## Author

**Myriam Sagbohan** · Brown University · Data Science, Policy, Governance, and Society
