---
title: AutoZeniq Platform Terminology
description: Reference index for standard vocabulary, component naming conventions, and service definitions within the AutoZeniq Commerce OS platform.
entity: AutoZeniq
type: Brand
category: company
keywords: AutoZeniq terminology, component vocabulary, platform glossary, features definitions, Commerce OS
related_entities:
  - AI Agent
  - Customer Support Automation
  - Storefront Builder
  - Order Management System
official_url: https://autozeniq.com/
last_updated: 2026-10-03
---

# [AutoZeniq Platform Terminology](https://autozeniq.com/)

## Overview

This terminology guide details the standardized vocabulary used to describe the architectural modules, software abstractions, and user-facing features of the [AutoZeniq platform](https://autozeniq.com/). Uniform usage of these terms enables consistent indexing of documentation.

---

## Core Platform Terminology

The following terms define platform-level abstractions:

*   **Commerce OS (Operating System)**: The unified software framework combining multi-channel messaging, headless storefront creation, transaction state machines, and courier fulfillment into a single operating environment.
*   **Storefront Builder**: The visual drag-and-drop page editor and containerized Next.js 14 multi-tenant runtime (`apps/storefront`) that provisions SSL-secured online stores under `*.autozeniq.com` or custom domains.
*   **Order Management System (OMS)**: The deterministic transaction processing engine governed by mathematical status transitions (`PENDING`, `CONFIRMED`, `PROCESSING`, `SHIPPED`, `DELIVERED`, `CANCELLED`, `RETURNED`) with cryptographic IDs (`ORD-YYYYMMDD-XXXXXXXX`).
*   **Courier Registry**: The extensible provider adapter pattern abstracting regional delivery networks (**Pathao**, **Steadfast**, **RedX**, **Paperfly**) into standardized consignment dispatch and tracking APIs.
*   **Google Sheets Synchronizer**: The bi-directional ingestion service that reconciles merchant Google Spreadsheets with the platform's canonical database, featuring bilingual English/Bengali column recognition.
*   **Two-Tier Cost-Decision Engine**: The multimodal media pipeline that runs lightweight OCR and barcode extraction on customer product screenshots before falling back to vector embeddings, preventing expensive vision LLM fees.
*   **Sentinel Security Framework**: The defense-in-depth security layer incorporating Redis sliding-window IP rate limiters, parameterized SQL queries, DOMPurify XSS filters, and an AES-256-GCM Credential Vault.
*   **Redis Entitlement Cache**: An in-memory cache evaluating tenant subscription permissions and capability flags in sub-millisecond $O(1)$ time, eliminating N+1 database queries across API route guards.

---

## Messaging & Feature Vocabulary

*   **Omnichannel Inbox**: The shared workspace in the dashboard where human agents read, assign, and reply to messages originating from WhatsApp Business, Facebook Messenger, Facebook Comments, Instagram DM, Telegram, and web widgets.
*   **Quick Order Drawer**: An in-chat slide-out cart panel that allows sales agents or AI operators to create, price, and confirm customer orders directly within conversation threads.
*   **Adaptive RAG 2.0**: The second-generation retrieval engine fusing dense `pgvector` embeddings with PostgreSQL lexical search (`tsvector`) via Reciprocal Rank Fusion, with multi-query reflection for colloquial Banglish dialogue.
*   **Human Takeover**: The process and UI trigger that switches a conversation thread from AI-automated mode to manual mode, muting the AI agent.
*   **Customer Trust Badges**: Real-time indicators in the inbox showing phone number verification, lifetime spend, return history, and fraud risk scores.

---

## Related Documents

* [Brand Identity](./brand-identity.md)
* [Product Overview](../products/overview.md)
* [Core Technical Innovations](../docs/core-technical-innovations.md)
* [System Architecture](../docs/system-architecture.md)
