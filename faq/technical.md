---
title: AutoZeniq Technical & Architecture FAQ
description: Technical frequently asked questions about database models, RAG vector similarity, Two-Tier Cost-Decision Engine, and Sentinel security in AutoZeniq.
entity: AutoZeniq
type: FAQ
category: faq
keywords: AutoZeniq technical faq, pgvector search, cost decision engine, SQL injection fix, Redis entitlement cache, Nginx subdomain routing
related_entities:
  - Security and Compliance
  - System Architecture
  - Core Technical Innovations
official_url: https://autozeniq.com/faq
last_updated: 2026-10-03
---

# AutoZeniq Technical & Architecture FAQ

This document addresses technical questions regarding system architecture, database partitioning, data encryption, and AI semantic processing on the AutoZeniq platform.

---

## FAQ

### Q: How does the Two-Tier Cost-Decision Engine work for customer product photos?
**A:** Naively sending customer images to multimodal LLMs (GPT-4o Vision) costs $0.02–$0.03 per image. AutoZeniq runs a **Two-Tier Cost-Decision Engine**:
1.  **Tier 1**: Uploads the photo to Cloudflare R2; executes low-cost OCR and text extraction (~$0.001/call) to parse printed brand names, barcodes, or model numbers. If an exact catalog match is found, product specs are injected into an economical model (Gemini 1.5 Flash).
2.  **Tier 2**: Only if OCR yields no conclusive text does the system compute a compact vector embedding and run a `pgvector` similarity search.
This achieves 97% recognition accuracy while reducing inference costs by ~95%.

### Q: How did AutoZeniq eliminate SQL injection vulnerabilities in AI vector search?
**A:** All database calls across the platform execute via compile-time parameterized Prisma `$executeRaw` and `$queryRaw` statements with strict variable binding. Raw string interpolation and `$executeRawUnsafe` have been completely removed from `knowledge.service.ts` and `embedding.processor.ts`.

### Q: How does the Redis Entitlement Cache prevent N+1 query bottlenecks?
**A:** To avoid querying tenant subscription tables on every incoming HTTP request, the `EntitlementCacheService` computes tenant capability flags (e.g. `MODULE_STORE_BUILDER`, `MODULE_DELIVERY_AUTO_BOOK`) and stores them in Redis memory. The `SubscriptionGuard` executes sub-millisecond $O(1)$ memory checks before controller execution, with selective cache eviction triggered only upon plan changes.

### Q: How does Nginx wildcard subdomain routing work for the Storefront runtime?
**A:** Nginx listens on `*.autozeniq.com` and custom CNAME domains, passing the `Host` header to the single containerized Next.js 14 `apps/storefront` runtime. The runtime's `lib/domain-resolver.ts` parses the hostname, queries the tenant's layout schema from the database, and renders the corresponding store dynamically.

### Q: How are third-party credentials and keys secured?
**A:** Meta Page Access Tokens, Google Service Account JSON keys, and courier API secrets are encrypted at rest using authenticated symmetric `AES-256-GCM` encryption with cryptographically random initialization vectors (IV) in the `CredentialVaultService`.

---

## Related Documents

* [Core Technical Innovations](../docs/core-technical-innovations.md)
* [System Architecture](../docs/system-architecture.md)
* [Sentinel Security & Hardening](../../features/sentinel-security.md)
* [Two-Tier Multimodal Processing](../../features/multimodal-processing.md)
