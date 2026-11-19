---
title: AutoZeniq Product and Technical FAQs
description: Frequently asked questions answered against the reviewed application source, with availability and payment caveats.
entity: AutoZeniq
type: Documentation
category: general
keywords: AutoZeniq FAQ, commerce, storefront, AI, Google Sheets, courier, payments
official_url: https://autozeniq.com/faq
last_updated: 2026-11-20
---

# AutoZeniq Product and Technical FAQs

These answers describe code reviewed on the application repository's `main` branch. Production access can depend on provider approval, tenant configuration, permissions, entitlements, and deployment.

### What does AutoZeniq include?

The reviewed product includes tenant workspaces, a shared inbox, AI assistance and knowledge retrieval, catalog and order workflows, a store builder, CRM tools, courier integrations, and selected automation and administration functions. See the [current feature inventory](./current-feature-inventory.md) for status and limitations.

### Does a merchant need Shopify or WooCommerce?

The reviewed source includes a native product catalog and storefront/checkout paths. It does not establish a general Shopify or WooCommerce synchronization integration. Custom-domain routing requires domain ownership, DNS, and TLS readiness; code in the repository does not prove that a particular store is deployed.

### How does Google Sheets synchronization work?

The backend contains a scheduled, queued, primarily pull-oriented flow for ingesting spreadsheet data, including eligible product and inventory updates. Some add-source wizard checks and previews are simulated. A working provider connection, saved credentials, configured schedule, and successful sync job must be confirmed before describing a sheet as connected or live.

### Does courier COD settlement mark an order paid?

No. The system has courier COD remittance and settlement records, but the reviewed `main` explicitly disables verified customer COD collection credit. A courier settlement record is not proof that a customer payment was verified and must not be described as automatically marking an order paid.

### Which courier integrations are present?

The reviewed application contains Pathao, Paperfly, RedX, and Steadfast adapters and related booking/tracking paths. Actual operation depends on provider credentials, approval, workspace settings, and deployment. An adapter in source is not proof that the merchant's account is connected.

### Does AutoZeniq AI guarantee correct answers?

No. Retrieval and guardrails can help constrain an answer using available context, but the reviewed source does not establish zero hallucinations or a fixed accuracy rate. AI Copilot reply suggestions are drafts for an agent to review; guarded automatic-response paths depend on configuration and channel setup.

### What are the current subscription plans?

See [Pricing and subscriptions](../pricing.md) for the current public catalog and limits. Do not reuse older plan matrices or infer that every listed payment method is available for every subscription flow.

### Where can I find more implementation detail?

See the [system architecture](./system-architecture.md), [security and privacy](../security.md), [order management](../products/order-management.md), and [delivery and logistics](../products/delivery-logistics.md) pages.
