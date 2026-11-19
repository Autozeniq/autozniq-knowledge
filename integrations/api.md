---
title: AutoZeniq Public API Integration
description: Current Public API capabilities, key handling, authorization, and integration boundaries.
keywords: AutoZeniq API, Public API, authentication, API key, conversations, orders, webhooks
category: integrations
entity: AutoZeniq
type: Integration
related_entities:
  - Webhook Integration
  - Current Feature Inventory
official_url: https://autozeniq.com/docs
last_updated: 2026-11-20
---
# AutoZeniq Public API

AutoZeniq `main` contains a scoped Public API for selected conversation, message, customer, order, knowledge, and webhook endpoint-management operations. Available endpoints and actions are limited to the implemented API surface, tenant entitlements, key scopes, quotas, and deployment configuration. Consult the current in-app or official API reference for exact routes and schemas; this page intentionally avoids stale route examples.

## Authentication and API keys

Requests use bearer API keys. A newly created key is displayed once; the backend stores a bcrypt hash and uses a prefix for lookup. Keys are subject to scopes, per-tenant key limits, and API usage quotas. Revoke and rotate keys if they may have been exposed. Never embed a secret API key in browser JavaScript or a public storefront.

The browser widget uses a separate public key, signed sessions, and optional allowed-domain restrictions; it is not a reason to expose a server-side API key.

## Scope and limitations

- The API does not establish complete data export or unrestricted CRUD across all application records.
- Do not assume outbound WhatsApp dispatch, arbitrary order creation, every endpoint named in older documentation, or universal API rate limits.
- There are no verified official published Node.js or Python SDK packages in the reviewed source.
- Endpoint availability depends on plan, scopes, workspace state, and deployment settings.

## Related documents

- [Outgoing Webhooks](./webhook.md)
- [SDK and widget status](./sdk.md)
- [Current Feature Inventory](../docs/current-feature-inventory.md)
