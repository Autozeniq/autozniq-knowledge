---
title: AutoZeniq Capabilities and Boundaries
description: Evidence-based overview of current AutoZeniq product capabilities, limitations, and availability dependencies.
entity: AutoZeniq
type: Platform
category: features
keywords: AutoZeniq capabilities, current features, implementation status, commerce automation, support, storefront
related_entities:
  - AI Agent
  - Commerce Automation
  - Customer Support Automation
  - Storefront Builder
  - Order Management System
  - Delivery Logistics
official_url: https://autozeniq.com/features
last_updated: 2026-11-20
---
# AutoZeniq Capabilities

This page summarizes important product capabilities based on the application repository's default branch. It describes code paths and tests, not a deployment guarantee. Real availability can depend on plan entitlements, workspace settings, migrations, credentials, provider account approvals, and production configuration. The [Current Feature Inventory](./docs/current-feature-inventory.md) provides detailed status and documentation corrections.

## Customer support and AI

- A tenant-scoped shared inbox provides conversation lists, message history, human replies, assignment, and AI pause/takeover/resume controls.
- AI Copilot can draft suggestions for a human agent; suggestions are not automatically sent.
- Guarded AI auto-reply, configurable AI settings/rules, and an AI playground are present. Auto-reply depends on entitlements, supported channels, available models, and configuration.
- Image and voice processing paths are available subject to file validation, quotas, configuration, and plan access.
- Some channel-specific capabilities vary. The reviewed code does not establish universal typing/presence/read receipts, internal notes, ticketing, or automated team routing.

## Knowledge and automation

- Tenant-authorized PDF, DOC/DOCX, CSV, JSON, and text sources can be parsed and indexed in background jobs.
- Knowledge retrieval combines semantic vector search and keyword search. Conversational retrieval can expand/rewrite queries, rank sources, and detect possible conflicts.
- Google Sheets processing can classify tabs, map common English and Bengali headers, update product/inventory data, and report progress. Verified behavior is primarily pull-oriented; parts of the add-source UI are simulated.
- Workflow graphs can be saved, validated, published, and queued. Verified triggers include `order_placed` and `chat_keyword`; `notify_agent` is the executable action found in the reviewed path. Unsupported actions fail closed.

## Storefront, products, orders, and inventory

- Product tools manage tenant-scoped products, variants, categories, images, stock fields, publication state, and bulk operations.
- Inventory workflows distinguish reservation, deduction, release, adjustment, and eligible restocking.
- The storefront supports product/category pages, cart and checkout, delivery quotes, customer/shipping details, configured payment modes, coupon validation, order submission, and public tracking.
- Order records include validated status transitions and related item/payment/timeline records. Reviews require signed purchase verification and a delivered order. Merchants can manage eligible return/exchange requests.
- The store builder provides page editing, draft preview, publishing, version history, navigation, themes, and domain management. The reviewed default themes are `modern`, `elegant`, and `minimal`.
- Custom domains route only when ownership, DNS, TLS, and freshness checks pass.

## Payments, delivery, and CRM

- Current public plans are Starter (BDT 999/month or BDT 9,990/year), Growth (BDT 2,999/month or BDT 29,990/year), and Enterprise (custom/contact sales). See [Pricing](./pricing.md) for the exact reviewed catalog.
- Subscription checkout paths include SSLCommerz in BDT and direct bKash tokenized checkout, with server-side provider verification. Immediate upgrades require verified payment settlement; proration can provide a quote.
- Store checkout supports COD-only, advance-plus-COD, full online, and partial payment modes when configured. Verified customer COD collection credit is currently unavailable on the reviewed default branch; courier remittance is not payment proof.
- Delivery paths include Pathao, Paperfly, RedX, and Steadfast booking/tracking, conditional auto-booking, and courier remittance records. The delivery analytics page includes sample data and should not be read as live performance reporting.
- CRM includes contacts, leads, assignment, pipelines/deals, activities, work queue, scheduled follow-ups, and queued campaigns. Default pipeline stages are New Lead, Contacted, Qualified, Proposal Sent, and Negotiation.
- Affiliate applications are closed, terms/rates are unset, and earning, approval, and payout actions are disabled.

## Integrations, security, and operations

- Provider connections/OAuth exist for supported messaging channels; API access uses scoped developer keys. API key plaintext is shown once and stored as a bcrypt hash. Website widgets use separate public keys and can enforce allowed domains.
- Outgoing webhooks have endpoint, delivery-history, and replay paths. Secret API keys should never be placed in browser code.
- Store tracking separates analytics, advertising, and matching consent; optional purposes default to denied. Invalid, stale, expired, or withdrawn consent can suppress queued event delivery. Tracking retention is 90 days.
- Scoped controls include live workspace authorization, encrypted integration credentials, webhook signatures, AI input/output guardrails, public API/widget rate controls, and fail-closed production configuration.
- PostgreSQL/pgvector and Redis are used with selected BullMQ background processors. Processors are registered in the backend application; a separate worker service is not established by the reviewed Compose file. Storage supports R2 when configured and local persistent fallback.
- Production deployment is manually dispatched from `main` after migration/compatibility checks. Runtime validation rejects weak or missing production configuration; database rollback is not automatic.

## Claims not established by repository evidence

Do not present unverified statements as shipped or guaranteed capabilities. The reviewed source does not substantiate universal typing/read receipts, internal notes, ticketing, arbitrary automation actions, full bidirectional Sheets order sync, all advertised SDK packages, immediate plan upgrades, verified COD payment credit, live delivery sample charts, universal tenant isolation claims, a universal public rate limit, zero-hallucination or fixed accuracy/latency outcomes, SOC 2/HIPAA certification, data residency, or an SLA. See the [Current Feature Inventory](./docs/current-feature-inventory.md) for status details.

## Related documents

- [Products Overview](./products/overview.md)
- [Current Feature Inventory](./docs/current-feature-inventory.md)
- [Pricing](./pricing.md)
- [System Architecture](./docs/system-architecture.md)
- [Security](./security.md)
