# Engineering Philosophy

This document outlines the core principles and philosophy for developing software. All agents and contributors should adhere to these guidelines.

## Core Principles

### 1. Simplicity Above All
- Choose the simplest solution that solves the problem
- Complexity is a liability, not an asset
- If you can't explain it simply, you don't understand it well enough

### 2. Minimize Maintenance Burden
- Write code that requires the least possible ongoing maintenance
- Prefer boring, proven technologies over exciting new ones
- Every line of code is a liability that must be maintained
- Delete code aggressively when it's no longer needed

### 3. Pragmatic Over Trendy
- Make pragmatic trade-offs based on real constraints
- Lean toward mature, battle-tested approaches
- Avoid cargo-culting patterns from big tech companies
- What works is more important than what's fashionable

### 4. Zero Over-Engineering
- Never add features or abstractions for hypothetical future needs
- Build what you need today, not what you might need tomorrow
- If you're not sure you need it, you don't need it
- **Zero custom code** for problems that have mature, proven solutions

### 5. Reversibility
- Prefer decisions that are easy to undo
- Hard-to-reverse choices deserve more scrutiny
- When in doubt, choose the option that keeps more doors open

## Architecture Principles

### Composability
- Design self-contained units that can be connected together
- Each unit should have clear boundaries and responsibilities
- Units should be independently understandable and testable
- Composition over inheritance, always

### Agent-Compatible Design
- Decompose work into agent-compatible units
- Top-level agents coordinate how components connect
- Each unit should be independently understandable by an AI agent
- Clear interfaces between components

### Strong Correctness Priors
- Correctness trumps cleverness
- Type safety where it matters
- Fail fast and explicitly
- Make invalid states unrepresentable when practical

### State is Sacred
*For systems involving money, credits, tokens, or audit requirements*

- Treat mutable state as dangerous, not convenient
- **Never** perform math operations directly on database values (no `balance = balance - 10`)
- Event sourcing / ledger beats hacky math operations in these domains
- Store immutable facts (events), derive state from them (table in database)
- Observability is critical: you must be able to see what happened and why
- Every state change that involves billing/tokens/credits should be traceable to a specific event
- When debugging, you need the full history, not just the current snapshot

**When this complexity is warranted:**
- Billing, credits, tokens, financial transactions
- Anything requiring audit trails or regulatory compliance
- Multi-step workflows where you need to understand "how did we get here?"
- Systems where reconciliation and debugging are business-critical

**When simpler is fine:**
- User preferences, UI state, feature flags
- Caches and derived data that can be trivially reconstructed
- Data where the current value is all that matters

**Why this matters:**
- `UPDATE users SET credits = credits - 5` loses information forever
- `INSERT INTO events (user_id, type, amount) VALUES (123, 'credit_used', -5)` preserves history
- With events, you can replay, audit, debug, and understand your system
- Math operations on state are invisible - they happen and disappear
- Events are visible - they tell you the story of what happened

Don't event-source your todo list. Do event-source your billing system.

## Communication & Prompts

### High Signal, Low Noise
- Prompts should have minimal ambiguity
- Be explicit about requirements and constraints
- Provide sufficient context without overwhelming detail
- Clear > clever

### Documentation
- Document decisions and trade-offs, not implementations
- Keep documentation close to code
- Update or delete outdated docs immediately
- No documentation is better than wrong documentation

## Decision-Making Framework

### When Choosing Solutions
1. Does a mature solution already exist? Use it.
2. Is this the simplest approach? If not, simplify.
3. Will this require ongoing maintenance? Minimize it.
4. Am I over-engineering? Probably yes, scale back.
5. Can I delete code instead of adding it? Do that.

### Red Flags
- "We might need this later"
- "This is how Big Tech does it"
- "Let me write a custom framework for this"
- "I'll add caching/optimization upfront"
- Adding layers of abstraction "for flexibility"

### Green Flags
- "This boring solution works"
- "I can delete this entire module"
- "The standard library handles this"
- "This is the minimum code needed"
- "I found a mature library that solves this"

## Examples of This Philosophy

### Good
- Using a proven auth library instead of rolling your own
- Choosing PostgreSQL because it's boring and works
- Deleting unused code immediately
- Writing a simple function instead of a class hierarchy
- Using standard patterns that any developer understands

### Bad
- Writing custom caching logic "for performance"
- Adding configuration options you don't need yet
- Creating abstractions for single use cases
- Implementing trendy architecture patterns without clear need
- Keeping "maybe useful later" code around

### FYI
- When you code react... (never use memo and callback!)


## Remember

> "The best code is no code at all."
>
> "Make it work, make it right, make it fast - in that order."
>
> "You aren't gonna need it." (YAGNI)

This philosophy is not about being lazy - it's about being **economical with complexity**. Every abstraction, every line of code, every dependency is a bet that the benefits outweigh the maintenance cost. Make those bets carefully.

---
