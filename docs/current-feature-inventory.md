---
title: AutoZeniq Current Feature Inventory and Status
description: Source-verified inventory of product areas, implementation status, limits, and documentation corrections.
entity: AutoZeniq
type: Reference
category: products
keywords: AutoZeniq features, implementation status, feature inventory, current product, release status
related_entities:
  - AutoZeniq
  - Commerce Automation
  - Customer Support Automation
  - Storefront Builder
  - Order Management System
  - Delivery Logistics
authority: Reviewed against application main and knowledge main
source_commit: 0002f9abd36022b8aef9d85d42c02b92a4311e89
last_updated: 2026-11-20
---
# AutoZeniq: Current Feature Inventory

This is the consolidated, source-checked inventory of important AutoZeniq product and platform capabilities. It records what is present in the application repository's `main` branch and where older knowledge pages needed correction. A feature in source code or a test is **not** proof that it is enabled in production, deployed to customers, approved by a provider, or included in a contract. Availability can depend on plan entitlements, tenant settings, provider credentials, migrations, and deployment configuration.

## How to read the status

- **On main** means the reviewed default-branch code or tests contain the described behavior. It does not claim production deployment or general availability.
- **Partial / configuration-dependent** means a flow exists but depends on configuration, provider capability, or an incomplete user-facing path.
- **Disabled** means the current default-branch code explicitly prevents the action.
- **Not verified** means the reviewed source does not support making the claim; it does not mean the feature is planned or will be built.
- **Development branch only** must not be presented as a current feature unless merged into `main` and verified there.

This inventory compares the repositories' default branches. Development branches and open pull requests are not treated as shipped unless their changes have been merged into application `main`. The inventory reflects application `main` commit `0002f9a` (2026-11-19), not unmerged branch work.

## Product and platform inventory

### Workspaces, authentication, teams, and platform administration — On main, with caveats

AutoZeniq provisions a tenant workspace, owner membership, and eligible trial subscription at registration. Bearer access/refresh tokens support login and refresh. Authorization checks current account, tenant, membership, role, and status in the database rather than trusting token role claims alone. Owners and admins manage workspace settings and team membership; invitations can reserve seats and send an email.

The platform control plane supports tenant search/details, profile and status operations, allow-listed settings, plan/usage and manual-payment operations, feature flags, audit views, maintenance, staff roles, and selected operational monitoring. Super-admin impersonation is a reason-required, audited, revocable session with a 30-minute expiry.

**Limits:** the dashboard's invite-accept route currently simulates verification with mock state; do not describe invitation acceptance as a complete end-to-end activation flow. A separate super-admin login, dedicated JWT role authority, mandatory 2FA, or support-agent impersonation was not verified. Public claims of a dedicated `SuperAdminGuard` are stale: current authorization uses shared authentication plus database-backed role checks.

### Shared inbox, messaging, and AI assistance — On main, channel/configuration-dependent

The tenant-scoped inbox supports conversation search/listing, message history, human replies, assignment, AI pause/takeover/resume, and selected real-time updates. Text, image, and voice media upload/processing paths are present. AI Copilot can generate reply suggestions for agents; suggestions are drafts and are not automatically sent. AI settings, rules, a prompt playground, model administration, and guarded AI auto-reply paths are present. Push and WebSocket notifications are available where configured.

**Limits:** do not promise universal typing indicators, presence, read receipts, collision locks, internal notes, ticketing, or automated team/round-robin assignment from the reviewed code. Channel feature flags and model mappings do not prove that every provider adapter or message type is complete. Use the AI-state terms `active`, `paused`, and `disabled`; avoid describing AI as an order-state status.

### Knowledge ingestion, search, and conversational retrieval — On main

Tenant-authorized PDF, DOC/DOCX, CSV, JSON, and plain-text sources can be parsed and indexed asynchronously. Retrieval combines semantic vector search with PostgreSQL keyword search. Conversational Adaptive RAG can cache results, rewrite or expand queries, route by query type, rerank sources, expand parent context, apply thresholds, and detect possible conflicts.

**Limits:** the reviewed code does not establish a URL crawler, a complete Q&A/chunk editor, universal citation display, a live knowledge-gap API, HyDE generation, zero hallucinations, fixed response times, or measured accuracy/cost improvements. Do not publish performance figures without current benchmark evidence.

### External data and Google Sheets — Partial / configuration-dependent

The backend contains a scheduled, queued Google Sheets synchronization flow that can discover tabs, classify product/FAQ/policy/knowledge content, map common English and Bengali headers, update product/inventory data, and report progress. Credential storage uses authenticated encryption and production requires configured encryption keys.

**Limits:** verified behavior is primarily pull-oriented. The dashboard add-source wizard uses simulated connection checks and mock previews in parts of the flow; its UI is not proof that a connection was persisted. Full bidirectional order append, OAuth, every advertised schedule, or every public spreadsheet workflow was not established by the reviewed implementation.

### Workflow automation — Partial; unsupported actions fail closed

