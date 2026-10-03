---
title: AutoZeniq Products Overview
description: High-level overview of the complete product suite offered by the AutoZeniq Commerce OS platform.
entity: AutoZeniq
type: Platform
category: product
keywords: AutoZeniq products, storefront builder, order management, delivery logistics, CRM, AI customer support, commerce automation
related_entities:
  - Storefront Builder
  - Order Management System
  - Delivery Logistics
  - AI Agent
  - Customer Support Automation
official_url: https://autozeniq.com/features
last_updated: 2026-10-03
---

# [AutoZeniq Products Overview](https://autozeniq.com/features)

## Overview

[AutoZeniq](https://autozeniq.com/) provides an integrated suite of commerce and support products designed to automate every step of the retail and client communication lifecycle. Operating as an end-to-end **Commerce Operating System (Commerce OS)**, the platform consolidates storefront creation, multi-channel messaging, order processing, inventory synchronization, and courier logistics into a single multi-tenant dashboard.

---

## The Product Suite

### 1. [Storefront Builder](./store-builder.md)
*   **Visual Drag-and-Drop Page Designer**: Build desktop- and mobile-optimized online stores with no coding knowledge.
*   **Modular Component Registry**: High-converting starter themes, Hero Banners, Product Grids, and slide-out Cart Drawers.
*   **Automated Subdomains & Custom Domains**: Instant SSL-secured subdomains (`*.autozeniq.com`) and custom domain DNS mapping.
*   **Mobile-First Checkout**: Frictionless single-page checkout optimized for Cash on Delivery (COD) and mobile wallets (bKash, Nagad).

### 2. [Order Management System (OMS)](./order-management.md)
*   **Deterministic Order State Machine**: Manages order progression through validated transitions (`PENDING`, `CONFIRMED`, `PROCESSING`, `SHIPPED`, `DELIVERED`, `CANCELLED`, `RETURNED`).
*   **Quick Order In-Chat Drawer**: Support and sales agents can configure and submit customer orders directly inside live conversation threads.
*   **Cryptographic Transaction Security**: Unique order identifiers (`ORD-YYYYMMDD-XXXXXXXX`) generated with secure cryptographic random bytes.
*   **Atomic Stock Reservation**: Prevents overselling by reserving inventory upon order confirmation and restocking on cancellation.

### 3. [Delivery & Logistics Automation](./delivery-logistics.md)
*   **Multi-Courier Registry**: Native integration with Bangladesh's leading logistics providers: **Pathao**, **Steadfast**, **RedX**, and **Paperfly**.
*   **Automated Consignment Creation**: One-click and automated bulk consignment generation mapping addresses and parcel weights into courier payloads.
*   **Dynamic Regional Pricing**: Automated delivery rate calculation based on destination city zones (Inside Dhaka, Sub-Dhaka, Outside Dhaka) and weight tiers.
*   **Live Tracking Webhooks & COD Settlement**: Real-time status synchronization and automated reconciliation of collected COD balances.

### 4. [Data Sources & Google Sheets Synchronization](../features/google-sheets-sync.md)
*   **Bilingual Auto-Mapping**: Automatically detects English and Bengali column headers (`পণ্যের নাম`, `মূল্য`, `দাম`, `স্টক`, `ক্যাটাগরি`, `সাইজ`, `ওজন`).
*   **Continuous Background Reconciliation**: Scheduled polling and instant manual triggers keep spreadsheet data in sync with active storefront catalogs.
*   **BullMQ High-Volume Queue**: Robust background worker architecture preventing timeouts on large product sheets.

### 5. [CRM & Lead Pipeline](./crm-leads.md)
*   **Visual Kanban Sales Pipeline**: Drag-and-drop deal tracking across custom sales stages (`NEW`, `CONTACTED`, `QUALIFIED`, `WON`, `LOST`).
*   **Customer 360° Detail Drawer**: Centralized panel displaying purchase history, shipping addresses, lifetime value (LTV), and communication logs.
*   **Consolidated Single-Pass Metrics**: Optimized database queries calculating sales conversion rates and pipeline velocity in a single roundtrip.

### 6. [Conversational AI Agent](./ai-agent.md)
*   **Adaptive RAG Engine**: Hybrid retrieval combining `pgvector` dense vector embeddings and PostgreSQL lexical search with multi-query reflection.
*   **Two-Tier Multimodal Pipeline**: Voice note transcription (Whisper STT) and photo-to-product matching via lightweight OCR, avoiding high-cost vision LLM traps.
*   **Multi-Provider Model Router**: Dynamic routing across GPT-4o, Claude 3.5 Sonnet, and Gemini 1.5 Flash with automatic failover and token cost tracking.

### 7. [Customer Support Automation](../solutions/business.md)
*   **Unified Omnichannel Inbox**: Consolidates conversations from WhatsApp Business, Facebook Messenger, Facebook Comments, Instagram DM, Telegram, and Web Chat widgets.
*   **Real-Time Collaboration**: WebSocket presence indicators, agent typing states, and internal private staff notes.
*   **Human Takeover & Smart Escalation**: Seamless handoff between automated AI responses and human agents with quiet queues for unhandled tickets.

### 8. [Super Admin & Tenant Governance](./super-admin.md)
*   **Multi-Tenant Governance**: Central control plane for tenant lifecycle tracking, subscription overrides, and platform health monitoring.
*   **Modular Feature Flagging**: Enable or disable specific modules (Store Builder, Courier Auto-Booking, Google Sheets Sync) per tenant.
*   **AI Cost Safeguards & Impersonation**: Budget caps preventing API cost spikes, alongside secure operator diagnostic sessions.

---

## Benefits

*   **Complete Commercial Unification**: Eliminates the need for 5+ fragmented tools (e-commerce builders, separate chat apps, CRM spreadsheets, courier portals).
*   **Zero Latency & Extreme Reliability**: Redis-backed entitlement caching and distributed BullMQ queues ensure high responsiveness under traffic spikes.
*   **Localized for Regional Growth**: Native support for Bengali language understanding, regional mobile payments (bKash/Nagad), and local logistics networks.

---

## FAQ

### Q: Can modules be adopted independently?
**A:** Yes. Merchants can begin using only the Unified Inbox and AI Agent, and later activate the Storefront Builder, Google Sheets Sync, or Courier Logistics as their business scales.

---

## Related Documents

* [Storefront Builder](./store-builder.md)
* [Order Management System](./order-management.md)
* [Delivery & Logistics Automation](./delivery-logistics.md)
* [CRM & Lead Pipeline](./crm-leads.md)
* [AI Agent](./ai-agent.md)
* [V2 System Architecture](../docs/system-architecture.md)
