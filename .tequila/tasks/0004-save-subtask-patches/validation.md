# Validation of *Save Subtask Patches*

## Validation Method

User review of all three modified files to confirm correctness, consistency, and completeness.

## Steps

1. Review `references/PRINCIPLE.md` lines 54–57: verify `patches/` folder entry documents the naming convention (`{subtask_id}-{subtask_name}.patch`, 3-digit zero-padded, kebab-case verb-led)
2. Review `references/actions/IMPLEMENT-TASK.md` line 14: verify the patch-saving step is present after subtask completion, with correct naming convention and generation method
3. Review `references/actions/ARCHIVE-TASK.md` line 14: verify commit-splitting guidance references patch files in `.tequila/tasks/{task-id}/patches/`
4. Confirm consistency: naming convention is the same across all three files

## Expected Outcome

All three files consistently describe the `patches/` folder and the `{subtask_id}-{subtask_name}.patch` naming convention. The implementation step generates patches; the archive step consumes them for commit splitting.

## Result

- Status: PASS
- User confirmed all three files are correct and consistent
