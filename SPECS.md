# SPECS.md (Specs-as-Code)

## Principles

Specs-as-code means the specs live in version control alongside the work they describe.

- Specs are the source of truth for what must be built and how to verify it.
- Specs describe product intent and user value, not just implementation details.
- Specs define observable behavior and guardrails (constraints, invariants, compatibility); include implementation details only when they affect the contract.
- Specs are small and modular: one feature/change area per spec folder.
- Every change has a verification path (`how-to-test.md`) and a record (`changelog.md`).
- Project-wide invariants live in `specs/PRINCIPLES.md` — every spec must respect them.

## Organization

- All specs live under `specs/`.
- Each spec is a folder: `specs/<area>/<feature>/`.
- The folder is the unit of change and contains `spec.md`, `how-to-test.md`, `data-model.md`, `changelog.md`, and `implementation.md`.
- Agent-run validation scenario catalogs live under `packages/scenarios/`; runner prompts live under `tests/ci-agent/`.
- Review matrices and scenario planning docs may live next to the relevant spec when they explain coverage before it becomes executable.

## What is `specs/INDEX.md`?

`specs/INDEX.md` is the canonical table of contents for specs.

- Humans and agents start here to find the right spec without scanning the whole tree.
- Every spec must be listed there (no dead links).

## What is `specs/PRINCIPLES.md`?

`specs/PRINCIPLES.md` captures the project's architectural and development principles.

- These are rules, not aspirations — they constrain every spec and implementation.
- When a spec or implementation violates a principle, it must be explicitly justified in `implementation.md`.

## Start here

1. Read `specs/PRINCIPLES.md` — understand project-wide constraints
2. Read `specs/INDEX.md` — find the relevant spec(s)
3. Read the spec's `spec.md`
4. Read the spec's `data-model.md`
5. Follow the spec's `how-to-test.md`
6. Check the spec's `changelog.md` for recent changes
7. If the change affects deployed or agent-observable behavior, check the relevant scenario matrix/catalog and runner prompt

## Definition of Done (for any change)

1. Relevant `spec.md` updated
2. Relevant `data-model.md` updated
3. Relevant `changelog.md` appended (do not rewrite history)
4. You followed the spec's `how-to-test.md` (update it if the procedure changed)
5. `specs/INDEX.md` updated if you added/moved a spec
6. If spec status is `active`: Cross-artifact consistency checklist in `how-to-test.md` passes
7. Relevant validation scenario matrix/catalog updated if the behavior change affects live, agent-run, or regression scenario coverage

## Spec lifecycle

Each spec has a lifecycle state in `spec.md` frontmatter:

- `draft`
  - Work-in-progress; the contract may change.
  - May contain `[NEEDS CLARIFICATION: question]` markers.
- `active`
  - Current contract; default for "this is how the system should work".
  - Must have zero unresolved `[NEEDS CLARIFICATION]` markers.
- `deprecated`
  - Still documented, but should not be used for new work. Prefer pointing to the replacement spec in `spec.md`.

The `version` field tracks meaningful changes to the contract:

- Patch: clarification/formatting only (no behavioral change)
- Minor: backwards-compatible behavior change
- Major: breaking change to the contract

## Writing good specs (checklist)

### What/why vs how

`spec.md` describes **what** users need and **why**. It must not contain technology choices, API design, code structure, or implementation strategy — those belong in `implementation.md`.

This separation ensures requirements survive technology changes and are readable by non-technical stakeholders.

### Ambiguity markers

When something is unknown or needs a decision, mark it inline:

```
[NEEDS CLARIFICATION: What happens when the user has no permissions?]
```

Rules:
- A spec cannot move from `draft` to `active` with unresolved markers.
- Limit to 3 markers per spec — if you have more, the scope is too broad.

### User scenarios

Write user scenarios with explicit priority (P1 = must-have, P2 = should-have, P3 = nice-to-have). Each scenario should be independently testable:

```markdown
### P1: [Scenario name]

**As a** [role], **I want** [goal], **so that** [value].

**Why this priority:** [Explain why this is P1.]

**Independent test:** [Describe how to verify this scenario independently.]

**Acceptance:**

- Given [context], When [action], Then [outcome]
```

### Validation scenarios

User scenarios in `spec.md` describe customer intent and product value. Validation scenarios describe concrete system exercises that agents, CI, or humans run to prove the behavior works in practice. Keep these layers linked but separate:

- Use `spec.md` for customer-facing workflows, requirements, acceptance criteria, and guardrails.
- Use `how-to-test.md` for deterministic verification steps for the spec.
- Use scenario matrices near the relevant spec for broad coverage planning, edge cases, and review status.
- Use `packages/scenarios/<suite>/index.toml` as the source of truth for executable agent-run scenario catalogs.
- Use `tests/ci-agent/*.md` for the runner prompts that tell validation agents how to execute and report those catalogs.

