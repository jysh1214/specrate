# Proposal of *Save Subtask Patches*

## Motivation

Each subtask represents a discrete change — a file creation, modification, or rename — that maps to a Git commit. Currently, there is no mechanism to capture these changes as reviewable, replayable artifacts. By saving each subtask as a Git patch file, users gain:

1. **Reviewability** — patches can be inspected at any time, even before committing.
2. **Natural commit mapping** — each patch corresponds to exactly one subtask and one future commit.
3. **Reproducibility** — any subtask's change can be replayed with `git apply` using its patch file.

## Summary

- Add a `patches/` subfolder to the task folder structure (`.tequila/tasks/{task-id}/patches/`)
- After each subtask is implemented, save its diff as a patch file named `{subtask_id}_{subtask_name}.patch`, where `{subtask_name}` follows the same kebab-case, verb-led convention as `{task-id}`
- Update PRINCIPLE.md to document the `patches/` folder and patch naming convention
- Update the relevant action guide(s) (IMPLEMENT-TASK and/or ARCHIVE-TASK) to include the patch-saving step

## Impact

- Affected code: `references/PRINCIPLE.md`, `references/actions/IMPLEMENT-TASK.md`, `references/actions/ARCHIVE-TASK.md`
