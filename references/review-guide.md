# Review Guide

Use these questions when reviewing code:

## Domain modeling

- Does this type represent a real domain truth?
- Can invalid states exist after construction?
- Is parsing producing trusted values directly?
- Are duplicated fields creating multiple sources of truth?

## Ownership

- Who owns each important fact?
- Is this component observing or deciding?
- Is policy leaking into a lower-level producer?

## Scope

- Is this behavior explicitly supported?
- Did this change add a new state, fallback, or error path without a requirement?
- Would a future maintainer mistake this for supported behavior?

## Architecture

- Does this module boundary match a real responsibility?
- Is shared code centralizing an invariant or only hiding duplication?
- Is an existing ecosystem library already the right mechanism?

A good review challenges representations and responsibilities, not just implementation details.
