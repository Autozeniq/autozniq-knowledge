---
title: AutoZeniq Products Overview
description: Status-qualified overview of AutoZeniq support, AI, commerce, CRM, delivery, and platform administration.
entity: AutoZeniq
type: Platform
category: product
keywords: AutoZeniq products, storefront, order management, delivery, CRM, AI support, commerce
related_entities:
  - Storefront Builder
  - Order Management System
  - Delivery Logistics
  - AI Agent
  - Customer Support Automation
official_url: https://autozeniq.com/features
last_updated: 2026-11-20
---
# AutoZeniq Products Overview

AutoZeniq brings customer-support and commerce workflows into a multi-tenant workspace. The current application source includes a shared inbox, guarded AI assistance, tenant knowledge and retrieval, CRM and lead tools, product/inventory management, storefront checkout, order and delivery workflows, integrations, and platform administration.

The [Current Feature Inventory](../docs/current-feature-inventory.md) distinguishes current `main` code from partial/simulated flows, disabled actions, and unverified claims. Repository evidence is not proof of production deployment, provider approval, or general availability.

## Product areas

### [Storefront Builder](./store-builder.md)
Manage storefront pages and settings, preview drafts, publish changes, review versions, configure navigation, and use the reviewed `modern`, `elegant`, and `minimal` base themes. Managed subdomains and custom-domain routing depend on domain readiness checks. The storefront supports product/category pages, cart and checkout, delivery quotes, coupons, and order tracking.

### [Order Management](./order-management.md)
Create and manage tenant orders through validated states, with item/payment/timeline records, inventory workflows, configurable payment modes, and order submission safeguards. A courier remittance record does not by itself verify customer payment.

### [Delivery & Logistics](./delivery-logistics.md)
The codebase includes Pathao, Paperfly, RedX, and Steadfast adapters, consignment booking, tracking, conditional auto-booking, COD remittance records, and fraud scoring. Verified customer COD collection credit is currently unavailable in the reviewed implementation. Some delivery analytics are sample data.

### [CRM & Leads](./crm-leads.md)
Manage contacts and leads, assign work, maintain deals and pipelines, schedule follow-ups, and queue campaigns. Current default pipeline stages are New Lead, Contacted, Qualified, Proposal Sent, and Negotiation. Campaign read/reply figures shown in the UI are not provider-measured analytics.

### [AI and customer support](./ai-agent.md)
Use a tenant-scoped inbox, human replies, assignment, and AI takeover controls alongside knowledge-grounded AI assistance, rules, and agent suggestions. Copilot suggestions are drafts and are not sent automatically. Channel support and AI behavior depend on entitlements and configuration.

### [Knowledge and data sources](../features/knowledge-base.md)
Ingest supported files for background indexing and retrieval. Google Sheets synchronization is primarily pull-oriented; parts of the add-source UI are simulated. See [Google Sheets Sync](../features/google-sheets-sync.md).

### [Billing and entitlements](../features/billing-entitlements.md)
The reviewed public catalog has Starter, Growth, and Enterprise options. Subscription payment verification, tenant commerce payment modes, staged order payments, invoice records, and disabled affiliate economics are distinct workflows. See [Pricing](../pricing.md).

### [Super Admin](./super-admin.md)
Platform administrators have tenant governance and selected operational controls. Authentication and authorization use shared account handling with current database-backed roles; older claims of separate admin login or mandatory 2FA are not verified.

## Important boundaries

- Feature availability may depend on tenant entitlement, plan, provider credentials, account approval, configuration, and deployment.
- A design document, feature-key constant, UI screen, sample chart, or remote branch alone does not prove an enabled end-to-end feature.
- Do not publish unverified accuracy, latency, cost, conversion, customer/revenue, compliance, uptime, or SLA figures as measured facts.

## Related documents

- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [Capabilities](../capabilities.md)
- [Pricing](../pricing.md)
- [System Architecture](../docs/system-architecture.md)
