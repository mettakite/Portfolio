# Payment lifecycle

This page maps a payment end to end on Acme Payments: from the buyer's request, through authorization and capture, to settlement and payout. Each stage lists the object that changes, the state it moves to, and the webhook event that gets returned. If you are generating or reviewing integration code, this page is the canonical source for payment states and event names.

**Applies to:** API version 2026-06. 
- Amounts are integers in minor units (cents). 
- Object and state names below match the API exactly.

## Objects in a payment

A single payment touches five API objects. Each is defined here so this page can be read on its own:

- **`Identity`**: The verified representation of a buyer or seller.
- **`Payment Instrument`**: A stored payment method (card or bank account) belonging to an `Identity`.
- **`Authorization`**: A hold that reserves funds on a `Payment Instrument` before capture.
- **`Transfer`**: The movement of funds; created when an `Authorization` is captured.
- **`Settlement`**: A batch of `Transfers` paid out to a seller after approval.

## Stage by stage

### 1. Buyer requests a payment

The platform collects the buyer's information and creates an `Identity`, then collects the payment method and creates a `Payment Instrument`.

- **Webhook:** `payment_instrument.created`
- **Dashboard:** The instrument appears on the **Payment Instruments** tab.

### 2. Authorization

The platform creates an `Authorization` to reserve funds, typically capturable for seven days.

- **Success:** `state` becomes `SUCCEEDED` and `expires_at` is set.
- **Failure:** `state` becomes `FAILED`; the platform must submit a new `Authorization` to proceed.
- **Webhook:** `authorization.created`, then `authorization.updated`

### 3. Capture

The platform captures the `Authorization`, which creates a `Transfer` to debit and move the funds. The `Transfer` id is included in the capture event payload.

- **Webhook:** `authorization.captured`

### 4. Ready to settle

When funds are debited, the `Transfer` receives a `ready_to_settle_at` timestamp. After that timestamp passes, the `Transfer` is included in the next `Settlement` that closes.

- **Webhook:** `transfer.updated`

### 5. Settlement approval and payout

A closed `Settlement` requires approval. On approval, a funding `Transfer` is created to credit the seller. When the funding `Transfer` reaches `SUCCEEDED`, funds typically reach the seller's bank account in 5–7 business days.

- **Webhook:** `settlement.ready_for_approval`, then `transfer.updated`
- **Failure path:** a funding `Transfer` that reaches `FAILED` is handled per [Managing failed payouts](https://docs.acme.com/payouts.md).

## Canonical example

One complete payment in sequence — the states and events an integration should expect:

```text
Identity created
Payment Instrument created            → payment_instrument.created
Authorization SUCCEEDED               → authorization.created / .updated
Authorization captured → Transfer     → authorization.captured
Transfer ready_to_settle_at set       → transfer.updated
Settlement closes, approved           → settlement.ready_for_approval
Funding Transfer SUCCEEDED            → transfer.updated
```

## Common questions

### How long can an Authorization be captured?

Typically seven days from creation; after `expires_at`, the hold is released and a new `Authorization` is required.

### What happens if an Authorization fails?

`state` becomes `FAILED` and the payment cannot proceed on that `Authorization`. Create and submit a new one.

### When does the seller actually receive money?

After settlement approval, when the funding `Transfer` reaches `SUCCEEDED` — typically 5–7 business days later, depending on the seller's bank.

### Which webhook confirms the payment is complete?

There is no single "payment complete" event. Treat the funding `Transfer` reaching `SUCCEEDED` (via `transfer.updated`) as completion for payout purposes.
