---
title: AutoZeniq SDK and Widget Integration Status
description: Verified Public API and browser widget integration boundaries; published SDK package availability is not confirmed.
entity: AutoZeniq
type: Integration
category: integrations
keywords: AutoZeniq SDK, API client, web widget, browser key, developer integration
related_entities:
  - Public API Integration
  - Webhook Integration
  - Current Feature Inventory
official_url: https://autozeniq.com/docs
last_updated: 2026-11-20
---
# SDK and Widget Integration Status

The reviewed application source includes a website chat widget integration and a scoped Public API. It does not verify official published Node.js (`@autozeniq/node`) or Python (`autozeniq`) package releases or the methods described in older examples. Do not install or build production integrations against unverified package names and examples.

## Website widget

The widget uses a separate public key, can enforce allowed-domain restrictions, and uses signed sessions. This browser credential is distinct from a secret Public API key. Exact script URL, JavaScript methods, event names, and customization options should be taken from the current dashboard or official reference; older snippets in this document are not a supported contract.

## Server-side integrations

Use a scoped Public API key only in a trusted server-side environment. Keys are displayed once and stored as bcrypt hashes. Apply key scopes and quotas, avoid logging secrets, and revoke keys if exposed. See the [Public API guide](./api.md).

## Webhook verification

Outgoing webhook deliveries are HMAC-signed. Use the current per-endpoint secret and current official signature-verification instructions, if provided. The old sample snippets in this file are not authoritative; do not verify signatures against re-serialized JSON or use ordinary string comparison.

## Related documents

- [Public API](./api.md)
- [Outgoing Webhooks](./webhook.md)
- [Current Feature Inventory](../docs/current-feature-inventory.md)
