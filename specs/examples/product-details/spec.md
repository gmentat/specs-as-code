---
id: examples.product-details
title: Product Details API Example
area: examples
status: active
---

# Product Details

## Scope

- Retrieve one public product's name and availability.

## Non-goals

- Search, purchasing, pricing, and inventory management.

## Requirements

- **FR-001**: The API MUST return the current product details defined by IF-001 for a known product. Supports UC-001. Verified by T-001.
- **FR-002**: The API MUST return the IF-001 `product_not_found` response for an unknown product ID. Supports UC-001. Verified by T-002.

## Success criterion

- **SC-001**: The storefront can resolve UC-001 with one API request.

## Acceptance criteria

- [x] IF-001 has one exact canonical contract.
- [x] Every model field is required by UC-001.
- [x] Every requirement has a verification case.
