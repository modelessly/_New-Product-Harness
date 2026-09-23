# Example Task — Not A Product

This sample shows how specific a task, its acceptance criteria, and a handoff should be. It is not scope for any product. The library-hold story below is fictional. Delete this file, and this folder if it is empty, once `TASKS.md` contains a real first task. See `docs/repo-setup.md`.

## TASKS.md entry

`HOLD-01 — Save a hold for a book`

- Outcome: A librarian can record a hold and see it after reopening the app.
- Acceptance criteria: Enter a title and a name, save, and see the hold on the list. Quit and reopen, and the same hold is still there. If saving fails, the hold is not shown as saved, and the screen offers a retry. An empty list shows one action to add a hold.
- Verification: `npm test -- hold` from the app directory, plus the restart smoke check in `README.md`.
- Dependencies: none

## PLANNER.md handoff

- Task ID / milestone: `HOLD-01`
- Status: verification incomplete
- Next action: Run the restart smoke check on a device and record the result here.
- Branch / worktree: `hold-01` at `abc1234`; no uncommitted changes
- Changes and relevant files: Hold create/read in `src/holds.ts` and `src/HoldList.tsx`
- Checks and outcomes: `npm test -- hold` passed (12 tests). Restart smoke check not run.
- Manual / visual evidence: Added a hold in the browser at 1280px and 390px. Retry appeared when storage was disabled. Restart was not exercised.
- Remaining acceptance criteria: Restart persistence is unconfirmed on device.
- Unavailable or failed checks: Device restart smoke check.
- Known risks / assumptions: This sample uses local storage only.
