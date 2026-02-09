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
- The folder is the unit of change and contains `spec.md`, `how-to-test.md`, and `changelog.md`.

## What is `specs/INDEX.md`?

`specs/INDEX.md` is the canonical table of contents for specs.

- Humans and agents start here to find the right spec without scanning the whole tree.
- Every spec must be listed there (no dead links).

## Start here

1. Read `specs/INDEX.md` — find the relevant spec(s)
2. Read the spec’s `spec.md`
3. Follow the spec’s `how-to-test.md`
4. Check the spec’s `changelog.md` for recent changes

## Definition of Done (for any change)

1. Relevant `spec.md` updated
2. Relevant `changelog.md` appended (do not rewrite history)
3. You followed the spec’s `how-to-test.md` (update it if the procedure changed)
4. `specs/INDEX.md` updated if you added/moved a spec

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

## Boundaries (recommended)

- Always:
  - Keep `spec.md`, `how-to-test.md`, `changelog.md`, and `specs/INDEX.md` consistent.
  - Append to `changelog.md` (do not rewrite history).
- Ask first:
  - Renaming/moving specs.
  - Changing the spec folder contract.
- Never:
  - Rewrite `changelog.md` history.

## Spec folder contract

A spec lives in `specs/<area>/<feature>/` and must include:

- `spec.md` — the living requirement
- `implementation.md` — design/implementation notes: architecture decisions, sequencing, key algorithms, data flow, dependencies. Non-normative (`spec.md` is the contract) but essential for the next agent or developer to understand *how* things work.
- `how-to-test.md` — how to verify this spec holds
- `changelog.md` — append-only history of changes

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
