# Methodology Comparison

## Overview of all task-clarification and context-engineering methodologies integrated into TCE.

| Methodology | Origin | Focus | Strengths | Weaknesses | When to use |
|-------------|--------|-------|-----------|------------|-------------|
| **8Q Tarik Shehihar** | Coaching | Deep clarification | Covers result → risks → gratitude | Slow, not for quick tasks | Vague feature requests |
| **GROW** | John Whitmore | Action orientation | Fast, action-oriented | No context/risk coverage | Quick fixes, first steps |
| **5-Layer Context Stack** | Phil Schmid / Google DeepMind | Context architecture | Structured for complex AI systems | Requires technical maturity | Complex tasks (🟡🔴) |
| **Anthropic CE** | Anthropic | Context economy | Practical, production-ready | No clarification questions | Production prompts, budgeting |
| **SMART** | Doran (1981) | Criteria verification | Rigorous achievability check | No context generation | Acceptance criteria |
| **5W2H** | Kaizen / Lean | Completeness | Fast, universal | Shallow | Quick task setup, "do it yourself" |
| **SCQA** | Barbara Minto | Problem framing | Structures bugs and issues | Problem scenarios only | Bug reports, incidents |

## Integration Notes

### Tarik + GROW
Tarik Q1 (Result) → GROW Goal
Tarik Q7 (Risks) → GROW Reality
Tarik Q4 (Approach) → GROW Options
Tarik Q5 (First step) → GROW Will

### Tarik + 5-Layer Stack
Tarik Q1-Q3 → Layer 1 (System Prompt: Goal + Criteria)
Tarik Q6 → Layer 4 (Tools & APIs)
Tarik Q8 → Layer 3 (Retrieval / Context)
Tarik Q4-Q5 → Layer 5 (Output Format)

### SCQA for bug reports
Situation → current behavior
Complication → what's broken
Question → what needs fixing
Answer → proposed solution (cross-check with Tarik Q1)
