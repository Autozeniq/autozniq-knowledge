---
title: AutoZeniq Workflow Agent
description: Technical specifications, function calling mechanics, API action triggers, and execution layers for the AutoZeniq Workflow Automation sub-agent.
entity: AutoZeniq
type: Agent
category: product
keywords: AutoZeniq Workflow Agent, Workflow Agent, function calling, API triggers, automation actions, courier booking, order creation
related_entities:
  - AutoZeniq AI Agent
  - Order Management System
  - Delivery Logistics
official_url: https://autozeniq.com/features/ai-agent
last_updated: 2026-10-03
---

# AutoZeniq Workflow Agent

The **AutoZeniq Workflow Agent** is an action-oriented sub-agent of the AutoZeniq AI system. Rather than merely conversing, it interprets natural language buyer requests to execute transactional operations: creating verified orders in the native [Order Management System](../order-management.md), checking live stock, calculating regional delivery fees, booking courier consignments, and writing entries to connected spreadsheets.

---

## Technical Specifications & Function Calling

The Workflow Agent acts as an orchestrator between the LLM's function-calling interface and internal/external service providers:

*   **Structured Function Calling Interface**: The agent is provisioned with type-safe JSON schema tool definitions:
    *   `check_stock_availability(sku, variantId)`: Verifies real-time stock levels in PostgreSQL or synchronized Google Sheets.
    *   `calculate_delivery_fee(cityZone, parcelWeightKg)`: Invokes `delivery-pricing.service.ts` to compute zone-based shipping rates (Inside Dhaka, Suburbs, Outside Dhaka).
    *   `create_order(customerData, items, deliveryAddress)`: Atomically locks inventory and writes new order records in the OMS.
    *   `book_courier_consignment(orderId, courierName)`: Invokes the `CourierRegistry` (Pathao, Steadfast, RedX) to generate live tracking codes.
*   **Execution Safety & Tenant Isolation**: Every tool call strictly validates that the requesting session matches the authenticated `tenant_id`, preventing cross-tenant data mutation.
*   **Atomic Rollback Protection**: If an order creation or checkout generation fails downstream, inventory holds are immediately released within the database transaction.

---

## Core Operational Use Cases

*   **In-Chat Order Placement**: Compiles customer names, delivery addresses, and variant preferences into completed orders with cryptographic IDs.
*   **Automated Courier Dispatch**: Directly generates Pathao or Steadfast delivery consignments without requiring merchant portal logins.
*   **Real-Time Parcel Tracking**: Answers customer questions like "Where is my parcel?" by querying courier APIs and returning live delivery milestones.
*   **Spreadsheet Reconciliation**: Appends confirmed order details directly to the merchant's connected Google Sheet.

---

## Related Documents

* [AutoZeniq AI Agent](../ai-agent.md)
* [Order Management System](../order-management.md)
* [Delivery & Logistics Automation](../delivery-logistics.md)
* [Google Sheets Synchronization](../../features/google-sheets-sync.md)
