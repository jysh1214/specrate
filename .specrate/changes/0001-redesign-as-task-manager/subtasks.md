# Subtasks of *Redesign as Task Manager*

## Core Documents

- [x] Rewrite `references/PRINCIPLE.md` — remove specs concept, define task/subtask hierarchy, update folder structure, update lifecycle states, make validation required
- [x] Rewrite `SKILL.md` — update overview, rename decisions from "change" to "task", update action references

## Action Guides

- [x] Rename and rewrite `references/actions/PROPOSE-CHANGE.md` → `PROPOSE-TASK.md`
- [x] Rename and rewrite `references/actions/PLAN-CHANGE.md` → `PLAN-TASK.md` — reference `subtasks.md` instead of `tasks.md`
- [x] Rename and rewrite `references/actions/IMPLEMENT-CHANGE.md` → `IMPLEMENT-TASK.md`
- [x] Rename and rewrite `references/actions/VALIDATE-CHANGE.md` → `VALIDATE-TASK.md` — validation is now required
- [x] Rename and rewrite `references/actions/ARCHIVE-CHANGE.md` → `ARCHIVE-TASK.md` — remove spec-delta merge step
- [x] Rename and rewrite `references/actions/AMEND-CHANGE.md` → `AMEND-TASK.md`
- [x] Rename and rewrite `references/actions/CREATE-PR.md` → `CREATE-PR.md` (keep name, update content)
- [x] Rename and rewrite `references/actions/DOCUMENT-ISSUES.md` → `DOCUMENT-ISSUES.md` (keep name, update content)
- [x] Update `references/actions/SHOW-STATUS.md` — remove spec status, show tasks only

## Templates

- [x] Rename `assets/templates/CHANGES-PROPOSAL.md` → `TASKS-PROPOSAL.md` — remove "Affected specs" from Impact section
- [x] Rename `assets/templates/CHANGES-TASKS.md` → `TASKS-SUBTASKS.md` — update heading and terminology
- [x] Rename `assets/templates/CHANGES-DESIGN.md` → `TASKS-DESIGN.md` — update heading
- [x] Update `assets/templates/VALIDATION.md` — no structural changes needed
- [x] Update `assets/templates/OUTPUTS-STATUS.md` — remove spec columns, show tasks only
- [x] Update `assets/templates/CREATE-PR.md` — replace change terminology with task
- [x] Update `assets/templates/DOCUMENT-ISSUES.md` — replace change terminology with task
- [x] Delete `assets/templates/SPECS-SPEC.md`
- [x] Delete `assets/templates/CHANGES-SPEC-DELTA.md`

## Documentation

- [x] Update `README.md` — remove spec references, update lifecycle diagram, update usage examples
- [x] Update `CLAUDE.md` — reflect new task-centric architecture

## Notes

- Action guides that are renamed should have the old file deleted and a new file created.
- All references to "change" in content should become "task", and "change-id" should become "task-id".
- All references to "tasks.md" (the artifact) should become "subtasks.md".
