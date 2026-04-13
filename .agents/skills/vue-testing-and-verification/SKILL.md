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

- unit tests for isolated logic and pure helpers
- component tests for Vue rendering, props, events, and state transitions
- integration-style checks for cross-component flow, routing, async boundaries, and shared services
- verification depth
- test selection
- completion evidence
- explicitly not covering project architecture or component API design

## Core Rules

- Treat lint, build, and typecheck as baselines
- Add tests where regressions would be costly or subtle
- Match test depth to change risk
- Prefer unit tests for isolated logic, component tests for Vue interaction and rendering behavior, and integration-style checks when the risk spans boundaries
- If behavior cannot be tested directly, use the closest observable evidence available and state the limitation explicitly
- State what was verified and what was not
- Do not claim completion without evidence

## Workflow

- Identify the riskiest behavior in the change
- Choose the smallest direct test or verification command that still exercises the risky behavior
- If direct testing is not possible, choose the most relevant fallback evidence and explain why it is the closest available proof
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
