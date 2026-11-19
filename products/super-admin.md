---
title: AutoZeniq Super Admin and Tenant Governance
description: Status-qualified overview of platform tenant administration, operational controls, and privileged sessions.
entity: AutoZeniq
type: Product
category: products
keywords: AutoZeniq super admin, tenant governance, platform operations, impersonation, audit
related_entities:
  - Enterprise Billing
  - Security and Privacy
official_url: https://autozeniq.com/products/super-admin
last_updated: 2026-11-20
---
# Super Admin and Tenant Governance

The platform control plane provides selected tenant and operational administration. Current source includes tenant search/list/detail, profile and status actions, allow-listed settings, subscription/plan and manual-payment operations, feature flags, audit views, maintenance, staff roles, impersonation controls, and operational monitoring surfaces.

## Authentication and permissions

Super-admin routes use shared account authentication and database-backed role checks. The application rechecks the user's current role/account state; a token claim alone is not the source of authority. Current workspace roles include owner, admin, agent, billing manager, and viewer, with different permissions.

Do not claim a separate super-admin login, separate admin-user authentication system, a dedicated `SuperAdminGuard`, cryptographically authoritative role claims, mandatory two-factor authentication, or IP allowlisting based on the reviewed default-branch implementation. Those statements appear in older design material but are not established as current behavior.

## Tenant and platform controls

The reviewed control plane includes tenant search/details, profile/status operations, selected settings and feature flags, plan/usage operations, manual-payment administration, audit views, maintenance controls, internal staff role management, and selected commerce/infrastructure health screens. The presence of a screen or design checklist does not prove all controls are enabled in every deployment. Specific mutations and audit coverage vary by operation.

## Impersonation

The current impersonation flow is restricted to super-admin users, requires a reason, is limited to 30 minutes, records start/stop audit events, and supports listing/revoking sessions. It is a privileged diagnostic operation. Support-agent impersonation was not verified.

## Invitations and audit

Tenant invitations can be created and may reserve a seat and send an email. The reviewed invite-accept page currently simulates verification with mock state, so end-to-end invitation activation should not be advertised as complete. Audit records exist for selected operations; this does not establish that every action is logged or that the audit store is immutable/tamper-evident.

## Manual plan and payment operations

Administrative manual plan assignments are distinct from paid upgrades and must not be treated as subscription-payment records. Any manual payment workflow must be described only with its specific authorization and verification conditions. See [Pricing](../pricing.md) and [Billing & Entitlements](../features/billing-entitlements.md).

## Related documents

- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [Security and Privacy](../security.md)
- [Billing and Entitlements](../features/billing-entitlements.md)
- [System Architecture](../docs/system-architecture.md)
