# Engineering Philosophy

Detailed principles and examples for developing software in this project.

## Core Principles

### Simplicity Above All
- Choose the simplest solution that solves the problem
- Complexity is a liability, not an asset
- If you can't explain it simply, you don't understand it well enough

### Minimize Maintenance Burden
- Write code that requires the least possible ongoing maintenance
- Prefer boring, proven technologies over exciting new ones
- Every line of code is a liability that must be maintained
- Delete code aggressively when it's no longer needed

### Pragmatic Over Trendy
- Make pragmatic trade-offs based on real constraints
- Lean toward mature, battle-tested approaches
- Avoid cargo-culting patterns from big tech companies
- What works is more important than what's fashionable

### Avoid Over-Engineering
- Build what you need today, not what you might need tomorrow
- If you're not sure you need it, you don't need it
- Prefer mature solutions over custom code for solved problems

### Reversibility
- Prefer decisions that are easy to undo
- Hard-to-reverse choices deserve more scrutiny
- When in doubt, choose the option that keeps more doors open

## Examples

### Good Practices
- Using a proven auth library instead of rolling your own
- Choosing classic databases like PostgreSQL/MySQL/MongoDB because they work
- Deleting unused code immediately
- Writing a simple function instead of a class hierarchy
- Using standard patterns that any developer understands

### Practices to Avoid
- Writing custom caching logic "for performance" without evidence of need
- Adding configuration options you don't need yet
- Creating abstractions for single use cases
- Implementing trendy architecture patterns without clear need
- Keeping "maybe useful later" code around

## Guiding Quotes

> "The best code is no code at all."

> "Make it work, make it right, make it fast - in that order."

> "You aren't gonna need it." (YAGNI)

This philosophy is about being economical with complexity. Every abstraction,
every line of code, every dependency is a bet that the benefits outweigh
the maintenance cost. Make those bets carefully.
