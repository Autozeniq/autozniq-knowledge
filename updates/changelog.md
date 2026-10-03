---
title: AutoZeniq Product Changelog
description: Official product release logs, updates, and feature additions for the AutoZeniq Commerce OS platform.
entity: AutoZeniq
type: Platform
category: updates
keywords: AutoZeniq updates, product releases, changelog, features log, integrations launch, Commerce OS releases
related_entities:
  - AI Agent
  - Customer Support Automation
  - Storefront Builder
  - Order Management System
  - Delivery Logistics
official_url: https://autozeniq.com/changelog
last_updated: 2026-10-03
---

# [AutoZeniq Product Changelog](https://autozeniq.com/changelog)

## Overview

This changelog documents the continuous release history, architecture upgrades, performance optimizations, and security patches for the AutoZeniq Commerce OS platform.

---

## Release History

### Version 2.4 (September – October 2026)
*   **Storefront Builder Production Release**:
    *   Containerized `apps/storefront` Next.js runtime with dynamic Nginx wildcard subdomain routing (`*.autozeniq.com`) and custom domain DNS mapping.
    *   Optimized theme page provisioning queries, enabling instant store instantiation for new workspaces.
    *   Added full suite of composable blocks: HeroBanner, ProductGrid, CategoryGrid, CartDrawer, and localized BDT checkout.
*   **Order Management System (OMS) & State Machine**:
    *   Implemented deterministic status transition state machine with mathematical validation guards (`PENDING` -> `CONFIRMED` -> `PROCESSING` -> `SHIPPED` -> `DELIVERED`).
    *   Implemented cryptographically random, non-sequential order identifiers (`ORD-YYYYMMDD-XXXXXXXX`).
    *   Eliminated N+1 database queries during multi-variant order creation via batch pre-fetching.
    *   Integrated fraud detection scoring and high-risk customer warning badges.
*   **Sentinel Security Hardening Framework**:
    *   **Public Rate Limiting**: Added Redis sliding-window IP rate limiting to public widget (`/widget/*`) and knowledge search endpoints (`/knowledge/public/*`).
    *   **SQL Injection Remediation**: Replaced raw string interpolation `$executeRawUnsafe` with type-safe, parameterized Prisma `$executeRaw` across all vector search and embedding processing routines.
    *   **XSS Protection**: Implemented `DOMPurify` sanitization for all markdown, documentation, and blog article renderers.
    *   **Production JWT Secret Enforcement**: Eliminated insecure development fallback secrets; enforced strict startup validation in production.
    *   **AES-256-GCM Credential Vault**: Enhanced encryption utility with automated regression test suites (`encryption.util.spec.ts`) for third-party OAuth and courier tokens.
*   **Bolt Performance Optimization Initiative**:
    *   Consolidated lead metrics calculation into a single-pass SQL aggregation.
    *   Eliminated N+1 queries in the Redis Entitlement Cache service and data source listing endpoints.
    *   Optimized database seeding loops for tenant features, industries, and integrations.

### Version 2.3 (August – September 2026)
*   **Automated Delivery & Multi-Courier Logistics**:
    *   Introduced the extensible `CourierRegistry` integrating **Pathao**, **Steadfast**, **RedX**, and **Paperfly**.
    *   Implemented automated single-click and bulk consignment booking directly from the order dashboard.
    *   Built dynamic delivery pricing engine factoring destination city zones (Inside Dhaka, Suburbs, Outside Dhaka) and parcel weight tiers.
    *   Integrated inbound delivery tracking webhooks and Cash on Delivery (COD) settlement reconciliation.
*   **Data Sources & Google Sheets Synchronization**:
    *   Built bi-directional Google Sheets sync service with OAuth and Service Account authentication.
    *   Implemented bilingual column header auto-mapping (recognizing Bengali aliases like `পণ্যের নাম`, `মূল্য`, `দাম`, `স্টক`, `ক্যাটাগরি`, `সাইজ`, `ওজন`).
    *   Added automatic tab classification (Products, FAQs, Policies, Knowledge) and BullMQ background queue processing with live WebSocket progress bars.
*   **CRM & Sales Pipeline Module**:
    *   Launched visual Kanban sales pipeline tracking deals across custom stages (`NEW`, `CONTACTED`, `QUALIFIED`, `WON`, `LOST`).
    *   Introduced Customer 360° Detail Drawer with lifetime order value, communication transcripts, and append-only activity timeline.
