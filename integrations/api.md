---
title: AutoZeniq Public API Integration
description: Developer documentation and technical API endpoint guide for the AutoZeniq Public REST API.
keywords: AutoZeniq API, Developer API, API Authentication, API endpoints, REST API, API key
category: integrations
entity: AutoZeniq
type: Integration
related_entities:
  - Terminology
  - Webhook Integration
official_url: https://autozeniq.com/docs
last_updated: 2026-06-24
---

# [AutoZeniq Public API Integration](https://autozeniq.com/docs)

## Overview

The AutoZeniq Public API provides a RESTful interface for developers to programmatically integrate AutoZeniq capabilities with third-party software, internal CRMs, custom databases, and storefront engines. The API exposes endpoints to query conversations, transmit messages, manage contacts, and sync order histories. Refer to the official [developer documentation](https://autozeniq.com/docs) for full parameters and guidelines.

---

## Technical Architecture

The Public API is designed to ensure tenant isolation and secure communications:

### Simple Explanation
Developers use the AutoZeniq API to link their custom business websites or apps with the AutoZeniq database. For instance, when a developer generates a unique "API Key" in the developer settings, they can write code to automatically fetch chat histories, export contact phone numbers, or trigger WhatsApp messages when customers place orders on their site.

### Technical Explanation
1.  **Authentication Scheme**: Requests are authenticated via HTTP Bearer tokens:
    `Authorization: Bearer <api_key>`
2.  **Key Hashing and Storage**: API keys are generated in the Developer Settings panel. AutoZeniq displays the plaintext key once upon creation. The backend hashes the key using SHA-256 before storing it in the database to prevent token exposure.
3.  **Tenant Isolation**: All routes require validation by the `ApiKeyGuard` middleware. This guard extracts the hashed key, queries the database to resolve the associated `tenant_id`, and attaches the tenant context to the execution thread.
4.  **Rate Limiting**: Employs redis-based token bucket rate limiters, integrating with the platform's `AiCostGuardService` to limit API usage based on subscription quotas.

---

## Core Endpoint Catalog

The base URL for all API requests is: `https://api.autozeniq.com/v1/`

### Conversations
*   `GET /v1/conversations`: Retrieves a paginated list of conversation threads for the tenant.
*   `GET /v1/conversations/:id/messages`: Fetches message logs from a specific conversation thread.
*   `POST /v1/conversations/:id/status`: Updates the thread state (e.g. switching from `ai` to `open`).

### Messages
*   `POST /v1/messages/send`: Transmits an outbound text, media, or template message to a contact via the specified channel.
    *   **Payload Example**:
        ```json
        {
          "channelId": "uuid-string",
          "recipientId": "+88017xxxxxxxx",
          "message": {
            "type": "text",
            "content": "Your order has been verified."
          }
        }
        ```

### Contacts & Leads
*   `GET /v1/contacts`: Queries the tenant's CRM contacts list.
*   `POST /v1/contacts`: Creates or updates a customer profile.

### Orders
*   `POST /v1/orders`: Syncs storefront purchases to AutoZeniq's database.
*   `GET /v1/orders/:id`: Retrieves order status and item logs.

---

## Benefits

*   **Workflow Flexibility**: Connects chat metrics and leads to existing backend ERP systems.
*   **Custom Notifications**: Triggers messages to clients based on events in external systems (like stock alerts).
*   **Data Control**: Allows complete data export for compliance and auditing.

---

## Use Cases

*   **Custom Store Integrations**: Syncing product catalogs and orders from custom coded Node/Python backends instead of standard Shopify/WooCommerce plugins.
*   **ERP Lead Syncing**: Injecting contact numbers captured during conversations directly into internal ERP databases.
*   **Custom App Support**: Sending system monitoring alerts to staff members via WhatsApp Business.

---

## FAQ

### Q: What format does the Public API use?
**A:** The API accepts and returns standard JSON payloads. All dates are represented in ISO 8601 UTC format.

### Q: Where do I generate API keys?
**A:** Log in to the AutoZeniq dashboard, navigate to **Settings > Developer Portal**, and click **Generate API Key**. Be sure to copy the secret immediately, as it cannot be recovered.

---

## Related Documents

*   [Developer SDK Catalog](./sdk.md)
*   [Webhook Integration](./webhook.md)
*   [Product Overview](../products/overview.md)
*   [Terminology](../brand/terminology.md)
