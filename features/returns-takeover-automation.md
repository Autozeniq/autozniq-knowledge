---
title: Returns and Human Takeover Automation
description: Operational details, hybrid intent classification, return draft confirmation loops, order validation, and safety human takeover controls.
entity: AutoZeniq
type: Feature
category: features
keywords: AutoZeniq returns, exchange automation, human takeover, intent classification, AI action log, priority rules, support ticket
related_entities:
  - AI Agent
  - Support Tickets
  - Returns Management
official_url: https://autozeniq.com/features/returns-takeover
last_updated: 2026-07-01
---

# Returns and Human Takeover Automation

## Overview

The AutoZeniq **Returns and Human Takeover Automation** module manages customer return/exchange requests, handles support ticket escalations, and enforces strict human takeover mechanisms. Grounded in actual order history and protected by a two-step confirmation loop, it ensures high-risk operations are executed accurately and safely.

---

## Technical Architecture

The module operates as an intelligent workflow gatekeeper:

### Simple Explanation
When a customer asks to return or exchange a product, the AI checks their last delivered order. It verifies that they actually bought the product, checks the allowed return window, and drafts a return request. The AI will never book a return automatically; instead, it presents a summary and waits for the customer to type "Confirm Return". If the customer complains about a bad experience or legal matters, the AI immediately pauses itself, escalates the ticket priority, and alerts a human representative.

### Technical Explanation
1.  **Hybrid Intent Classification (`classifyIntentV2`)**:
    *   Pre-filters incoming text using keyword matching.
    *   Triggers a fast-timeout LLM prompt to verify intent (`return_exchange` vs `support_ticket` vs `general`) with a fallback safety net.
    *   Loads the dynamic `aiConfidenceThreshold` from `TenantModuleSettings` (defaulting to `0.85`) to block low-confidence AI routing.
2.  **Order-History Extraction & Validation**:
    *   Retrieves the customer's last delivered order.
    *   Uses LLM parsing to extract request details (`type`, `items` array with `orderItemId` & `quantity`, and `reason`).
    *   Enforces strict business limits: blocks drafts if requested items are not in the order, if requested quantity exceeds purchased quantity, or if the policy return window (e.g. 7 days) has expired.
3.  **Two-Step Confirmation Loop**:
    *   Saves the valid parameters as a temporary `returnDraft` object on the `Conversation` database model with a `returnDraftExpiresAt` timestamp (set to 24 hours).
    *   Requires the customer to explicitly text `"Confirm Return"` or `"Cancel Return"`. If expired, it refuses confirmation and requests a restart.
    *   Creates the final `ReturnRequest` record upon confirmation and logs the audit trail to `AiActionLog`.
4.  **Rule-Based Support Escalation**:
    *   On detecting complaints, classifies the subject, category, and priority using the LLM.
    *   Applies a priority override rule: pushes priority to `high` or `critical` if phrases relating to payment disputes (`টাকা কেটে`, `payment deducted`), legal actions (`court`, `মামলা`), or extreme anger are detected.
    *   Sets conversation state to `aiState: paused` with `pausedReason: support_escalation` and `pausedAt: new Date()`, disabling auto-replies.
    *   Dispatches WebSocket updates, push notifications, and in-app alerts to dashboard agents.

---

## Core Features

*   **Bilingual Parsing**: Extracts return details and reasons from Bengali, English, or mixed (Banglish) messages.
*   **Automatic Handover**: Pauses AI responses instantly when a customer requests human help or files a complaint.
*   **Audit Logging**: Writes immutable records of all automated actions and drafts to the `AiActionLog` table.
*   **Dynamic Policies**: Adapts validation rules based on tenant-specific settings for return and exchange windows.

---

## Benefits

*   **Zero False-Positive Returns**: Two-step confirmations and order checks prevent unauthorized return bookings.
*   **High-Priority Alerting**: Detects legal or financial risks instantly, escalating them to senior human support teams.
*   **Safe Takeover**: Disabling the AI agent during active human discussions prevents chat overlaps and conflicting replies.

---

## FAQ

### Q: Does the AI automatically refund money?
**A:** No. The AI only processes and logs the return request. The actual refund verification and payment transfer must be executed manually by a human store administrator.

### Q: Can the AI handle partial returns?
**A:** Yes. If a customer bought 3 shirts and wants to return only 1, the validation system allows it. If they try to return 4 shirts, the AI will reject the draft and prompt them with the correct limit.

---

## Related Documents

*   [AI Auto-Reply Feature](./ai-auto-reply.md)
*   [Automation rules](./automation.md)
*   [Unified Inbox](./unified-inbox.md)
