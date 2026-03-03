# Design of *Reorganize Subtask Structure*

## Context

Subtasks are currently tracked as checklist items in a single `subtasks.md` file, while patches live in a separate flat `patches/` directory. This makes it difficult to associate metadata (descriptions, review state) with individual subtasks. The new structure promotes each subtask to a self-contained directory.

## Goals / Non-Goals

- Goals: Replace `subtasks.md` and `patches/` with a `subtasks/` directory where each subtask is a folder containing `patch`, `description`, and `state` files
- Non-goals: Changing the task lifecycle states, changing the subtask naming convention, or altering how tasks themselves are structured

## Decisions

- Decision: Each subtask becomes a directory under `subtasks/` named `{index}-{subtask-name}` (e.g., `001-add-login-endpoint`), containing three files:
  - `description` — Created during PLAN-TASK with the planned intent; updated during IMPLEMENT-TASK with the AI's explanation of the actual patch (its purpose and role in the task)
  - `patch` — Created during IMPLEMENT-TASK with the Git diff for this subtask
  - `state` — Created during VALIDATE-TASK with `APPROVED` or `REJECTED` as the post-implementation review outcome
- Decision: The `TASKS-SUBTASKS.md` template is removed since subtasks are no longer a single Markdown file — the directory structure itself is the canonical representation
- Decision: Subtask completion is determined by the presence of a `patch` file (replaces the `- [x]` checklist grammar)
- Decision: Overall validation pass/fail (in `validation.md`) remains unchanged; per-subtask `state` files record granular review outcomes during validation
- Alternatives considered: Keeping `subtasks.md` as an index alongside the directories — rejected because it creates redundancy and a sync problem

## Risks / Trade-Offs

- Risk: Actions that currently grep for `- [ ]`/`- [x]` patterns need to switch to directory scanning — mitigated by updating all affected actions in the same task
- Trade-off: More files on disk per subtask (3 files vs. 1 checklist line + 1 patch file) — acceptable because it enables richer per-subtask metadata

## Migration Plan

- All affected action guides and templates are updated in a single task
- No runtime migration needed since this is a skill protocol (Markdown documents only)
- Existing tasks in other repositories using the old format are unaffected until they adopt the updated skill
