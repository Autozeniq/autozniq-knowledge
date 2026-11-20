---
title: Google Sheets Integration Guide
description: Google Sheets connection prerequisites, import behavior, verification steps, and limits.
entity: AutoZeniq
type: Integration
category: integrations
keywords: Google Sheets integration, spreadsheet sync, catalog import, inventory
related_entities:
  - Google Sheets Synchronization
  - Order Management System
official_url: https://autozeniq.com/integrations/google-sheets
last_updated: 2026-11-20
---
# Google Sheets Integration Guide

**Status: Configuration Required**

Google Sheets use depends on the current workspace connection flow, access to the selected sheet, plan entitlement, and the sync options enabled for the account. Confirm the current connection method and scopes in the official AutoZeniq documentation; older OAuth or service-account instructions are **Needs Verification**.

## Before you connect

- Confirm that the merchant can access the intended spreadsheet.
- Keep product, inventory, FAQ, and policy data in clearly labeled tabs.
- Review the proposed mapping before applying imported values.
- Keep a backup of important data and test with a small sheet first.

## Observable behavior

Where enabled, AutoZeniq may read selected tabs and classify or map supported product, inventory, FAQ, or policy information. Header matching and field mapping can require review. The currently documented scope should be treated as primarily import or pull oriented.

## Limitations

**Status: Partially Available.** Do not assume bidirectional catalog synchronization, order export, a fixed schedule, a universal row limit, immediate updates, or perfect mapping. Exact supported fields, schedules, conflict behavior, and write-back operations are **Needs Verification**.

## Errors and recovery

If access is denied, a sheet is missing, mapping is incomplete, or a sync fails, correct the provider permission or source data and run only the documented retry. Confirm the resulting catalog or knowledge content after a completed sync; a preview is not proof that data was saved or applied.

See [Google Sheets Synchronization](../features/google-sheets-sync.md) for related product guidance.
