# Proposal of *Add Validating State*

## Motivation

The current lifecycle jumps from `IMPLEMENTED` directly to `ARCHIVED` or `FAILED` with no intermediate state indicating that validation is in progress. Adding a `VALIDATING` state provides visibility into the workflow and makes the lifecycle more explicit.

## Summary

- Add `VALIDATING` as a new state in the task lifecycle between `IMPLEMENTED` and `ARCHIVED`
- Update the state machine: `PROPOSED → PLANNED → IMPLEMENTED → VALIDATING → ARCHIVED`
- VALIDATE-TASK.md sets the state to `VALIDATING` on entry
- ARCHIVE-TASK.md requires `VALIDATING` (instead of `IMPLEMENTED`) as its entry condition
- Update PRINCIPLE.md, CLAUDE.md, and FREE-BIRD.md to reflect the new state

## Impact

- Affected code: `references/PRINCIPLE.md`, `references/actions/VALIDATE-TASK.md`, `references/actions/ARCHIVE-TASK.md`, `references/actions/FREE-BIRD.md`, `CLAUDE.md`
