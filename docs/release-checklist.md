# Release Checklist

Select the stage and apply checks proportional to the product's actual risks. Record evidence and unresolved gaps in `PLANNER.md`. A demo pass does not imply production readiness.

## Every Shared Version

- [ ] The core promise and V1 boundaries in `PRODUCT.md` match the result.
- [ ] Task acceptance criteria are met and the relevant README commands pass.
- [ ] The core workflow has been exercised end to end, including relevant empty and failure states.
- [ ] Meaningful UI changes have been inspected for layout, keyboard/focus behavior, labels, and readability, or visual verification is explicitly incomplete.
- [ ] Secrets and private data are absent from the diff and shared artifacts.
- [ ] Setup/run instructions and current handoff are accurate.
- [ ] Checks run, results, known gaps, and next actions are recorded without overstating verification.

## Prototype Or Demo

- [ ] The intended experiment and decision threshold are clear in `PRODUCT.md`.
- [ ] Simulated behavior, sample data, and limitations are clear to participants.
- [ ] The demo avoids relying on valuable real data where recovery is not implemented.
- [ ] Observations and the resulting product decision are recorded after the experiment.

## Release To Real Users

Apply relevant checks below; document a reason for each N/A.

- [ ] Required build, tests, lint, and type checks pass on the release revision; CI runs meaningful repeatable checks where available.
- [ ] Persistence survives restart; interrupted writes and storage failures behave safely.
- [ ] Schema migrations are tested with representative prior data when applicable.
- [ ] Backup/export and recovery are verified where loss of user data matters.
- [ ] Permission denial, external-service failure, offline behavior, and interrupted workflows are handled as applicable.
- [ ] Accessibility and expected device/browser coverage have been checked on the core workflow.
- [ ] Performance is acceptable for expected usage.
- [ ] Dependencies and integrations have been reviewed for relevant security, privacy, and distribution constraints.
- [ ] Configuration and user-data handling are documented; secrets stay outside source control.
- [ ] A proportionate rollback/recovery procedure exists for deployment or migration failures.
- [ ] Known issues and support/recovery guidance are ready for users where needed.
- [ ] Publication/deployment is authorized by the user; existing explicit authorization is sufficient.

## Final Report

State what changed, which acceptance criteria were met, exact verification outcomes, remaining limitations, and the next action. Distinguish product-validation evidence from technical test results.
