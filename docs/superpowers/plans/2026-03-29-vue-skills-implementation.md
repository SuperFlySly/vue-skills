# Vue Skills Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Create five reusable `SKILL.md` files for Vue 3 + TypeScript projects covering architecture, component design, code quality, testing/verification, and code review.

**Architecture:** Keep the implementation minimal and explicit: one folder per skill under `skills/`, one `SKILL.md` per folder, and no extra scaffolding unless a real need appears during implementation. Each skill should share a consistent structure so agents can scan them quickly, but the content should stay narrowly scoped and avoid duplicated guidance.

**Tech Stack:** Markdown, git, ripgrep, shell verification

---

## File Structure

### New files

- `skills/vue-project-architecture/SKILL.md`
  Responsibility: project structure, boundaries, module ownership, and architecture scaling guidance.
- `skills/vue-component-design/SKILL.md`
  Responsibility: component API design, internal component structure, accessibility, and composable extraction guidance.
- `skills/vue-code-quality/SKILL.md`
  Responsibility: naming, TypeScript discipline, maintainability heuristics, and code-shape rules.
- `skills/vue-testing-and-verification/SKILL.md`
  Responsibility: verification standards, test depth, test selection, and completion criteria.
- `skills/vue-code-review/SKILL.md`
  Responsibility: review checklist and severity-based findings for Vue code.

### Existing files to modify

- `docs/superpowers/plans/2026-03-29-vue-skills-implementation.md`
  Responsibility: track task completion if the plan needs inline adjustments during execution.

### Shared skill structure

Each `SKILL.md` should contain:

- frontmatter with `name` and `description`
- short overview
- clear “use this when” trigger guidance
- explicit scope boundaries
- explicit rules and decision criteria
- concise workflow or checklist
- anti-patterns or “do not do this” section

## Task 1: Create The Skill Directory Structure

**Files:**
- Create: `skills/vue-project-architecture/SKILL.md`
- Create: `skills/vue-component-design/SKILL.md`
- Create: `skills/vue-code-quality/SKILL.md`
- Create: `skills/vue-testing-and-verification/SKILL.md`
- Create: `skills/vue-code-review/SKILL.md`

- [ ] **Step 1: Create the skill directories**

Run:

```bash
mkdir -p skills/vue-project-architecture skills/vue-component-design skills/vue-code-quality skills/vue-testing-and-verification skills/vue-code-review
```

Expected: command exits successfully with no output.

- [ ] **Step 2: Verify the directories exist**

Run:

```bash
find skills -maxdepth 1 -type d | sort
```

Expected output includes:

```text
skills
skills/vue-code-quality
skills/vue-code-review
skills/vue-component-design
skills/vue-project-architecture
skills/vue-testing-and-verification
```

- [ ] **Step 3: Confirm there is nothing to commit yet**

Run:

```bash
git status --short
```

Expected: no tracked changes yet, because git does not record empty directories.

## Task 2: Draft `vue-project-architecture`

**Files:**
- Create: `skills/vue-project-architecture/SKILL.md`

- [ ] **Step 1: Write the skill file with focused architecture guidance**

Write:

```markdown
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
- explicitly not covering component API design, naming standards, or review severity

## Core Rules

- Organize by responsibility, not by technical fashion
- Add layers only when they reduce coupling or confusion
- Keep public entry points intentional
- Split files when they mix responsibilities
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
```

- [ ] **Step 2: Verify the skill includes all required sections**

Run:

```bash
rg -n "^## (Overview|Use This When|Scope|Core Rules|Workflow|Architecture Checks|Anti-Patterns)$" skills/vue-project-architecture/SKILL.md
```

Expected: seven matches, one for each required section.

- [ ] **Step 3: Review for overlap with other planned skills**

Run:

```bash
sed -n '1,220p' skills/vue-project-architecture/SKILL.md
```

Expected review outcome: the file stays focused on structure and boundaries, not component API design, code style, testing, or review mechanics.

- [ ] **Step 4: Commit the architecture skill**

Run:

```bash
git add skills/vue-project-architecture/SKILL.md
git commit -m "feat: add Vue architecture skill"
```

Expected: commit succeeds.

## Task 3: Draft `vue-component-design`

**Files:**
- Create: `skills/vue-component-design/SKILL.md`

- [ ] **Step 1: Write the skill file with component contract guidance**

Write:

```markdown
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
- explicitly not covering project-wide architecture or review severity

## Core Rules

- Keep props and emits explicit and stable
- Prefer clear data flow over hidden coordination
- Separate presentational concerns from unrelated business logic
- Extract orchestration-heavy logic into composables
- Keep names aligned with user-facing purpose

## Workflow

- Define the component’s single responsibility
- Design the props, emits, and slots before the internal implementation
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
```

- [ ] **Step 2: Verify the skill includes all required sections**

Run:

