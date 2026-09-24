# Agent Onboarding And Handoff

## Start Or Resume

1. Follow the reading routes in `AGENTS.md`.
2. Inspect Git status, the current branch/revision, and existing edits before changing files.
3. If `PRODUCT.md` still contains unfilled placeholders such as `[Product Name]`, this checkout is the starter harness. Improve the harness, or follow `docs/repo-setup.md` with a PRD. Otherwise locate the active task in `PLANNER.md` and its acceptance criteria in `TASKS.md`.
4. Check relevant accepted decisions and actual source behavior. Treat stale handoff claims as leads to verify.
5. Summarize the next increment and material risks, then proceed within the authorized scope.

For clients without automatic repository instruction discovery, explicitly provide `AGENTS.md` and the relevant context. Do not rely on private chat history or vendor-specific memory to preserve project facts.

## Handoff

Update `PLANNER.md` when stopping meaningful unfinished work or completing a milestone. Include:

- Task ID, current status, and remaining acceptance criteria.
- Branch/worktree and revision at the time of verification; identify uncommitted work separately.
- What changed and the files that matter.
- Exact checks run, results, and manual or visual evidence.
- Failed or unavailable checks, blockers, assumptions, and known risks.
- The exact next action, including commands or file locations when useful.

Keep evidence concise and do not include secrets or raw session transcripts. Update durable facts in their authoritative documents rather than copying them into the handoff.

## Optional Concurrent-Agent Protocol

Use only when independent tasks justify parallel work and the client supports it. Sequential work is the default fallback.

- Assign each task one owner, acceptance criteria, dependencies, and explicit file or interface boundaries.
- Use separate branches/worktrees for concurrent editing when supported. In a shared checkout, assign non-overlapping files and stop to coordinate if ownership must change.
- Designate one integration owner. Only that owner updates shared planning/status documents during concurrent work; workers report their results to that owner.
- Agree on shared interfaces before dependent implementation. Do not have two agents edit the same file concurrently.
- Workers return their revision or patch, checks and results, and remaining risks. The integration owner reviews changes and reruns relevant checks on the combined result before marking the task done.
- On interruption or model change, leave the handoff above. Do not infer completion from an agent's confident summary.