Workflows can be saved as tenant-scoped graphs, validated, published, queued, leased, and recovered. Verified connected triggers include `order_placed` and `chat_keyword`. `notify_agent` is the executable action found in the reviewed path; `send_whatsapp_template` and `apply_coupon` fail closed. `cart_abandoned` has no safe automatic event emitter in the reviewed code and is a manual bridge only.

**Limits:** do not present courier booking, lead tagging, stock reservation, arbitrary webhooks, WhatsApp template sending, coupon application, or other design-only actions as available workflow-builder actions. Safe recovery is limited to notification-only graphs.

### Channels, developer API, widgets, and webhooks — On main, provider-dependent

Provider connection/OAuth paths exist for supported messaging providers including WhatsApp, Facebook Messenger, Instagram, Telegram, TikTok, and a website widget. Meta OAuth and WhatsApp Embedded Signup, provider webhook handling, token-health checks, and reconnect notifications are present. The scoped Public API covers conversations, messages, customers, orders, knowledge, and webhook endpoint management. Developer API keys are one-time displayed and stored as bcrypt hashes with prefix lookup. The widget uses a separate public key, can enforce allowed domains, and uses signed sessions. Outgoing webhooks have endpoint management, queued delivery, delivery history, and replay paths.

**Limits:** actual availability depends on provider approval, account permissions, tenant entitlements, credentials, and deployment settings. Do not claim published Node/Python SDK packages, undocumented widget JavaScript methods, permanent provider tokens, unverified event/retry catalogs, or a universal integration count. Never embed a secret API key in browser code.

### Catalog, inventory, storefront, checkout, and orders — On main

Product/catalog functions include tenant-scoped product and variant management, categories, images, stock fields, search, publication state, and bulk operations. Inventory paths support reservation, confirmation/deduction, release, adjustment, restocking, and transaction-safe order/return handling. The storefront includes product/category pages, cart and checkout, delivery quotes, customer/shipping details, configurable payment modes, coupon validation, idempotent order submission, and public tracking. Orders use tenant-scoped records, generated order identifiers, payment/timeline records, status validation, and optional fraud-risk evaluation.

The current order lifecycle includes `CREATED`, `PENDING_CONFIRMATION`, `CONFIRMED`, `PROCESSING`, `COURIER_BOOKED`, `SHIPPED`, `IN_TRANSIT`, `OUT_FOR_DELIVERY`, `DELIVERED`, `RTO`, `RETURNED`, and `EXCHANGED`, subject to the validated transition rules. Reviews require signed purchase verification and a delivered order. Merchants can manage return/exchange requests for delivered orders; approval can restock eligible returned quantities or verify exchange stock.

**Limits:** merchant-mediated returns are verified; shopper self-service return submission and automatic refund transfer were not. Do not equate reservation, stock deduction, release, return approval, courier remittance, or an order status with a verified payment capture.

### Store builder, domains, tracking, and public content — Mixed / configuration-dependent

The tenant store builder supports editing settings/pages/navigation, draft preview, publishing, version history, and rollback. The reviewed default theme blueprints are `modern`, `elegant`, and `minimal`. Managed subdomains and custom domains are handled by the storefront resolver. Custom-domain readiness requires ownership, DNS, and TLS checks; stale or failed readiness can disable routing. The runtime renders published pages and configured SEO metadata.

Store tracking supports Meta, Google, and TikTok configuration, browser/server modes, consent purposes, origin checks, an event outbox, and provider adapters. Analytics, advertising, and matching consent are separate; optional purposes start denied. Tracking diagnostics/endpoint acknowledgement do not prove that a provider processed or reported an event.

The CMS backend has broad public read APIs, but the inspected admin write surface is limited (settings, blog, pricing, and FAQs). Public pricing/FAQ/blog paths mix CMS content with local/static or mock fallbacks; freshness depends on CMS and revalidation configuration. The full admin console described in the CMS design document is not evidence of a shipped surface.

### Courier delivery, fraud, and COD — On main, with a material payment limitation

The delivery module contains Pathao, Paperfly, RedX, and Steadfast adapters, booking and bulk-booking paths, consignment records, tracking/public tracking, OTP, and signed/idempotent courier webhook handling. Conditional auto-booking follows tenant rules and selected risk/destination logic. Booking outcomes that are ambiguous are held for reconciliation rather than blindly retried. Fraud scoring uses hashed phone identifiers, anonymized platform RTO history, and tenant-local order history. Admin delivery and returns/fraud monitoring surfaces exist.

Courier COD remittance records and settlement workflows are implemented, but **verified customer COD collection credit is explicitly unavailable on the reviewed `main` branch**. A courier remittance/settlement record is not proof that a particular customer payment was verified and must not mark an order paid. The delivery analytics page labels its courier/RTO/cost/SLA examples as sample data; only narrower backend aggregates are live in the reviewed code.

### CRM, leads, pipelines, follow-ups, and campaigns — On main, with analytics caveats

