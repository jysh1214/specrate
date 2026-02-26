# Design of *Add Free Bird Mode*

## Context

Tequila currently requires the user to invoke each lifecycle action individually (plan, implement, validate, archive). For tasks where the scope is clear and validation criteria are known upfront, this manual shepherding adds friction without adding value. Free Bird mode automates the full flywheel in a single invocation.

The target repository is the Tequila skill itself — a set of Markdown documents with no runtime code. All changes are to skill protocol documents.

## Goals / Non-Goals

- Goals:
  - Add a single action that chains plan → implement → validate → archive automatically
  - On validation failure, enter an amend loop (document issues → amend → re-implement → re-validate) with a bounded retry limit
  - Require the task to already be in `PROPOSED` state with a valid `proposal.md`
  - Require the user to supply a validation description upfront so validation can run without prompting
  - Route the new mode from `SKILL.md` via a new decision branch
- Non-goals:
  - Changing the existing lifecycle state machine or any existing action files (other than the DOCUMENT-ISSUES template update)
  - Supporting partial flywheel runs (e.g., start from `PLANNED`) — the user can invoke individual actions for that

## Decisions

- **New action file only, no new templates:** Free Bird reuses all existing actions (PLAN-TASK, IMPLEMENT-TASK, VALIDATE-TASK, ARCHIVE-TASK, DOCUMENT-ISSUES, AMEND-TASK) by reference. It does not duplicate their logic; it describes the orchestration sequence and delegates to each action's defined steps.
- **Persistent reincarnation counter:** Free Bird creates a `reincarnation` file in `.tequila/tasks/{task-id}/` initialized to `15` (by default). After each completed amend loop iteration, the counter is decremented. When it reaches `0`, the action stops with the task in `FAILED` state, signaling that the current direction is likely wrong. This replaces the in-procedure counter with a persistent, observable artifact.
- **Validation description is a required input:** The user must supply it in the invocation (e.g., `validation: {description}`). This removes the need for interactive prompting during the validate step.
- **Per-iteration issue documentation:** Each failure iteration documents its issues via DOCUMENT-ISSUES.md, appending to the existing `issues.md`. This accumulates context across retries so each subsequent attempt is better informed.
- **Update DOCUMENT-ISSUES.md template:** The template is updated to show multiple `### Issue:` sections, making the repeatable structure explicit.
- **Update PRINCIPLE.md:** Add the `reincarnation` file to the task folder structure documentation.

## Risks / Trade-Offs

- **Reduced user oversight:** By automating the full cycle, the user loses the opportunity to review intermediate artifacts (subtasks, design) before implementation begins. Mitigation: the action documents make clear this mode is for well-scoped tasks with known validation criteria.
- **Amend loop may not converge:** Some failures may require human judgement to resolve. Mitigation: persistent reincarnation counter (15 by default) with a clear exit to `FAILED` state, plus accumulated issue documentation across iterations.

## Migration Plan

No migration needed. This is a purely additive change — a new action file and a new decision branch. Existing workflows are unaffected.
