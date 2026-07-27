---
id: examples.python-feature-flags
title: Python Feature Flags Example
area: examples
status: active
---

# Python Feature Flags

## Scope

- Read the enabled state of one named feature flag.

## Non-goals

- Flag administration, targeting, variants, scheduling, or storage design.

## Requirements

- **FR-001**: IF-001 MUST return the current Boolean state of a known feature flag. Supports UC-001. Verified by T-001.
- **FR-002**: IF-001 MUST raise `UnknownFlagError` for an unknown flag name. Supports UC-001. Verified by T-002.

## Success criterion

- **SC-001**: A Python service can make the feature decision with one interface call.

## Acceptance criteria

- [x] IF-001 is an exact typed Python declaration.
- [x] Every model element is required by UC-001.
- [x] Every requirement has a verification case.
