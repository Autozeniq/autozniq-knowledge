---
title: Google Sheets Data Synchronization
description: Status-qualified overview of spreadsheet discovery, queued ingestion, supported mapping, and dashboard connection limitations.
entity: AutoZeniq
type: Feature
category: features
keywords: AutoZeniq Google Sheets, spreadsheet synchronization, catalog import, Bengali header mapping, data source
related_entities:
  - Data Sources
  - Commerce Automation
  - Order Management System
official_url: https://autozeniq.com/features/google-sheets-sync
last_updated: 2026-11-20
---
# Google Sheets Data Synchronization

The backend contains a scheduled, queued Google Sheets synchronization flow. It can discover tabs, classify product/FAQ/policy/knowledge content, map common English and Bengali column names, apply eligible product/inventory updates, and report job progress.

## Current scope

The reviewed flow is primarily pull-oriented: it reads spreadsheet data into AutoZeniq. Credential storage uses authenticated encryption, and production use requires valid encryption configuration. The supported mapping is heuristic; it is not a published accuracy guarantee.

## Connection and scheduling caveats

Parts of the dashboard add-source wizard use simulated connection checks and mock previews. Those UI states do not prove a credential was saved, provider access was granted, or a sheet was synchronized. A connected provider, account approval, configured schedule, and successful job are prerequisites to any live-availability claim.

Full bidirectional order append, a completed OAuth connection experience, every schedule option advertised in older docs, and every public spreadsheet workflow were not established by the reviewed implementation. Do not describe it as a live two-way database or promise instant synchronization.

## Related documents

- [Google Sheets Integration Guide](../integrations/google-sheets.md)
- [Current Feature Inventory](../docs/current-feature-inventory.md)
- [Knowledge Base](./knowledge-base.md)
- [Order Management](../products/order-management.md)
