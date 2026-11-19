---
title: AutoZeniq Outgoing Webhooks
description: Endpoint management, HMAC signing, queued delivery history, and status-qualified webhook capabilities.
keywords: AutoZeniq webhooks, endpoint management, HMAC signing, delivery history, replay
category: integrations
entity: AutoZeniq
type: Integration
related_entities:
  - Public API Integration
  - Current Feature Inventory
official_url: https://autozeniq.com/docs
last_updated: 2026-11-20
---
# AutoZeniq Outgoing Webhooks

The reviewed Public API integration contains tenant-scoped webhook endpoint management, queued outgoing delivery, delivery history, and replay paths. Webhook availability is subject to endpoint configuration, entitlements, event support, quotas, and deployment settings. Not every internal event or action is necessarily exposed as a public webhook.

## Security and delivery

Outgoing payloads use HMAC signing with an endpoint-associated secret. Treat signatures as security controls, protect the secret, and verify against the exact raw request body using the current official instructions. Do not rely on the previous sample payload, signature header example, or verification snippet in this page; those details have not been revalidated against the complete current API contract.

Delivery history and replay support do not guarantee delivery, exactly-once processing, a fixed retry count, fixed delivery latency, or a static source IP list. Receiving services should verify signatures and handle duplicate event delivery safely.

## Event catalog

Use the current API/developer reference or endpoint settings to see the event types available to a workspace. Older examples listing `conversation.created`, `lead.qualified`, or other names are not an authoritative event catalog.

## Related documents

- [Public API](./api.md)
- [SDK and widget status](./sdk.md)
- [Current Feature Inventory](../docs/current-feature-inventory.md)
