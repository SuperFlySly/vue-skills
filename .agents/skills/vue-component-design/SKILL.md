---
name: vue-component-design
description: Use when creating or changing Vue components and you need clear contracts, maintainable structure, and disciplined data flow
---

# Vue Component Design

## Overview

Build components with one clear purpose, explicit contracts, and internal logic that stays readable as the component grows.

## Use This When

- creating a new component
- revising a component API
- deciding whether logic should stay in a component or move to a composable

## Scope

- component contracts
- internal component structure
- accessibility and semantics
- not broader application design or cross-cutting process guidance

## Core Rules

- Keep props and emits explicit and stable
- Choose controlled or uncontrolled behavior deliberately, and document which state the component owns
- Prefer clear data flow over hidden coordination
- Separate presentational concerns from unrelated business logic
- Extract orchestration-heavy logic into composables
- Name components after the user-facing thing they represent, use props for the data they accept, emits for the events they raise, and slots for the content they place

## Workflow

- Define the component’s single responsibility
- Design the props, emits, slots, and controlled or uncontrolled state model before the internal implementation
- Keep rendering concerns obvious
- Extract logic only when it improves clarity or reuse

## Component Checks

- Can another engineer understand the component contract without reading the full implementation?
- Does the component do one thing well?
- Is accessibility part of the design rather than an afterthought?

## Anti-Patterns

- kitchen-sink components
- vague prop names
- hidden mutation through shared state
- slot APIs that expose internal implementation details
