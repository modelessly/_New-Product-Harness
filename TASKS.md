# TASKS.md

Implementation backlog.

Keep this file focused on actionable work. Keep completed task status here; decision rationale belongs in `DECISIONS.md` and the current handoff belongs in `PLANNER.md`.

## Task Format

Before implementation, give each active task an ID and fill:

- Outcome: `[observable user or developer result]`
- Acceptance criteria: `[specific behavior, including important failure cases]`
- Verification: `[command from README.md and/or reproducible manual steps]`
- Dependencies: `[none / task IDs]`

Example: `CORE-01 — Save an item`. Acceptance: create an item, restart, and confirm it remains; a storage failure shows a recoverable error. Verification: the product's persistence test plus the documented restart smoke check.

The phases below are a starter backlog, not automatically accepted product scope. Remove inapplicable tasks and expand the current increment into the format above. Match the specificity of `docs/examples/filled-task.md`, then delete that example.

## Phase 0: Product Setup

- [ ] Map the PRD into `PRODUCT.md`, `ARCHITECTURE.md`, `docs/design.md`, and `docs/roadmap.md`
- [ ] Fill every blocking field in `PRODUCT.md` before implementation
- [ ] Choose the UI foundation explicitly in `docs/design.md`
- [ ] Define evidence, the riskiest assumption, and a small validation experiment when the PRD leaves them open
- [ ] Choose initial platform and stack in `ARCHITECTURE.md`
- [ ] Replace harness-history entries in `DECISIONS.md` with the inherited harness revision note
- [ ] Write the first real task, then delete `docs/examples/`
- [ ] Capture initial product risks
- [ ] Create or connect the project repository

## Phase 1: Foundation

- [ ] Create app or package scaffold
- [ ] Establish minimal folder structure
- [ ] Populate and verify the command contract in `README.md`
- [ ] Add formatting and linting, if appropriate
- [ ] Add first smoke test or verification path
- [ ] Implement app shell or entry point
- [ ] Add CI once meaningful reproducible checks exist

## Phase 2: Core Workflow

- [ ] Implement the smallest end-to-end user workflow
- [ ] Persist the minimum useful user data, if required
- [ ] Add empty, loading, and error states
- [ ] Verify the workflow manually
- [ ] Add focused tests around durable logic

## Phase 3: V1 Completion

- [ ] Complete remaining included V1 capabilities
- [ ] Add onboarding or first-run UX only if needed
- [ ] Handle permissions and failure states
- [ ] Improve accessibility basics
- [ ] Validate performance for expected V1 usage
- [ ] Run the product experiment and record evidence and the next decision in `PRODUCT.md`
- [ ] Prepare release checklist

## Backlog

- [ ] `[future task]`
- [ ] `[future task]`
- [ ] `[future task]`
