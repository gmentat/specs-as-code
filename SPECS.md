# SPECS.md (Specs-as-Code)

## Principles

Specs-as-code means the specs live in version control alongside the work they describe.

- Specs are the source of truth for what must be built and how to verify it.
- Specs describe product intent and user value, not just implementation details.
- Specs define observable behavior and guardrails (constraints, invariants, compatibility); include implementation details only when they affect the contract.
- Specs are small and modular: one feature/change area per spec folder.
- Every change has a verification path (`how-to-test.md`) and a record (`changelog.md`).

## Organization

- All specs live under `specs/`.
- Each spec is a folder: `specs/<area>/<feature>/`.
- The folder is the unit of change and contains `spec.md`, `how-to-test.md`, `data-model.md`, `changelog.md`, and `implementation.md`.

## What is `specs/INDEX.md`?

`specs/INDEX.md` is the canonical table of contents for specs.

- Humans and agents start here to find the right spec without scanning the whole tree.
- Every spec must be listed there (no dead links).

## Start here

1. Read `specs/INDEX.md` — find the relevant spec(s)
2. Read the spec’s `spec.md`
3. Read the spec’s `data-model.md`
4. Follow the spec’s `how-to-test.md`
5. Check the spec’s `changelog.md` for recent changes

## Definition of Done (for any change)

1. Relevant `spec.md` updated
2. Relevant `data-model.md` updated
3. Relevant `changelog.md` appended (do not rewrite history)
4. You followed the spec’s `how-to-test.md` (update it if the procedure changed)
5. `specs/INDEX.md` updated if you added/moved a spec

## Spec lifecycle

Each spec has a lifecycle state in `spec.md` frontmatter:

- `draft`
  - Work-in-progress; the contract may change.
- `active`
  - Current contract; default for “this is how the system should work”.
- `deprecated`
  - Still documented, but should not be used for new work. Prefer pointing to the replacement spec in `spec.md`.

The `version` field tracks meaningful changes to the contract:

- Patch: clarification/formatting only (no behavioral change)
- Minor: backwards-compatible behavior change
- Major: breaking change to the contract

## Writing good specs (2026 checklist)

- Keep specs specific and testable (inputs/outputs, edge cases, constraints).
- Include product framing such as user story and core value when defining workflows or features.
- State scope and non-goals explicitly (what is out of scope).
- Call out guardrails/invariants (what must not change; backwards-compat expectations).
- Use clear headings so agents can navigate quickly (e.g. User Story, Core Value, Scope, Non-goals, Behavior, Guardrails, Acceptance criteria).
- Prefer smaller specs; split large work into phases/specs.
- Put acceptance criteria in checkboxes and keep it tight.
- Make `how-to-test.md` executable (exact commands + expected results) where possible.

## Writing good `data-model.md` (checklist)

- Define the **atomic unit** / **center-of-gravity** objects for the feature.
  - The atomic unit is the object other parts of the system reference most often (the “primary key in your head”).
- List the entities and their **stable identifiers**.
  - Clarify which IDs are deterministic vs DB-assigned.
  - Clarify which objects are immutable vs updated in-place.
- State the **boundaries**.
  - What is the primary query boundary (e.g. `docset_id`, `workspace_id`, `user_id`)?
  - What are the ownership/tenant rules?
- Specify **relationships**.
  - Foreign-key style links between entities.
  - Any “scaffold” fields that exist to support later UX (e.g. chunk -> `block_ids[]` for citations/highlights).
- Call out **derived fields** vs persisted fields.
- Call out critical **invariants**.
  - Uniqueness, allowed state transitions, no-plaintext-secrets, citation stability/versioning, etc.

## Boundaries (recommended)

- Always:
  - Keep `spec.md`, `data-model.md`, `how-to-test.md`, `changelog.md`, and `specs/INDEX.md` consistent.
  - Append to `changelog.md` (do not rewrite history).
- Ask first:
  - Renaming/moving specs.
  - Changing the spec folder contract.
- Never:
  - Rewrite `changelog.md` history.

## Spec folder contract

A spec lives in `specs/<area>/<feature>/` and must include:

- `spec.md` — the living requirement
- `how-to-test.md` — how to verify this spec holds
- `data-model.md` — the atomic unit / center-of-gravity objects and relationships that the feature builds around (stable IDs, boundaries, relationships, invariants, versioning)
- `changelog.md` — append-only history of changes
- `implementation.md` — design/implementation notes: architecture decisions, sequencing, key algorithms, data flow, dependencies. Non-normative (`spec.md` is the contract) but essential for the next agent or developer to understand *how* things work.

Each `spec.md` starts with YAML frontmatter:

```yaml
---
id: area.feature-name
title: Feature Name
area: area
status: draft
version: 0.1.0
---
```

`specs/INDEX.md` is the canonical index — every spec must be listed there.

## Conventions

- Prefer editing an existing spec over creating a new one.
- Keep changes minimal.
- Do not invent new repository structure without updating a spec.
