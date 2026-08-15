# engineering-discipline

Reusable engineering discipline for LLM-assisted software development.

The goal is to describe maintainability preferences and design principles that
should guide implementation and review.

## Usage

Apply this discipline when asking an agent to design, implement, refactor, or
review software.

The core ideas are:

1. Model domain truths, not convenient data shapes.
2. Give every fact one semantic owner.
3. Do not model failures, states, or concepts outside the explicitly agreed scope.
4. Separate observation/data from policy/judgment.
5. Never hide meaningful failures behind silent fallback.
6. Centralize shared invariants and use established libraries for commodity mechanisms.
7. Organize code by domain responsibility, not arbitrary helper categories.

Detailed explanations, examples, and review guidance are provided in `SKILL.md`
and the `references/` directory.
