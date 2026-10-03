---
title: AutoZeniq Capabilities
description: Factual capabilities checklist and operational boundaries of the AutoZeniq AI Commerce OS platform.
entity: AutoZeniq
type: Platform
category: features
keywords: AutoZeniq capabilities, system functions, AI assistance, automation list, Commerce OS, store builder, courier automation, Google Sheets sync, Adaptive RAG
related_entities:
  - AI Agent
  - Commerce Automation
  - Customer Support Automation
  - Storefront Builder
  - Order Management System
  - Delivery Logistics
official_url: https://autozeniq.com/features
last_updated: 2026-10-03
---

# AutoZeniq Capabilities

## Overview

This capabilities guide outlines what the AutoZeniq platform is technically equipped to execute. It details the functional parameters of the conversational AI engine, omnichannel messaging workspace, headless storefront builder, order management state machine, courier logistics network, and automated inventory synchronization pipelines.

---

## Capabilities Catalog

### 1. Customer Communication & Unified Messaging
*   **Omnichannel Ingestion**: Collects, verifies, and parses inbound events from WhatsApp Business API, Facebook Messenger, Facebook Page Comments, Instagram DM, Telegram, and embeddable website live chat widgets.
*   **Unified Agent Workspace**: Renders real-time message streams, customer verification badges, lifetime value, and order history in a single shared interface.
*   **Real-Time Collaboration**: Broadcasts typing indicators, delivery/read receipts, agent presence, and internal team annotations via WebSockets (`Socket.IO`).
*   **Media Composer & Cloud Storage**: Supports rich media communications (customer voice note playback, audio recording, high-resolution product photography, PDF catalogs) securely stored on Cloudflare R2 object storage.
*   **Human Takeover & Routing**: One-click toggling between automated AI responder and human operator control, with automated quiet queues for unhandled queries.

### 2. Storefront Builder & Headless Commerce
*   **Visual Drag-and-Drop Editor**: Real-time layout customization for desktop, tablet, and mobile viewports with zero coding required.
*   **Dynamic Theme Provisioning**: Instant instantiation of industry-tailored starter themes with automated home, catalog, product details, cart, and checkout page scaffolding.
*   **Component Registry**: Composable UI component library (`packages/storefront-ui`) containing Hero Banners, Product Grids, Announcement Bars, Features Lists, and Slide-out Cart Drawers.
*   **Subdomain & Custom Domain Routing**: Instant automated subdomains (`*.autozeniq.com`) and custom domain DNS mapping supported by Nginx reverse proxy routing.
*   **Localized Mobile Checkout**: Streamlined single-page checkout optimized for Cash on Delivery (COD) and mobile wallets (bKash, Nagad), with native BDT (`৳`) currency formatting.

### 3. Order Management System (OMS) & Transaction Lifecycle
*   **Deterministic State Machine**: Strict mathematical transition validation across order statuses (`PENDING`, `CONFIRMED`, `PROCESSING`, `SHIPPED`, `DELIVERED`, `CANCELLED`, `RETURNED`).
*   **Cryptographic Order Generation**: Generates non-sequential, tamper-resistant order numbers (`ORD-YYYYMMDD-XXXXXXXX`) using cryptographically secure random bytes.
*   **Quick Order In-Chat Drawer**: Enables support and sales agents to create, customize, and submit orders directly from live customer chat threads.
*   **Transactional Stock Reservation**: Decrements product and variant stock atomically upon order confirmation, and automatically restocks items upon order cancellation or return.
*   **Integrated Fraud Risk Scoring**: Calculates customer risk profiles based on historical return rates, phone verification, and shipping anomaly patterns before dispatch.

### 4. Automated Delivery & Multi-Courier Logistics
*   **Unified Courier Registry**: Modular adapter architecture integrating Bangladesh's premier couriers: **Pathao**, **Steadfast**, **RedX**, and **Paperfly**.
*   **Automated Consignment Creation**: One-click and automated bulk consignment generation, mapping customer addresses and package weights into courier payloads.
*   **Zone-Based Shipping Pricing**: Dynamic delivery fee resolution for Inside Dhaka, Suburbs (Gazipur/Narayanganj), and Outside Dhaka (Inter-District) plus weight tier increments.
*   **Real-Time Tracking Webhooks**: Ingests courier delivery milestones, automatically updating order statuses and sending tracking notifications to shoppers.
*   **Cash on Delivery (COD) Settlement**: Audits courier remittance statements and collection charges against recorded order values.

