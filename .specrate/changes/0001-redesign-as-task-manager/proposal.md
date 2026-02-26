# Proposal of *Redesign as Task Manager*

## Motivation

Specrate currently centers on specs (what the system does) and changes (how it evolves), requiring spec-deltas, immutability rules, and an archiving step that merges deltas into specs. This model is heavyweight for everyday engineering work — bug fixes, research tasks, and chores don't fit the spec-delta pattern. Users want a simpler, task-centric workflow where documentation updates are just normal subtasks.

## Summary

- **BREAKING** Remove the specs concept entirely (`.specrate/specs/`, `spec-delta.md`)
- Replace "change" terminology with "task" as the primary unit of work
- Introduce a three-level hierarchy: Jira ticket (optional) → Task → Subtask
- Task maps to a Git PR; subtask maps to a Git commit
- Rename `tasks.md` to `subtasks.md` to reflect the new hierarchy
- Make `validation.md` required (after IMPLEMENTED) instead of optional
- Remove the archiving rule "merge spec-delta into specs" — documentation updates happen as normal subtasks
- Simplify task folder: `state`, `proposal.md`, `subtasks.md`, `validation.md`, `design.md` (optional), `issues.md` (if FAILED), `ticket` (optional)

## Impact

- Affected specs: N/A (specs concept is being removed)
- Affected code: SKILL.md, references/PRINCIPLE.md, all action guides in references/actions/, all templates in assets/templates/, README.md, CLAUDE.md
