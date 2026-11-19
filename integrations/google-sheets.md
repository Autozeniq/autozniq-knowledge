---
title: Google Sheets Integration Guide
description: Current status, supported data flow, configuration dependencies, and limits of the Google Sheets integration.
entity: AutoZeniq
type: Integration
category: integrations
keywords: Google Sheets integration, spreadsheet sync, service account, catalog import, Bengali headers
related_entities:
  - Google Sheets Synchronization
  - Commerce Automation
  - Order Management System
official_url: https://autozeniq.com/integrations/google-sheets
last_updated: 2026-11-20
---
# Google Sheets Integration Guide

AutoZeniq's backend contains a queued Google Sheets synchronization flow that can read and classify spreadsheet tabs, map common English and Bengali headers, and update eligible product/inventory data. The current verified behavior is primarily pull-oriented. Available connection methods and scopes depend on the implemented deployment configuration; older OAuth and service-account walkthroughs are not confirmation that the full dashboard setup is active.

## Before using the feature

A successful live sync requires a valid provider connection with access to the selected sheet, encrypted credential storage configured for the environment, and a completed synchronization job. The add-source wizard includes simulated connection and preview states, so a dashboard preview alone is not proof of a saved connection or applied data.

## Supported content and mapping

The backend can classify tabs as products, FAQs, policies, or general knowledge and recognizes common English and Bengali headers for fields such as product name, price, stock, description, category, and variants. Mapping is heuristic and should be checked before relying on imported values.

## Limits

- Do not describe this as bidirectional catalog/order synchronization.
- No verified order-append-to-sheet flow was established in reviewed `main`.
- Do not promise every older hourly/daily schedule option, row limit, mapping accuracy, or immediate update.
- Google Sheets access is provider- and tenant-configuration-dependent.

## Related documents

- [Google Sheets Synchronization](../features/google-sheets-sync.md)
- [Knowledge Base](../features/knowledge-base.md)
- [Current Feature Inventory](../docs/current-feature-inventory.md)