Tenant-scoped contacts, leads, assignment (including round-robin paths), lead conversion, pipelines/deals, activity records, work queue, scheduled follow-ups, and queued campaign broadcasts are present. Current default pipeline stages are **New Lead, Contacted, Qualified, Proposal Sent, and Negotiation**. `WON` and `LOST` are deal statuses, not default pipeline stages. Contact duplicate detection uses the tenant/channel/external-identifier tuple in the reviewed creation path, not phone number alone.

Campaign creation and queued broadcasts are implemented subject to entitlements/quota. The dashboard's read/reply counts are derived estimates, not provider-measured engagement analytics.

### Subscription pricing, entitlements, invoices, and affiliate status — On main, with explicit limits

The reviewed public catalog lists:

- **Starter:** BDT 999/month or BDT 9,990/year; 1,000 messages/month, 1 team member, and 2 channels.
- **Growth:** BDT 2,999/month or BDT 29,990/year; 5,000 messages/month, 5 team members, and 6 channels.
- **Enterprise:** custom pricing and contact sales; limits and terms are contract-defined.

Starter and Growth are the self-serve trial/checkout offers. The default trial is 14 days. Entitlements combine plan features/limits, subscription state, usage, add-ons, and tenant overrides. Verified subscription paths include SSLCommerz BDT checkout and direct bKash tokenized checkout; server-side provider verification is required. Durable invoice snapshots and recovery paths are present for verified/manual payment flows. Tenant commerce payment modes include COD-only, advance-plus-COD, full online, and partial payment; advance-plus-COD requires an explicit fixed or percentage rule.

Plan-change proration can produce a quote. Immediate upgrades are not complete until a verified payment-intent settlement path is available. Do not assert that every UI-listed method (such as Nagad, Rocket, card brands, or bank transfer) is active for every subscription flow. Do not publish a plan matrix from older pages instead of the current catalog.

**Affiliate program — Disabled:** the data model and read-only UI exist, but applications are closed, commission rates and payout terms are unset, and earning, commission approval, activation, and payouts are disabled pending explicit authorization. Do not publish rates, earnings, or availability.

### Analytics, audit, notifications, and operations — Mixed

The merchant dashboard and selected analytics endpoints cover support/AI activity, leads, response time, usage, and channel activity, with some analytics plan-gated. Tenant audit records are tenant-scoped, role-restricted, and filterable/paginated; their presence does not prove that every platform action is audited or that the ledger is immutable. Super-admin commerce/health surfaces include selected backend-backed operational signals; parts of the super-admin dashboards and the delivery analytics page use fixed, synthetic, or sample values. Do not describe those values as live customer, revenue, cost, uptime, or SLA results.

In-app notifications and WebSocket updates are implemented; FCM requires configuration. Transactional email uses the configured Brevo integration. Redis-backed BullMQ processors handle selected background tasks in the backend application process; a separate worker service is not established by the reviewed Compose deployment.

### Security, privacy, and runtime — On main for scoped controls; broad claims unverified

Reviewed controls include live workspace membership/role checks, API scopes and quotas, separate widget rate controls, encrypted integration/tracking credentials, HMAC webhook verification/signing, AI input/output guardrails and common-identifier redaction, and a 90-day tracking-data purge. Consent is purpose-separated, default-deny for optional purposes, versioned/validated, and can suppress queued tracking events after withdrawal or expiry. Production runtime validation rejects missing/weak secrets and invalid required configuration rather than silently generating keys.

These controls do **not** establish universal tenant isolation across every query/table, a universal public API rate limit, TLS version, DOMPurify coverage everywhere, immutable audit storage, a security certification, dedicated infrastructure, data residency, or an SLA. Do not claim SOC 2, HIPAA, or other certification without separate approval and evidence.

## Highest-priority corrections made to older knowledge

Older pages described capabilities more broadly than the checked source supports. Use this inventory and the updated linked pages where statements conflict. In particular:

1. Replace the old pricing matrix and plan limits; use the values above.
2. Distinguish subscription payments from staged storefront payments, provider verification from COD remittance, and affiliate records from enabled affiliate earnings.
3. Correct order statuses, CRM pipeline stages, payment-mode options, inventory/return behavior, actual store themes, and domain readiness requirements.
4. Label simulations, sample analytics, static CMS fallbacks, design documents, registry-only flags, and development branches accurately.
5. Remove or qualify unsupported accuracy, speed, cost, conversion, uptime, customer/revenue, and “zero/guaranteed” claims.
6. Treat implementation and tests as source evidence only; verify production deployment/provider access before making live-availability or contractual claims.

## Related documents

- [Capabilities](../capabilities.md)
- [Products overview](../products/overview.md)
- [Pricing and subscriptions](../pricing.md)
- [Billing and entitlements](../features/billing-entitlements.md)
- [Order management](../products/order-management.md)
- [Delivery and logistics](../products/delivery-logistics.md)
- [CRM and leads](../products/crm-leads.md)
- [Store builder](../products/store-builder.md)
- [Super Admin](../products/super-admin.md)
- [Security and privacy](../security.md)
- [System architecture](./system-architecture.md)
- [Product changelog](../updates/changelog.md)
