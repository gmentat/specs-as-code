# Implementation notes

This is an example `implementation.md` to demonstrate the required spec folder contract.

## Decisions

| Decision | Options considered | Chosen | Rationale | Consequences |
|----------|--------------------|--------|-----------|--------------|
| How minimal should the sample be? | Full-featured example; Minimal skeleton | Minimal skeleton | Easier to scan; the template itself shows all sections | Some guidance is pushed into templates and `SPECS.md`, not this file |

## Architecture decisions

N/A — this spec has no application code. The requirements are satisfied by the presence and contents of files in this folder:

- FR-001 is satisfied by the required files in this folder.
- FR-002 is satisfied by the YAML frontmatter in `spec.md`.
- FR-003 is satisfied by the entry in `specs/INDEX.md`.

## Sequencing

## Key algorithms

## Data flow

## Dependencies

## Risks and mitigations

- Risk: Template and sample drift over time. Mitigation: Update `specs/examples/sample-spec/*` whenever `specs/TEMPLATE/*` changes.
