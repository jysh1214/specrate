# Issues of *Add Free Bird Mode*

## Issues

### Issue: Missing reincarnation counter file

Free Bird mode uses an internal retry counter in the procedure text but has no persistent, observable mechanism for tracking retries. The user requested a `.tequila/tasks/{task-id}/reincarnation` file that starts at 15 (by default), decrements after each flywheel loop, and stops Free Bird when it reaches zero.

#### Root Cause

The original design used an in-procedure counter (step 2 / step 7) rather than a persistent file. The reincarnation file was not part of the initial proposal.

#### Suggested Fix

- Update `FREE-BIRD.md` to create a `reincarnation` file initialized to `15` at the start, decrement it after each amend loop iteration, and stop when it reaches `0`.
- Update `references/PRINCIPLE.md` to document the `reincarnation` file in the task folder structure.
- Update `design.md` and `subtasks.md` to reflect this change.

### Issue: Issues not documented per failure iteration

Free Bird's amend loop references DOCUMENT-ISSUES.md but doesn't emphasize that issues must be documented for each failure iteration so that context accumulates for subsequent retries. Additionally, the `DOCUMENT-ISSUES.md` template only shows a single issue section, making it unclear that multiple `### Issue:` sections are supported.

#### Root Cause

The DOCUMENT-ISSUES action already says "append the new issues to the existing file" but the template only shows one issue section, which is ambiguous. Free Bird's procedure should explicitly call out per-iteration issue documentation.

#### Suggested Fix

- Update `assets/templates/DOCUMENT-ISSUES.md` to show multiple `### Issue:` sections, making the repeatable structure explicit.
- Update `FREE-BIRD.md` step 7 to clarify that issues are documented for each failure iteration.
