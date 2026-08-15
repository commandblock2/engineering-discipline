# Architecture Guidance

## Centralize shared invariants

Share code when it centralizes a contract, invariant, or correctness rule.

Good shared components:

- parsers
- validation logic
- identifier types
- serialization formats
- protocol handling
- digest and integrity checks

Avoid extracting code only because it looks similar. Similar code can represent different responsibilities.

## Use established libraries for commodity mechanisms

Prefer mature ecosystem libraries for common mechanisms such as:

- parsing
- serialization
- compression
- hashing
- CLI handling
- path handling
- temporary files

Reserve custom implementations for domain-specific behavior where the project owns the semantics.

## Organize code by domain responsibility

Modules should reflect responsibilities and ownership.

Prefer:

```
order/
  model.rs
  pricing.rs
  persistence.rs
```

over:

```
utils/
helpers/
common/
misc/
```

A file split is valuable when it makes ownership and invariants easier to understand, not merely because a file is large.

## Respect boundaries

A component should consume another component's published contract rather than depending on its internal representation.

Ask:

- Does this module own this decision?
- Is it consuming a fact or taking ownership of another domain's responsibility?
