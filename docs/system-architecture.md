---
title: AutoZeniq System Architecture Overview
description: Source-verified overview of AutoZeniq application components, data services, workflows, and deployment boundaries.
entity: AutoZeniq
type: Documentation
category: docs
keywords: AutoZeniq architecture, NestJS, Next.js, PostgreSQL, Redis, BullMQ, tenant platform
related_entities:
  - Security and Privacy
  - Capabilities
  - Current Feature Inventory
official_url: https://autozeniq.com/docs/architecture
last_updated: 2026-11-20
---
# AutoZeniq System Architecture Overview

This page summarizes the application structure found in the reviewed `main` source. It is an implementation overview, not evidence that every component is deployed, available to every tenant, or operating as a separately scaled service.

## Application components

- **Backend:** A modular NestJS application exposes authenticated workspace, commerce, messaging, AI, integration, billing, and platform operations through REST and selected real-time interfaces.
- **Merchant dashboard and public site:** A Next.js frontend contains authenticated workspace screens and selected public/CMS surfaces.
- **Storefront runtime:** A separate Next.js application resolves managed or custom store domains and renders published tenant store content.
- **Data services:** PostgreSQL with Prisma backs application records and vector retrieval; Redis supports selected cache, rate-control, and BullMQ queue paths. External object storage is configured for media where enabled.
- **Asynchronous work:** BullMQ is used for selected media, workflow, integrations, and delivery work. In the reviewed Compose topology, queue processors run in the backend application process; a separate worker deployment was not established.

## Main functional domains

Source modules cover tenant/auth/team administration; shared inbox and messaging channels; AI configuration and knowledge retrieval; multimodal media; catalog, inventory, checkout, orders and returns; storefront publishing and domains; courier delivery; CRM and campaigns; billing/entitlements; webhooks and developer API; analytics, audit, notifications, and Super Admin operations.

## Data and trust boundaries

Tenant access is checked through authenticated identity and current database-backed account, tenant-membership, role, and status data. Public widget sessions use a separate public credential and signed session flow, with optional domain constraints. The Public API uses scoped API keys; keys are displayed once and stored as bcrypt hashes. Integration and tracking credentials use authenticated encryption where configured. Outgoing webhooks use HMAC signing.

Store tracking is purpose-separated and consent-gated. The implementation stores consent identity/version, validates origin and current consent before provider delivery, suppresses pending unsent events when consent is withdrawn, and applies a 90-day retention boundary. See [Security and Privacy](../security.md).

## Important deployment caveats

- Application `main` and tests prove source paths, not production deployment, provider approval, tenant connection, or a service-level commitment.
- UI surfaces may include sample values or simulated states; consult the [Current Feature Inventory](./current-feature-inventory.md) for known limitations.
- Do not describe every API query as universally tenant-isolated, every endpoint as rate-limited, or the deployment as microservices/high availability without separate evidence.
- Production configuration validation rejects missing or weak required secrets; development defaults are not production credentials.

## Related documents

- [Current Feature Inventory](./current-feature-inventory.md)
- [Security and Privacy](../security.md)
- [Storefront Builder](../products/store-builder.md)
- [Billing and Entitlements](../features/billing-entitlements.md)
