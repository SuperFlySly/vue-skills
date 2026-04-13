# Vue Naming Conventions Update Design

## Goal

Strengthen the existing Vue skills with explicit naming-convention guidance without creating a separate naming skill.

The update should make naming more actionable while preserving the current skill boundaries:

- `vue-component-design` owns component-surface naming.
- `vue-code-quality` owns local implementation naming.

## Scope

Update these files:

- `skills/vue-component-design/SKILL.md`
- `skills/vue-code-quality/SKILL.md`

Do not add a new `vue-naming-conventions` skill.

## `vue-component-design` Updates

Add component-surface naming guidance:

- Component names should describe the user-facing concept, not the implementation detail.
- Props should name accepted data or configuration. Avoid vague names such as `value`, `data`, or `item` unless the component domain makes them obvious.
- Emits should name user or domain events. Avoid implementation-shaped event names such as `clickButton` when the component intent is `submit`, `select`, or another domain action.
- Slots should name placed content by role, not layout mechanics.
- Composables extracted from components should use `useX` and name the behavior or state they provide.

## `vue-code-quality` Updates

Add local implementation naming guidance:

- Functions that perform work should use verb phrases.
- Values, constants, and factories should use noun phrases when that better matches what they represent.
- Booleans should use predicate names such as `is`, `has`, `can`, or `should`.
- Types and interfaces should use domain concept names rather than transport or UI implementation names, unless the transport or UI boundary is the actual concept.
- Helpers should include enough context to avoid generic names such as `handle`, `process`, `format`, or `map`.
- Files and exports should make the primary responsibility obvious.

## Explicit Non-Goals

Do not add universal Vue prefix rules such as:

- `BaseX`
- `AppX`
- project-specific prefixes such as `PButton`

Do not add mandatory folder naming rules. Those should remain project conventions, not universal skill rules.

## Acceptance Criteria

- `vue-component-design` includes practical naming guidance for components, props, emits, slots, and extracted composables.
- `vue-code-quality` includes practical naming guidance for functions, values, booleans, types/interfaces, helpers, files, and exports.
- The guidance remains concise enough to fit the current skill style.
- The update does not blur the boundary between component-contract naming and local implementation naming.
- No new skill folder is created.
