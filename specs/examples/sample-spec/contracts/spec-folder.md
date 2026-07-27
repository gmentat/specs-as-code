# IF-001: Spec folder contract

This is the canonical client-visible declaration for a spec folder.

## Location

```text
specs/<area>/<feature>/
```

## Required entries

```text
use-cases.md
data-model.md
interfaces.md
spec.md
how-to-test.md
changelog.md
```

## Conditional and optional entries

- `contracts/` is present when `interfaces.md` links to a separate canonical contract.
- `implementation.md` is optional and non-normative.

## `spec.md` frontmatter

```yaml
---
id: <area>.<feature>
title: <non-empty title>
area: <area>
status: draft | active | deprecated
---
```

## Validity

- Every required entry exists.
- `specs/INDEX.md` links to `spec.md`.
- Every linked contract exists.
- An active spec has no unresolved clarification markers in its contract-definition files.
