# New Product Harness

A lightweight, model-agnostic starter for turning a product idea into a focused, buildable project. Keep the core promise narrow, build incrementally, and verify observable behavior.

## Start A Product

1. Copy or clone the harness and follow `docs/repo-setup.md`, including checking the Git remote before pushing.
2. Give the agent your idea and the startup prompt below. It should ask only unanswered kickoff questions and help populate the documents.
3. Choose the platform and UI foundation explicitly. No design system is selected by default.
4. Build the smallest useful end-to-end workflow and validate the riskiest product assumption.

```text
Read AGENTS.md, PRODUCT.md, and PLANNER.md. Follow docs/repo-setup.md for a new product. Ask only unanswered kickoff questions, including the UI foundation: Modeless, shadcn/ui, native platform controls, another/custom system, a recommendation, or not applicable. Help fill the product and architecture decisions, define observable acceptance criteria, summarize the approach and material risks, then implement the smallest useful increment once the necessary decisions are clear. Follow the verification and handoff rules in AGENTS.md.
```

## Agent Compatibility

The coding client determines file discovery and available tools, not the model name. Codex uses `AGENTS.md`; `CLAUDE.md` and `GEMINI.md` point their clients to the same workflow. For any other client, including one using Grok or a local model, explicitly provide the startup prompt and ensure it can read these files. If it cannot access the repository, supply the relevant file contents and review/apply its proposed changes yourself.

The portable baseline uses Markdown and shell commands. Network access, plugins, browsers, and multiple agents are optional. Check the client's active instructions when available and verify behavior rather than assuming an adapter was loaded.

## Documentation Map And Ownership

| File | Authoritative information | Read when |
| --- | --- | --- |
| `AGENTS.md` | Agent workflow, constraints, definition of done | Every task |
| `PRODUCT.md` | Product intent, V1 scope, success criteria, evidence | Every task |
| `PLANNER.md` | Active work and handoff | Every task |
| `ARCHITECTURE.md` | Platform, stack, state and integration decisions | Technical work |
| `docs/design.md` | UI foundation and visual/interaction direction | UI work |
| `TASKS.md` | Ordered backlog and task acceptance criteria | Planning or selecting work |
| `DECISIONS.md` | Decision rationale and supersession history | Relevant decisions |
| `MEMORY.md` | Optional distinct collaboration preferences | When present/relevant |
| `docs/repo-setup.md` | Kickoff and clone-to-product checklist | New product |
| `docs/agent-onboarding.md` | Resume and optional concurrent-agent protocol | Onboarding/handoff |
| `docs/prompts.md` | Copyable task prompts | As needed |
| `docs/release-checklist.md` | Stage-appropriate release checks | Sharing or releasing |
| `docs/roadmap.md` | Optional future possibilities, not committed scope | Future planning |

Change facts in their authoritative home; link to them elsewhere instead of duplicating them. Accepted decisions explain rationale; keep current product/architecture documents consistent when a decision changes.

## Command Contract

For this documentation-only harness, review Markdown links, obsolete references, and `git diff --check`. There is no application build or test suite yet. When starting a product, replace the rows below with exact commands, working directories, and prerequisites; use `N/A` with a reason for inapplicable checks. Never leave guessed commands presented as working instructions.

| Purpose | Exact command | Directory / prerequisites |
| --- | --- | --- |
| Setup / install | `[fill when stack is chosen]` | `[runtime version, package manager, lockfile]` |
| Run locally | `[fill]` | `[configuration; use .env.example without secrets]` |
| Build | `[fill or N/A with reason]` | `[fill]` |
| Lint / format check | `[fill or N/A with reason]` | `[fill]` |
| Type check | `[fill or N/A with reason]` | `[fill]` |
| Focused tests | `[fill]` | `[how to select a task's tests]` |
| Full tests / smoke check | `[fill]` | `[expected pass signal]` |

Document a short manual core-workflow check when automation is insufficient. Add reproducible scripts and CI once meaningful checks exist; avoid tool-specific verification as the only path.
