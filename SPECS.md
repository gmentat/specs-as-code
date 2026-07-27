# SPECS.md

Specs as code keeps product and software contracts in version control alongside the implementation. The specs explain why a capability exists, how users or clients use it, the minimum domain model, the interfaces they rely on, the behavior that must hold, and how that behavior is verified.

Humans and agents use the same contracts to plan, implement, review, and test changes. The specs are the source of truth for what must be built, and the implementation must conform to them. Specs change deliberately when the intended contract changes, not merely to accommodate a solution. Implementation details are non-normative unless users or clients depend on them.

## Core rules

1. Start with current use cases.
2. Derive the minimum data model and client interfaces needed for those use cases.
3. Specify observable behavior and constraints before implementation details.
4. Every model element, interface, abstraction, and dependency MUST serve a current use case, requirement, or invariant.
5. Choose the simplest design that does so; do not add fields, abstractions, or extension points for hypothetical needs.
6. Keep each concept in one canonical file; link instead of duplicating.
7. Keep one coherent feature or change area per spec folder.

Additional project-wide rules MAY live in `specs/PRINCIPLES.md`. Rules defined there constrain every spec and implementation.

## Protected contracts

Product intent and use cases, normative requirements, stable interfaces, and critical data-model identity, relationships, states, and invariants are protected contracts.

- Fit the solution to the contracts. Never change a contract merely to fit an implementation.
- Change a protected contract only for a demonstrated current need or to correct the contract.
- Before changing one, explain the need and any relevant impact on users, clients, data, compatibility, or migration.
- Obtain human approval before making the change. If approval is unavailable, mark the issue for clarification and leave the contract unchanged.

## Spec folder

Specs live in `specs/<area>/<feature>/`.

| File | Status | Purpose |
|------|--------|---------|
| `use-cases.md` | Required | Users or clients, triggers, flows, and outcomes |
| `data-model.md` | Required | Minimum domain concepts and invariants |
| `interfaces.md` | Required | Clients, stable boundaries, and contract links |
| `contracts/` | Conditional | Canonical exact interface definitions |
| `spec.md` | Required | Normative scope, behavior, requirements, and guardrails |
| `how-to-test.md` | Required | Verification steps and consistency checks |
| `changelog.md` | Required | Append-only contract history |
| `implementation.md` | Optional | Non-normative internal decisions |

Create `contracts/` only when an interface uses an established contract format or is too large to define clearly inline. Never create an empty placeholder.

If no domain model or stable interface exists, say so briefly in the corresponding file. Do not invent one.

Every spec MUST be linked from `specs/INDEX.md`. Create the index when adding the first spec if it does not exist.

## Workflow

For new capabilities and meaningful behavior changes:

1. Define `use-cases.md`.
2. Derive `data-model.md`.
3. Define `interfaces.md` and any needed files under `contracts/`.
4. Complete `spec.md`.
5. Write `implementation.md` only if durable internal context is needed.
6. Derive `how-to-test.md` from the preceding artifacts.
7. Run the specification review below, correct its findings, and rerun it.
8. Append the change to `changelog.md`.
9. After application code changes, perform the post-implementation comparison below.

When changing an existing capability, read `specs/PRINCIPLES.md` when present, then `specs/INDEX.md` and the required files in workflow order. Read `implementation.md` only when it exists and is relevant.

## Specification review

After drafting the required artifacts and before writing application code, review the specification read-only.

Check:

- Are the primary, meaningful failure, and recovery paths defined or explicitly out of scope?
- Is every requirement clear, objective, and independently verifiable?
- Are assumptions that affect behavior, data, interfaces, or tests explicit?
- Do use cases, the model, interfaces/contracts, requirements, and tests agree without duplication?
- Is every model element and interface justified by a current use case or requirement?
- Do tests cover the current use cases, requirements, invariants, operations, and documented errors?

Report each finding with its file and line and the relevant contract reference. Do not edit files during the review. Correct findings in the artifact that owns the concept, apply the protected-contract approval rules, then rerun the review. Do not begin implementation while findings that affect behavior, contracts, or verification remain.

A fresh reviewing agent or context is preferable but not required. The reviewer applies these checks and treats `specs/PRINCIPLES.md`, when present, as additional constraints; principles alone are not the test.

## Post-implementation comparison

Before declaring implementation complete:

