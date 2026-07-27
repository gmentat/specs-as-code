# Data model

## Atomic unit

`product`: one catalog item a shopper can view.

## Entity

### `product`

- **Required by:** UC-001 and FR-001
- **Identity:** Stable `product_id`
- **Attributes:** Non-empty `name`; `availability` is `in_stock` or `out_of_stock`

## Invariants

- A product keeps the same `product_id`.
- Availability is exactly one of `in_stock` or `out_of_stock`.

## Minimality check

- Price, inventory count, variants, and categories are excluded because UC-001 does not require them.
