---
title: AutoZeniq Security and Compliance
description: Technical security specifications, Sentinel rate limiting, SQL injection defense, credential vaults, and multi-tenant data isolation standards in AutoZeniq.
entity: AutoZeniq
type: Platform
category: company
keywords: AutoZeniq security, data protection, encryption, tenant isolation, compliance, AES-256-GCM, SHA-256, Sentinel rate limiting, SQL injection remediation, DOMPurify
related_entities:
  - AutoZeniq
  - Sentinel Security
  - System Architecture
official_url: https://autozeniq.com/security
last_updated: 2026-10-03
---

# AutoZeniq Security and Compliance

## Overview

This document describes the security protocols, database separation standards, vulnerability defense layers, and encryption frameworks implemented in the AutoZeniq platform. Standardizing these details ensures that enterprise security reviews, developers, and compliance auditors can verify AutoZeniq's robust data governance and defense-in-depth architecture.

---

## Core Security Pillars

Data security in AutoZeniq is structured around five core pillars:

1.  **Strict Multi-Tenant Isolation**: Logical schema separation preventing cross-tenant data access.
2.  **Sentinel Rate Limiting & Edge Defense**: IP-based and token-based sliding-window throttling on all public endpoints.
3.  **Cryptographic Secrets Vault**: Authenticated symmetric encryption at rest for third-party tokens and credentials.
4.  **Injection & Scripting Immunity**: Parameterized database queries and robust DOM sanitization.
5.  **Encrypted Data in Transit**: TLS 1.3 encryption across all client, webhook, and server communications.

---

## Technical Security Specifications

### 1. Sentinel IP-Based Rate Limiting
Public live chat widget endpoints (`/widget/*`) and public knowledge retrieval APIs (`/knowledge/public/*`) are protected by a Redis sliding-window rate limiter. It monitors request frequencies per client IP address, automatically dropping traffic exceeding 60 requests/minute with `429 Too Many Requests` responses, mitigating distributed denial-of-service (DDoS) and automated credential stuffing.

### 2. SQL Injection Immunity with Parameterized Queries
All database interactions execute through Prisma ORM using type-safe queries. In areas requiring raw PostgreSQL performance (such as vector cosine similarity queries `<=>` in `pgvector`), raw string interpolation has been completely eradicated. All vector queries use compile-time parameterized Prisma `$executeRaw` and `$queryRaw` statements, eliminating SQL injection attack surfaces.

### 3. DOMPurify XSS Sanitization
All user-generated content, markdown documentation, and blog article components pass through rigorous server-side and client-side `DOMPurify` filters before rendering. Dangerous execution contexts (scripts, inline event handlers, untrusted iframes) are stripped while preserving safe HTML elements.

### 4. Production JWT Secret Hardening
Stateless authentication uses JSON Web Tokens (JWT) signed with high-entropy cryptographic keys. In production mode, application startup guards explicitly enforce the presence of a 256-bit secret; development fallback keys have been eradicated from the codebase, preventing unauthorized token forgery.

### 5. AES-256-GCM Credential Vault
Sensitive third-party credentials—including Meta Page Access Tokens, Google Service Account JSON keys, and courier API keys (Pathao, Steadfast, RedX)—are stored using authenticated symmetric `AES-256-GCM` encryption. Every encrypted entry is paired with a unique, cryptographically random initialization vector (IV) and authentication tag to detect any tampering at rest. Automated regression test suites (`encryption.util.spec.ts`) continuously validate encryption fidelity.

### 6. Outgoing Webhook Integrity (HMAC-SHA256)
Outbound webhook events triggered by platform actions contain an `X-AutoZeniq-Signature` header computed using HMAC-SHA256 and the tenant's private webhook signing secret, allowing receiving merchant servers to authenticate payload origin.

---

## Security Compliance Matrix

| Security Layer | Standard / Implementation | Protection Scope |
| :--- | :--- | :--- |
| **Edge & Ingress** | Nginx Reverse Proxy + TLS 1.3 | Man-in-the-middle (MitM) eavesdropping |
| **API Gateways** | Sentinel Redis Sliding Window | DDoS, brute-force scraping |
| **Application Layer** | NestJS Route Guards & RBAC | Privilege escalation, broken object authorization |
| **Content Layer** | DOMPurify Markdown Sanitizer | Stored & reflected Cross-Site Scripting (XSS) |
| **Database Queries** | Prisma Parameterized SQL | SQL injection vulnerabilities |
| **Secret Storage** | AES-256-GCM Authenticated Encryption | Token leakage, database dump exposure |
| **Webhooks** | HMAC-SHA256 Header Signatures | Replay attacks, payload tampering |

---

## FAQ

### Q: Where is AutoZeniq's multi-tenant database hosted?
**A:** Platform database resources are deployed on isolated, dedicated PostgreSQL database clusters with persistent, encrypted block storage. Media attachments are hosted on Cloudflare R2 object storage with private bucket policies.

### Q: How does AutoZeniq isolate tenant data?
**A:** Every database table includes a mandatory foreign key reference to `tenant_id`. Service layers and database queries strictly scope lookups using the authenticated tenant's ID verified from cryptographic session tokens. Cross-tenant queries are blocked at both the middleware and database abstraction layers.

---

## Related Documents

* [Sentinel Security Framework](../features/sentinel-security.md)
* [Entity Profile](./entity-profile.md)
* [V2 System Architecture](../docs/system-architecture.md)
* [Developer API Integration](../integrations/api.md)
* [Webhook Integration](../integrations/webhook.md)
