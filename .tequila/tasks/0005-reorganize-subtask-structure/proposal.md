# Proposal of *Reorganize Subtask Structure*

## Motivation

Subtasks currently exist as checklist items in a single `subtasks.md` file, with patches stored separately in a flat `patches/` directory. This separation makes it hard to associate a subtask with its patch and provides no place to record per-subtask metadata such as a human-readable description of the patch or a post-implementation review state. Reorganizing subtasks into individual directories allows each subtask to be a self-contained unit with its own patch, description, and review state.

## Summary

- Replace the flat `patches/` directory and `subtasks.md` checklist with a `subtasks/` directory containing one subdirectory per subtask
- Each subtask directory is named `{index}-{subtask-name}` (e.g., `001-add-login-endpoint`) and contains:
  - `patch` — the Git patch file for this subtask's changes
  - `description` — AI-written explanation of the patch (its purpose and its role in the overall task)
  - `state` — post-implementation review state, either `APPROVED` or `REJECTED`
- Update the folder structure specification in `PRINCIPLE.md` to reflect the new subtask layout
- Update all actions that create, read, or manipulate subtasks: PLAN-TASK, IMPLEMENT-TASK, VALIDATE-TASK, ARCHIVE-TASK, AMEND-TASK
- Update or replace the `TASKS-SUBTASKS.md` template to match the new directory-based structure
- **BREAKING**: The `patches/` directory and `subtasks.md` file are replaced by the `subtasks/` directory

## Impact

- Affected code: `references/PRINCIPLE.md` (folder structure spec), `references/actions/PLAN-TASK.md`, `references/actions/IMPLEMENT-TASK.md`, `references/actions/VALIDATE-TASK.md`, `references/actions/ARCHIVE-TASK.md`, `references/actions/AMEND-TASK.md`, `assets/templates/TASKS-SUBTASKS.md`
