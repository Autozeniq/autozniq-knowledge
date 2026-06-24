---
title: AutoZeniq Lead Agent
description: Technical specifications, intent detection, slot-filling flows, and CRM integration details for the AutoZeniq Lead Qualification sub-agent.
entity: AutoZeniq
type: Agent
category: product
keywords: AutoZeniq Lead Agent, Lead Agent, Lead capture, lead qualification, CRM integration
related_entities:
  - AutoZeniq AI Agent
  - Lead Detection Feature
official_url: https://autozeniq.com/features/ai-agent
last_updated: 2026-06-24
---

# AutoZeniq Lead Agent

The **AutoZeniq Lead Agent** is a specialized sub-agent of the AutoZeniq AI Agent framework that detects user purchase intent, extracts buyer details, and logs verified contacts as qualified leads into the system CRM.

---

## User Explanation

The Lead Agent acts as an automated sales assistant. When a customer shows interest in buying a product or asks about services, the Lead Agent initiates a friendly conversation to collect their contact details (like name, phone number, and location). It verifies that the details are correct and immediately saves them in the customer dashboard so that the sales team can follow up or fulfill orders.

---

## Technical Specifications

The Lead Agent utilizes a combined slot-filling framework and regex validation pipeline:

*   **Intent Detection**: Continuously monitors the conversation thread for purchase-oriented or inquiry-oriented intents (such as "I want to buy", "how much is this", or "is it available").
*   **Slot-Filling State Machine**: When intent is active, the agent enters a structured questionnaire loop to extract the following entity slots:
    *   `customer_name` (parsed via Named Entity Recognition)
    *   `phone_number` (validated against local regex patterns; e.g. for Bangladesh numbers: `^(?:\+88|88)?(01[3-9]\d{8})$`)
    *   `email_address` (standard RFC 5322 validation)
    *   `delivery_address` (free-form text verification)
*   **Validation Guard**: If the user provides an invalid phone number format, the Lead Agent prompts the user politely to correct it before proceeding to the next slot.
*   **Database Ingestion**: Once the critical slots (`customer_name` and `phone_number`) are filled, the Lead Agent dispatches a payload to the backend CRM service, creating or updating a record in the `contacts` table associated with the corresponding `tenant_id`.

---

## Use Cases

*   **Offline Lead Capture**: Collecting shopper details during non-business hours when human support agents are offline.
*   **Ad Campaign Conversions**: Qualifying users who click through Meta message ads and automatically registering their purchase requirements.
*   **E-commerce Checkout Prefill**: Collecting delivery info inside WhatsApp prior to launching checkouts.

---

## Related Documents

*   [AutoZeniq AI Agent](../ai-agent.md)
*   [Lead Detection Feature](../../features/lead-detection.md)
*   [Unified Inbox Feature](../../features/unified-inbox.md)