```bash
rg -n "^## (Overview|Use This When|Scope|Core Rules|Workflow|Component Checks|Anti-Patterns)$" skills/vue-component-design/SKILL.md
```

Expected: seven matches, one for each required section.

- [ ] **Step 3: Review for missing component-specific concerns**

Run:

```bash
sed -n '1,220p' skills/vue-component-design/SKILL.md
```

Expected review outcome: props/emits, composable extraction, naming, and accessibility are all present.

- [ ] **Step 4: Commit the component design skill**

Run:

```bash
git add skills/vue-component-design/SKILL.md
git commit -m "feat: add Vue component design skill"
```

Expected: commit succeeds.

## Task 4: Draft `vue-code-quality`

**Files:**
- Create: `skills/vue-code-quality/SKILL.md`

- [ ] **Step 1: Write the skill file with maintainability and naming guidance**

Write:

```markdown
---
name: vue-code-quality
description: Use when writing or refactoring Vue and TypeScript code and you need maintainable naming, file shape, and implementation discipline
---

# Vue Code Quality

## Overview

Write code that reveals intent quickly, keeps contracts clear, and stays safe to change.

## Use This When

- adding new Vue or TypeScript logic
- refactoring confusing code
- reviewing naming, file shape, and implementation clarity

## Scope

- naming
- file and function shape
- TypeScript contract clarity
- explicitly not covering project architecture selection or review process

## Core Rules

- Prefer intention-revealing names
- Keep files and functions focused
- Use TypeScript to clarify contracts
- Isolate complex transformations
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
- vague names like `data`, `handler`, or `process` without context
- giant files with mixed responsibilities
- type complexity that obscures behavior
```

- [ ] **Step 2: Verify the skill includes all required sections**

Run:

```bash
rg -n "^## (Overview|Use This When|Scope|Core Rules|Workflow|Quality Checks|Anti-Patterns)$" skills/vue-code-quality/SKILL.md
```

Expected: seven matches, one for each required section.

- [ ] **Step 3: Review for duplicated architecture or review guidance**

Run:

```bash
sed -n '1,220p' skills/vue-code-quality/SKILL.md
```

Expected review outcome: the file focuses on code quality and naming, not architecture planning or review severity.

- [ ] **Step 4: Commit the code quality skill**

Run:

```bash
git add skills/vue-code-quality/SKILL.md
git commit -m "feat: add Vue code quality skill"
```

Expected: commit succeeds.

## Task 5: Draft `vue-testing-and-verification`

**Files:**
- Create: `skills/vue-testing-and-verification/SKILL.md`

- [ ] **Step 1: Write the skill file with verification standards**

Write:

```markdown
---
name: vue-testing-and-verification
description: Use when implementing or finishing Vue changes and you need the right level of testing and verification before calling the work complete
---

# Vue Testing And Verification

## Overview

Verify behavior with evidence that matches the risk of the change.

## Use This When

- finishing a feature or bug fix
- deciding what tests a Vue change deserves
- preparing to claim a change is complete

## Scope

- verification depth
- test selection
- completion evidence
- explicitly not covering project architecture or component API design

## Core Rules

- Treat lint, build, and typecheck as baselines
- Add tests where regressions would be costly or subtle
- Match test depth to change risk
- State what was verified and what was not
- Do not claim completion without evidence

## Workflow

- Identify the riskiest behavior in the change
- Choose the smallest test or command that proves it works
- Run baseline checks and targeted checks
- Report both evidence and residual risk

## Verification Checks

- What logic can fail silently without a targeted test?
- Which command proves the change works?
- What residual risk remains after the commands you ran?

## Anti-Patterns

- “build passes” as proof of correctness
- skipping tests for nontrivial logic
- claiming success without command output
- vague verification notes
```

- [ ] **Step 2: Verify the skill includes all required sections**

Run:

```bash
rg -n "^## (Overview|Use This When|Scope|Core Rules|Workflow|Verification Checks|Anti-Patterns)$" skills/vue-testing-and-verification/SKILL.md
```

Expected: seven matches, one for each required section.

- [ ] **Step 3: Review for concrete verification language**

Run:

```bash
sed -n '1,220p' skills/vue-testing-and-verification/SKILL.md
```

Expected review outcome: the file clearly distinguishes baseline checks from behavior validation.

- [ ] **Step 4: Commit the testing and verification skill**

Run:

```bash
git add skills/vue-testing-and-verification/SKILL.md
git commit -m "feat: add Vue testing and verification skill"
```

Expected: commit succeeds.

## Task 6: Draft `vue-code-review`

**Files:**
- Create: `skills/vue-code-review/SKILL.md`

- [ ] **Step 1: Write the skill file with review standards**

Write:

