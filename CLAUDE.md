# CLAUDE.md

This project prioritizes simplicity, low maintenance, and pragmatic trade-offs.

## Core expectations

- Prefer the simplest solution that works
- Favor mature, proven libraries over custom code
- Avoid over-engineering and speculative abstractions (YAGNI)
- Correctness over cleverness
- Prefer reversible decisions
- Delete code aggressively when no longer needed

## State handling

Systems involving money, credits, tokens, or audit requirements
must preserve history and traceability. Mutable state in these
domains is treated as dangerous. See `agent_docs/state_and_billing_rules.md`.

## When unsure, optimize for

- Fewer lines of code
- Less maintenance burden
- Clear, boring solutions
- Standard patterns any developer understands

## Additional context

For deeper guidance on specific topics, review relevant files in `agent_docs/`
before implementing non-trivial changes:

- `engineering_philosophy.md` - detailed principles and examples
- `architecture_principles.md` - composability, correctness, agent design
- `state_and_billing_rules.md` - event sourcing, ledgers, financial state
- `decision_framework.md` - red flags, green flags, decision checklist
