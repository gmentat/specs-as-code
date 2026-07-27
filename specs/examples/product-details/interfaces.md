# Interfaces

## Clients

- The storefront uses IF-001 for UC-001.

## IF-001: Retrieve product details

- **Supports:** UC-001
- **Operation:** `GET /v1/products/{product_id}`
- **Purpose:** Retrieve the product fields the storefront displays
- **Canonical contract:** [`contracts/product-details.openapi.yaml`](contracts/product-details.openapi.yaml)

### Semantics

- **Side effects:** None.
- **Guarantee:** Availability is a snapshot at response time.
