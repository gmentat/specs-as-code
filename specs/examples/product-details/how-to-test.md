# How to test

## T-001: Known product

- **Covers:** UC-001, FR-001, IF-001 `getProduct`
- **Steps:** Request `GET /v1/products/prod_123` when that product exists and is in stock.
- **Expected:** Status `200`; the body conforms to `Product` and reports `availability: in_stock`.

## T-002: Unknown product

- **Covers:** UC-001 failure path, FR-002, IF-001 `404`
- **Steps:** Request `GET /v1/products/missing` when that ID does not exist.
- **Expected:** Status `404`; the body is exactly `{ "code": "product_not_found" }`.

## Contract checks

- [x] `interfaces.md` links to the canonical OpenAPI file.
- [x] The OpenAPI document parses and defines `getProduct`, its path parameter, success response, and documented error.
- [x] The model and OpenAPI schemas use the same fields and allowed values.
- [x] No optional `implementation.md` is needed.

## Specification review

- [x] UC-001 defines the successful request and the meaningful failure path.
- [x] Both requirements are independently verifiable.
- [x] No assumption or dependency affecting behavior or contracts is hidden.
- [x] The model, interface contract, requirements, and tests agree without duplication.
