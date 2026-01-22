# Decision Framework

A checklist and heuristics for making technical decisions.

## When Choosing Solutions

1. Does a mature solution already exist? Use it.
2. Is this the simplest approach? If not, simplify.
3. Will this require ongoing maintenance? Minimize it.
4. Am I over-engineering? Probably yes, scale back.
5. Can I delete code instead of adding it? Do that.

## Red Flags

Watch out for these phrases and patterns:

- "We might need this later"
- "This is how Big Tech does it"
- "Let me write a custom framework for this"
- "I'll add caching/optimization upfront"
- Adding layers of abstraction "for flexibility"

## Green Flags

These are signs you're on the right track:

- "This boring solution works"
- "I can delete this entire module"
- "The standard library handles this"
- "This is the minimum code needed"
- "I found a mature library that solves this"

## Quick Decision Test

Before implementing, ask:

1. What's the simplest thing that could possibly work?
2. Am I solving a real problem or a hypothetical one?
3. Will I understand this code in 6 months?
4. Could I explain this approach to a junior developer?
5. What happens if I just don't do this?
