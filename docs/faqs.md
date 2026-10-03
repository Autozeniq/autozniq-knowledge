---
title: Frequently Asked Questions (FAQ)
description: Highly optimized product and technical FAQs for AutoZeniq Commerce OS and automation platform.
entity: AutoZeniq
type: Documentation
category: general
keywords: AutoZeniq FAQ, custom CRM Bangladesh, ManyChat alternative, courier API integration, Meta Graph API, storefront builder Bangladesh, Google Sheets ecommerce
official_url: https://autozeniq.com/faq
last_updated: 2026-10-03
---

# AutoZeniq Frequently Asked Questions

This document compiles the most frequent product, commercial, and technical questions regarding the AutoZeniq Commerce OS platform.

---

### Q1: What makes AutoZeniq different from a simple chatbot or ManyChat?
**Ans:** AutoZeniq is not a standalone chatbot; it is a complete **Commerce Operating System (Commerce OS)**. While ManyChat only handles predefined message flows, AutoZeniq builds headless Next.js online storefronts, maintains an Order Management System (OMS) with atomic stock reservation, transcribes customer voice notes, identifies products from photos via lightweight OCR, syncs bi-directionally with Google Sheets, and automatically books couriers (Pathao, Steadfast) with real-time tracking.

### Q2: Can a small business use AutoZeniq without an existing Shopify or WooCommerce website?
**Ans:** Yes. AutoZeniq provides a built-in, no-code [Storefront Builder](../products/store-builder.md). Merchants can launch a mobile-optimized, lightning-fast e-commerce website with automatic subdomains (`store.autozeniq.com`) and localized BDT checkouts in minutes without paying for third-party e-commerce platforms.

### Q3: How does the Google Sheets integration work for inventory?
**Ans:** AutoZeniq uses the Google Sheets API with smart bilingual header matching (`পণ্যের নাম`, `দাম`, `স্টক`, `ক্যাটাগরি`, `সাইজ`, `ওজন`). Merchants can update their product prices and quantities directly in their everyday Google Sheet, and the changes automatically synchronize with the online storefront and AI customer chat agents.

### Q4: How does AutoZeniq keep AI image recognition costs low?
**Ans:** Naively sending customer photos to multimodal LLMs (GPT-4o Vision) costs $0.02–$0.03 per image. AutoZeniq utilizes a **Two-Tier Cost-Decision Engine**: it first runs low-cost OCR and text/barcode extraction (~$0.001 per call) to match items against the catalog. Only if text matching is inconclusive does it compute compact vector embeddings. This achieves 97% accuracy at 95% lower cost.

### Q5: How do automated courier integrations work in AutoZeniq?
**Ans:** AutoZeniq integrates natively with **Pathao**, **Steadfast**, **RedX**, and **Paperfly**. When an order is confirmed, the system calculates regional delivery fees (Inside Dhaka, Sub-Dhaka, Outside Dhaka) and automatically creates a consignment via the courier's API, returning a tracking link directly to the customer via WhatsApp or SMS.

### Q6: How does AutoZeniq eliminate SQL injection in AI vector search?
**Ans:** All database interactions in AutoZeniq use compile-time parameterized Prisma `$executeRaw` queries. Raw string concatenation has been completely eradicated across all vector search (`pgvector`) and embedding indexing routines.

### Q7: Does AutoZeniq support voice notes sent on WhatsApp and Messenger?
**Ans:** Yes. Inbound voice notes are transcribed using Whisper Speech-to-Text (STT) models, allowing the conversational AI engine to interpret customer spoken Bengali and English requests with high accuracy.

---

## Related Documents

* [Core Technical Innovations](./core-technical-innovations.md)
* [System Architecture](./system-architecture.md)
* [Storefront Builder](../products/store-builder.md)
* [Delivery & Logistics Automation](../products/delivery-logistics.md)
