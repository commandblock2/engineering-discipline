---
name: engineering-discipline
description: Apply engineering-discipline principles when designing, implementing, refactoring, or reviewing software, especially when modeling domain state, assigning ownership of semantic facts, and evaluating fallback behavior.
---

# Engineering Discipline

Apply this discipline when designing, implementing, refactoring, or reviewing software.

The core rules are:

1. Make invalid state unrepresentable.
   - Model domain truths, not convenient data shapes.
   - Parsing is the construction boundary.
   - Do not model states outside the agreed scope.

2. Keep exactly one truth.
   - Every semantic fact has one and only one owner.
   - Use language ownership constructs to express that relationship.

3. No unapproved fallback semantics.
   - Fallback behavior must come from the modeled behavior itself or an ADR-level exception.

Detailed guidance:

- `references/invalid-state.md`
- `references/ownership.md`
- `references/fallback.md`
