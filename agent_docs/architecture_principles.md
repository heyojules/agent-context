# Architecture Principles

Guidelines for system design and component architecture.

## Composability

- Design self-contained units that can be connected together
- Each unit should have clear boundaries and responsibilities
- Units should be independently understandable and testable
- Prefer composition over inheritance

## Agent-Compatible Design

- Decompose work into agent-compatible units
- Top-level agents coordinate how components connect
- Each unit should be independently understandable by an AI agent
- Maintain clear interfaces between components

## Strong Correctness Priors

- Correctness trumps cleverness
- Use type safety where it matters
- Fail fast and explicitly
- Make invalid states unrepresentable when practical

## Communication and Documentation

### High Signal, Low Noise
- Prompts should have minimal ambiguity
- Be explicit about requirements and constraints
- Provide sufficient context without overwhelming detail
- Clear is better than clever

### Documentation Guidelines
- Document decisions and trade-offs, not implementations
- Keep documentation close to code
- Update or delete outdated docs immediately
- No documentation is better than wrong documentation
