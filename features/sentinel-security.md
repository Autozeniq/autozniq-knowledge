---
title: AutoZeniq Security Controls and Sentinel Notes
description: Selected security controls present in the reviewed application source, with scope and verification caveats.
entity: AutoZeniq
type: Feature
category: features
keywords: AutoZeniq security, rate limiting, encryption, authentication, webhook signing, privacy
related_entities:
  - Security and Privacy
  - System Architecture
  - Current Feature Inventory
official_url: https://autozeniq.com/security
last_updated: 2026-11-20
---
# Security Controls and Sentinel Notes

Older materials used “Sentinel” to describe a broad, comprehensive platform security framework. This page instead records scoped controls verifiable in the reviewed `main` source. Presence in code does not prove every control is active in every deployment.

## Controls found in reviewed paths

- Authenticated application operations check current account and tenant membership/role data.
- Public API keys are scoped and stored as bcrypt hashes; widget access uses separate public credentials, signed sessions, and optional allowed-domain checks.
- Integration/tracking credentials use authenticated encryption where those paths are enabled.
- Outgoing webhook payloads use HMAC signing; provider-specific inbound webhook paths apply signature verification where implemented.
- Production configuration validation rejects missing, malformed, placeholder, or weak required authentication/encryption secrets.
- Store tracking separates consent purposes, fails closed without valid consent identity/version, suppresses queued unsent deliveries after revocation, quarantines legacy null-consent rows, and enforces a 90-day tracking retention boundary.

## Scope limitations

This does not establish a universal Redis IP limiter on all public endpoints, fixed thresholds, TLS version, comprehensive DOMPurify coverage, zero SQL injection risk, an immutable audit log, security certification, external penetration testing, or a vulnerability-response SLA. See [Security and Privacy](../security.md) for broader claim limits.

## Related documents

- [Security and Privacy](../security.md)
- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [System Architecture](../docs/system-architecture.md)