1. Compare the current code and tests with the use cases, data model, interfaces/contracts, requirements, and any project principles.
2. Report each gap as `missing`, `partial`, `contradictory`, or `unrequested`, with evidence and its contract reference.
3. Resolve gaps in the implementation by default. Do not edit a protected contract to hide implementation drift.
4. Apply the protected-contract approval rules if a contract is genuinely wrong or must change.
5. Rerun `how-to-test.md`. Completion requires no unresolved contract gaps.

The comparison is read-only until its findings are reported. Remediation is a separate step.

## Artifact rules

### `use-cases.md`

- Give each use case a stable `UC-###` identifier and priority.
- State the actor or client, trigger, goal, expected outcome, and shortest successful flow.
- Include only meaningful alternate or failure paths.
- Define what users observe and the concepts they must understand.
- Include an independently verifiable acceptance example.
- Exclude implementation and storage details.

### `data-model.md`

- Model the domain, not a speculative database schema.
- Identify the atomic unit and only the entities, attributes, relationships, and states required now.
- Link each model element to a use case, requirement, or invariant.
- Define identity, ownership, lifecycle, and state transitions only where required.
- Prefer derived information over duplicate persisted state.
- Exclude placeholders and elements intended only for anticipated features.

### `interfaces.md`

- Document stable boundaries used by clients: APIs, commands, events, shared libraries, or file formats.
- Give each interface a stable `IF-###` identifier and identify its clients and supported use cases.
- Every interface MUST contain or link to an exact client-visible declaration. A prose-only description is insufficient.
- Keep a small declaration inline. Put it under `contracts/` when it uses a standard file format or is too long to keep inline. Maintain one canonical definition.
- Use the boundary's native contract form:
  - HTTP: OpenAPI
  - GraphQL: schema definition language
  - RPC: Protobuf or the relevant IDL
  - Events: AsyncAPI or an exact message schema
  - Library or module: exact public signatures and types
  - CLI: command grammar, arguments, streams, and exit codes
  - File or configuration: JSON Schema or a precise grammar
- State only semantics the declaration cannot express, such as error conditions, side effects, preconditions, idempotency, ordering, or compatibility guarantees.
- Prefer intent-oriented operations over storage-shaped CRUD.
- Include only operations required by current use cases.
- Keep private functions, classes, adapters, and replaceable internal boundaries in code.

### `spec.md`

- Define scope, non-goals, observable behavior, requirements, and guardrails.
- Link to use cases, model concepts, and interfaces instead of repeating them.
- Give functional requirements stable `FR-###` identifiers.
- Use `MUST`, `SHOULD`, or `MAY` with an explicit subject and verifiable result.
- Give measurable success criteria stable `SC-###` identifiers.
- Exclude technology choices and internal code structure.

### `how-to-test.md`

- Give verification cases stable `T-###` identifiers and explicit expected results.
- Cover every P1 use case, requirement, model invariant, interface operation, and documented error.
- Exercise the real client-visible boundary for the primary journey when practical.
- Link external test suites or scenario catalogs instead of duplicating them.
- Include the specification review checks.

### `implementation.md`

This file is optional and non-normative. Create it only when important internal decisions cannot be understood easily from the code. Never create a placeholder or repeat contracts.

### `changelog.md`

Append dated entries. Never rewrite or remove history.

## Status

Each `spec.md` starts with:

```yaml
---
id: area.feature-name
title: Feature Name
area: area
status: draft
---
```

Status:

- `draft`: contract may change; clarification markers are allowed.
- `active`: current contract; no clarification markers are allowed.
- `deprecated`: retained for reference; point to a replacement when one exists.

Use `[NEEDS CLARIFICATION: specific question]` for unresolved decisions. Allow at most three per spec folder.

## Completion checklist

- [ ] Required files exist and the spec is in `specs/INDEX.md`.
- [ ] Specification review has no unresolved findings affecting behavior, contracts, or verification.
- [ ] Any protected contract change has human approval.
- [ ] `how-to-test.md` passes.
- [ ] After application code changes, the post-implementation comparison has no unresolved contract gaps.
- [ ] An active spec has no unresolved clarification markers.
- [ ] `implementation.md`, when present, agrees with the contracts.
- [ ] `changelog.md` contains a new appended entry.

## Agent boundaries

- Keep changes minimal and prefer updating an existing spec.
- Ask before changing a protected contract, renaming or moving a spec, or changing this folder contract.
- Never rewrite changelog history.
