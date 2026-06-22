# Ketan Mehta — Technical Writer 

**Developer and product documentation for complex, regulated fintech and payments platforms.**

San Francisco Bay Area · [kmehta853@gmail.com](mailto:kmehta853@gmail.com) · [LinkedIn](https://www.linkedin.com/in/ketan-mehta-39598963/) · [GitHub](https://github.com/mettakite)

---

I'm a technical writer with eight years of experience producing developer and product documentation for API-first payments platforms. I've been the **sole documentation owner** — a writing team of one — for two regulated fintech products, [Finix](https://finix.com) and [Nium](https://nium.com), including ownership of their documentation and OpenAPI specifications. 

My focus is turning intricate, end-to-end product behavior — onboarding, payments, payouts, settlements, cross-border FX, compliance — into precise, structured documentation that developers and internal teams can actually follow.

## Approach

- **Whole workflows**: I document complete flows end to end — each state change, webhook, and handoff — rather than isolated features, since the gaps between steps are where integrations break.
- **Verified against the product**: I write from the live product and QA/dev environments, so the documentation matches how the platform actually behaves.
- **OpenAPI as a core deliverable**: I author and maintain the spec itself — endpoint descriptions, fields, enums, and code samples samples that make it usable.
- **Docs-as-code**: Git-based authoring in Markdown/MDX, published through Redocly, Docusaurus, and Vercel pipelines.
- **Quality tooling**: I build automation (see my Docs Drift Script) to surface documentation drift at scale, with review kept human-led.

## Featured work

### Finix — Senior Technical Writer · *sole documentation owner* (2022–2024)

API-first payments platform for software companies. I was sole technical writer and the sole owner of developer documentation.

**Stack:** Redocly developer portal · MDX · docs-as-code · OpenAPI

Documentation I wrote and owned in this role includes:

- **Payment Lifecycle**: An end-to-end walkthrough of a payment from buyer request → `Authorization` → capture → `Transfer` → `Settlement`, mapping each state change to its webhook and dashboard view. A clear example of full-workflow documentation rather than feature-by-feature reference.
- **Onboarding with the Finix API**: A precise, step-by-step walkthrough on how to onboard a merchant: collecting the merchant's information and consent, creating an `Identity` for the merchant, adding associated owners with 25%+ ownership, adding a bank account, and verifying the merchant — the kind of gap-free, compliance-sensitive flow that has to be exactly right.
- **Merchant payouts & settlements**: Approving settlements, managing payouts, collecting fees, and batch-settlement workflows.
- **Developer reference**: Webhooks and event types, errors and failure codes, API keys, user roles, rate limits, idempotency, and versioning.
- **Platform guides**: Platform onboarding checklist and quick-start guides for software platforms building on Finix.
- **OpenAPI specification**: Endpoint descriptions, request/response fields, enums, and examples, with tags and endpoint groups mapped into the portal's navigation.

*Excerpts from several of these pages are in [Writing Samples](./writing-samples.md). Full articles available on request.*

### Nium — Senior Technical Writer · *sole documentation owner* (2024–2026)

Global cross-border payments platform. Migrated the entire documentation set from ReadMe to a GitHub/Vercel docs-as-code platform.

**Stack:** Docusaurus · Vercel · MDX · OpenAPI

Documentation I wrote and owned in this role includes:

- **Global onboarding & KYC**: Region-specific onboarding (UK, Europe), individual and business customer lifecycles, required documents, and Verification of Payee (VoP) guidelines.
- **Payouts**: Transfer money, beneficiaries, bulk payouts, and payout tracking, plus payins, wallets, and cards.
- **Cross-border money movement**: Foreign exchange, open banking, transactions, reports, and fees and limits across a global payments network.
- **Release notes**: Authored 50+ changelog entries keeping developers current with a fast-moving platform.
- **OpenAPI specification**: Endpoint descriptions, usage explanations, hyperlinks to guides, and code samples.
- **Platform migration**: Moved documentation and OpenAPI content from ReadMe to a GitHub/Vercel docs-as-code system, improving version control, publishing workflows, and long-term maintainability.

*Excerpts from several of these pages are in [Writing Samples](./writing-samples.md). Full articles available on request.*

### Docs Drift Script — documentation QA tooling

[github.com/mettakite/Docs-Drift-Script](https://github.com/mettakite/Docs-Drift-Script)

A Python workflow that compares OpenAPI specifications against Markdown documentation to surface stale references, missing coverage, and source-content gaps. Its first run flagged **500+ potential inconsistencies across roughly 300 articles**, giving writers, engineers, and product teams a shared, prioritized review list. Built with AI tools (ChatGPT, Claude Code, GitHub Copilot) as development aids, while keeping human validation in mind.

## Toolbox

| | |
|---|---|
| **Documentation** | Developer & API docs · end-to-end workflow & process docs · step-by-step guides · reference docs · release notes · structured authoring · content QA & governance |
| **Domains** | Payments · cross-border / FX · onboarding & KYC · compliance & regulated workflows · platform integrations · open banking |
| **Docs-as-code & tooling** | Markdown / MDX · Git / GitHub · OpenAPI / Swagger · Redocly · Docusaurus · ReadMe · Vercel · Postman · Jira · VS Code |
| **AI-assisted docs** | ChatGPT · Claude · Claude Code · GitHub Copilot — AI-assisted QA, governance, and drift detection (human-in-the-loop) |

## Selected samples

For curated excerpts of documentation I wrote and solely owned — see **[Selected Writing Samples](./writing-samples.md)**:

- **[Payment Lifecycle (Finix)](./writing-samples.md#1-payment-lifecycle--finix)** -end-to-end workflow from buyer request to merchant payout
- **[Onboarding with the Finix API (Finix)](./writing-samples.md#2-onboarding-with-the-finix-api--finix)** — precise, compliance-sensitive steps with consent capture
- **[Key Concepts (Nium)](./writing-samples.md#3-key-concepts--nium)** — explaining complex global payments infrastructure clearly
- **[Payouts (Nium)](./writing-samples.md#4-payouts--nium)** — audience-aware orientation to a global payouts product

Full pages available to walk through on request.

## About

I started in high-touch customer support — Tier 3 and executive escalations at Fitbit — and moved into technical writing because I kept seeing the same pattern: good support, good integrations, and good customer trust all depend on accurate source documentation. Across Fitbit, Hustle, Finix, and Nium I've helped customers and internal teams understand complex products and fixed the systems that cause people to get stuck.

📫 [kmehta853@gmail.com](mailto:kmehta853@gmail.com) · [LinkedIn](https://www.linkedin.com/in/ketan-mehta-39598963/) · [GitHub](https://github.com/mettakite)
