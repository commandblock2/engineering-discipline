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

Unsupported external input must be rejected at the boundary.

If an unsupported state is reached internally, panic at the detection site. Do not invent semantics to continue.

## Review

Review must check both:

- missing required states;
- extra modeled states or behavior outside the agreed scope.
