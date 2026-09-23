# PRODUCT.md

Product brief and PRD template.

Replace the placeholders in this file from the PRD when starting a new product. This is the source of truth for what the product is, who it serves, and what the first version must prove.

Map a full PRD with `docs/repo-setup.md`. Ask only where the PRD is silent and the answer changes the next increment. If the PRD conflicts with a non-goal or with `AGENTS.md`, stop and ask before changing scope.

Do not implement until every blocking field below is filled with product-specific content. The platform in `ARCHITECTURE.md` and the UI foundation in `docs/design.md` are also blocking; use "not applicable" when a product has no GUI.

Blocking: Product Name, One-Sentence Description, Core User, Core Moment, Problem, V1 User Promise, V1 Included, V1 Excluded, at least one Core Workflow, Success Criteria.

Fill from the PRD when it contains them: Vision, Product Thesis, Evidence And Riskiest Assumption, Emotional Goals, What This Product Is, What This Product Is Not, Open Questions.

Later ideas go only to `docs/roadmap.md`.

## Product Name

Blocking.

`[Product Name]`

## One-Sentence Description

Blocking.

`[A plain-language description of what this product helps someone do.]`

## Vision

From the PRD when present.

`[Describe the long-term product promise in a few paragraphs. Keep it concrete enough to guide tradeoffs.]`

## Core User

Blocking.

`[Who is this for? Name the user type, their context, and what they are trying to accomplish.]`

## Core Moment

Blocking.

`[What specific situation creates the need for this product? What is happening right before the user opens it?]`

## Problem

Blocking.

`[What is painful, slow, confusing, risky, emotionally unsatisfying, or underserved today?]`

## Product Thesis

From the PRD when present.

`[State the bet. Example: If we make X dramatically simpler, then Y user will choose this product over Z alternative.]`

## Evidence And Riskiest Assumption

From the PRD when present. If the PRD is silent, ask before the first increment. This decides what the slice must prove.

- Evidence for the problem: `[observations, interviews, existing behavior; distinguish evidence from assumptions]`
- Current alternative: `[how the user handles this today]`
- Riskiest assumption: `[what must be true for this product to be useful]`
- Smallest experiment: `[prototype session, observed workflow, or other low-cost check]`
- Decision threshold: `[result that supports continuing, changing direction, or stopping]`
- Result and next decision: `[not tested / date, evidence, conclusion]`

A working implementation proves behavior, not demand. Use lightweight research before adding measurement infrastructure.

## Emotional Goals

From the PRD when present. This section owns the feelings. `docs/design.md` translates them into interaction and visuals.

The product should feel:

- `[feeling 1]`
- `[feeling 2]`
- `[feeling 3]`

The product should not feel:

- `[anti-feeling 1]`
- `[anti-feeling 2]`
- `[anti-feeling 3]`

## What This Product Is

From the PRD when present.

- `[clear identity statement]`
- `[clear identity statement]`
- `[clear identity statement]`

## What This Product Is Not

From the PRD when present.

- `[explicit non-goal]`
- `[explicit non-goal]`
- `[explicit non-goal]`

## V1 User Promise

Blocking.

`[In the first usable version, the user should be able to achieve this specific outcome.]`

## V1 Scope

### Included

Blocking.

- `[must-have capability]`
- `[must-have capability]`
- `[must-have capability]`

### Explicitly Excluded

Blocking.

- `[not in V1]`
- `[not in V1]`
- `[not in V1]`

## Core Workflows

At least one workflow is blocking.

### Workflow 1: `[Name]`

1. `[Step]`
2. `[Step]`
3. `[Step]`

### Workflow 2: `[Name]`

1. `[Step]`
2. `[Step]`
3. `[Step]`

## Success Criteria

Blocking.

The first version is successful if:

- `[observable outcome]`
- `[observable outcome]`
- `[observable outcome]`

## Open Questions

From the PRD when present. Leave these open until answered.

- `[Question that must be answered before or during implementation]`
- `[Question that must be answered before or during implementation]`
- `[Question that must be answered before or during implementation]`

## Future Directions

Later ideas live only in `docs/roadmap.md`. Move an idea into the V1 scope above, and add an accepted task, before building it.
