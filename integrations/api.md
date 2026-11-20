---
title: AutoZeniq Public API Integration
description: Public API availability, setup prerequisites, safe key handling, and integration boundaries.
keywords: AutoZeniq API, Public API, authentication, API key, conversations, orders, webhooks
category: integrations
entity: AutoZeniq
type: Integration
related_entities:
  - Webhook Integration
  - SDK and Widget Integration
official_url: https://autozeniq.com/docs
last_updated: 2026-11-20
---
# AutoZeniq Public API

**Status: Needs Verification**

The Public API may be available for selected workspaces and plans. Before building an integration, confirm the current API reference, enabled scope, and workspace entitlement with AutoZeniq support or the official documentation.

## Prerequisites and setup

- An AutoZeniq workspace with API access enabled.
- A server-side integration that can keep credentials private.
- The current official API reference for supported resources, permissions, request formats, and limits.
- A test request and an agreed failure/retry approach before using the integration in production.

The exact routes, schemas, scopes, quotas, and supported actions are **Needs Verification**. Do not use older snippets or undocumented routes as a contract.

## Key safety

Treat an API key as a secret. Store it only in a trusted server-side secret store, do not place it in browser code or a public storefront, and do not log it. Revoke and replace a key if it may have been exposed. A browser widget credential, when offered, is separate from a server-side API key.

## Observable behavior and limits

Where enabled, the API can expose selected workspace data and actions. It is not automatically a complete export, unrestricted record-management interface, or guarantee of outbound channel delivery. Availability can vary by plan, workspace configuration, provider connection, and current documentation.

## Errors and support

Handle authentication, permission, validation, rate-limit, timeout, and provider failures without assuming that a request was applied. Use the official error guidance and contact AutoZeniq support when the result is ambiguous. Do not retry a state-changing request blindly unless the current API documentation provides a safe retry method.

## Related documents

- [Outgoing Webhooks](./webhook.md)
- [SDK and widget status](./sdk.md)
- [Current Feature Inventory](../docs/current-feature-inventory.md)
