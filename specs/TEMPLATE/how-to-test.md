# How to test

## T-001: [Primary journey]

- **Covers:** UC-001, FR-001, IF-001 `[operation]`
- **Steps:** [Actions through the real client-visible interface]
- **Expected:** [Observable result]

## T-002: [Meaningful failure or invariant]

- **Covers:** [Alternate path, FR-###, interface error, or model invariant]
- **Steps:** [Actions]
- **Expected:** [Observable behavior and state]

## Contract checks

- [ ] Required files exist: `use-cases.md`, `data-model.md`, `interfaces.md`, `spec.md`, `how-to-test.md`, and `changelog.md`; `implementation.md` may be absent
- [ ] `spec.md` frontmatter contains valid `id`, `title`, `area`, and `status`
- [ ] `specs/INDEX.md` links to this spec
- [ ] Every interface contains an exact declaration or links to one existing canonical file under `contracts/`
- [ ] Contract files parse, lint, or compile with project tooling when their format supports it
- [ ] An active spec has no unresolved clarification markers in `use-cases.md`, `data-model.md`, `interfaces.md`, or `spec.md`
- [ ] Every P1 use case, requirement, invariant, interface operation, and documented error is covered above

## Specification review

<!-- Run read-only before application code. Correct findings in their owning artifact,
     then rerun the review. -->

- [ ] Are primary, meaningful failure, and recovery paths defined or explicitly out of scope?
- [ ] Is every requirement clear, objective, and independently verifiable?
- [ ] Are assumptions that affect behavior, data, interfaces, or tests explicit?
- [ ] Do use cases, the model, interfaces/contracts, requirements, and tests agree without duplication?
- [ ] Is every model element and interface justified by a current use case or requirement?
- [ ] Do tests cover current use cases, requirements, invariants, operations, and documented errors?
- [ ] Does optional `implementation.md`, if present, agree with the contracts?

## Post-implementation comparison

<!-- Run after application code changes. Report findings before making fixes. -->

- [ ] Code and tests conform to the use cases, model, interfaces/contracts, requirements, and project principles
- [ ] Missing, partial, contradictory, and unrequested behavior has been resolved or explicitly reported
- [ ] No protected contract was changed merely to match the implementation
