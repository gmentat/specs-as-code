# How to test

## T-001: Known flag

- **Covers:** UC-001, FR-001, IF-001 `is_enabled`
- **Steps:** Call `is_enabled("new_checkout")` when that flag is enabled.
- **Expected:** The result is `True`.

## T-002: Unknown flag

- **Covers:** UC-001 failure path, FR-002, IF-001 `UnknownFlagError`
- **Steps:** Call `is_enabled("missing")` when no such flag exists.
- **Expected:** `UnknownFlagError` is raised.

## Contract checks

- [x] The inline Python declaration compiles.
- [x] Its names and types agree with `data-model.md`.
- [x] No `contracts/` directory is needed for this small declaration.
- [x] No optional `implementation.md` is needed.

## Specification review

- [x] UC-001 defines the successful call and the meaningful failure path.
- [x] Both requirements are independently verifiable.
- [x] No assumption or dependency affecting behavior or contracts is hidden.
- [x] The model, inline interface, requirements, and tests agree without duplication.
