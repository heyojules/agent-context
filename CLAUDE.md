# CLAUDE.md

This project prioritizes simplicity, low maintenance, and pragmatic trade-offs.

## Scope

These principles apply to production and long-lived code.
Prototypes, experiments, and one-off scripts may intentionally deviate for speed.
When deviating, explain briefly in code or comments.

## Priority order

When principles conflict, prioritize in this order:
1. Correctness (especially for money, security, data integrity)
2. Simplicity and clarity
3. Maintainability over time
4. Reversibility of decisions
5. Performance and optimization

## Agent behavior

- Do not invent abstractions without clear need
- Prefer modifying existing code over introducing new layers
- When adding complexity, explicitly justify why simpler options fail
- Favor mature libraries over custom code for solved problems

## When unsure

If requirements, constraints, or trade-offs are unclear:
- Ask clarifying questions before implementing
- Propose a minimal approach and explain alternatives
- Default to the simplest reversible solution

## State handling

Systems involving money, credits, tokens, or audit requirements must
preserve history and traceability. See `agent_docs/state_and_billing_rules.md`.

## Non-goals

- Maximizing theoretical elegance
- Implementing trendy architectures
- Premature optimization
- Speculative future-proofing

## Additional context

For deeper guidance, review relevant files in `agent_docs/` before non-trivial changes:
- `engineering_philosophy.md` - principles and examples
- `architecture_principles.md` - composability, correctness
- `state_and_billing_rules.md` - event sourcing, financial state
- `decision_framework.md` - red/green flags, decision checklist
