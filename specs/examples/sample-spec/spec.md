---
id: examples.sample-spec
title: Sample Spec
area: examples
status: active
version: 0.2.1
---

<!-- This file describes WHAT and WHY. No implementation details here. -->

# Sample Spec

## Core value

Provide a minimal, concrete example of a spec folder that follows the spec folder contract, so new contributors and agents can see the conventions in action.

## User scenarios

### P1: Copy the template to start a new spec

**As a** contributor, **I want** to copy the sample spec folder as a starting point, **so that** I follow all conventions without reading the full guide.

**Why this priority:** This is the primary workflow for new contributors and agents; without it, the template is harder to adopt correctly.

**Independent test:** Copy the folder, replace placeholders, and run this folder's `how-to-test.md` steps end-to-end.

**Acceptance:**

- Given a new feature needs a spec, When I copy the sample folder and replace placeholder text, Then the result passes the spec folder contract checks.

## Edge cases

- What happens when the contributor forgets to update frontmatter fields like `id` or `status`?
- How does the system handle missing required files in the spec folder?

## Scope

- Demonstrate required files, frontmatter, numbered requirements, and cross-artifact consistency.

## Non-goals

- Implementing application code.
- Demonstrating every optional section (keep it minimal).

## Behavior

- This spec folder demonstrates the required files and frontmatter.
- It is listed in `specs/INDEX.md`.

## Guardrails

- The sample must always pass its own `how-to-test.md`.

## Requirements

- **FR-001**: Spec folder MUST contain `spec.md`, `implementation.md`, `how-to-test.md`, `data-model.md`, `changelog.md`. Verified by how-to-test step 1.
- **FR-002**: `spec.md` MUST have valid YAML frontmatter with `id`, `title`, `area`, `status`, `version`. Verified by how-to-test step 2.
- **FR-003**: Spec MUST be listed in `specs/INDEX.md`. Verified by how-to-test step 3.

## Key entities

- **spec_document**: The spec folder's primary contract, represented by `spec.md` frontmatter + the required companion files.
- **spec_file**: A required file in the spec folder, identified by its repo-relative path.

## Success criteria

- **SC-001**: A contributor can copy this folder and produce a valid spec with no guidance beyond the template comments.

## Acceptance criteria

- [ ] Folder contains `spec.md`, `implementation.md`, `how-to-test.md`, `data-model.md`, `changelog.md`
- [ ] `spec.md` has valid YAML frontmatter
- [ ] Spec is listed in `specs/INDEX.md`
- [ ] No unresolved `[NEEDS CLARIFICATION]` markers remain (status is `active`)
- [ ] All requirements (FR-*) are covered by `how-to-test.md`

## Notes

- This repo is a template; projects should replace this with real specs.
