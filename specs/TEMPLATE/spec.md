---
id: area.feature-name
title: Feature Name
area: area
status: draft
version: 0.1.0
---

<!-- This file describes WHAT users need and WHY.
     Do not include technology choices, API design, code structure, or
     implementation strategy here — those belong in implementation.md.
     Mark unknowns inline: [NEEDS CLARIFICATION: specific question]
     A spec cannot move from draft to active with unresolved markers. -->

# Feature Name

## Core value

Why this feature matters in one or two sentences.

## User scenarios

### P1: Primary scenario

**As a** [role], **I want** [goal], **so that** [value].

**Why this priority:** [Explain why this is P1.]

**Independent test:** [Describe how to verify this scenario independently.]

**Acceptance:**

- Given [context], When [action], Then [outcome]

### P2: Secondary scenario (if applicable)

**As a** [role], **I want** [goal], **so that** [value].

**Why this priority:** [Explain why this is P2.]

**Independent test:** [Describe how to verify this scenario independently.]

**Acceptance:**

- Given [context], When [action], Then [outcome]

## Edge cases

- What happens when [boundary condition]?
- How does the system handle [error scenario]?

## Scope

## Non-goals

## Behavior

## Guardrails

## Requirements

<!-- Each requirement uses RFC2119-style normative language (MUST/SHOULD/MAY) with an explicit subject and is independently testable. -->

- **FR-001**: [Subject] MUST [behavior]. Verified by [test reference].
- **FR-002**: [Subject] MUST [behavior]. Verified by [test reference].

## Key entities

- **[Entity]**: [What it represents]

## Success criteria

<!-- Measurable outcomes, technology-agnostic. -->

- **SC-001**: [Measurable outcome]
- **SC-002**: [Measurable outcome]

## Acceptance criteria

- [ ] Folder contains `spec.md`, `implementation.md`, `how-to-test.md`, `data-model.md`, `changelog.md`
- [ ] `spec.md` has valid YAML frontmatter
- [ ] Spec is listed in `specs/INDEX.md`
- [ ] No unresolved `[NEEDS CLARIFICATION]` markers remain (if status is `active`)
- [ ] All requirements (FR-*) are covered by `how-to-test.md`

## Notes
