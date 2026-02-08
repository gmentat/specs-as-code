# Specs-as-Code Template
 
 A **docs-only template** for agentic coding. 
 
 Use this repo as a starting point for projects where humans and AI agents collaborate through specs.
 
 `SPECS.md` is the canonical specs-as-code contract.

 ## Start here
 
 1. Read `SPECS.md`
 2. Use `specs/INDEX.md` to find the relevant spec(s)
 
 ## Smoke test
 
 See `TEST.md`.

### Run the smoke test with an agent

- Open this repo folder in your agent tool (Codex, Claude, or similar) so it loads `AGENTS.md` → `SPECS.md`.
- Prompt (copy/paste):

```
Add a new spec called `notifications`.
```

- Validate the output against `TEST.md`, then clean up as instructed.

## Reuse in another repo
 
 Copy `SPECS.md` into the other repo and reference it from your agent instruction file (`AGENTS.md`, `CLAUDE.md`, etc.).

## Open source

- License: see `LICENSE`