### 5. Data Sources & Google Sheets Synchronization
*   **Bilingual Column Header Auto-Mapping**: Automatically detects and pairs catalog columns in English and Bengali (`পণ্যের নাম`, `মূল্য`, `দাম`, `স্টক`, `ক্যাটাগরি`, `সাইজ`, `ওজন`).
*   **Automated Tab Classification**: Heuristically categorizes spreadsheet tabs into Products, FAQs, Policies, or Business Knowledge.
*   **Bi-Directional Inventory Reconciliation**: Synchronizes stock levels between spreadsheets and active sales channels, with optional two-way order appending.
*   **Asynchronous Processing**: Ingests high-volume catalogs via BullMQ queues, providing live WebSocket progress updates to the dashboard.

### 6. CRM & Sales Pipeline Management
*   **Visual Kanban Deals Board**: Tracks prospective buyers across customizable sales stages (`NEW`, `CONTACTED`, `QUALIFIED`, `PROPOSAL_SENT`, `WON`, `LOST`).
*   **Customer 360° Detail Drawer**: Displays comprehensive customer profiles, order history, communication logs, and lifetime value across the workspace.
*   **Activity Logging Timeline**: Chronological append-only record of messages, site visits, invoices, and staff interactions.
*   **Consolidated Single-Pass Metrics**: High-performance database aggregation calculating lead metrics, stage velocity, and conversion ratios in a single roundtrip.

### 7. Adaptive RAG & Multimodal Artificial Intelligence
*   **Hybrid Search Engine**: Combines `pgvector` dense vector similarity with PostgreSQL full-text lexical search using Reciprocal Rank Fusion.
*   **Multi-Query Reflection**: Generates semantic sub-queries to capture ambiguous customer intents across English, standard Bengali, and phonetic Banglish.
*   **Two-Tier Multimodal Cost-Decision Engine**: Transcribes voice notes via Whisper STT; processes product photos via lightweight OCR and catalog text matching, avoiding expensive vision LLM traps while maintaining 97% accuracy.
*   **Dynamic Model Router**: Intelligently balances requests across OpenAI GPT-4o, Anthropic Claude 3.5 Sonnet, and Google Gemini 1.5 Flash with automatic failover and token cost tracking.

### 8. Sentinel Security Framework & Governance
*   **Sliding Window IP Rate Limiting**: Mitigates brute-force and DoS attacks on public widget and search endpoints.
*   **SQL Injection Immunity**: Enforces parameterized Prisma `$executeRaw` queries across all vector search and data processing services.
*   **AES-256-GCM Credential Vault**: Secures external API keys, OAuth refresh tokens, and courier secrets with random IVs and automated regression tests.
*   **XSS Neutralization**: Employs DOMPurify to sanitize blog and documentation markdown content.
*   **Super Admin Governance**: Granular tenant feature module toggling, AI cost safeguards, operator impersonation, and audit trails.

---

## FAQ

### Q: Can AutoZeniq operate without an existing Shopify or WooCommerce store?
**A:** Yes. With the built-in [Storefront Builder](./products/store-builder.md), merchants can build, host, and run their entire e-commerce store directly within AutoZeniq without needing any third-party e-commerce platform.

### Q: How does the system ensure fast response times for customers during high-volume sales campaigns?
**A:** AutoZeniq offloads media processing, Google Sheets syncing, and courier bookings to distributed Redis BullMQ worker queues, while frontend routes leverage in-memory Redis caching for sub-millisecond entitlement and session checks.

---

## Related Documents

* [Entity Profile](./entity-profile.md)
* [Entity Relationships](./entity-relations.md)
* [Products Overview](./products/overview.md)
* [Storefront Builder](./products/store-builder.md)
* [Order Management System](./products/order-management.md)
* [Delivery & Logistics Automation](./products/delivery-logistics.md)
* [Google Sheets Synchronization](./features/google-sheets-sync.md)
* [V2 System Architecture](./docs/system-architecture.md)