Validation scenarios should be small enough to diagnose, realistic enough to catch integration failures, and cross-linked to the requirements or matrix rows they cover. A good executable scenario entry names:

- scenario id and title
- priority or gating level
- capability or behavior under test
- allowed environments / execution mode
- setup requirements
- expected terminal state or observable signals
- checks the agent must verify
- references to relevant FR-* requirements or scenario matrix rows

Do not duplicate full scenario catalogs inside `spec.md`, `how-to-test.md`, or `SPECS.md`; link to the catalog/matrix instead. The catalog is the authority for scenario metadata once a scenario is executable.

### Numbered requirements

Number functional requirements with an FR prefix and use RFC2119-style normative language (`MUST`, `SHOULD`, `MAY`) with an explicit subject (for example: System, User, Spec folder). Each must be independently verifiable:

```markdown
- **FR-001**: [Subject] MUST [behavior]. Verified by [test reference].
```

Number success criteria with an SC prefix. Keep them measurable and technology-agnostic:

```markdown
- **SC-001**: [Measurable outcome]
```

### Acceptance criteria

- Put acceptance criteria in checkboxes and keep them tight.
- Include structural checks (files exist, frontmatter valid, listed in INDEX).
- Include a check that all `[NEEDS CLARIFICATION]` markers are resolved (for `active` specs).
- Include a check that all FR-* requirements are covered by `how-to-test.md`.

### General

- Keep specs specific and testable (inputs/outputs, edge cases, constraints).
- Include product framing such as user story and core value when defining workflows or features.
- State scope and non-goals explicitly (what is out of scope).
- Call out guardrails/invariants (what must not change; backwards-compat expectations).
- Use clear headings so agents can navigate quickly.
- Prefer smaller specs; split large work into phases/specs.
- Make `how-to-test.md` executable (exact commands + expected results) where possible.

## Writing good `implementation.md` (checklist)

- Record key technical decisions in the Decisions table with options considered and rationale.
- Include consequences/tradeoffs for each decision.
- Document architecture, sequencing, algorithms, data flow, and dependencies.
- Record key risks and mitigations.
- If an implementation violates a principle from `specs/PRINCIPLES.md`, justify it explicitly.

## Writing good `data-model.md` (checklist)

- Define the **atomic unit** / **center-of-gravity** objects for the feature.
  - The atomic unit is the object other parts of the system reference most often (the "primary key in your head").
- List the entities and their **stable identifiers**.
  - Clarify which IDs are deterministic vs DB-assigned.
  - Clarify which objects are immutable vs updated in-place.
- State the **boundaries**.
  - What is the primary query boundary (e.g. `docset_id`, `workspace_id`, `user_id`)?
  - What are the ownership/tenant rules?
- Specify **relationships**.
  - Foreign-key style links between entities.
  - Any "scaffold" fields that exist to support later UX (e.g. chunk -> `block_ids[]` for citations/highlights).
- Call out **derived fields** vs persisted fields.
- Call out critical **invariants**.
  - Uniqueness, allowed state transitions, no-plaintext-secrets, citation stability/versioning, etc.

## Writing good `how-to-test.md` (checklist)

- Include numbered verification steps with explicit expected results.
- Make steps executable (exact commands + expected output) where possible.
- Cover every requirement (FR-*) and acceptance criterion from `spec.md`.
- Link to relevant validation scenario matrices, catalogs, or runner prompts when live/agent validation is part of the verification path.
- Include the **cross-artifact consistency checklist** (template provides one) and run it when the spec moves to `active` or after significant edits.

## Boundaries (recommended)

- Always:
  - Keep `spec.md`, `implementation.md`, `data-model.md`, `how-to-test.md`, `changelog.md`, and `specs/INDEX.md` consistent.
  - Append to `changelog.md` (do not rewrite history).
- Ask first:
  - Renaming/moving specs.
  - Changing the spec folder contract.
- Never:
  - Rewrite `changelog.md` history.

## Spec folder contract

A spec lives in `specs/<area>/<feature>/` and must include:

- `spec.md` — the living requirement (what + why, no implementation details)
- `how-to-test.md` — how to verify this spec holds, plus cross-artifact consistency checklist
- `data-model.md` — the atomic unit / center-of-gravity objects and relationships that the feature builds around (stable IDs, boundaries, relationships, invariants, versioning)
- `changelog.md` — append-only history of changes
- `implementation.md` — design/implementation notes: decisions log, architecture decisions, sequencing, key algorithms, data flow, dependencies. Non-normative (`spec.md` is the contract) but essential for the next agent or developer to understand *how* things work.

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
