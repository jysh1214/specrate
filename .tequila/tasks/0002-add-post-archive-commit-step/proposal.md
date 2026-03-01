# Proposal of *Add Post-Archive Commit Step*

## Motivation

Currently, the tequila skill does not enforce the "one subtask, one commit" principle. There is no instruction in the workflow telling the agent when or how to commit. This leads to agents either not committing at all or committing at arbitrary points. The commit step should happen after archiving, giving the user control over whether to commit and producing clean, subtask-aligned commits.

## Summary

- Add a post-archive step to ARCHIVE-TASK.md that asks the user whether they want to commit
- If yes, split the diff into separate commits aligned with subtasks (one subtask, one commit)
- When subtask boundaries cannot be cleanly separated, combine into a single commit noting the covered subtasks
- If the user declines, leave changes uncommitted
- Update FREE-BIRD.md to include the same commit step after archiving

## Impact

- Affected code: `references/actions/ARCHIVE-TASK.md`, `references/actions/FREE-BIRD.md`
