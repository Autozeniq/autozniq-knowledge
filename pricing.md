---
title: AutoZeniq Pricing and Subscription Tiers
description: Current public BDT plan prices, catalog limits, trials, and verified subscription payment paths.
entity: AutoZeniq
type: Platform
category: company
keywords: AutoZeniq pricing, subscription plans, BDT billing, Starter, Growth, Enterprise, bKash, SSLCommerz
related_entities:
  - AutoZeniq
  - Enterprise Billing
  - Super Admin and Tenant Governance
official_url: https://autozeniq.com/pricing
last_updated: 2026-11-20
---
# AutoZeniq Pricing and Subscription Tiers

The current reviewed public catalog is stated in Bangladeshi taka (BDT). Check the [official pricing page](https://autozeniq.com/pricing) for any live catalog changes. This document is based on the catalog currently checked into the application repository; it does not confirm that a particular price or offer is active in every deployment.

## Public plans

| Plan | Monthly | Annual | Published limits |
|---|---:|---:|---|
| **Starter** | BDT 999/month | BDT 9,990/year | 1,000 messages/month, 1 team member, 2 channels |
| **Growth** | BDT 2,999/month | BDT 29,990/year | 5,000 messages/month, 5 team members, 6 channels |
| **Enterprise** | Custom | Custom | Contract-defined limits and terms; contact sales |

Starter and Growth are the self-serve signup and trial offers. The default trial period is **14 days**. Enterprise is a custom/contact-sales offer rather than a self-serve checkout plan. Plan limits are governed by the reviewed catalog and entitlement configuration; older tables in this knowledge base are not authoritative.

## Subscription billing and payments

The reviewed application code includes subscription checkout paths for **SSLCommerz in BDT** and **direct bKash tokenized checkout**. A subscription is activated only after the server verifies the provider result against the server-created payment intent, tenant, plan, billing cycle, currency, and amount. Durable invoice snapshots are linked to verified subscription/manual payment records, with a recovery path for persisted invoices.

Do not assume every provider or method displayed elsewhere is enabled for every subscription flow. In particular, UI labels for Nagad, Rocket/Upay, card brands, or bank transfer are not by themselves evidence of an active self-serve subscription checkout path.

## Entitlements and plan changes

Plan access is evaluated using the subscription, plan features/limits, usage, team seats, tenant overrides, and configured add-ons. Add-on data structures do not prove that a public add-on purchase flow is available.

Proration can produce a plan-change quote. An immediate upgrade is not complete until the corresponding payment intent has been verified and settled. Scheduled downgrade behavior is limited by billing-provider configuration; do not promise frictionless or immediate plan changes based on the quote alone.

## Commerce checkout is separate

Merchant storefront payment modes are configured separately from a merchant's AutoZeniq subscription. Available mode settings include COD-only, advance-plus-COD, full online payment, and partial payment. Advance-plus-COD requires an explicit fixed amount or percentage rule. A storefront order may be paid in multiple stages and by different methods; order or courier status alone is not proof of settlement.

Verified customer COD collection credit is currently unavailable in the reviewed default-branch implementation. Courier remittance records must not be represented as verified customer payment.

## Affiliate program

The public affiliate program is currently closed. Applications are not accepted, commission rates and payout terms are unset, and affiliate earning, commission approval, and payouts are disabled pending explicit authorization. No commission or earnings estimate is published here.

## FAQ

### Is Enterprise available through self-serve checkout?
No. Enterprise is a custom/contact-sales offer in the reviewed public catalog.

### Can I upgrade in the middle of a billing period?
The system can calculate a proration quote, but an immediate upgrade depends on a verified payment-settlement flow. Do not treat the quote as a completed paid plan change.

### Does this page list every payment method supported by every AutoZeniq product?
No. Subscription-provider paths and merchant storefront payment modes are different. Provider, currency, account approval, and deployment configuration can affect availability.

## Related documents

- [Billing and Entitlements](./features/billing-entitlements.md)
- [Current Feature Inventory](./docs/current-feature-inventory.md)
- [Storefront Builder](./products/store-builder.md)
- [Order Management](./products/order-management.md)
- [Super Admin](./products/super-admin.md)
