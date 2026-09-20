# Product Kickoff And Repository Setup

Use this once when turning the harness into a product. The agent helps fill the documents; the user does not need to write a complete PRD first.

## Kickoff Interview

Read the supplied idea and existing documents first. Ask only unanswered questions, in small batches:

1. Who is the user, what situation triggers the need, and what outcome matters most?
2. What is the narrow V1 promise, and what is explicitly excluded?
3. Which platform comes first? Are there existing code, stack, device, budget, deadline, privacy, or offline constraints?
4. Which UI foundation should we use: **Modeless**, **shadcn/ui**, **native platform controls**, **another/custom system**, **recommend based on the product**, or **not applicable**?
5. What evidence supports the problem, what is the riskiest assumption, and what small experiment could test it?

Do not silently choose a UI foundation. If the user requests a recommendation, explain platform fit and tradeoffs and resolve the choice before substantial UI implementation. Record the authoritative source/version in `docs/design.md`; request a reference if Modeless or another system is unavailable rather than inventing its conventions. A component foundation does not replace visual direction.

Only unresolved decisions that materially affect the next increment should block it. Label conservative assumptions and keep them reversible. Do not require every optional template field to be completed before starting.

## Clone To Product

1. Copy or clone the harness; rename the folder/repository.
2. Inspect Git status and remotes. Point the new product at its own repository before any push; do not push product code into the harness remote.
3. Populate `PRODUCT.md`, including V1 scope and the first validation experiment.
4. Choose the platform/stack in `ARCHITECTURE.md` and UI direction in `docs/design.md`.
5. Replace the command contract in `README.md` when scaffold commands are known. Record runtime/package-manager versions and configuration prerequisites.
6. Put ordered tasks with acceptance criteria in `TASKS.md`; set the first active task in `PLANNER.md`.
7. Review optional `MEMORY.md` preferences. Keep roadmap ideas optional.
8. Record product-specific setup decisions in `DECISIONS.md`. Its harness-history entries describe the template, not product-specific choices.
9. Replace template placeholders that affect current work and search for inherited product names, paths, URLs, and remotes. Future optional fields may remain explicitly unresolved.
10. Follow `AGENTS.md` to implement and verify the first increment.

## Setup Files

Add `.env.example` only when configuration is needed; never include secrets. Add team conventions, scripts, or CI when they serve an actual workflow. Adapt `.gitignore` to the selected stack. Keep client adapters small and defer shared rules to `AGENTS.md`.