```markdown
---
name: vue-code-review
description: Use when reviewing Vue changes and you need a high-signal checklist for correctness, maintainability, architecture, and testing gaps
---

# Vue Code Review

## Overview

Review Vue code for real engineering risk: weak boundaries, unclear contracts, hidden complexity, and missing verification.

## Use This When

- reviewing a pull request
- auditing a change before merge
- checking whether a Vue change is maintainable

## Scope

- review findings
- maintainability and architecture risk
- testing gaps
- explicitly not covering implementation planning or project setup

## Core Rules

- Prioritize findings over summaries
- Review for behavior and maintainability, not just formatting
- Flag unclear boundaries and contracts
- Treat missing tests for meaningful logic as findings
- Keep feedback specific and actionable

## Workflow

- Identify the highest-risk behavior or structure first
- Turn each concern into a concrete finding or clear pass
- Order findings by severity
- Keep summaries brief and secondary

## Review Checks

- Does the code make responsibility and ownership obvious?
- Are names, boundaries, and APIs understandable without guesswork?
- Is the implementation simpler than the problem, or more elaborate than necessary?

## Anti-Patterns

- summary-only reviews
- style nitpicks that ignore structural risk
- vague comments without an actionable concern
- approving under-tested complex logic
```

- [ ] **Step 2: Verify the skill includes all required sections**

Run:

```bash
rg -n "^## (Overview|Use This When|Scope|Core Rules|Workflow|Review Checks|Anti-Patterns)$" skills/vue-code-review/SKILL.md
```

Expected: seven matches, one for each required section.

- [ ] **Step 3: Review for correct review posture**

Run:

```bash
sed -n '1,220p' skills/vue-code-review/SKILL.md
```

Expected review outcome: the file emphasizes findings, risk, and specificity rather than generic encouragement.

- [ ] **Step 4: Commit the code review skill**

Run:

```bash
git add skills/vue-code-review/SKILL.md
git commit -m "feat: add Vue code review skill"
```

Expected: commit succeeds.

## Task 7: Cross-Skill Consistency Pass

**Files:**
- Modify: `skills/vue-project-architecture/SKILL.md`
- Modify: `skills/vue-component-design/SKILL.md`
- Modify: `skills/vue-code-quality/SKILL.md`
- Modify: `skills/vue-testing-and-verification/SKILL.md`
- Modify: `skills/vue-code-review/SKILL.md`

- [ ] **Step 1: Verify all skill files exist**

Run:

```bash
rg --files skills | sort
```

Expected output:

```text
skills/vue-code-quality/SKILL.md
skills/vue-code-review/SKILL.md
skills/vue-component-design/SKILL.md
skills/vue-project-architecture/SKILL.md
skills/vue-testing-and-verification/SKILL.md
```

- [ ] **Step 2: Verify all files contain the shared section structure**

Run:

```bash
for file in skills/*/SKILL.md; do
  echo "== $file =="
  rg -n "^## " "$file"
done
```

Expected: every file shows `Overview`, `Use This When`, `Core Rules`, one skill-specific check section, and `Anti-Patterns`.
Expected: every file also shows `Scope` and `Workflow`.

- [ ] **Step 3: Read all skills together and trim overlap**

Run:

```bash
for file in skills/*/SKILL.md; do
  echo "-----"
  sed -n '1,220p' "$file"
done
```

Expected review outcome:

```text
Each skill is narrow.
Architecture covers structure decisions.
Component design covers component contracts.
Code quality covers naming and implementation clarity.
Testing covers verification evidence.
Code review covers findings and review posture.
```

- [ ] **Step 4: Commit the consistency pass**

Run:

```bash
git add skills
git commit -m "refactor: align Vue skill set"
```

Expected: commit succeeds.

## Task 8: Final Verification

**Files:**
- Modify: `skills/vue-project-architecture/SKILL.md`
- Modify: `skills/vue-component-design/SKILL.md`
- Modify: `skills/vue-code-quality/SKILL.md`
- Modify: `skills/vue-testing-and-verification/SKILL.md`
- Modify: `skills/vue-code-review/SKILL.md`

- [ ] **Step 1: Run a final file inventory check**

Run:

```bash
find skills -maxdepth 2 -type f | sort
```

Expected output:

```text
skills/vue-code-quality/SKILL.md
skills/vue-code-review/SKILL.md
skills/vue-component-design/SKILL.md
skills/vue-project-architecture/SKILL.md
skills/vue-testing-and-verification/SKILL.md
```

- [ ] **Step 2: Run a final status check**

Run:

```bash
git status --short
```

Expected: clean working tree after the final commit.

- [ ] **Step 3: Capture the final commit history**

Run:

```bash
git log --oneline -5
```

Expected: recent commits for scaffolding, each skill, the consistency pass, and the final verification state.

- [ ] **Step 4: Report completion with residual risks**

Use this completion note:

```text
Created five Vue skill files under `skills/`.
Verified section structure and cross-skill separation.
Residual risk: content quality still depends on manual review of wording and future real-world usage.
```
