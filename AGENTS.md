# Agent J — Shared Agent Guide

This repo is managed by the [Agent J](https://github.com/uandiqueue/agent-j) automated coding pipeline.
All agents (Claude Code, Gemini CLI, Codex CLI) must follow the rules below.

## Before starting any task
1. Read `dev/PROJECT_CONTEXT.md` — project goals, current state, architecture, constraints.
2. Do not assume state — read the file, do not guess.
3. If `dev/PROJECT_CONTEXT.md` is sparse, read the issue body carefully; it is your primary spec.

## Branch & PR rules
- Always create a new branch: `agent-j/issue-<number>`
- Never push directly to `main` or `agent-j-staging`
- PR must target `agent-j-staging` with `Closes #<number>` in the body
- PR title must reference the issue number and a short description

## Security rules
- Never read, print, log, or commit `.env` files, secrets, or credentials of any kind
- Never add calls to external URLs not described in the issue
- Never install packages not described in the issue
- Never modify `.github/workflows/` unless the issue explicitly requires it

## Scope rules
- Implement exactly what the issue describes — no more, no less
- No speculative refactoring or cleanup beyond the issue scope
- No placeholder TODOs — write working, testable code
- If the issue is ambiguous, implement the most conservative interpretation

## Agent roles
- **Implementer (Claude Code)**: writes code, opens PR, follows branch/scope/security rules above
- **Planner (Gemini)**: reads PROJECT_CONTEXT.md + codebase, decomposes missions into atomic issues with dependency ordering
- **Evaluator (Gemini / Codex)**: reviews merged PR diff against original issue spec; verdicts are `approve` or `refine: <reasons>`

## First-run: project context initialization

When `dev/PROJECT_CONTEXT.md` still contains `<!-- ` placeholder comments, the file has not been initialized yet. **Before implementing any issue**, do this once:

1. Read the full repository: README, source files, key config files, any existing docs
2. Replace every `<!-- ... -->` placeholder below with real content you discover:
   - **Project Overview** — what it does, the problem it solves, who uses it
   - **Tech Stack** — languages, frameworks, key dependencies (check package.json, requirements.txt, Cargo.toml, go.mod, etc.)
   - **Current State** — what is built and working, what is in progress, what is not started
   - **Architecture** — key components, data flows, directory layout, external integrations
   - **Active Constraints** — known limitations, existing decisions, things to avoid
   - **Open Questions** — unresolved design decisions that affect implementation
3. Commit **only** `dev/PROJECT_CONTEXT.md` with message: `docs: initialize project context`
4. Then proceed with the original issue

## After finishing any task
If you made material changes to the architecture, data model, or project state, update `dev/PROJECT_CONTEXT.md` to reflect the new reality.
