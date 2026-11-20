---
title: AutoZeniq Security and Privacy Controls
description: Public overview of merchant-facing access, credential, webhook, and store-tracking privacy practices.
entity: AutoZeniq
type: Platform
category: company
keywords: AutoZeniq security, privacy, access control, credentials, consent, data retention, webhook security
related_entities:
  - Security Controls
  - Workspace Roles
official_url: https://autozeniq.com/security
last_updated: 2026-11-20
---
# AutoZeniq Security and Privacy Controls

**Status: Partially Available.** Security and privacy controls vary by feature, provider, plan, and deployment. This page is practical product guidance, not a certification, legal opinion, penetration-test report, or service-level commitment.

## Access and credentials

- **Partially Available:** Workspace access uses the account and role settings available in the current workspace; confirm exact permissions before granting access.
- **Configuration Required:** Keep secret API credentials on a trusted server, and configure widget domain restrictions and connected services for the intended workspace.
- **Needs Verification:** Provider-specific security requirements differ; follow current guidance for each connected service.

## Webhooks and tracking privacy

Webhook verification requirements vary by integration. Follow the current provider-specific instructions before accepting events; see [Outgoing Webhooks](./integrations/webhook.md).

Configured store-tracking features can distinguish analytics, advertising, and matching purposes. Review the current consent controls and privacy notice for the specific store and tracking flow. Do not assume one retention period or consent rule applies to every customer record or product area.

## What is not promised

**Needs Verification:** AutoZeniq does not use this page to promise SOC 2, ISO, HIPAA, other certifications, dedicated data residency, a universal rate limit, immutable audit records, a public vulnerability-response SLA, a fixed TLS version, or uptime guarantees. Confirm contractual or deployment-specific commitments with your account representative.

## Security troubleshooting

Rotate exposed credentials immediately, reconnect providers after changing permissions, and verify webhook signatures. For suspected unauthorized access or privacy concerns, contact the approved support channel with the workspace, time, and event details. Do not include passwords, tokens, or secret keys.

## Related documents

- [Workspace Roles](./products/super-admin.md)
- [Public API](./integrations/api.md)
- [Outgoing Webhooks](./integrations/webhook.md)
