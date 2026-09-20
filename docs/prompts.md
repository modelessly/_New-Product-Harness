# Reusable Prompts

Use with any coding client. Explicitly supply file contents if the client cannot read the repository. `AGENTS.md` defines the workflow; these prompts select the task.

## Start A New Product

```text
Read AGENTS.md, PRODUCT.md, and PLANNER.md. Follow docs/repo-setup.md to interview me only about unanswered kickoff decisions, including the UI foundation (Modeless, shadcn/ui, native controls, another/custom system, recommendation, or not applicable). Help populate the authoritative documents, define the smallest useful increment and acceptance criteria, explain material risks, and begin once the necessary decisions are clear.
```

## Turn A Brief Into Tasks

```text
Follow AGENTS.md. Read PRODUCT.md, ARCHITECTURE.md, and TASKS.md. Organize the V1 backlog into small ordered tasks with observable acceptance criteria and verification steps. Keep future ideas out of committed scope.
```

## Review Architecture

```text
Follow AGENTS.md. Review ARCHITECTURE.md against PRODUCT.md and relevant source. Identify overengineering, unclear state ownership, reliability gaps, and risky dependencies. Recommend focused changes with tradeoffs; do not implement during this review.
```

## First Vertical Slice

```text
Follow AGENTS.md. Implement the smallest end-to-end workflow supporting PRODUCT.md's V1 promise. Use the chosen UI foundation in docs/design.md, minimal persistence only if needed, and the command contract in README.md. Verify acceptance criteria and leave evidence and handoff context.
```

## Continue Existing Work

```text
Follow AGENTS.md. Inspect PLANNER.md and Git state, read context relevant to the active task, verify the handoff's assumptions, and continue the next unfinished increment. Preserve existing edits and report verification evidence.
```

## Product And Design Review

```text
Follow AGENTS.md. Review PRODUCT.md and docs/design.md for a clear user promise, narrow scope, supported assumptions, coherent UI foundation, and accessible interactions. If screens exist, inspect them. Recommend focused improvements and a small experiment to test the riskiest assumption.
```

## Review A Change

```text
Follow AGENTS.md. Review the actual diff against task acceptance criteria. Look for correctness, regressions, data handling, accessibility, and missing verification. Report actionable findings with file locations and evidence; distinguish unverified concerns. Do not edit during the review.
```

## Handoff

```text
Use docs/agent-onboarding.md to update PLANNER.md with current revision, uncommitted changes, verification evidence, unresolved criteria, and the exact next action. Update authoritative product or technical documents only when their facts changed.
```
