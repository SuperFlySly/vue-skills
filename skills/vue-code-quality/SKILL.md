---
name: vue-code-quality
description: Use when writing or refactoring Vue and TypeScript code and you need maintainable naming, file shape, and implementation discipline
---

# Vue Code Quality

## Overview

Write code that reveals intent quickly, keeps contracts clear, and stays safe to change.

## Use This When

- writing Vue or TypeScript code that needs clearer names, file shape, local contracts, or implementation flow
- refactoring confusing code for readability and maintainability
- keeping implementation decisions focused on clarity and local maintainability

## Scope

- code-quality decisions made while writing or refactoring
- naming
- file and function shape
- TypeScript contract clarity
- separation of concerns in implementation
- maintainability heuristics for local code structure
- local implementation clarity rather than project architecture, component API design, or verification strategy

## Core Rules

- Prefer intention-revealing names
- Keep files and functions focused
- Separate orchestration, transformation, and side effects so each unit has one clear job
- Use TypeScript to clarify contracts
- Isolate complex transformations
- Favor shapes that make the happy path and the main data flow easy to scan
- Use maintainability heuristics: smaller units, fewer responsibilities, shallow nesting, and obvious dependencies
- Avoid clever patterns that hide flow
- Keep comments short and rare

## Workflow

- Name the unit by its purpose before refining the implementation
- Keep the happy path readable
- Pull hard-to-read logic into small, testable helpers
- Remove abstraction that does not improve clarity

## Quality Checks

- Would a reader understand the purpose of this file from its name and exports?
- Is the hardest logic easy to locate and test?
- Did abstraction reduce duplication, or just move it around?

## Anti-Patterns

- anonymous helper piles
- Vue watchers, computed values, or lifecycle hooks that mix unrelated concerns
- vague names like `data`, `handler`, or `process` without context
- giant files with mixed responsibilities
- composables or local APIs whose names hide what they actually do
- TypeScript types so abstracted or recursive that the runtime behavior becomes hard to follow
