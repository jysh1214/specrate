# Action: Show Status

When showing the current status of specs and changes, follow these steps:

1. Check whether the `.specrate/` folder exists.
   - If it does not exist, report that there are no specrate-managed artifacts yet (no specs/changes to show), and stop.
2. Summarize specs.
   - Check whether `.specrate/specs/` exists.
   - If it exists, list each `.specrate/specs/{spec-id}/` folder and whether it contains the required file `spec.md`.
   - Report the total number of specs and flag any specs missing `spec.md`.
3. Summarize changes.
   - Check whether `.specrate/changes/` exists.
   - If it exists, enumerate each `.specrate/changes/{change-id}/` folder.
   - For each change folder:
     - Read `.specrate/changes/{change-id}/state`.
       - If missing, mark the change state as `MISSING`.
       - If present but not one of `PROPOSED`, `PLANNED`, `IMPLEMENTED`, `ARCHIVED`, mark it as `INVALID` and include the raw content.
     - Verify required files exist:
       - Always required: `state`, `proposal.md`, `spec-delta.md`.
       - Required for `PLANNED` and later: `tasks.md`.
       - Optional: `design.md`.
     - If `tasks.md` exists, compute task progress using task list grammar:
       - Count completed tasks: lines containing `- [x]` (case-insensitive).
       - Count pending tasks: lines containing `- [ ]`.
       - Report `{completed}/{total}`.
     - Flag inconsistencies:
       - State is `IMPLEMENTED` but there are pending tasks.
       - State is `ARCHIVED` but the change still exists under `.specrate/changes/` (this is allowed, but mention it is now historical).
4. Present the status in a compact report.
   - Include counts and group changes by state.
   - For each change, show: `change-id`, state, task progress (if applicable), and any missing/invalid required files.
   - If there are many items, show a representative subset and indicate that more exist.
5. Provide next-step suggestions.
   - If there are `PROPOSED` changes, suggest planning them.
   - If there are `PLANNED` changes, suggest implementing them.
   - If there are `IMPLEMENTED` changes, suggest archiving them.
   - If there are missing/invalid files, suggest amending/fixing those changes first.
