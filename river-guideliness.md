# The River: Core Guidelines for Software Development

## Fundamental Principles

### 1. Flow-Based Organization
Code should be organized around complete flows of functionality rather than arbitrary technical boundaries. Each significant feature should be treated as its own "river", a coherent path from beginning to end. The goal is to maintain locality, visibility and comprehensibility of the entire process.

### 2. Complete Responsibility
Functions should aim to handle their entire responsibility from start to finish, regardless of length. Rather than fragmenting logic across multiple small functions, allow each function to tell its complete story. The key metric is not size but clarity, isolation and coherence of flow.

### 3. Natural Boundaries
Systems should be divided along natural feature boundaries, like a watershed contains multiple rivers. Each feature flow should maintain its independence while connecting with others at well-defined points. These boundaries should emerge from the problem domain rather than being imposed by technical considerations.

## Implementation Guidelines

### Code Structure
1. Keep the entire flow of a feature visible and comprehensible in one place
2. Allow functions to be as long as needed to handle their complete responsibility
3. Maintain linear, easy-to-follow progression through each function
4. Use clear section comments to guide readers through longer flows
5. Keep feature flows independent of each other where possible

### Abstraction Rules
1. Prefer local abstractions that serve immediate context over global utilities
2. Allow patterns to emerge naturally rather than creating abstractions upfront
3. Abstract only when it genuinely improves understanding, performance  or maintainability. And do it only after reflecting on the potential cost vs benefit of doing so. 
4. Keep abstractions close to where they're used, preserving context
5. Accept similar patterns in different contexts rather than forcing reuse

### Error Handling
1. Handle errors within the flow where they occur
2. Provide rich context in error messages by leveraging local knowledge
3. Design flows to contain and isolate failures
4. Make error states and recovery paths visible within the main flow

### Cross-Cutting Concerns
1. Treat logging, security, and monitoring as part of the local environment
2. Allow each flow to handle cross-cutting concerns in context-appropriate ways
3. Accept that similar patterns may repeat across different flows
4. Focus on clarity and completeness within each flow rather than global consistency

### Growth and Scaling
1. Add new capabilities as new rivers rather than complicating existing ones
2. Maintain constant complexity by isolating it within each flow while the system grows
3. Allow each flow to evolve independently based on its specific needs
4. Focus on isolation and fault containment between flows

## Code Review Guidelines

### What to Look For
1. Clear progression of logic from start to finish
2. Appropriate handling of edge cases and errors within the flow
3. Rich context in error messages and logging
4. Natural and necessary abstractions that serve the local context
5. Proper isolation between different feature flows

### Questions to Ask
1. Can you understand the complete flow without jumping between files?
2. Are abstractions serving the immediate context or forcing premature generalization?
3. Is similar code truly duplicate, or serving different contexts?
4. Are boundaries between flows natural and appropriate?
5. Does the code tell a clear, coherent story?

## Anti-Patterns to Avoid

1. Breaking flows into small functions - unless with clear and worthwhile benefits
2. Creating global abstractions - unless absolutly necessary
3. Forcing reuse between unrelated contexts - unless absolutly needed
4. Obscuring flow with unnecessary indirection - unless with clear benefit
5. Separating related functionality for the sake of "clean code" - is always bad

## Decision Framework

When organizing code, ask:
1. Does this organization make the flow more or less visible?
2. Does this abstraction serve the immediate context or is its benefits so large it is warranted?
3. Is this repetition isolated or truly harmful?
4. Are these boundaries emerging from the domain or being forced?
5. Does this structure help or hinder understanding the complete story?

Remember: The goal is not theoretical purity but practical comprehensibility. Let the natural flow of the problem guide the structure of your solution.
