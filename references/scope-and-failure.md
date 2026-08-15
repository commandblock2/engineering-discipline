# Closed Scope and Failure Discipline

## Do not model concepts outside agreed scope

A system should model the behavior it intentionally supports, not every state someone can imagine encountering.

Do not add:

- speculative states
- future lifecycle phases
- generic extension points without a requirement
- fallback interpretations
- compatibility concepts that change the domain model
- error variants for situations the system does not claim to handle

The absence of a concept from the accepted scope means unsupported.

## Reject unsupported external requests

When unsupported behavior comes from external input, reject it at the boundary.

Example:

```rust
enum OutputFormat {
    Json,
    Toml,
}

fn parse_format(value: &str) -> Result<OutputFormat, Error> {
    match value {
        "json" => Ok(OutputFormat::Json),
        "toml" => Ok(OutputFormat::Toml),
        other => Err(Error::Unsupported(other.into())),
    }
}
```

Do not preserve unsupported concepts inside the domain model unless they are explicitly part of the domain.

## Panic when impossible internal scope violations occur

After accepted input has entered trusted execution, reaching behavior outside the modeled scope indicates a violated assumption.

Do not silently recover or invent semantics.

Prefer:

```rust
panic!("execution reached unsupported mode");
```

over:

```rust
warn!("unsupported mode; using a default behavior");
continue_with_guess();
```

The goal is not to make software handle every imaginable case. The goal is to make the implemented behavior precise and trustworthy.

## Never hide meaningful failures behind fallback

A fallback is only acceptable when it is explicitly part of the contract.

Otherwise it hides information and creates behavior the system never promised.
