---
name: vue-project-architecture
description: Use when starting or restructuring a Vue 3 + TypeScript project and you need to choose an appropriate architecture without overbuilding it
---

# Vue Project Architecture

## Overview

Choose the simplest structure that keeps ownership, boundaries, and change surfaces clear.

## Use This When

- starting a new Vue project
- adding a new area that might deserve its own module boundary
- restructuring a codebase that has become hard to navigate

## Scope

- choosing structure and boundaries
- deciding when a new layer is justified
- defining public module surfaces
- limited to project-level structural decisions and module boundaries

## Core Rules

- Organize by responsibility, not by technical fashion
- Add layers only when they reduce coupling or confusion
- Keep public entry points intentional
- Split modules when boundaries blur responsibilities
- Do not copy large-project architecture into a small project without evidence

## Workflow

- Identify the current pain: navigation, coupling, ownership, or growth pressure
- Choose the simplest structure that addresses that pain
- Add only the boundaries that clearly reduce confusion
- Re-check whether any layer can be removed without losing clarity

## Architecture Checks

- Can a reader find where UI, state coordination, and domain logic live?
- Does each module have one obvious owner and purpose?
- Would removing a layer make the code easier to understand?

## Anti-Patterns

- premature service layers
- generic `utils` dumping grounds
- barrels that expose everything by default
- deeply nested folders with no boundary value
