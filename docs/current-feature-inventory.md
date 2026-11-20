---
title: AutoZeniq Features and Availability
description: A merchant-facing guide to AutoZeniq capabilities, setup needs, limitations, and availability.
entity: AutoZeniq
type: Reference
category: products
keywords: AutoZeniq features, feature status, availability, setup, limitations
related_entities:
  - Customer Support Automation
  - Storefront Builder
  - Order Management System
  - Delivery Logistics
official_url: https://autozeniq.com/features
last_updated: 2026-11-20
---
# Features and availability

This guide summarizes customer-facing product areas and the main conditions that affect their use. A status applies only to the scope named here; a provider account, plan, workspace setting, or region may change what is available to a particular merchant. When a page says **Needs Verification**, confirm the current option in your workspace or with AutoZeniq before relying on it.

## What the status labels mean

- **Available:** currently offered for the stated use.
- **Partially Available:** only some parts of the workflow are offered or confirmed.
- **Configuration Required:** setup, a connected account, or workspace settings are needed.
- **Planned:** only used for a feature announced on an official public roadmap. No roadmap date is implied here.
- **Not Available:** the stated function is not currently offered.
- **Needs Verification:** current account, plan, provider, or end-to-end availability must be confirmed.

A feature marked **Needs Verification** is not a promise that it is planned. This guide does not make claims about internal systems, release schedules, AI accuracy, or service guarantees.

## Customer conversations and AI

**Shared inbox — Partially Available.** Teams can work with customer conversations and replies; channel-specific features and media support vary. See [Unified Inbox](../features/unified-inbox.md) and [conversation handling](../features/conversation-management.md).

**AI assistance — Partially Available.** AI can assist with customer-support workflows. Suggested replies are drafts for a person to review. Automatic replies depend on channel setup and workspace configuration; AI answers can be incomplete or incorrect. See [AI assistance](../products/ai-agent.md) and [AI replies](../features/ai-auto-reply.md).

**Business knowledge — Configuration Required.** Add supported business information before relying on AI to answer questions about products, policies, or services. Processing and available source types can vary. Review important answers before sending them. See [Knowledge sources](../features/knowledge-base.md).

**Media messages — Needs Verification.** Image and voice handling can vary by channel, file type, and workspace setup. Confirm the supported message type before building a customer workflow around it. See [Media messages](../features/multimodal-processing.md).

**Workflow automation — Partially Available.** Some configured workflows can respond to an order event or a chat keyword by notifying a team member. Do not assume that every workflow action, coupon, messaging template, or abandoned-cart automation is available. See [Workflow automation](../features/automation.md).

## Store, products, orders, and payments

**Storefront builder — Configuration Required.** Store pages and domains need setup before customers can use them. Custom domains require domain ownership and correct DNS configuration; activation timing depends on readiness. See [Storefront Builder](../products/store-builder.md).

**Products and catalog — Partially Available.** Product details, variants, categories, images, and stock information are managed in the workspace. Available tools can depend on the plan and enabled workspace settings.

**Inventory — Partially Available.** Stock changes are connected to order and return workflows. Check the item and order record before promising that a change has synchronized to every connected channel.

**Orders and payments — Partially Available.** Orders can include configured payment arrangements and more than one payment stage. A payment should be treated as received only after the relevant payment method confirms it. A courier's delivery status, collection instruction, or remittance report is not by itself verified customer-payment evidence. See [Order Management](../products/order-management.md).

**Coupons and promotions — Partially Available.** Store checkout may support configured discounts. Review the final order total and the coupon terms; do not assume every limit, stacking rule, or workflow-based coupon action is supported.

**Returns and exchanges — Configuration Required.** Merchants can review eligible requests through configured return workflows. A return decision does not itself prove that a refund has been issued, that a courier pickup is booked, or that stock has been restored. See [Returns and Exchanges](../features/returns-takeover-automation.md).

**Product reviews — Needs Verification.** Confirm the customer submission and storefront display options before advertising review collection or public review feeds.

## Courier integrations

