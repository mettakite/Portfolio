# Selected Writing Samples — Ketan Mehta

These are excerpts from developer and product documentation I wrote and as the only technical writer at **Finix** and **Nium**, two API-first payments platforms. They're representative samples — trimmed for length, with internal links, images, and example credentials removed. I'm happy to walk through the full pages on request.

[← Back to portfolio](./README.md)

---

## Payment Lifecycle — Finix

*End-to-end workflow documentation (not a feature summary)*

**Focus:** Documenting a complete, multi-system flow — from the buyer's first request to the merchant's payout — including state changes, webhooks, and dashboard touchpoints at each step.

> Most transactions in Finix follow a similar pattern:
>
> 1. The buyer requests to make a payment with the merchant.
> 2. The platform collects the buyer's information and creates an `Identity` to represent the buyer in Finix.
> 3. The platform collects the buyer's payment information and creates a `Payment Instrument` to represent the payment method. Once created, Finix notifies the merchant with a webhook (sent when a `Payment Instrument` is created from a bank account, debit, or credit card) and an entry on the **Payment Instruments** tab of the Finix Dashboard.
> 4. The platform creates an `Authorization` to reserve funds on the `Payment Instrument`, to be captured (debited) at a later date — usually within seven days.
> 5. If the `Authorization` succeeds, `Authorization#state` updates to **SUCCEEDED** and `Authorization#expires_at` is set with a timestamp. If it fails, `state` updates to **FAILED**, and the platform must submit the `Authorization` again.
> 6. The platform captures the `Authorization`. A webhook is sent when the `Authorization` is captured, and the Dashboard entry updates.
>
> *…the guide continues through the `Transfer`, the `ready_to_settle_at` timestamp, `Settlement` approval, and the funding `Transfer` that pays the merchant's bank account in 5–7 business days.*

Each step ties an API action to the resource state it changes, the webhook it fires, and where it surfaces in the dashboard — so a developer can build correct monitoring and reconciliation around it.

---

## Onboarding with the Finix API — Finix

*Precise, gap-free steps in a compliance-sensitive flow*

**Focus:** Documenting regulated merchant onboarding with exact required language, explicit consent capture, and a clean field reference.

> Onboarding with the API follows the same flow regardless of the business type:
>
> 1. Collect information and consent for Finix's Terms of Service.
> 2. Create an `Identity`.
> 3. Add Associated Identities for owners with 25%+ ownership.
> 4. Add a bank account.
> 5. Verify the `Identity`.
>
> **Showing the Finix Terms of Service**
>
> You must present your merchants a link to the Finix Terms of Service. The merchant must explicitly consent to the Terms of Service before you submit the Merchant `Identity` and identifying information to Finix.
>
> You indicate that you received the merchant's consent by providing the following fields when you create an `Identity`:
>
> | Field | Type | Description |
> |---|---|---|
> | `merchant_agreement_accepted` | *boolean*, **required** | Whether the merchant has accepted the Finix Terms of Service. |
> | `merchant_agreement_ip_address` | *string*, **required** | IP address of the merchant when they accepted the Terms of Service. |
> | `merchant_agreement_timestamp` | *string*, **required** | Timestamp of when the merchant accepted the Terms of Service. |
> | `merchant_agreement_user_agent` | *string*, **required** | The browser user agent when the merchant accepted the Terms of Service. |

In a regulated flow, the exact consent wording and the captured audit fields aren't optional details — they're the documentation. This page specifies both precisely.

---

## Key Concepts — Nium

*Making complex global infrastructure clear*

**Focus:** Explaining a multi-entity, multi-currency global platform (clients → customers → wallets → virtual account numbers) in plain, structured language a new integrator can follow.

> Nium is a flexible, comprehensive, and easy-to-embed fintech infrastructure platform. Companies use Nium to launch and manage their payment platforms, with features including:
>
> - Domestic or cross-border transfers
> - Holding balances in multicurrency wallets
> - Card issuing
> - Receiving multiple currencies into a single wallet locally — for example, receiving GBP in the UK using the Faster Payments Service (FPS) or the Clearing House Automated Payment System (CHAPS)
>
> **Multicurrency wallets**
>
> Every customer or account holder gets a multicurrency wallet. Because a wallet is considered an account, the terms *wallet* and *account* are used interchangeably. A wallet holds one or as many currencies as are configured for the platform client.
>
> **Virtual account numbers**
>
> Based on the product configuration, the platform automatically assigns virtual account numbers (VANs) at the wallet-currency level. For example, if a VAN for SGD from Nium's Singapore bank partner needs to be assigned, the platform allocates an SGD VAN when the wallet is created and maps it to the wallet's SGD currency — letting the account holder fund SGD using local bank rails such as Singapore's Fast And Secure Transfers (FAST) service.

Spelling out acronyms on first use, defining terms as they appear, and grounding abstract concepts in concrete examples keeps a dense, infrastructure-heavy topic readable.

---

## Payouts — Nium

*Audience-aware orientation to a broad capability*

**Focus:** Giving both developers and non-technical operators a fast, accurate mental model of a global payouts product before they dive into specifics.

> Nium Payouts lets you send money to over **190 countries** and make real-time, on-demand payments in more than **100 countries**. Funds move from source to destination during the transaction, automatically routed and settled in real time.
>
> Supported transaction types include:
>
> - **Individual to Individual (P2P)**
> - **Corporate to Individual (B2P)**
> - **Corporate to Corporate (B2B)**
> - **Individual to Corporate (P2B)**
>
> Payouts can be delivered to a beneficiary's **bank account, card, digital wallet**, or — in some countries — through **cash pickup**.
>
> **Sending payouts** — Nium offers several methods depending on your team's setup:
>
> - **API integration** — *Best for technical teams, payroll platforms, and large banks.* Integrate directly with Nium's APIs to automate and scale high-volume payouts.
> - **Nium Portal** — *Best for small businesses and teams without developers.* Create single or batch payouts from a browser without writing code.

The "Best for" framing routes each reader to the right path immediately, instead of making them infer which integration method fits their team.