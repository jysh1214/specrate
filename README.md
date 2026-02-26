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
          │  │   PASS      FAIL                       │
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

1. Show current status: "Follow tequila skill, show the current status of tasks"
2. Propose a new task: "Follow tequila skill, propose a new task to {description of the task}" (optionally include Jira ticket)
3. Amend an existing task: "Follow tequila skill, amend the task {task-id}: {description of the amendment}"
4. Plan a proposed task: "Follow tequila skill, plan the proposed {task-id}"
5. Implement a planned task: "Follow tequila skill, implement the planned {task-id}"
6. Validate an implemented task: "Follow tequila skill, validate the implemented {task-id}: {description of validation}"
7. Archive an implemented task: "Follow tequila skill, archive the implemented {task-id}"
8. Prepare a PR: "Follow tequila skill, prepare a PR for {task-id}"
9. Document issues in a task: "Follow tequila skill, document issues found in {task-id}"

Refer to the [SKILL.md](./SKILL.md) file for how the skill works in detail.

## Acknowledgements

This project is forked from [Specrate](https://github.com/rickygao/specrate), which was heavily inspired by [OpenSpec](https://openspec.dev).