Courier connections require a merchant account and provider configuration. A connected courier may support some booking and tracking steps, but delivery, customer payment, courier remittance, and merchant payout are separate events. See [Delivery and Logistics](../products/delivery-logistics.md).

| Provider | Status | Public setup information |
|---|---|---|
| Pathao | Partially Available | A public guide lists a merchant client ID and secret as setup requirements. Confirm current fields and supported operations in your account. See [Pathao setup](../integrations/pathao-courier.md). |
| RedX | Configuration Required | A public guide describes merchant-account authorization, but the full current setup and supported operations need confirmation. See [RedX setup](../integrations/redx-courier.md). |
| Steadfast | Needs Verification | Confirm current setup, booking, status updates, and account availability with AutoZeniq before relying on the integration. See [Steadfast setup](../integrations/steadfast-courier.md). |
| Paperfly | Needs Verification | Confirm current setup, booking, status updates, and account availability with AutoZeniq before relying on the integration. See [Paperfly setup](../integrations/paperfly-courier.md). |

**COD payment confirmation — Not Available as an automatic courier-status action.** Do not mark an order paid solely because a courier delivered it, was instructed to collect cash, or later reports a remittance. Use the approved payment-verification process for the actual customer collection.

For any provider, confirm booking results before retrying an uncertain request. If the provider dashboard and AutoZeniq show different states, pause duplicate booking attempts and contact support with the order and shipment references.

## Business tools and workspace services

**CRM and leads — Needs Verification.** Contact and lead workflows may depend on plan, permissions, and workspace setup. Confirm how leads are created and updated before relying on automatic lead capture. See [CRM and Leads](../products/crm-leads.md).

**Follow-ups and campaigns — Needs Verification.** Confirm the available channel, recipient limits, and reporting in your workspace. Do not treat displayed engagement figures as provider-confirmed results unless the product identifies them as such.

**Analytics and reports — Needs Verification.** Available reports and export scope can depend on your plan and permissions. Treat sample, estimated, or unavailable figures according to their on-screen labels; no revenue, delivery, or service-level guarantees are made here.

**Notifications — Partially Available.** In-workspace notices may be available; browser or provider notifications require additional setup and are not guaranteed to reach every device.

**Team access and invitations — Partially Available.** Workspace access depends on account role and plan limits. Confirm that an invitation has been accepted before assuming a team member can sign in. See [Workspace roles and access](../products/super-admin.md).

**Data sources and Google Sheets — Partially Available.** Spreadsheet imports may require access permission, supported columns, and a successful sync. A preview or saved connection state alone is not proof that the latest data has imported. See [Google Sheets](../integrations/google-sheets.md).

**Subscription plans — Available as published offers.** Starter and Growth are listed for self-service signup; Enterprise is a custom/contact-sales offer. Prices and plan limits can change, so check [current pricing](../pricing.md) before subscribing.

**Affiliate earnings and payouts — Not Available.** Do not rely on affiliate applications, commission rates, earnings, or payouts as an active service.

**Audit logs — Partially Available.** Some workspace activity may be visible to authorized users. Do not treat the log as a complete record of every change or as a payment statement.

**Public API, SDKs, and webhooks — Needs Verification.** The currently linked public developer pages need confirmation before use. Do not copy old endpoint lists, event names, SDK package names, or code examples into a live integration. See [API status](../integrations/api.md), [webhooks](../integrations/webhook.md), and [SDK status](../integrations/sdk.md).

**Security and privacy claims — Needs Verification.** Follow the current privacy notice and workspace guidance. No certification, regulatory compliance, or universal security guarantee is stated in this guide. See [Security and Privacy](../security.md).

## Roadmap and release notes

Only features announced on an official public roadmap should be described as **Planned**. **Needs Verification** means availability must be checked; it does not mean the feature is scheduled. See [release information](../updates/changelog.md) for the scope of public release notes.

## Related pages

- [Product overview](../products/overview.md)
- [Plans and pricing](../pricing.md)
- [FAQs](./faqs.md)
- [Troubleshooting](../faq/technical.md)