*   **In-Chat Quick Order Creation**:
    *   Engineered slide-out Quick Order drawer inside customer conversation threads, allowing agents to configure products, variants, and shipping addresses without leaving the chat.

### Version 2.2 (July – August 2026)
*   **Meta Platform Native OAuth Connection**:
    *   Introduced one-click Meta Business Login popup dialog for Facebook Pages, Messenger, and Instagram Direct Messaging.
    *   Configured Cross-Origin-Opener-Policy (COOP) headers (`same-origin-allow-popups`) for secure window message exchange.
    *   Implemented daily token validation cron worker and automatic long-lived token renewal.
*   **Multimodal AI & Cost-Decision Engine**:
    *   Deployed voice note processing pipeline using Whisper STT for customer audio messages on WhatsApp and Messenger.
    *   Engineered lightweight OCR-first image processing pipeline, extracting text and barcodes to match products from customer screenshots without expensive vision LLM fees.
*   **Enterprise Billing & Entitlements Engine**:
    *   Introduced tiered subscription plans (Starter, Growth, Enterprise) with modular capability feature flagging.
    *   Engineered Redis-backed Entitlement Cache service for sub-millisecond route guard checks.
    *   Integrated **SSLCommerz** payment gateway for seamless BDT subscription payments via bKash, Nagad, and credit cards.
*   **Super Admin Governance Control Plane**:
    *   Added global tenant administration, per-tenant feature module toggling, AI cost safeguards, operator impersonation sessions, and immutable audit logging.

### Version 2.1 (July 2026)
*   **Adaptive RAG 2.0**:
    *   Implemented hybrid retrieval combining dense vector similarity (`pgvector` HNSW indexes) and PostgreSQL lexical search with Reciprocal Rank Fusion.
    *   Added multi-query reflection for ambiguous customer inquiries across English, standard Bengali, and Banglish.
    *   Built multi-stage confidence scoring to seamlessly escalate uncertain queries to human agents.
*   **Resilient Multi-Provider Model Router**:
    *   Dynamic prompt routing across OpenAI GPT-4o, Anthropic Claude 3.5 Sonnet, and Google Gemini 1.5 Flash with automatic failover and token cost tracking.
*   **Public CMS & Blog Platform**:
    *   Launched high-converting public blog platform with automated SEO schemas, reading progress tracking, table of contents, and AI-generated article summaries.
*   **Real-Time Notifications**:
    *   Integrated Firebase Cloud Messaging (FCM) and real-time WebSocket hooks with React Query cache invalidation.

### Version 2.0 (June 2026)
*   **One-Click Meta Login**: Introduced Meta OAuth popup dialog supporting Facebook Pages and Messenger channels.
*   **WhatsApp Embedded Signup**: Added embedded registration flow for WhatsApp Business Accounts (WABA).
*   **Token Validation Cron**: Scheduled worker verifying social channel token validity daily.
*   **Theme Toggle & i18n**: Dark and light theme modes across dashboard with bilingual English and Bengali interface localization.

### Version 1.5 (May 2026)
*   **Public REST API Release**: Launched Developer Portal with SHA-256 API key hashing and scoping.
*   **Outgoing Webhook Subscriptions**: Built HMAC-SHA256 signed event delivery with BullMQ retries.
*   **Embeddable Live Chat Widget**: Released JavaScript website live chat widget with real-time Socket.IO synchronization.

### Version 1.0 (March 2026)
*   **Multi-Tenant Dashboard Architecture**: Official release of multi-tenant workspace isolation.
*   **Omnichannel Inbox**: Integrated incoming message routers for Facebook Messenger, Telegram, and web widgets.
*   **RAG Knowledge Base**: Implemented vector indexing using PostgreSQL `pgvector`.
*   **Rule Engine**: Introduced conditional keyword triggers and automated lead detection classifiers.

---

## FAQ

### Q: Where are technical updates, security advisories, and schema changes announced?
**A:** Technical release notes are updated in this changelog. Security advisories, breaking API changes, and schema updates are communicated directly through the Developer Portal and Super Admin dashboard.

---

## Related Documents

* [Products Overview](../products/overview.md)
* [Capabilities Catalog](../capabilities.md)
* [V2 System Architecture](../docs/system-architecture.md)
* [Sentinel Security & Hardening](../features/sentinel-security.md)
