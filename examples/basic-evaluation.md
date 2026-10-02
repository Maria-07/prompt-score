# Basic evaluation example

## Scenario

Evaluate three product-description prompts for the same goal.

### Goal

Generate a professional product description for a smartwatch with a 7-day battery, heart-rate tracking, and water resistance.

### Candidates

- Prompt A response
- Prompt B response
- Prompt C response

## Rubric

- Accuracy 25%
- Relevance 20%
- Instruction following 20%
- Clarity 15%
- Tone 20%

## Example output

```text
Goal: Generate a professional product description for a smartwatch.
Scale: 1-10
Rubric: Accuracy 25%, Relevance 20%, Instruction following 20%, Clarity 15%, Tone 20%

Candidate B — 9.1/10 (Winner)
- Accuracy: 9/10 — correctly describes battery life, heart-rate tracking, and water resistance without unsupported claims.
- Relevance: 9/10 — stays focused on the product and its benefits.
- Instruction following: 10/10 — follows the requested structure and tone.
- Clarity: 9/10 — easy to read and well organized.
- Tone: 9/10 — polished and professional.

Candidate A — 8.6/10
- Accuracy: 8/10 — mostly correct, but slightly overstates the benefits.
- Relevance: 8/10 — relevant, but includes extra product positioning.
- Instruction following: 9/10 — largely follows instructions.
- Clarity: 9/10 — clear and readable.
- Tone: 8/10 — professional but slightly generic.

Candidate C — 7.3/10
- Accuracy: 7/10 — includes some accurate features but less precise wording.
- Relevance: 7/10 — less tightly targeted.
- Instruction following: 7/10 — misses some requested phrasing.
- Clarity: 8/10 — understandable.
- Tone: 7/10 — acceptable but less polished.

Ranking:
1. Candidate B — 9.1/10
2. Candidate A — 8.6/10
3. Candidate C — 7.3/10

Winner: Candidate B
Reason: It best balances correctness, structure, and professional tone while remaining focused.

Weaknesses: Slightly more verbose than necessary.
Recommendations: Keep the structure and trim unnecessary phrasing.
```

## What this demonstrates

- weighted scoring works with real examples
- the winner is justified by evidence
- the evaluator explains why one response is better than another
- prompt improvement advice is concrete and actionable
