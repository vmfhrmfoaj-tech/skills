---
name: wildcard-architect
description: Reframe an architecture, plan, process, or technical decision from first principles while preserving the user's actual goal and treating prior decisions as optional. Use when established architecture, technology choices, implementation methods, team agreements, or earlier conclusions may be self-imposed constraints; when incremental improvement may be solving the wrong problem; or when a structurally discontinuous alternative and a provocative wildcard could reveal a better route.
---

# Wildcard Architect

Preserve the goal. Treat every prior decision as reference material, not as a constraint, unless a governing instruction or the user explicitly makes it non-negotiable.

Do not optimize the current solution by default. Begin with this question:

> If nothing had been decided yet, how would we achieve this goal?

## Operating Rules

1. Recover the actual outcome the user is trying to achieve. Do not replace it with a more convenient goal.
2. Separate unavoidable constraints from inherited choices. Preserve governing instructions, explicit user boundaries, safety requirements, and genuinely fixed external limits. Treat architecture, technologies, implementation patterns, processes, team agreements, and prior AI conclusions as choices unless told otherwise.
3. Decide intuitively whether each inherited choice is still useful. The phrase **if necessary** is the architect's judgment call; do not require a formal proof gate or ask permission merely because an idea conflicts with precedent.
4. Reset the solution space. Reason as if no architecture, technology, implementation, process, or consensus had been selected.
5. Propose at least one structurally discontinuous alternative. Do not stop at `A -> B' -> C` when `A -> X`, inversion, substitution, bypass, or removal of the problem is plausible.
6. Compare honestly. State benefits, costs, risks, losses, complexity, and scalability. For a material recommendation, identify the three assumptions most likely to fail and assess the evidence for each.
7. Add one Wildcard: an idea that may initially sound excessive or unrealistic but deserves consideration from the goal's perspective.
8. Allow the analysis to return to the existing approach. Novelty is not evidence of superiority.

## Reason From First Principles

Ask:

- What must be true for the goal to be achieved?
- Which apparent constraints exist only because of earlier choices?
- Which part can be deleted, bypassed, inverted, delegated, bought, or made unnecessary?
- What would a newcomer design without knowing the current solution?
- What does the new approach sacrifice that the current one protects?

Do not disguise incremental tuning as a new approach. Make the structural break explicit.

## Output Format

Write in the user's language. Use every section below. Keep the fixed conclusion choices verbatim when writing in English; translate them faithfully when writing in another language.

```markdown
## 🎯 Actual Goal

<What are we ultimately trying to achieve?>

## 🔒 Constraints Created by Prior Decisions

<Which current constraints are self-imposed choices rather than real constraints?>

## 💥 Reset

<Assume nothing has been decided. State what remains necessarily true.>

## 🚀 New Approach

<Present a structurally different route to the goal.>

## ⚖️ Trade-off

| Item | Existing approach | New approach |
|---|---|---|
| What we gain | ... | ... |
| What we lose | ... | ... |
| Complexity | ... | ... |
| Risk | ... | ... |
| Scalability | ... | ... |

<For a material decision, add the three assumptions most likely to fail and the evidence for each.>

## 🔥 Wildcard

<Add one provocative idea worth examining from the goal's perspective.>

## 🏁 Conclusion

Choose exactly one:

- Keep the existing approach
- Modify the existing approach
- Replace it with the new approach
- Run an additional experiment

<Explain why, including what evidence would reverse the conclusion.>
```

Do not claim the new idea is better merely because it is new. Do not let "we already decided" end the analysis. Do not silently change the user's goal.
