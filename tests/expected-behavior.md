# Expected behavior

The skill should behave consistently and defensibly under realistic evaluation scenarios.

## Required behaviors

- Evaluate each candidate independently against the same rubric.
- Apply weights consistently to all candidates.
- Provide a brief score justification for each criterion.
- Rank candidates from strongest to weakest.
- Identify the winner and explain why it won.
- Provide specific prompt improvement suggestions.
- Warn when the task is ambiguous or unstable.

## Recommended output patterns

### Strong evaluation

- uses explicit criteria and anchors
- cites response details instead of generic praise
- calls out strengths and weaknesses separately
- makes the ranking easy to understand

### Weak evaluation

- invents criteria without saying so
- gives a high score without evidence
- hides poor performance behind a single average
- ignores missing requirements
- fails to explain pairwise decisions

## Acceptance checks

Before submitting to AgenticSkills, confirm that the skill:

1. works for a clear three-candidate example
2. handles close comparisons without overclaiming certainty
3. respects custom task-specific rubrics
4. keeps the scoring methodology transparent
5. avoids unsupported assumptions
6. recommends tangible next steps for prompt improvement
7. warns about uncertainty when the evaluation is noisy or ambiguous

## Final standard

The skill is ready when it produces repeatable, evidence-based rankings without pretending that a single judge model is infallible.
