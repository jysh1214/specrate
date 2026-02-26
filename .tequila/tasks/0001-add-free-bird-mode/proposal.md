# Proposal of *Add Free Bird Mode*

## Motivation

Running the full Tequila lifecycle (propose, plan, implement, validate, archive) requires the user to invoke each action individually, shepherding the task through every state transition. For well-scoped tasks where the validation criteria are known upfront, this manual hand-off is unnecessary friction. A single-command "Free Bird" mode would let Tequila fly through the entire flywheel autonomously, only stopping when validation fails — at which point it amends and retries until the task passes.

## Summary

- Add a new **FREE-BIRD** action in `references/actions/FREE-BIRD.md` that orchestrates the full lifecycle: plan → implement → validate → archive
- The action assumes the target task is already in the `PROPOSED` state (with a valid `proposal.md`) and a validation description is provided by the user
- On validation failure, the action enters an amend loop: document issues → amend task → re-implement → re-validate, repeating until the task passes or a maximum retry limit is reached
- Add a new decision branch in `SKILL.md` to route "Free Bird mode" requests to the new action
- Update `references/PRINCIPLE.md` if any lifecycle clarifications are needed to support the automated flow

## Impact

- Affected code: `SKILL.md`, `references/actions/FREE-BIRD.md` (new), `references/PRINCIPLE.md`
