# Subtasks of *Add Free Bird Mode*

## Action Document

- [x] Create `references/actions/FREE-BIRD.md` defining the orchestration sequence: plan → implement → validate → archive
- [x] Update `FREE-BIRD.md` to use a persistent `reincarnation` file (initialized to 15, decremented after each loop, stops at 0)
- [x] Update `FREE-BIRD.md` to explicitly document issues for each failure iteration before amending
- [x] Specify required inputs: `{task-id}` (must be in `PROPOSED` state) and `validation: {description}`
- [x] Reference existing actions (PLAN-TASK, IMPLEMENT-TASK, VALIDATE-TASK, ARCHIVE-TASK, DOCUMENT-ISSUES, AMEND-TASK) by delegation rather than duplicating their steps

## Template Update

- [x] Update `assets/templates/DOCUMENT-ISSUES.md` to show multiple `### Issue:` sections

## Principle Update

- [x] Add `reincarnation` file to the task folder structure in `references/PRINCIPLE.md`

## Skill Routing

- [x] Add a new decision branch in `SKILL.md` to route "Free Bird mode" requests to `FREE-BIRD.md`
