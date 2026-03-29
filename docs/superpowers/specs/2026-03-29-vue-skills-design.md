# Vue Skills Design

## Goal

Create a small set of narrowly scoped `SKILL.md`-based instructions for AI coding agents that help them build high-quality greenfield Vue 3 + TypeScript projects.

The skills should be grounded in patterns observed in the two reference repositories in this workspace:

- `prefect-design`: a low-level reusable Vue component system
- `prefect-ui-library`: a higher-level Vue library with domain models, services, maps, schemas, and application-facing components

The resulting skills should be generic and reusable across future Vue projects, with Prefect patterns cited as evidence and examples rather than copied as strict defaults.

## Source Analysis Summary

### `prefect-design`

Key strengths:

- Strong component-oriented organization under `src/components`
- Consistent local `index.ts` exports per component folder
- Clear separation between components, compositions, layouts, models, plugins, types, and utilities
- Typed props and emits in representative components such as `src/components/Wizard/PWizard.vue`
- A library-style entry point in `src/index.ts` that defines a public API and installable Vue plugin

Observed risks and caveats:

- Very large barrel exports such as `src/components/index.ts` can become hard to review and easy to bloat
- The component surface is large relative to visible automated test coverage
- Some patterns are design-system specific and should not be treated as universal Vue defaults

### `prefect-ui-library`

Key strengths:

- Clear higher-level separation between components, compositions, services, maps, models, schemas, router, localization, and utilities
- Useful transport and integration boundaries in `src/services`, especially the base `Api` class
- Strong evidence of translating domain and API concerns outside presentational components through `services`, `maps`, and `models`
- Library entry point in `src/index.ts` that exposes a public surface and handles plugin setup

Observed risks and caveats:

- Some files, such as `src/maps/filters.ts`, are large enough to create review and maintenance pressure
- There are tests present, but the amount of test coverage appears modest relative to the amount of transformation and orchestration logic
- Some implementation areas rely on ESLint exceptions, which is sometimes justified but should not become a default habit in future projects

### Cross-Repo Conclusions

The two repositories together suggest a useful architectural split for future Vue projects:

- a reusable UI/system layer for low-level components and shared presentation primitives
- a domain/application layer for services, models, maps, schemas, routing, and feature-specific components

They also show that good structure alone is not enough. A future skill set should preserve the strong layering and typed boundaries while being stricter about testing and verification.

## Proposed Skill Set

### 1. `vue-project-architecture`

Purpose:
Help agents structure a Vue 3 + TypeScript project with clear module boundaries, explicit public surfaces, and a sane default layering model.

Primary guidance:

- Organize code by responsibility, not by file type alone
- Keep components, compositions, services, maps/adapters, models/types, and utilities distinct
- Use top-level `index.ts` files intentionally to define public APIs, not as dumping grounds
- Split reusable UI/system concerns from domain/application concerns
- Prefer small, focused modules over large mixed-responsibility files

Reference evidence:

- `prefect-design/src/index.ts`
- `prefect-design/src/components`
- `prefect-ui-library/src/index.ts`
- `prefect-ui-library/src/services`
- `prefect-ui-library/src/maps`
- `prefect-ui-library/src/models`

### 2. `vue-component-design`

Purpose:
Teach agents how to build reusable, typed, maintainable Vue components with clear interfaces and minimal domain leakage.

Primary guidance:

- Keep presentation components focused on rendering and emitting intent
- Use typed props and emits
- Prefer controlled interfaces where inputs and update events are explicit
- Extract reactive behavior into compositions when component scripts start coordinating too much logic
- Preserve accessibility and styling discipline
- Avoid combining API transport, domain mapping, and presentation in one SFC

Reference evidence:

- `prefect-design/src/components/Wizard/PWizard.vue`
- `prefect-design/src/components/*`
- `prefect-design/src/compositions`

### 3. `vue-domain-data-flow`

