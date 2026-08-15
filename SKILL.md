# Engineering Discipline Skill

Apply this skill when designing, implementing, reviewing, or refactoring software where maintainability and semantic correctness matter.

This discipline focuses on modeling the domain intentionally instead of allowing implementation convenience to define the system.

## Core principles

1. Model domain truths, not convenient data shapes.
2. Give every fact one semantic owner.
3. Do not model failures, states, or concepts that are outside the explicitly agreed scope.
4. Separate observation/data from policy/judgment.
5. Never hide meaningful failures behind silent fallback.
6. Centralize shared invariants and use established libraries for commodity mechanisms.
7. Organize code by domain responsibility, not arbitrary helper categories.

## Detailed guidance

Read the relevant references before making architectural decisions:

- `references/domain-modeling.md` — domain truths, invariants, and semantic ownership
- `references/scope-and-failure.md` — closed scope and unsupported behavior
- `references/architecture.md` — responsibilities, shared invariants, and structure
- `references/review-guide.md` — applying the discipline during review
