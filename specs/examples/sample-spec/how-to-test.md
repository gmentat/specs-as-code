# How to test

## Behavior verification

### T-001: Required artifact contract

- **Covers:** UC-001, FR-001, IF-001
- **Steps:** Compare this folder with the layout declared in `contracts/spec-folder.md`.
- **Expected:** Every required entry exists; conditional and optional entries follow their stated rules.

### T-002: Identity and lifecycle

- **Covers:** FR-002 and the data-model identity, state, and active-spec invariants
- **Steps:** Compare `spec.md` frontmatter with `contracts/spec-folder.md`; search `use-cases.md`, `data-model.md`, `interfaces.md`, and `spec.md` for unresolved clarification markers.
- **Expected:** The frontmatter conforms and no clarification marker exists.

### T-003: Discovery

- **Covers:** FR-003 and the data-model index relationship
- **Steps:** Open `specs/INDEX.md` and follow the sample link.
- **Expected:** The link resolves to this `spec.md`.

### T-004: Contract failure

- **Covers:** IF-001 documented error
- **Steps:** Evaluate a temporary copy with one required entry omitted.
- **Expected:** The copy is invalid and the missing-entry rule is identifiable.

## Specification review

- [x] UC-001 defines the primary and meaningful alternate paths
- [x] Every requirement is clear and independently verifiable
- [x] No assumption or dependency affecting behavior or contracts is hidden
- [x] Every requirement supports UC-001
- [x] Every model element is currently justified
- [x] IF-001 supports UC-001, uses data-model terminology, and links one exact declaration
- [x] The linked contract exists and is not duplicated in `interfaces.md`
- [x] Required behavior and invariants are verified
- [x] `spec.md` does not duplicate use-case, model, or interface definitions
- [x] Terminology is consistent
- [x] No optional `implementation.md` is needed
- [x] No unresolved clarification markers remain
