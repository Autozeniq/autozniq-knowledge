---
title: AutoZeniq SDK and Widget Integration Status
description: Status of published SDKs, website widget setup, and safe developer integration boundaries.
entity: AutoZeniq
type: Integration
category: integrations
keywords: AutoZeniq SDK, API client, web widget, developer integration
related_entities:
  - Public API Integration
  - Webhook Integration
official_url: https://autozeniq.com/docs
last_updated: 2026-11-20
---
# SDK and Widget Integration Status

## Published SDK packages

**Status: Needs Verification**

Confirm any official package name, supported language, version, installation method, and compatibility directly in the current AutoZeniq developer documentation. Do not install packages or rely on methods from older examples unless they are listed in the current official reference.

## Website chat widget

**Status: Configuration Required**

A website widget may be available for a workspace. Setup requirements, script location, browser credential, allowed domains, session behavior, customization, supported browsers, and message features are **Needs Verification** for the current account. Follow the current dashboard or official documentation rather than copying an unverified snippet.

Never place a secret server-side API key in browser code. If a public widget credential is provided, use it only for the documented browser integration and restrict its allowed domains where that option is available.

## Observable behavior and limitations

A configured widget can expose the channel features enabled for the workspace. It does not by itself confirm that a Page, phone number, courier, payment provider, or other service is connected. Published SDK availability, widget events, and customization options are not guaranteed across plans.

## Errors and support

Test the widget on an approved domain and check the current connection status. If it does not load, verify domain configuration, workspace access, browser errors, and provider approval without exposing credentials. For API or webhook failures, use the [Public API](./api.md) and [Outgoing Webhooks](./webhook.md) guidance and contact support for current contract details.
