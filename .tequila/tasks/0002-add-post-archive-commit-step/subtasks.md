# Subtasks of *Add Post-Archive Commit Step*

## ARCHIVE-TASK.md

- [x] Add step 6 to ARCHIVE-TASK.md: after summarizing, ask the user whether they want to commit the changes. If yes, split the diff into separate commits aligned with subtasks (one subtask, one commit). When boundaries cannot be cleanly separated, combine into a single commit noting the covered subtasks. If the user declines, leave changes uncommitted.

## Notes

FREE-BIRD.md delegates to ARCHIVE-TASK.md at its archive step, so the commit prompt will be inherited automatically. No changes needed to FREE-BIRD.md.
