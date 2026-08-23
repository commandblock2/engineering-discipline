# Make invalid state unrepresentable

A state that the accepted model says must not exist shall not be representable as a normal program value.

## Model domain truths, not convenient data shapes

Types must represent domain truths rather than storage layouts or implementation convenience.

Use enums, constrained types, and constructors to encode invariants. Do not use broad structures whose correctness depends on callers remembering relationships between fields.

When multiple fields represent one fact, keep exactly one representation whenever possible.

## Parsing is the construction boundary

Parsing and deserialization must either produce a valid domain value or fail.

Do not create invalid-capable intermediate decoded representations of the same domain concept.

Accepted:

```
external input -> valid domain value
external input -> error
```

Rejected:

```
external input -> unchecked value -> validate() -> domain value
```

Once a domain value exists, ordinary code must be able to rely on its invariants.

## Scope is part of validity

States outside the explicitly agreed scope are invalid states.

Do not add speculative states, statuses, lifecycle phases, compatibility modes, recovery paths, or future behavior merely because they are possible.

Unsupported external input must be rejected at the boundary when the accepted
contract defines boundary validation as its recovery behavior. Rejection must
not construct or return an invalid domain value.

If an unexpected external value produces an invalid or unsupported state, or if
such a state is reached internally, and no explicit error recovery is defined,
panic or propagate the exception at the detection site. This rule is absolute
except for explicitly documented exceptions. Do not invent a new error state,
status, outcome, fallback, compatibility path, or recovery path to continue.

## Review

Review must check both:

- missing required states;
- extra modeled states or behavior outside the agreed scope.
