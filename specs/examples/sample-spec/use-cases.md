# Use cases

## Product understanding

- **Intended users or clients:** Contributors and coding agents
- **Problem:** Starting a spec without missing or duplicating its contracts
- **Core value:** A small example that can be copied and adapted
- **User-visible concepts:** Spec folder, required artifact, canonical interface contract, optional implementation notes

## UC-001: Create a feature spec

- **Priority:** P1
- **Actor or client:** Contributor or coding agent
- **Trigger:** A capability needs a new spec
- **Goal:** Create a valid spec folder
- **Expected outcome:** The folder is complete, minimal, consistent, and indexed

### Main flow

1. Copy the required templates.
2. Define the use cases, model, interfaces and any separate contracts, requirements, and tests in order.
3. Add the spec to `specs/INDEX.md`.

### Alternate or failure paths

- No domain model or stable interface exists → state that briefly instead of inventing one.
- An interface needs a standard format or is too long to keep inline → place its canonical definition under `contracts/`.
- Durable internal design context is needed → add `implementation.md`; otherwise omit it.

### Acceptance examples

- Given a defined capability, when a contributor follows the template, then the resulting folder passes its `how-to-test.md` checks.
