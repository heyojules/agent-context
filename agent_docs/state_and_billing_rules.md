# State and Billing Rules

Guidelines for handling mutable state, especially in financial and audit-sensitive domains.

## State is Sacred

*For systems involving money, credits, tokens, or audit requirements*

- Treat mutable state as dangerous, not convenient
- Avoid math operations directly on database values (e.g., `balance = balance - 10`)
- Prefer event sourcing / ledger patterns in these domains
- Store immutable facts (events), derive state from them
- Observability is critical: you must be able to see what happened and why
- Every state change involving billing/tokens/credits should be traceable to a specific event
- When debugging, you need the full history, not just the current snapshot

## When This Complexity is Warranted

- Billing, credits, tokens, financial transactions
- Anything requiring audit trails or regulatory compliance
- Multi-step workflows where you need to understand "how did we get here?"
- Systems where reconciliation and debugging are business-critical

## When Simpler is Fine

- User preferences, UI state, feature flags
- Caches and derived data that can be trivially reconstructed
- Data where the current value is all that matters

## Why This Matters

```sql
-- This loses information forever:
UPDATE users SET credits = credits - 5

-- This preserves history:
INSERT INTO events (user_id, type, amount) VALUES (123, 'credit_used', -5)
```

- With events, you can replay, audit, debug, and understand your system
- Math operations on state are invisible - they happen and disappear
- Events are visible - they tell you the story of what happened

## Rule of Thumb

Don't event-source your todo list. Do event-source your billing system.
