---
title: AutoZeniq Billing and Entitlements
description: Current subscription, plan-entitlement, payment-verification, invoice, and plan-change behavior.
entity: AutoZeniq
type: Feature
category: features
keywords: AutoZeniq billing, entitlements, subscription, usage, invoice, SSLCommerz, bKash
related_entities:
  - Pricing
  - Super Admin and Tenant Governance
official_url: https://autozeniq.com/features/billing-entitlements
last_updated: 2026-11-20
---
# Billing and Entitlements

AutoZeniq's billing area models subscription plans, versioned plan terms, feature/limit entitlements, usage, tenant overrides, payment records, and invoices. Access decisions can use the current subscription state, configured plan limits/features, usage, seats, add-ons, and tenant-specific overrides. A Redis-backed cache is used where configured; access must not be inferred from a cache design description alone.

## Public catalog and trial

The reviewed public catalog is **Starter: BDT 999/month or BDT 9,990/year**, **Growth: BDT 2,999/month or BDT 29,990/year**, and **Enterprise: custom/contact sales**. Current published limits are Starter: 1,000 messages/month, 1 team member, 2 channels; Growth: 5,000 messages/month, 5 team members, 6 channels; Enterprise limits are contract-defined. Starter and Growth are the self-serve trial/checkout plans. The default trial period is 14 days.

Use [pricing.md](../pricing.md) for the current public catalog. Do not copy older plan matrices or treat the CMS display catalog as proof that runtime entitlements have been provisioned in a particular deployment.

## Verified subscription payment paths

The reviewed default branch contains SSLCommerz BDT checkout and direct bKash tokenized subscription checkout. Payment intents are created server-side and the provider result is verified against the expected tenant, plan, cycle, currency, and exact amount before subscription activation. Callback handling and payment-ledger records use idempotency controls.

Durable invoice snapshots are linked to verified subscription/manual-payment records. The invoice service includes a recovery path for successful payments whose invoice persistence needs repair. These implementation paths do not prove that every provider or payment method appearing in a frontend list is enabled for subscriptions.

## Plan changes and manual operations

Proration can calculate a quote. An immediate upgrade is not a completed change until a compatible payment intent is available and verified. Scheduled downgrades depend on billing-provider configuration and are not universally available. Manual plan assignments in the platform control plane are administrative actions, not paid upgrades; they must not be described as payment records.

Manual/offline payment operations require their own authorization and verification workflow. Do not claim that any manual payment automatically creates a paid subscription unless the specific verified path is configured and completed.

## Storefront payment modes are separate

Tenant storefronts can configure COD-only, advance-plus-COD, full online, and partial payment modes. Advance-plus-COD requires an explicit fixed or percentage rule. Orders may be paid in stages and through multiple methods; payment status should reflect provider verification or verified courier collection, not an order status or an unverified remittance record.

The current main branch explicitly disables verified customer COD collection credit because the available courier adapters do not establish the required collection evidence. Do not claim that COD remittance automatically marks an order paid.

## Affiliate economics are disabled

Affiliate program tables and read-only views exist, but the current code hard-disables commission earning, commission approval, and payouts. The public affiliate program is closed and rates/terms are unset. Do not publish commission rates, expected earnings, approval workflows, or payout availability.

## What this page does not promise

This page does not claim an active public add-on checkout, a full-featured trial, automatic read-only trial expiration, instant upgrades, sub-millisecond response guarantees, universal no-overuse enforcement, or every UI-listed payment method. Availability depends on configuration, entitlements, provider access, and verified transactions.

## Related documents

- [Pricing](../pricing.md)
- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [Order Management](../products/order-management.md)
- [Super Admin](../products/super-admin.md)
- [Security](../security.md)
