# Data model

## Atomic unit

`spec`: one coherent capability contract stored in one folder.

## Entities and stable identifiers

### `spec`

- **Purpose:** Groups the contracts for UC-001.
- **Required by:** UC-001, FR-001, and FR-002
- **Identity:** Unique `id` in `spec.md` frontmatter
- **Attributes:** `title`, `area`, and `status`

## Relationships and boundaries

- One spec owns the artifacts required by IF-001 (UC-001, FR-001).
- `specs/INDEX.md` links to each spec (FR-003).

## States and transitions

- `draft` → `active` or `deprecated` (spec lifecycle)
- `active` → `deprecated` (spec lifecycle)

## Derived information

- Folder validity is derived from IF-001, its index entry, and coverage checks.

## Invariants

- A spec ID is unique.
- One spec folder contains exactly one `spec.md`.
- An active spec has no unresolved clarification markers.

## Minimality check

- [x] Every element is required now.
- [x] No speculative or duplicate state remains.
