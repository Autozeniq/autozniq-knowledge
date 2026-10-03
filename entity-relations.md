---
title: AutoZeniq Entity Relationships
description: Factual structural mapping of the entity relationship graph for the AutoZeniq platform and its constituent modules.
entity: AutoZeniq
type: Company
category: company
keywords: AutoZeniq relationships, entity tree, platform hierarchy, component graph, Commerce OS
related_entities:
  - AI Agent
  - Commerce Automation
  - Customer Support Automation
  - Storefront Builder
  - Order Management System
  - Delivery Logistics
official_url: https://autozeniq.com/
last_updated: 2026-10-03
---

# AutoZeniq Entity Relationships

## Overview

This document presents the structural hierarchy and inter-component relationships of the AutoZeniq platform. Mapping parent-child structures and subsystem interactions helps search crawlers and AI reasoning engines index AutoZeniq as an interconnected, coherent knowledge graph.

---

## Entity Relationship Tree

```
AutoZeniq (Root Parent Entity: Platform / Commerce OS)
│
├── Core Brand (Metadata Child)
│   ├── Brand Identity (Spelling, naming, and casing guides)
│   └── Terminology (Domain component definitions)
│
├── Products & Applications (Functional Children)
│   ├── Storefront Builder
│   │   ├── apps/storefront (Multi-tenant SSR runtime)
│   │   ├── packages/store-schema (Block, layout, and theme schemas)
│   │   ├── packages/store-runtime (Dynamic JSON layout renderer)
│   │   └── packages/storefront-ui (Mobile-first e-commerce UI component library)
│   │
│   ├── Order Management System (OMS)
│   │   ├── Deterministic State Machine (Pending -> Confirmed -> Shipped -> Delivered)
│   │   ├── In-Chat Quick Order Drawer
│   │   └── Fraud Risk Scoring Engine
│   │
│   ├── Delivery & Logistics Automation
│   │   ├── Courier Registry (Modular adapter framework)
│   │   ├── Pathao Courier Adapter
│   │   ├── Steadfast Courier Adapter
│   │   ├── RedX Adapter
│   │   ├── Paperfly Adapter
│   │   └── COD Settlement Service
│   │
│   ├── Data Sources & Catalog Synchronization
│   │   ├── Google Sheets Bi-Directional Synchronizer
│   │   ├── Bilingual Column Auto-Mapper (English & Bengali aliases)
│   │   └── Canonical Product Store Normalizer
│   │
│   ├── CRM & Sales Pipeline
│   │   ├── Visual Kanban Deals Board
│   │   ├── Customer 360° Detail Drawer
│   │   └── Append-Only Activity Logging Timeline
│   │
│   ├── Conversational AI Agents
│   │   ├── Adaptive RAG Engine (Hybrid pgvector + lexical search)
│   │   ├── Multimodal Processing Engine (Whisper STT & Lightweight OCR)
│   │   ├── Resilient Multi-Provider Model Router (GPT-4o, Claude 3.5, Gemini 1.5)
│   │   └── Prompt Guardrails & Jailbreak Defense
│   │
│   └── Customer Support Automation
│       ├── Unified Omnichannel Inbox
│       ├── Live Chat Web Widget
│       └── Human Takeover & Re-routing Controller
│
├── Platform Governance & Financials
│   ├── Super Admin Panel (Tenant feature flags & health monitor)
│   ├── Enterprise Billing & Redis Entitlement Cache
│   ├── Sentinel Security Framework (Rate limiters & parameterized queries)
│   └── AES-256-GCM Credential Vault
│
└── Developer Portal (Access Interface)
    ├── Public REST API
    ├── Outgoing Webhook Subscriptions (HMAC-SHA256 signed)
    └── Developer Client SDKs
```

---

## Component Interaction Flow

1. **Inbound Message Ingestion**: Customer inquiries arriving via WhatsApp, Facebook Messenger, Instagram DM, Telegram, or Web Chat are authenticated and normalized by the Ingress Gateway.
2. **Context Retrieval & Multimodal Pipeline**:
   * Voice notes are transcoded and transcribed into text via `VoiceService` (Whisper).
   * Image attachments are analyzed via lightweight OCR to extract barcodes/model numbers, querying the product database without expensive vision LLM calls.
   * Text queries pass to the **Adaptive RAG Engine**, executing hybrid searches across vector embeddings and database catalog rows.
3. **Conversational Commerce & Order Creation**:
   * When a customer decides to purchase, the AI Agent or human agent opens the **Quick Order Drawer** to assemble cart items, calculate zone-based delivery pricing, and place the order.
   * Stock is reserved atomically in the database to prevent overselling.
4. **Logistics Dispatch**:
   * Confirmed orders transition through the state machine to trigger the **Delivery Auto-Booking Service**.
   * The system invokes the designated courier adapter (Pathao, Steadfast, RedX, Paperfly) to generate a consignment and tracking number.
5. **Real-Time Tracking & Settlement**:
   * Couriers emit status webhooks back to AutoZeniq, updating orders to `SHIPPED` and `DELIVERED`.
   * The COD Settlement module reconciles courier remittance statements against order balances.

---

## FAQ

### Q: How do the Storefront Builder and Social Messenger channels share inventory?
**A:** Both the Storefront runtime and social messaging channels read from and write to the same centralized `products` and `product_variants` database tables. When stock decreases from a storefront purchase, the AI Agent on WhatsApp immediately knows the updated stock quantity.

---

## Related Documents

* [Entity Profile](./entity-profile.md)
* [Capabilities Catalog](./capabilities.md)
* [Storefront Builder](./products/store-builder.md)
* [Order Management System](./products/order-management.md)
* [Delivery & Logistics Automation](./products/delivery-logistics.md)
* [V2 System Architecture](./docs/system-architecture.md)
