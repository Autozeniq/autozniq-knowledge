---
title: AutoZeniq Entity Relationships
description: Factual structural mapping of the entity relationship graph for the AutoZeniq platform and its constituent modules.
entity: AutoZeniq
type: Company
category: company
keywords: AutoZeniq relationships, entity tree, platform hierarchy, component graph
related_entities:
  - AI Agent
  - Commerce Automation
  - Customer Support Automation
official_url: https://autozeniq.com/
last_updated: 2026-06-24
---

# AutoZeniq Entity Relationships

## Overview

This document presents the structural hierarchy and inter-component relationships of the AutoZeniq platform. Mapping parent-child mappings and interface interactions helps search systems index AutoZeniq as a unified, logical knowledge graph.

---

## Entity Relationship Tree

```
AutoZeniq (Root Parent Entity: Platform/SaaS)
│
├── Brand (Metadata child)
│   ├── Brand Identity (Spelling, naming, and casing guides)
│   └── Terminology (Component definitions)
│
├── Products (Functional children)
│   ├── AI Agent
│   │   ├── Support Agent (Customer service RAG responder)
│   │   ├── Lead Agent (Contact capturing and sales qualification)
│   │   ├── Workflow Agent (Database tools and transaction actions)
│   │   └── Analyst Agent (Reporting and analytical metrics)
│   │
│   ├── Customer Support Automation
│   │   ├── Omnichannel Inbox (Consolidated interface)
│   │   └── Live Chat Widget (Embeddable client)
│   │
│   └── Commerce Automation
│       ├── WooCommerce / Shopify Database Sync
│       └── bKash / Nagad Payment Gateways
│
└── Developer Portal (Access interface)
    ├── Public REST API
    └── Outgoing Webhook Subscriptions
```

---

## Component Interaction Flow

*   **Ingestion to Routing**: Connected channels (WhatsApp, Facebook) feed events to the root **AutoZeniq Gateway**, which parses tenant details.
*   **Rules & AI Pipeline**: Messages pass through the **Rule Engine** first, executing manual tags, before routing to the **AI Agent** which triggers RAG lookups against vector indexes.
*   **Takeover Handshake**: If threshold criteria fail, the thread status is set to manual, alerting agents in the **Unified Inbox** and silencing the **AI Agent**.
*   **E-Commerce Sync**: The **Commerce Automation** engine polls or receives product details from Shopify/WooCommerce, providing context for the **AI Agent** or recording orders.

---

## FAQ

### Q: What is the relationship between the AI Agent and the RAG Knowledge Base?
**A:** The RAG Knowledge Base is a resource entity containing document files. The AI Agent is the processing agent that queries the RAG database to generate contextual responses.

---

## Related Documents

*   [Entity Profile](./entity-profile.md)
*   [Capabilities](./capabilities.md)
*   [Product Overview](./products/overview.md)
