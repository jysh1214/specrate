# Subtasks of *Reorganize Subtask Structure*

## Folder Structure

- [x] Update `references/PRINCIPLE.md` folder structure section — remove `subtasks.md` and `patches/` entries, add `subtasks/` directory spec with `description`, `patch`, and `state` files
- [x] Remove `assets/templates/TASKS-SUBTASKS.md` template (no longer applicable since subtasks are directories, not a single Markdown file)

## Action Guides

- [x] Update `references/actions/PLAN-TASK.md` — create subtask directories with `description` files instead of a `subtasks.md` checklist
- [x] Update `references/actions/IMPLEMENT-TASK.md` — read subtask directories, save `patch` and update `description` per subtask instead of writing to `patches/` and checking off `subtasks.md`
- [x] Update `references/actions/VALIDATE-TASK.md` — read subtask directories, write per-subtask `state` files (`APPROVED`/`REJECTED`) during validation
- [x] Update `references/actions/ARCHIVE-TASK.md` — read `patch` files from subtask directories instead of `patches/`, verify completion by directory contents instead of `subtasks.md` checklist
- [x] Update `references/actions/AMEND-TASK.md` — reference subtask directories instead of `subtasks.md` for amendments and state consistency checks