Purpose:
Guide agents on how to move data through a Vue application without leaking backend payload shapes directly into the component tree.

Primary guidance:

- Use services for transport and request orchestration
- Use maps/adapters to translate between backend request/response shapes and domain-facing shapes
- Keep models/types stable and meaningful to the UI layer
- Let components consume domain-oriented data instead of raw API payloads whenever the domain is nontrivial
- Be explicit about ownership of data transformation logic

Reference evidence:

- `prefect-ui-library/src/services/Api.ts`
- `prefect-ui-library/src/services`
- `prefect-ui-library/src/maps/filters.ts`
- `prefect-ui-library/src/models`
- `prefect-ui-library/src/schemas`

### 4. `vue-testing-and-verification`

Purpose:
Make agents verify behavior, not just compile success, and apply testing effort where Vue projects often underinvest.

Primary guidance:

- Test transformation logic, mapping code, and reactive orchestration
- Treat `lint`, `build`, and `typecheck` as baseline verification, not complete validation
- Add focused tests for utility logic, composables, and nontrivial domain transforms
- Prefer verification evidence before claiming a change is complete
- Escalate missing tests as a real quality risk during review

Reference evidence:

- `prefect-ui-library/package.json`
- `prefect-design/package.json`
- `prefect-ui-library/.github/workflows/tests.yaml`
- `prefect-design/.github/workflows/tests.yaml`
- `prefect-ui-library/src/compositions/usePagination.ts`
- `prefect-ui-library/src/maps/filters.ts`

### 5. `vue-code-review`

Purpose:
Provide a high-signal review checklist for Vue changes, focused on architectural integrity, API quality, and testing sufficiency.

Primary guidance:

- Look for boundary violations between components, compositions, services, maps, and models
- Check whether component contracts are narrow, typed, and comprehensible
- Flag large files and barrels that obscure ownership or bloat the public surface
- Look for backend-shaped data leaking into presentation code
- Treat missing tests for nontrivial logic as a review finding, not a suggestion

Reference evidence:

- `prefect-design/src/components/index.ts`
- `prefect-ui-library/src/maps/filters.ts`
- `prefect-ui-library/src/services/index.ts`
- `prefect-ui-library/src/components`

## Skill Authoring Principles

Each skill should:

- Be narrowly scoped enough that an agent can select it confidently from task wording
- Give explicit rules, not vague advice
- Include concrete signals for when the skill applies
- Include anti-patterns to avoid
- Prefer generic Vue 3 + TypeScript guidance while citing Prefect examples as supporting evidence
- Stay useful in greenfield projects, not just library repositories

Each skill should avoid:

- Encoding Prefect-specific naming as a universal standard
- Treating barrel exports or plugin registration as mandatory everywhere
- Assuming every Vue project needs the same level of layering on day one
- Over-prescribing patterns that only make sense for published component libraries

## Initial Implementation Shape

Create one folder per skill under a root-level skills directory dedicated to this project. Each skill should include at minimum:

- `SKILL.md`

Suggested initial set:

- `skills/vue-project-architecture/SKILL.md`
- `skills/vue-component-design/SKILL.md`
- `skills/vue-domain-data-flow/SKILL.md`
- `skills/vue-testing-and-verification/SKILL.md`
- `skills/vue-code-review/SKILL.md`

## Open Decisions Already Resolved

- Use a small set of narrowly scoped skills instead of one broad Vue skill
- Optimize for generic greenfield Vue 3 + TypeScript work
- Implement actual `SKILL.md` files, not only prose guidance
- Use the workspace root as the owning repository for the new instructions

## Next Step

After this design is reviewed and approved, write an implementation plan for the skill files themselves. The implementation phase should include:

- creating the root-level skill folder structure
- drafting each `SKILL.md`
- ensuring each skill has a clear trigger, scope, checklist, and anti-pattern section
- validating that the skills do not contradict each other unnecessarily
