# Specrate

Specrate is an agent skill that manages specs and changes in a structured way. It provides a framework for proposing, planning, implementing, and archiving changes to the system's specs.

## Installation

Install the skill by git-cloning into your repo's `.claude/skills` folder.

Note: the skill itself is installed under `.claude/skills/specrate`, while the documents it manages are created/updated under `.specrate/` at your repository root.

```sh
mkdir -p .claude/skills && git clone https://github.com/jysh1214/specrate.git .claude/skills/specrate && rm -rf .claude/skills/specrate/.git
```

## Usage

Specrate manages spec and change artifacts under `.specrate/` at the repository root (see [references/PRINCIPLE.md](./references/PRINCIPLE.md) for conventions).

1. Show current status: "Show the current status of specs and changes"
2. Propose a new change: "Propose a new change to {description of the change}" (optionally include Jira ticket)
3. Amend an existing change: "Amend the change {change-id}: {description of the amendment}"
4. Plan a proposed change: "Plan the proposed {change-id}"
5. Implement a planned change: "Implement the planned {change-id}"
6. Archive an implemented change: "Archive the implemented {change-id}"
7. Prepare a PR: "Prepare a PR for {change-id}"
8. Document issues in a change: "Document issues found in {change-id}"
9. Fix a spec from codebase: "Fix the spec for {spec-id, or description of the spec scope} from the codebase"

Refer to the [SKILL.md](./SKILL.md) file for how the skill works in detail.

## Acknowledgements

This skill was heavily inspired by the [OpenSpec](https://openspec.dev).
