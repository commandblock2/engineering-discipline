# Keep exactly one truth

For every semantic fact, there shall be exactly one owner.

There shall be one and only one authoritative representation of a fact.

Other code may borrow, reference, observe, or derive from that fact, but shall not maintain another authoritative copy.

## Express ownership in the language

Use language constructs to make ownership relationships explicit.

In Rust:

- `T` represents ownership.
- `&T` represents borrowed access without ownership.
- `&mut T` represents temporary exclusive authority.
- `Box<T>` represents unique heap ownership.
- `Arc<T>` represents shared ownership.
- `Weak<T>` represents non-owning access to shared data.

These constructs must express the intended domain relationship, not merely silence compiler errors.

`Arc<Mutex<T>>` shall not be used as an escape hatch to avoid deciding ownership.

## Review

For every important fact, ask:

> Where is the one and only one truth of this fact?

If there are multiple authoritative answers, the model is incorrect.
