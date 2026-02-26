# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Specrate is an agent skill (not a traditional application) that manages specs and changes in a structured way. It is installed into other repositories as a skill under `.claude/skills/specrate/` or `.augment/skills/specrate/`. There is no build system, no tests, and no runtime code — the project consists entirely of Markdown documents that define a skill protocol.

## Repository Structure

- `SKILL.md` — Skill entry point with YAML front matter; defines the decision tree that routes user intent to specific actions
- `references/PRINCIPLE.md` — Core conventions, folder structure specification, and change lifecycle state machine
- `references/actions/` — 10 action guides (SHOW-STATUS, PROPOSE-CHANGE, PLAN-CHANGE, IMPLEMENT-CHANGE, VALIDATE-CHANGE, ARCHIVE-CHANGE, AMEND-CHANGE, CREATE-PR, DOCUMENT-ISSUES)
- `assets/templates/` — 9 Markdown templates for artifacts (specs, proposals, designs, tasks, validations, etc.)

## Key Concepts

- **Specs** describe "what" the system does (functional, user-oriented, implementation-agnostic)
- **Changes** describe "how" the system evolves, tracked through a lifecycle: `PROPOSED → PLANNED → IMPLEMENTED → ARCHIVED` (with `FAILED` as a side state from any active state)
- Specs are **never edited** during an in-flight change; they are only updated at the `ARCHIVED` step by integrating `spec-delta.md`
- All artifacts live under `.specrate/` in the target repository

## Conventions

- Change IDs use a 4-digit auto-incrementing prefix followed by kebab-case verb-led description: `0001-add-multi-factor-auth`
- Spec IDs are kebab-case noun phrases: `access-control`, `payment-processing`
- `.specrate/work` tracks the currently focused change ID
- Do not create auxiliary documents outside `.specrate/` unless explicitly instructed
- Favor minimal implementations; avoid scope creep
