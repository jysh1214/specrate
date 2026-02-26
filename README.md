# Specrate

Specrate is an agent skill that manages specs and changes in a structured way. It provides a framework for proposing, planning, implementing, and archiving changes to the system's specs.

## Installation

Claude code:

```sh
mkdir -p .claude/skills && git clone https://github.com/jysh1214/specrate.git .claude/skills/specrate && rm -rf .claude/skills/specrate/.git
```

Auggie:

```sh
mkdir -p .augment/skills && git clone https://github.com/jysh1214/specrate.git .augment/skills/specrate && rm -rf .augment/skills/specrate/.git
```

## Change Lifecycle

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
          │  └──┤ AMEND CHANGE │ │ PROPOSE NEW      ├─┘
          └─────┤ (fix & retry)│ │ CHANGE           │
                └──────────────┘ └──────────────────┘
```

## Usage

Specrate manages spec and change artifacts under `.specrate/` at the repository root (see [references/PRINCIPLE.md](./references/PRINCIPLE.md) for conventions).

1. Show current status: "Follow specrate skill, show the current status of specs and changes"
2. Propose a new change: "Follow specrate skill, propose a new change to {description of the change}" (optionally include Jira ticket)
3. Amend an existing change: "Follow specrate skill, amend the change {change-id}: {description of the amendment}"
4. Plan a proposed change: "Follow specrate skill, plan the proposed {change-id}"
5. Implement a planned change: "Follow specrate skill, implement the planned {change-id}"
6. Validate an implemented change: "Follow specrate skill, validate the implemented {change-id}"
7. Archive an implemented change: "Follow specrate skill, archive the implemented {change-id}"
8. Prepare a PR: "Follow specrate skill, prepare a PR for {change-id}"
9. Document issues in a change: "Follow specrate skill, document issues found in {change-id}"

Refer to the [SKILL.md](./SKILL.md) file for how the skill works in detail.

## Acknowledgements

This skill was heavily inspired by the [OpenSpec](https://openspec.dev).
