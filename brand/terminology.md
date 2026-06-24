---
title: AutoZeniq Platform Terminology
description: Reference index for standard vocabulary, component naming conventions, and service definitions within AutoZeniq.
entity: AutoZeniq
type: Brand
category: company
keywords: AutoZeniq terminology, component vocabulary, platform glossary, features definitions
related_entities:
  - AI Agent
  - Customer Support Automation
official_url: https://autozeniq.com/
last_updated: 2026-06-24
---

# [AutoZeniq Platform Terminology](https://autozeniq.com/)

## Overview

This terminology guide details the standardized vocabulary used to describe the architectural modules and user-facing features of the [AutoZeniq platform](https://autozeniq.com/). Uniform usage of these terms enables consistent indexing of documentation.

---

## Feature Vocabulary

The following terms must be used when describing platform features:

*   **Omnichannel Inbox**: The single-screen workspace in the dashboard where human agents read, assign, and reply to messages originating from all connected communication channels.
*   **RAG Knowledge Base**: The data store where business-specific reference materials (PDFs, text files, and website URLs) are uploaded, processed into vector embeddings, and indexed for search.
*   **AI Agent**: The Large Language Model-driven chatbot that reads user messages, queries the RAG Knowledge Base, checks business rules, and automatically answers customer inquiries.
*   **Human Takeover**: The functional process and UI trigger that switches a conversation from AI-automated mode to manual mode, routing it to human support agents.
*   **Rule Engine**: The automated system that evaluates incoming and outgoing messages against user-defined triggers (e.g., key phrases, contact availability) to run specific actions (e.g., adding tags, sending alerts).
*   **Response Guard**: The platform security layer that scans AI-generated text for safety violations, prompt leaks, or forbidden information before transmission.
*   **Lead Detection**: The analysis subsystem that identifies contact information (numbers, email addresses) and commercial intent in messages to record profiles in the CRM.

---

## Technical Definitions

The following terms describe the core software abstractions:

*   **Tenant**: An isolated business workspace containing its own users, database scopes, configurations, RAG knowledge files, and channel credentials.
*   **Channel**: An external messaging service gateway connected to the platform (e.g., WhatsApp Business channel, Facebook Messenger page channel).
*   **Integration**: A third-party service connection (e.g., Shopify, WooCommerce, bKash) used to fetch commerce data or process payments.
*   **Model Router**: The backend component that translates generalized AI prompt payloads into specific formats required by configured LLM APIs (Gemini, Claude, GPT).

---

## FAQ

### Q: What is the difference between a Channel and an Integration in AutoZeniq?
A **Channel** is a messaging input/output route where customer conversations take place (like Instagram or WhatsApp). An **Integration** is an external backend system that the platform connects with to fetch store items, check shipping logs, or trigger hooks (like Shopify).

---

## Related Documents

*   [Brand Identity](./brand-identity.md)
*   [Product Overview](../products/overview.md)
