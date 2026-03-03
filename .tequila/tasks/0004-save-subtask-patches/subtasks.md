# Subtasks of *Save Subtask Patches*

## Documentation

- [x] Add `patches/` folder and patch naming convention to PRINCIPLE.md folder structure

## Action Guides

- [x] Update IMPLEMENT-TASK.md to save a patch file after each subtask completion
- [x] Update ARCHIVE-TASK.md to use patch files when creating subtask-aligned commits

## Notes

- Patch files are named `{subtask_id}-{subtask_name}.patch` where `{subtask_id}` is the 1-based index of the subtask (zero-padded to 3 digits) and `{subtask_name}` is kebab-case, verb-led (same convention as task IDs)
- Example: for task `0004-save-subtask-patches`, a subtask patch might be `0001-add-patches-folder-to-principle.patch`
- Patches are saved during implementation (not at archive time), so they serve as incremental snapshots
- At archive time, patches guide the commit splitting — each patch maps to one commit
