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
   - If an unexpected external value or any other condition is outside the
     accepted model and no explicit error recovery is defined, panic or
     propagate the exception at the detection site. This rule is absolute
     except for explicitly documented exceptions.
   - Do not represent that condition as a new error state, status, outcome,
     fallback, compatibility path, or recovery path.

2. Keep exactly one truth.
   - Every semantic fact has one and only one owner.
   - Use language ownership constructs to express that relationship.

3. No unapproved fallback or recovery semantics.
   - Fallback or recovery behavior must come from the modeled behavior itself
     or an ADR-level exception.
   - When no explicit error recovery is defined, panic or propagate the
     exception. There is no escape hatch for inventing a recoverable state.

Detailed guidance:

- `references/invalid-state.md`
- `references/ownership.md`
- `references/fallback.md`
