---
title: AutoZeniq Outgoing Webhooks
description: Webhook availability, endpoint setup, delivery handling, and verification boundaries.
keywords: AutoZeniq webhooks, endpoint setup, delivery history, retries, event verification
category: integrations
entity: AutoZeniq
type: Integration
related_entities:
  - Public API Integration
  - SDK and Widget Integration
official_url: https://autozeniq.com/docs
last_updated: 2026-11-20
---
# AutoZeniq Outgoing Webhooks

**Status: Needs Verification**

Webhook support and the current event catalog must be confirmed in the official AutoZeniq documentation or with support for the target workspace. Public documentation and current product understanding may differ; do not copy older routes, event names, verification details, or payload examples into a production integration.

## Prerequisites and setup

- A workspace with webhook access enabled.
- A public HTTPS receiver that can validate, acknowledge, and process deliveries safely.
- The current official instructions for endpoint setup, supported events, payloads, and verification.
- A plan for duplicate, delayed, malformed, and out-of-order deliveries.

## Observable behavior and limits

When enabled, a configured endpoint may receive notifications for supported workspace events. Exact events, delivery timing, retry behavior, replay options, payload fields, and source-network details are **Needs Verification**. Webhooks do not guarantee that a downstream action succeeded or that a message was delivered by another provider.

Keep event receipt separate from business confirmation. For example, a delivery notification is not proof of customer payment, and a webhook received by your server is not proof that your own processing completed.

## Errors and safe handling

Return the acknowledgement required by the current documentation, process asynchronously where appropriate, and make handlers idempotent. Record enough information to investigate failures without storing unnecessary personal data or secrets. If verification fails, the payload is incomplete, or a delivery is ambiguous, stop the affected action and contact support rather than guessing.

## Related documents

- [Public API](./api.md)
- [SDK and widget status](./sdk.md)
- [Current Feature Inventory](../docs/current-feature-inventory.md)
