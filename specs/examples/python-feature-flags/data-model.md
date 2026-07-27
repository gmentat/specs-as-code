# Data model

## Atomic unit

`feature_flag`: one named binary decision.

## Entity

### `feature_flag`

- **Required by:** UC-001 and FR-001
- **Identity:** Stable, non-empty `name`
- **Attribute:** Boolean `enabled`

## Invariants

- Each name identifies at most one feature flag.

## Minimality check

- Targeting, rollout percentages, variants, and scheduling are excluded because UC-001 does not require them.
