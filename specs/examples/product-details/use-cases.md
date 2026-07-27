# Use cases

## Product understanding

- **Intended users:** Shoppers viewing a public catalog
- **Problem:** A shopper needs to know what a product is and whether it is available
- **Core value:** Current product details in one request
- **User-visible concepts:** Product and availability

## UC-001: View product details

- **Priority:** P1
- **Actor:** Shopper using the storefront
- **Trigger:** The shopper opens a product
- **Goal:** See its name and current availability
- **Expected outcome:** The storefront displays the requested product or reports that it does not exist

### Main flow

1. The storefront requests the product by ID.
2. The API returns its ID, name, and availability.
3. The storefront displays them.

### Failure path

- The product ID is unknown → the API returns `product_not_found`.

### Acceptance example

- Given an in-stock product, when the shopper opens it, then the storefront displays its name and `in_stock` status.
