# Scoring methodology

PromptScore should favor transparency and repeatability over pseudo-precision.

## Core score model

Use a normalized score between 0 and 10 or 0 and 100.

- 1-10 is easier for human review and comparison
- 0-100 can be useful when the rubric is weighted heavily or the audience expects percentages
- Weighted overall score = sum of criterion scores × weights

## Weighting rules

- Total weight must equal 100%
- Higher-risk or higher-priority criteria should receive more weight
- Avoid overloading the rubric with duplicate dimensions

Example:

```text
Accuracy: 30%
Instruction following: 25%
Relevance: 20%
Clarity: 15%
Conciseness: 10%
```

## Score interpretation

### 1-10 scale

- 0-2: unacceptable or major failure
- 3-4: weak or materially incomplete
- 5-6: mixed quality; partially meets needs
- 7-8: strong performance with minor issues
- 9-10: excellent and highly aligned with the goal

### 0-100 scale

- 0-39: significant problems
- 40-59: partial success
- 60-79: acceptable quality
- 80-89: strong quality
- 90-100: exceptional quality

## Evidence requirement

Every score should include a brief explanation grounded in the response content. Examples:

- “Correctly captures the product’s key benefits and avoids unsupported claims.”
- “The answer follows the required format exactly, but adds a small amount of excess wording.”
- “The response omits one required constraint, which lowers instruction-following.”

## Anchor guidance

Each criterion should define what the score means in practice.

Example for instruction following:

- 2 = multiple required constraints are ignored
- 5 = some constraints are met, but important ones are missed
- 8 = the response follows the main requirements and format
- 10 = every explicit requirement is satisfied exactly

## Pairwise comparison method

When candidate scores are close, compare them directly:

1. Identify the decisive criteria.
2. Evaluate which response meets the most important requirements better.
3. Explain the tradeoff briefly and honestly.
4. Use pairwise analysis as a tie-breaker, not a replacement for the rubric.

## Stability and uncertainty

If repeated evaluations lead to different winners, call this out.

Examples of warning language:

- “The ranking is close enough that evaluation noise may be material.”
- “This score relies on qualitative judgment where clearer anchors are needed.”
- “The winner changed across runs; the rubric may need to be tightened.”

## Final rule

A good score is not just a number. It is a number plus transparent reasoning, evidence, and clear context.
