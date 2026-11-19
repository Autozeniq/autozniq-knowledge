---
title: AutoZeniq Storefront Builder
description: Tenant store editing, themes, preview and publishing, domain readiness, public rendering, and tracking.
entity: AutoZeniq
type: Product
category: products
keywords: AutoZeniq store builder, storefront, page editor, theme, custom domain, checkout
related_entities:
  - Commerce Automation
  - Order Management System
  - Delivery Logistics
official_url: https://autozeniq.com/products/store-builder
last_updated: 2026-11-20
---
# AutoZeniq Storefront Builder

The Storefront Builder is the tenant-managed surface for editing store settings and pages, previewing drafts, publishing, and reviewing or rolling back versions. The public storefront runtime resolves a managed subdomain or custom domain, retrieves published page data, and renders configured layout and SEO metadata.

## Editing and themes

The reviewed dashboard/backend paths include store and page settings, page CRUD, draft saves, preview tokens, publishing, version history, rollback, navigation, assets, and page settings. Three checked-in default theme blueprints are named `modern`, `elegant`, and `minimal`. Older references to four named theme blueprints do not match the current defaults.

The storefront supports product/category pages, cart, order tracking, delivery quotes, configured payment modes, coupon validation, checkout, and order submission. Feature availability may depend on plan and configuration.

## Domains

Managed subdomains and custom domains are supported in the codebase. Custom-domain routing is readiness-gated: domain ownership evidence, DNS configuration, TLS state, and a fresh verification check are required. Readiness is periodically revalidated; stale or failed checks can disable routing. Do not promise automatic SSL issuance or instant custom-domain activation without deployment evidence.

## Tracking and privacy

Store tracking can be configured for Meta, Google, and TikTok with browser/server modes, event preferences, and consent controls. Analytics, advertising, and matching are distinct purposes; optional purposes start denied. Server delivery checks consent and store scope and can suppress queued events after consent withdrawal or expiry. Dashboard acknowledgement is not proof that a provider processed or reported the event.

## CMS and public content

The backend provides public read APIs for a broad set of CMS content, including pricing, FAQs, features, blog, documentation, and related records. The inspected admin write routes are narrower and cover settings, blog, pricing, and FAQ operations; the complete multi-screen admin surface in the technical design document is not established by current code.

Some public pages use local/static fallback data, and legacy API routes return mock data. Content freshness therefore depends on the particular page path and CMS revalidation configuration. Do not claim that every public page is fully database-backed or updates instantly.

## Related documents

- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [Order Management](./order-management.md)
- [Pricing](../pricing.md)
- [System Architecture](../docs/system-architecture.md)
- [Security and Privacy](../security.md)
