# Design of *Redesign as Task Manager*

## Context

Specrate is being redesigned from a spec/change tracking system to a task-centric workflow manager. The current user base is AI coding agents (Claude Code, Auggie). The redesign must keep the skill simple and Markdown-based — no JSON metadata, no complex querying, no project management bloat.

## Goals / Non-Goals

- Goals: Replace specs/changes with a Task → Subtask hierarchy; keep the lifecycle states; make validation required; support optional Jira ticket linking; rename `tasks.md` to `subtasks.md`
- Non-goals: Adding rich metadata (priorities, assignees, dates), project/epic grouping, task dependencies, structured data formats (JSON/YAML)

## Decisions

- Decision: Remove `.specrate/specs/` and `spec-delta.md` entirely. Documentation updates are just subtasks.
- Decision: Rename `.specrate/changes/` to `.specrate/tasks/`. Task folders use the same ID format (`0001-verb-description`).
- Decision: Use `subtasks.md` instead of `tasks.md` to avoid confusion with the top-level "task" concept.
- Decision: Keep the same 5 states (PROPOSED, PLANNED, IMPLEMENTED, FAILED, ARCHIVED) — they map well to the task lifecycle.
- Decision: Keep all action guide filenames but rename from `*-CHANGE` to `*-TASK` where applicable.
- Decision: Rename template files from `CHANGES-*` to `TASKS-*`.
- Alternatives considered: Adding JSON metadata, task dependencies, priority fields — deferred as future enhancements to keep the initial redesign focused.

## Risks / Trade-Offs

- Existing users of the spec/change model will need to migrate manually. Mitigation: this is a v2 with a clean break.
- Without specs, there is no formal "source of truth" document. Trade-off accepted: validation.md serves as the quality gate, and documentation updates happen as normal subtasks.

## Migration Plan

1. Update PRINCIPLE.md to remove specs, rewrite around tasks/subtasks
2. Rename and update all action guides
3. Rename and update all templates
4. Update SKILL.md decision tree
5. Update README.md and CLAUDE.md
6. Remove spec-related templates (SPECS-SPEC.md, CHANGES-SPEC-DELTA.md)
