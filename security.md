---
title: AutoZeniq Security and Privacy Controls
description: Verified application security, access-control, credential, webhook, and store-tracking privacy controls with scope limits.
entity: AutoZeniq
type: Platform
category: company
keywords: AutoZeniq security, privacy, access control, credentials, consent, data retention, webhook security
related_entities:
  - Sentinel Security
  - System Architecture
  - Current Feature Inventory
official_url: https://autozeniq.com/security
last_updated: 2026-11-20
---
# AutoZeniq Security and Privacy Controls

This page describes selected controls found in the reviewed application `main` source. It is not a certification, penetration-test report, legal compliance statement, or guarantee of production configuration.

## Access and tenant authorization

Authenticated application routes use current account and workspace membership/role checks. Public API keys are scoped and stored as bcrypt hashes after one-time display. The website widget uses a separate public key, signed sessions, and optional allowed-domain checks. Do not put a secret Public API key into frontend code.

## Credentials and request integrity

Integration and tracking credentials are encrypted with authenticated AES-256-GCM where those credential paths are used. Outgoing merchant webhooks are HMAC-signed. Provider webhook handling and courier events apply provider-specific verification and idempotency controls in reviewed paths; exact requirements vary by provider.

Production runtime validation rejects missing, malformed, placeholder, or weak required secrets/configuration, including encryption and authentication keys, before dependent modules load. It does not silently generate replacement production keys.

## Store tracking consent and retention

Store tracking separates analytics, advertising, and advertising matching consent; optional purposes default to denied. Events require valid server-side consent identity/version and store scope. Provider delivery rechecks consent and retention, rejects expired or stale consent, and suppresses queued unsent deliveries after withdrawal. Legacy events without consent identity are quarantined rather than sent. Store tracking records and related consent/context are bounded by a 90-day retention policy.

These controls are specific to the store-tracking paths reviewed; they should not be described as universal retention rules for all customer records.

## Security claims not established here

The reviewed source does not establish SOC 2, ISO, HIPAA, or other certification; dedicated or isolated database clusters; universal enforcement on every query/table; TLS version across all deployments; comprehensive sanitization across every renderer; an immutable audit ledger; a public bounty or response-time commitment; or a universal IP rate limit. Do not state those guarantees without current independent evidence and product approval.

## Related documents

- [Sentinel Security](./features/sentinel-security.md)
- [System Architecture](./docs/system-architecture.md)
- [Current Feature Inventory](./docs/current-feature-inventory.md)
- [Public API](./integrations/api.md)
- [Outgoing Webhooks](./integrations/webhook.md)
