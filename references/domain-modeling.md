# Domain Modeling

## Model domain truths, not convenient data shapes

Types should represent concepts the program is willing to believe.

A type that exists should already satisfy its structural invariants. Do not create broad data structures that represent every imaginable combination and rely on callers to remember validation rules.

Prefer:

```rust
struct Port(NonZeroU16);

enum ConnectionState {
    Disconnected,
    Connecting,
    Connected(Session),
}
```

over:

```rust
struct Connection {
    connected: bool,
    connecting: bool,
    session: Option<Session>,
    port: u16,
}
```

## Parsing is the construction boundary

External input is not a domain value.

Successful parsing should produce a valid domain value directly:

```
external input -> valid domain type
external input -> error
```

Avoid creating an intermediate decoded object that represents invalid domain states and then validating it afterward.

## Give every fact one semantic owner

Every important fact should have one authoritative owner.

Other components may reference, bind to, or derive from that fact, but should not maintain competing definitions.

Ask:

- Who owns this fact?
- Who is allowed to change its meaning?
- Are these fields two representations of the same fact?

Duplicated data is acceptable when it is a deliberate external representation or provenance record. It is dangerous when multiple components become authoritative.

## Separate observations from judgments

Components that observe reality should report facts.

Components that own policy should interpret those facts.

Prefer:

```rust
struct Measurement {
    value: f64,
}

enum Decision {
    Accept,
    Reject,
}
```

instead of making the measurement producer decide every possible future policy.

This keeps evidence reusable and policies independently evolvable.
