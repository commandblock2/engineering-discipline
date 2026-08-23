# No unapproved fallback semantics

There shall be absolutely no fallback behavior unless:

1. the fallback is explicitly authorized by an ADR or equivalent ADR-level exception catalog; or
2. the behavior being modeled explicitly defines that fallback semantics.

Fallback is part of the model, not a general robustness technique.

When no explicit error recovery is defined, panic or propagate the exception
at the detection site. Do not replace an unspecified failure with a new error
state, status, outcome, fallback, compatibility path, or recovery path. This
rule is absolute except for explicitly documented exceptions.

## Language constructs are not inherently forbidden

`unwrap_or_default`, `unwrap_or`, and similar constructs are acceptable when the modeled behavior says the alternate value is the correct semantic result.

Example:

```rust
let retry_count = message.retry_count.unwrap_or(0);
```

is valid if the protocol defines missing retry count as zero.

The same code is invalid if it hides an unspecified design decision.

## Do not invent behavior

Do not add:

- silent defaults;
- alternate implementations;
- compatibility paths;
- ignored errors;
- best-effort recovery;
- automatic retries;
- inferred behavior.

If a fallback appears necessary, stop and determine whether a missing abstraction, missing state, or missing design decision exists.

Use explicit incomplete markers:

```rust
todo!("define behavior before implementation")
```

or:

```rust
unimplemented!("not part of current scope")
```

rather than hiding unfinished design behind fallback behavior.

## Review

Every fallback-shaped path must answer:

> Which accepted semantic contract or ADR-level decision authorizes this exact fallback?

If there is no answer, it must be removed or explicitly designed.
