# Tequila

Tequila is an agent skill that manages tasks in a structured way, with a strong focus on engineering workflow. It provides a framework for proposing, planning, implementing, validating, and archiving tasks.

Forked from [Specrate](https://github.com/rickygao/specrate).

## Installation

Claude code:

```sh
mkdir -p .claude/skills && git clone https://github.com/jysh1214/tequila.git .claude/skills/tequila && rm -rf .claude/skills/tequila/.git
```

Auggie:

```sh
mkdir -p .augment/skills && git clone https://github.com/jysh1214/tequila.git .augment/skills/tequila && rm -rf .augment/skills/tequila/.git
```

## Task Lifecycle

```
                  ┌───────────┐
          ┌──────▶│  PROPOSE  │◀──────────────────────┐
          │       └─────┬─────┘                       │
          │             ▼                             │
          │       ┌───────────┐                       │
          │  ┌───▶│   PLAN    │                       │
          │  │    └─────┬─────┘                       │
          │  │          ▼                             │
          │  │    ┌───────────┐                       │
          │  │    │ IMPLEMENT │                       │
          │  │    └─────┬─────┘                       │
          │  │          ▼                             │
          │  │    ┌───────────┐                       │
          │  │    │ VALIDATE  │                       │
          │  │    └─────┬─────┘                       │
          │  │          │                             │
          │  │     ┌────┴────┐                        │
          │  │     │         │                        │
          │  │   pass      fail                       │
          │  │     │         │                        │
          │  │     ▼         ▼                        │
          │  │ ┌───────┐ ┌─────────────────┐          │
          │  │ │ARCHIVE│ │ DOCUMENT ISSUES │          │
          │  │ └───────┘ └────────┬────────┘          │
          │  │           ┌────────┴────────┐          │
          │  │           │                 │          │
          │  │           ▼                 ▼          │
          │  │  ┌──────────────┐ ┌──────────────────┐ │
          │  └──┤ AMEND TASK   │ │ PROPOSE NEW      ├─┘
          └─────┤ (fix & retry)│ │ TASK             │
                └──────────────┘ └──────────────────┘
```

## Usage

Tequila manages task artifacts under `.tequila/` at the repository root (see [references/PRINCIPLE.md](./references/PRINCIPLE.md) for conventions).

0. Run Free Bird mode (full automated flywheel — requires a proposed task):
```txt
Follow tequila skill, run Free Bird mode for {task-id}; validation: {description of validation}
```
   The task must already be in `PROPOSED` state (use step 1 first). Free Bird then takes over: plan → implement → validate → archive, with automatic amend-and-retry on failure.
1. Propose a new task:
```txt
Follow tequila skill, propose a new task to {description of the task} (optionally include Jira ticket)
```
2. Plan a proposed task:
```txt
Follow tequila skill, plan the proposed {task-id}
```
3. Implement a planned task:
```txt
Follow tequila skill, implement the planned {task-id}
```
4. Validate an implemented task:
```txt
Follow tequila skill, validate the implemented {task-id}: {description of validation}
```
5. Archive a validated task (commit changes):
```txt
Follow tequila skill, archive the validated {task-id}
```
6. Amend an existing task:
```txt
Follow tequila skill, amend the task {task-id}: {description of the amendment}
```
7. Show current status:
```txt
Follow tequila skill, show the current status of tasks
```
8. Document issues in a task:
```txt
Follow tequila skill, document issues found in {task-id}
```

Refer to the [SKILL.md](./SKILL.md) file for how the skill works in detail.

## Acknowledgements

This project is forked from [Specrate](https://github.com/rickygao/specrate), which was heavily inspired by [OpenSpec](https://openspec.dev).
