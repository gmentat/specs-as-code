# Data model

## Atomic unit

Describe the center-of-gravity object this spec is built around.

## Entities and stable identifiers

- List each entity in scope.
- Define stable IDs for each entity.
- Note which IDs are deterministic vs DB-assigned.
- Note which entities are immutable vs updated in-place.

## Boundaries

- Define the primary query boundary (for example: `workspace_id`, `user_id`, `docset_id`).
- Define ownership and tenant isolation rules.

## Relationships

- Define foreign-key style links between entities.
- Include scaffold fields needed for product UX.

## Derived vs persisted fields

- List persisted fields.
- List derived fields and how they are computed.

## Invariants

- Define uniqueness constraints.
- Define allowed state transitions.
- Define security constraints (for example: no plaintext secrets).
- Define versioning/citation stability constraints where relevant.
