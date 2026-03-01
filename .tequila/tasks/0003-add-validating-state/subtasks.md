# Subtasks of *Add Validating State*

## Updates

- [x] Update PRINCIPLE.md: add `VALIDATING` to the state list, lifecycle progression, and add a new "Validating" subsection under Task Lifecycle
- [x] Update VALIDATE-TASK.md: set state to `VALIDATING` on entry; on pass leave as `VALIDATING` (archive step handles the next transition); on fail set to `FAILED`
- [x] Update ARCHIVE-TASK.md: change entry condition from `IMPLEMENTED` to `VALIDATING`
- [x] Update FREE-BIRD.md: no changes needed — delegates to VALIDATE-TASK and ARCHIVE-TASK
- [x] Update CLAUDE.md: add `VALIDATING` to the lifecycle description
