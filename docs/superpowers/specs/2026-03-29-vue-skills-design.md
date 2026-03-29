# Vue Skills Design

## Goal

Create a small set of narrowly scoped `SKILL.md`-based instructions for AI coding agents that help them build high-quality Vue 3 + TypeScript projects.

The skills should focus on transferable engineering standards:

- strong component design
- clear naming and organisation
- maintainable architecture
- disciplined code quality
- reliable testing and verification
- high-signal code review

The final skills should stand on their own. They should not assume any particular repository shape, company conventions, or library-sized project structure.

## Extracted Design Principles

The skills should encode principles, not templates.

What matters:

- components with clear responsibilities and stable contracts
- code that is typed, readable, and easy to change safely
- naming that makes intent and ownership obvious
- organisation that helps people find the right code quickly
- architecture that matches the project's real complexity
- verification that checks behavior, not just compilation
- review standards that catch structural and maintainability problems early

What should be avoided:

- copying a large-project folder structure into a small project
- inventing layers that do not pay for their complexity
- mixing presentation, state coordination, transport, and data transformation without clear boundaries
- broad public surfaces that make ownership unclear
- weak naming that forces readers to inspect implementation details to understand purpose
- treating `lint`, `build`, or `typecheck` as sufficient evidence that behavior is correct

## Proposed Skill Set

### 1. `vue-project-architecture`

Purpose:
Help agents choose an appropriate project structure, define module boundaries, and scale architecture with complexity instead of guessing at a heavyweight layout up front.

Primary guidance:

- Organize code by responsibility and change surface
- Start with the simplest structure that keeps ownership clear
- Add layers only when they reduce confusion or coupling
- Keep module boundaries explicit
- Define public surfaces intentionally
- Split files and modules when responsibilities start to blur
- Prefer architecture that is easy to navigate over architecture that looks impressive

This skill should cover:

- folder structure
- module boundaries
- public API surfaces
- when to split logic into separate modules
- when not to split logic yet
- how architecture should evolve as a project grows

### 2. `vue-component-design`

Purpose:
Teach agents how to build Vue components with clear interfaces, predictable behavior, and maintainable internal structure.

Primary guidance:

- Keep each component focused on one clear purpose
- Design props and emits as stable contracts
- Prefer explicit data flow over hidden coupling
- Keep presentational concerns separate from unrelated business logic
- Extract reusable logic when the component script becomes orchestration-heavy
- Preserve accessibility, semantics, and styling discipline
- Make component names reflect purpose rather than implementation detail

This skill should cover:

- prop and emit design
- controlled and uncontrolled patterns
- slot design
- accessibility expectations
- internal component structure
- when to extract composables
- how to keep components reusable without over-abstracting

### 3. `vue-code-quality`

Purpose:
Help agents write Vue and TypeScript code that is readable, typed, maintainable, and easy to review.

Primary guidance:

- Prefer explicit, intention-revealing names
- Keep functions and modules focused
- Use TypeScript to clarify contracts rather than to impress the type checker
- Avoid cleverness that hides data flow or control flow
- Isolate complicated transformations so they can be understood and tested
- Keep comments rare and useful
- Optimize for safe change over minimal line count

This skill should cover:

- naming conventions
- file and function shape
- TypeScript discipline
- separation of concerns in implementation
- maintainability heuristics
- common anti-patterns in Vue and TS code

### 4. `vue-testing-and-verification`

Purpose:
Make agents verify behavior with enough evidence for the complexity of the change.

Primary guidance:

- Test logic where regressions are likely and expensive
- Treat verification as part of implementation, not a final formality
- Use `lint`, `build`, and `typecheck` as baselines, not as complete validation
- Add focused tests for transformations, composables, state coordination, and nontrivial component behavior
- Match the verification depth to the risk and complexity of the change
- State verification limits clearly when something cannot be tested

This skill should cover:

- what deserves unit tests
- what deserves component tests
- what deserves integration-style checks
- required verification before claiming completion
- how to report residual risk honestly

### 5. `vue-code-review`

Purpose:
Provide a high-signal review standard for Vue code that focuses on correctness, maintainability, architecture, and test sufficiency.

Primary guidance:

- Review for structural problems, not just syntax and style
- Check whether names, boundaries, and contracts are clear
- Flag components that do too much
- Flag architecture that is too weak or too elaborate for the problem
- Look for hidden coupling and unclear ownership
- Treat missing tests for nontrivial logic as a real finding
- Prefer specific, actionable review feedback tied to behavior or maintainability risk

This skill should cover:

- review checklist design
- severity-based findings
- architecture drift
- component contract quality
- maintainability risks
- testing gaps

## Skill Authoring Principles

Each skill should:

- be narrow enough that an agent can select it confidently
- give explicit rules and decision criteria
- explain when the skill applies
- explain when a simpler approach is correct
- include anti-patterns and review heuristics
- optimize for reusable Vue engineering judgment rather than one team's conventions

Each skill should avoid:

- hard-coding one project structure as the standard
- assuming a library-sized codebase
- encouraging premature abstraction
- teaching patterns without telling agents when not to use them
- overfitting to any specific reference repository

## Initial Implementation Shape

Create one folder per skill under a root-level skills directory. Each skill should include at minimum:

- `SKILL.md`

Suggested initial set:

- `skills/vue-project-architecture/SKILL.md`
- `skills/vue-component-design/SKILL.md`
- `skills/vue-code-quality/SKILL.md`
- `skills/vue-testing-and-verification/SKILL.md`
- `skills/vue-code-review/SKILL.md`

## Open Decisions Already Resolved

- Use a small set of narrowly scoped skills instead of one broad Vue skill
- Optimize for generic Vue 3 + TypeScript work
- Implement actual `SKILL.md` files, not only prose guidance
- Keep the skills independent from the original reference repositories

## Next Step

After this design is reviewed and approved, write an implementation plan for the skill files themselves. The implementation phase should include:

- creating the root-level skill folder structure
- drafting each `SKILL.md`
- ensuring each skill has a clear trigger, scope, checklist, and anti-pattern section
- checking that the skills complement each other without unnecessary overlap
