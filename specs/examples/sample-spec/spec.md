---
id: examples.sample-spec
title: Sample Spec
area: examples
status: active
---

# Sample Spec

## Scope

- Demonstrate a minimal, valid spec folder.

## Non-goals

- Implement application code.
- Add optional implementation notes without a concrete need.

## Behavior

- The sample follows the same contract as a real spec.
- Contributors can copy and adapt the required templates.

## Guardrails

- The sample remains minimal and passes `how-to-test.md`.
- Each concept has one canonical artifact.

## Requirements

- **FR-001**: A spec folder MUST conform to the IF-001 folder layout. Supports UC-001. Verified by T-001.
- **FR-002**: `spec.md` MUST conform to the IF-001 frontmatter declaration. Supports UC-001. Verified by T-002.
- **FR-003**: Every spec MUST be linked from `specs/INDEX.md`. Supports UC-001. Verified by T-003.

## Success criteria

- **SC-001**: A contributor can create a valid spec using only the templates and their inline instructions.

## Acceptance criteria

- [x] Required artifacts exist and the spec is indexed
- [x] No unresolved clarification markers remain
- [x] Every model element and interface has a current justification
- [x] Every interface has one exact canonical declaration
- [x] Every requirement is covered by `how-to-test.md`
