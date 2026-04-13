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
- Treat broken behavior, weak contracts, or architecture drift as higher severity than style issues
- Flag unclear boundaries, ownership, and contracts
- Treat missing tests for meaningful logic as findings
- Keep feedback specific and actionable

## Workflow

- Identify the highest-risk behavior or structure first
- Turn each concern into a concrete finding or clear pass
- Order findings by severity: correctness and contract failures first, maintainability and architecture risks second, minor clarity issues last
- Keep summaries brief and secondary
- If a concern does not rise to a meaningful risk, leave it out

## Review Checks

- Does the code make responsibility and ownership obvious?
- Is there architecture drift, such as duplicated logic, cross-layer coupling, or responsibilities leaking across components?
- Are component contracts explicit about props, emits, slots, and lifecycle expectations?
- Are names, boundaries, and APIs understandable without guesswork?
- Is the implementation simpler than the problem, or more elaborate than necessary?
- Are tests covering meaningful behavior, edge cases, and regression risk?
- Does the change leave important logic unverified or hard to verify?

## Anti-Patterns

- summary-only reviews
- style nitpicks that ignore structural risk
- vague comments without an actionable concern
- approving under-tested complex logic
