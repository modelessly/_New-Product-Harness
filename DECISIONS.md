# DECISIONS.md

Append-only decision log.

Use this file for product and architectural decisions that future agents or collaborators should understand. Do not rewrite history. If a decision changes, add a new entry that supersedes the earlier one.

## Decision Template

```md
---

## YYYY-MM-DD: [Decision Title]

Decision:
[What was decided.]

Reasoning:
[Why this direction was chosen.]

Tradeoffs:
[What this makes easier and what it makes harder.]

Status:
[Proposed / Accepted / Superseded]
```

---

## 2026-05-29: Use This Repository As A Product Harness

Decision:
This repository is a reusable product-start template rather than a product-specific codebase.

Reasoning:
The goal is to help a coding agent start new products faster by providing shared workflow instructions, product-shaping prompts, architecture guidance, and planning documents before application code exists.

Tradeoffs:
The template stays intentionally generic, so each new product still needs a real PRD and initial stack choice before implementation begins.

Status:
Accepted

---

## 2026-05-29: Keep V1 Scope Narrow By Default

Decision:
New products created from this harness should start with a narrow V1 and avoid backend infrastructure, authentication, cloud services, social features, AI generation, analytics, and unnecessary dependencies unless explicitly required by the product brief.

Reasoning:
Most early product risk is about proving the core workflow and user value. Extra infrastructure increases complexity before the product has earned it.

Tradeoffs:
Some products will need to add infrastructure earlier, but that decision should be deliberate and documented.

Status:
Accepted

---

## 2026-09-20: Use A Small Portable Workflow With Explicit Product Choices

Decision:
Keep `AGENTS.md` as the canonical workflow with small Claude and Gemini adapters and an explicit startup prompt for other clients. Remove the redundant `CODEX.md` entry point. Route context by task instead of requiring every document on every change.

Keep V1 scope and success criteria in `PRODUCT.md`, removing the duplicated scope document. Make the roadmap optional. Ask for the UI foundation at kickoff, including Modeless, shadcn/ui, native controls, custom/other, recommendation, or not applicable; there is no default system.

Add a reproducible command contract, observable task acceptance criteria, evidence-based handoffs, an optional concurrent-agent protocol, product-assumption experiments, and stage-appropriate release checks.

Reasoning:
Reduce conflicting instructions and context overhead while making completion and transfer between coding clients verifiable. Preserve the harness's narrow product focus without requiring a specific model, plugin, or orchestration tool.

Tradeoffs:
Selective reading requires clear routing and current authoritative documents. Optional coordination and release fields require product-specific setup; they should not become paperwork for trivial tasks. Cross-client behavior must be trialed in the actual clients rather than assumed from filenames.

Status:
Accepted
