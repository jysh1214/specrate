# Spec Delta of *Redesign as Task Manager*

## Apply to Spec *Specrate Core*

### Requirement: Specs Management (REMOVED)

- **Reason**: The specs concept adds unnecessary complexity. Documentation and requirement tracking can happen as normal subtasks within a task.
- **Replacement**: Documentation updates are handled as subtasks during implementation.

### Requirement: Spec Delta Tracking (REMOVED)

- **Reason**: Without specs, spec-deltas serve no purpose.
- **Replacement**: N/A

### Requirement: Task Hierarchy (ADDED)

The system **SHALL** organize work in a three-level hierarchy:

#### Scenario: Task with Jira ticket

- **WHEN** user proposes a task with a Jira ticket reference
- **THEN** the task folder includes an optional `ticket` file linking to the external tracker

#### Scenario: Task with subtasks

- **WHEN** user plans a task
- **THEN** the task is broken into subtasks tracked in `subtasks.md`
- **THEN** each subtask maps to a git commit
- **THEN** the task as a whole maps to a git PR

### Requirement: Task Folder Structure (MODIFIED)

The task folder **SHALL** contain:
- `state` (required) — PROPOSED, PLANNED, IMPLEMENTED, FAILED, ARCHIVED
- `proposal.md` (required) — motivation and goals
- `subtasks.md` (required after PLANNED) — replaces `tasks.md`
- `validation.md` (required after IMPLEMENTED) — validation method and result
- `design.md` (optional) — design rationale
- `issues.md` (required if FAILED) — issues, root causes, fixes
- `ticket` (optional) — Jira ticket link

### Requirement: Validation (MODIFIED)

- **From** optional validation
- **Reason**: Without specs as source of truth, validation becomes the primary quality gate and must be required.

### Requirement: Archive Without Spec Merge (MODIFIED)

- **From** Archive with spec-delta integration
- **Reason**: No specs to merge into. Archiving simply marks the task as completed for historical reference.
