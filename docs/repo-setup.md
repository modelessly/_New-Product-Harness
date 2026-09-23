# Product Kickoff And Repository Setup

Use this once when turning the harness into a product. Bring a full PRD. The agent maps it into the documents and asks only about gaps.

## Map The PRD

Read the PRD and the existing documents first. Copy facts into the file that owns them:

- User, triggering moment, problem, promise, V1 scope, non-goals, workflows, success criteria, emotional goals, and evidence go to `PRODUCT.md`.
- Platform, stack, persistence, and technical constraints go to `ARCHITECTURE.md`.
- Visual direction goes to `docs/design.md`. The UI foundation is a separate question below.
- Later ideas go only to `docs/roadmap.md`.
- Open questions stay open in `PRODUCT.md`.
- Use `docs/examples/filled-task.md` as the density target for the first real task, then delete `docs/examples/`.

If the PRD conflicts with a non-goal or with the standing constraints in `AGENTS.md`, stop and ask. Do not silently expand scope.

Ask only unanswered questions, in small batches. Do not re-ask anything the PRD already settles.

1. Which blocking `PRODUCT.md` fields are still empty after the mapping?
2. Which platform comes first? Which stack, device, budget, deadline, privacy, or offline constraints are still unset?
3. Which UI foundation or component library should we use? Ask for a named system, native platform controls, a recommendation, or not applicable.
4. If the PRD is silent on it: what is the riskiest assumption, and what small experiment could test it?

Do not silently choose a UI foundation. No system is the default. If the user requests a recommendation, explain platform fit and tradeoffs and resolve the choice before substantial UI implementation. Record the chosen system and its authoritative source or version in `docs/design.md`. If that source is unavailable, ask for a reference rather than inventing the system's conventions. A component foundation does not replace visual direction.

Do not implement until every blocking field in `PRODUCT.md` is filled and the platform and UI foundation are resolved (use "not applicable" when a product has no GUI). Only other unresolved decisions that materially affect the next increment should block it. Label conservative assumptions and keep them reversible.

## Clone To Product

1. Copy or clone the harness; rename the folder/repository.
2. Inspect Git status and remotes. Point the new product at its own repository before any push; do not push product code into the harness remote.
3. Map the PRD into `PRODUCT.md`, including V1 scope and the first validation experiment when the PRD provides one.
4. Choose the platform/stack in `ARCHITECTURE.md` and UI direction in `docs/design.md`.
5. Replace the command contract in `README.md` when scaffold commands are known. Record runtime/package-manager versions and configuration prerequisites. Commands must be non-interactive so a fresh agent environment can run them.
6. Put ordered tasks with acceptance criteria in `TASKS.md`, using `docs/examples/filled-task.md` as the density target. Set the first active task in `PLANNER.md`. Then delete `docs/examples/`.
7. Review optional `MEMORY.md` preferences. Keep roadmap ideas in `docs/roadmap.md`.
8. Start a product decision log. Remove every harness-history entry from `DECISIONS.md`, including entries about the template itself. Leave the decision template, then add this inherited note and nothing else from the harness log. Record product decisions after the note.

```md
## Inherited harness

Harness revision: `[revision from README.md at clone time]`

Standing product constraints live in `AGENTS.md`. Product decisions start below this note.
```

9. Replace template placeholders that affect current work and search for inherited product names, paths, URLs, and remotes. Future optional fields may remain explicitly unresolved.
10. Follow `AGENTS.md` to implement and verify the first increment.

## Setup Files

Add `.env.example` only when configuration is needed; never include secrets. Add team conventions, scripts, or CI when they serve an actual workflow. Adapt `.gitignore` to the selected stack. Keep client adapters small and defer shared rules to `AGENTS.md`.

If a subdirectory has different commands or ownership, add a nested `AGENTS.md` there with only that difference.
