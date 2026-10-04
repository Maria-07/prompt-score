# Pairwise comparison example

## Scenario

Two candidate responses receive nearly identical scores.

### Goal

Create a concise travel recommendation for a weekend trip to Lisbon.

### Candidates

- Candidate A: highly detailed but slightly longer
- Candidate B: brief, direct, and well structured

## Rubric

- Accuracy 30%
- Relevance 25%
- Clarity 20%
- Conciseness 15%
- Tone 10%

## Pairwise assessment

```text
Candidate A total: 8.7/10
Candidate B total: 8.8/10

Pairwise result: Candidate B is better for this goal.
Reason: Candidate B is more concise and still covers the key recommendations. Candidate A includes useful detail, but it is more verbose than necessary for the brief.

The 0.1 gap is within noise (threshold: 0.3), so the totals alone do not decide.

Decisive criteria:
- Conciseness (15%): Candidate B wins clearly
- Clarity (20%): Candidate B wins slightly
- Accuracy (30%): Candidate A wins slightly (more detail)
- Relevance (25%): tied

Recommendation: Use Candidate B as the baseline and add a small amount of detail if the user asks for more depth.
```

## Why this matters

Pairwise analysis helps when the absolute scores are close and the distinction is qualitative rather than numeric. It makes the ranking decision more interpretable and useful.
