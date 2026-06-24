---
name: design-feature
description: Turn a detailed feature requirement into an implementation-ready, technology-neutral design covering ownership, interfaces, modules, types, files, data flow, SOLID trade-offs, Mermaid diagrams, and a TDD implementation strategy. Use when designing a new feature or substantial change before implementation, especially when responsibility placement, public contracts, dependency direction, or architectural fit must be decided with the user.
---

# Design Feature

Produce a decision-complete feature design grounded in the repository. Adapt the design to the project's paradigm; do not force classes, patterns, or framework conventions where modules, functions, data types, or other constructs fit better.

## Required skills

Before analysis, verify that these skills are installed and available:

- `$improve-codebase-architecture`
- `$grill-with-docs`
- `$tdd`

Stop if any are missing. Name every missing skill and tell the user to install it. Do not silently reproduce or bypass a required skill's workflow.

## Workflow

### 1. Ground the requirement

- Restate the feature goal, observable outcomes, audience, scope, constraints, and compatibility needs.
- Explore the repository before asking questions. Read relevant source, tests, configuration, `CONTEXT.md` or `CONTEXT-MAP.md`, and ADRs.
- Separate discoverable facts from product or design choices. Resolve discoverable facts from the repository.
- Track assumptions and unresolved decisions; do not disguise either as facts.

### 2. Analyze the existing architecture

Invoke `$improve-codebase-architecture` for the affected area. Use its analysis to identify current modules, interfaces, seams, adapters, coupling, locality, leverage, and likely responsibility candidates.

- Treat the requested feature as the candidate being explored; focus the architecture analysis on changes needed to support it.
- Apply the deletion test to proposed modules and abstractions.
- Introduce a seam only for actual variation, an external system edge, or a demonstrated testing need. One adapter alone is normally a hypothetical seam.
- Record affected files and contracts, but do not design the final interface until meaningful ownership choices have been resolved.

### 3. Draft responsibility candidates with SOLID

Evaluate each candidate against all applicable principles:

- **Single responsibility**: give a module one coherent reason to change and place policy with its owner.
- **Open/closed**: add extension points only for evidenced variation; prefer direct change for a single known case.
- **Liskov substitution**: specify invariants, results, errors, ordering, and side effects that every adapter must preserve.
- **Interface segregation**: expose the smallest caller-relevant interface instead of a universal interface.
- **Dependency inversion**: point policy toward stable abstractions and place infrastructure behind a seam when variation or isolation is real.

Also assess cohesion, coupling, change locality, interface depth, and testability. Reject pass-through wrappers, speculative abstractions, and interfaces that merely mirror an implementation.

Use paradigm-appropriate constructs:

- Object-oriented code: classes, protocols/interfaces, value objects, and collaborators.
- Functional or data-oriented code: modules, functions, algebraic/data types, and explicit effects.
- UI code: view modules, state owners, actions, resources, and platform adapters.
- Mixed systems: choose the smallest useful combination and preserve dependency direction across seams.

### 4. Resolve meaningful choices with the user

A choice is meaningful when it changes a public contract, domain ownership, dependency direction, state ownership, failure semantics, compatibility, or the cost of future change. File naming, private helper placement, and other local reversible choices are not meaningful unless they affect one of those concerns.

When two or more credible responsibility candidates remain, invoke `$grill-with-docs` and use its questioning and repository cross-checking discipline:

- Ask one question at a time and wait for the answer.
- Present only credible alternatives, their consequences, and a clear recommended answer.
- Explain the recommendation using cohesion, coupling, locality, leverage, SOLID, and testability.
- Probe concrete success, failure, concurrency, lifecycle, and compatibility scenarios when relevant.
- Continue until ownership, interface direction, and important invariants are agreed.
- Trigger this loop because the design choice matters, not because documentation happens to exist.
- Do not create or update `CONTEXT.md`, ADRs, or any other repository file unless the user explicitly asks for those changes. When not authorized, include a proposed documentation update in the final design instead.

If no meaningful ambiguity remains, state the ownership choice and rationale without manufacturing a question.

### 5. Produce the detailed design

Turn agreed responsibilities into concrete interfaces, modules, types, and file placement. Specify:

- Each module's responsibility, owner, callers, dependencies, and reason to change.
- Public operations and data types, including invariants, errors, ordering, idempotency, and side effects where applicable.
- State ownership and the data/control flow across seams.
- Adapters for real external or runtime variation.
- Files to add, modify, or retire, grouped by responsibility rather than arbitrary layer.
- Migration, compatibility, rollout, and observability only when the feature requires them.

Always include a Mermaid structural or dependency diagram. Use `classDiagram` only when classes and their relationships are the clearest representation; otherwise use `flowchart`. Add a Mermaid `sequenceDiagram` when behavior crosses multiple modules or seams and ordering materially matters.

### 6. Add the TDD implementation strategy

After the public interface and behavior are stable, invoke `$tdd` to produce a test-first implementation strategy rather than implementation code.

- Map each accepted requirement to observable behavior through a public interface.
- Order work as vertical tracer bullets: one failing behavior test, minimal implementation to green, then the next behavior.
- Identify unit, integration, contract, end-to-end, or other test levels only where they add distinct confidence.
- Prefer real internal collaborators. Put test doubles at external systems, time, randomness, filesystem, or other genuine seams.
- Include critical success, failure, edge, and regression scenarios, prioritized by risk.
- Reserve refactoring and SOLID cleanup for green states.
- Do not prescribe tests for private methods, internal call counts, or speculative implementation shape.

### 7. Deliver and self-review

Read [design-output-template.md](design-output-template.md) and use its output contract. Before delivering, verify that:

- Every requirement maps to an owner, interface behavior, and test scenario.
- Each dependency arrow agrees with the stated ownership and dependency direction.
- Each abstraction passes the deletion test and has a justified seam.
- The structural diagram matches the file and responsibility tables.
- The TDD slices exercise public behavior and can be implemented one at a time.
- No unresolved meaningful decision is hidden in an assumption.

Return the complete design as Markdown in chat. Save it to a file only when the user explicitly requests a file.
