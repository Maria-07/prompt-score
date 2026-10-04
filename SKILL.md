---
name: prompt-score
description: Evaluate and rank prompt/response pairs with configurable rubrics, weighted scoring, evidence-based explanations, and winner selection for AI engineering workflows.
---

# prompt-score

## When to use this skill

Use prompt-score when you need to:

- compare several prompt variants against the same goal
- evaluate model responses consistently across repeated experiments
- rank candidate outputs using explicit criteria instead of subjective impressions
- explain why one answer is better than another with evidence and scoring
- identify prompt weaknesses and recommend improvements

Use it for tasks such as product descriptions, customer support replies, summarization, classification, code generation, structured-output validation, and instruction-following tasks.

Do not use prompt-score when:

- there are no prompt/response pairs to compare
- the task requires a deterministic validator rather than a rubric-based judge
- the evaluation goal is not defined clearly enough to anchor the criteria
- the criteria would be invented instead of being explicitly provided

## Required inputs

Provide the following:

1. Goal or task description.
2. A list of candidate prompt/response pairs.
3. A scoring scale: 1-10 or 0-100.
4. A rubric: either built-in criteria or custom criteria.
5. Optional weights for each criterion that sum to 100%.
6. Optional constraints such as format, safety rules, audience, or length.

## Optional inputs

- Pairwise mode: compare A vs B when candidates are close.
- Stability check: flag ranking volatility across repeated runs.
- Custom anchors: define what a 2, 5, 8, and 10 mean for each criterion.
- Deterministic checks: JSON schema validation, regex constraints, code execution results, or policy checks.

## Selecting a rubric

Choose the rubric based on task type.

### General-purpose rubric
- Accuracy
- Relevance
- Instruction following
- Completeness
- Clarity
- Conciseness
- Consistency
- Safety

### Code-oriented rubric
- Correctness
- Requirement coverage
- Security
- Maintainability
- Efficiency
- Error handling

### Support/communication rubric
- Accuracy
- Empathy
- Policy compliance
- Resolution quality
- Clarity
- Tone

Keep criteria independent where possible. Avoid double-counting the same quality under multiple labels.

## Scoring model

Use a normalized 0-10 or 0-100 scale.

- Default score range: 1-10
- Weighted overall score = sum of criterion score × criterion weight (e.g. 9×0.25 + 9×0.20 + 10×0.20 + 9×0.15 + 9×0.20 = 9.2)
- Converting scales: multiply a 1-10 score by 10 to get 0-100 (and divide by 10 for the reverse); never mix scales within one evaluation
- Round totals to one decimal place on 1-10 (whole numbers on 0-100)
- Weights should total 100%
- Prefer clear and honest precision: 8.7/10 is acceptable; avoid false precision when the rubric is coarse
- Every score must include a brief justification based on evidence in the response

### Recommended anchors

For each criterion, define explicit scoring anchors:

- 2 = seriously deficient
- 5 = partially meets the requirement
- 8 = strong and generally correct
- 10 = excellent, complete, and clearly aligned

Use these anchors as a reference, not as a rigid formula. If a criterion is more important or more nuanced, add tailored anchors.

## Evaluation workflow

1. Define the goal and constraints.
2. Choose the rubric and weights.
3. Normalize the scale and evidence expectations.
4. Evaluate each candidate independently against the rubric.
5. Record score, justification, and evidence for each criterion.
6. Compute the weighted overall score for each candidate.
7. If needed, perform pairwise comparison for close competitors.
8. Rank candidates from highest to lowest score.
9. Select the winner and explain why.
10. Identify weaknesses and provide concrete prompt improvements.
11. Flag uncertainty, instability, or ambiguous criteria.

## Required output structure

The final answer should include:

- goal summary
- rubric used
- score scale and weights
- per-candidate assessment
- total score and ranking
- winner selection
- evidence-based strengths and weaknesses
- recommendation for prompt improvement
- warnings about uncertainty or instability when relevant

### Output format

```text
Goal: <task>
Scale: 1-10
Rubric: <criteria and weights>

Candidate A: 8.6/10
- Accuracy: 9/10 — <evidence>
- Relevance: 8/10 — <evidence>
...

Ranking:
1. Candidate A — 8.6/10
2. Candidate B — 8.2/10
3. Candidate C — 7.1/10

Winner: Candidate A
Reason: <brief explanation>

Weaknesses: <concise issues>
Recommendations: <specific prompt improvements>
Warnings: <uncertainty, stability, or missing criteria if any>
```

## Special cases

- **Ambiguous or missing rubric:** if the goal is vague, criteria contradict each other, or weights do not sum to 100%, ask the user to clarify, or state the assumption you are making in Warnings. Never silently invent criteria.
- **Deterministic check fails** (invalid JSON, schema violation, failing tests, broken regex or length constraint): the candidate cannot win. Cap its Instruction following / Correctness score at 4 (1-10) or 40 (0-100) and say which check failed. Report the check result separately from judged scores.
- **Ties:** if two totals differ by 0.3 or less on 1-10 (3 or less on 0-100), treat the gap as within noise. Run a pairwise comparison; if that does not separate them either, report a tie and say what would break it.
- **Single candidate:** score it against the rubric, but do not produce a ranking or winner.
- **Missing responses or prompts:** score only what was supplied and list what was missing.

## Pairwise comparison

Use pairwise comparison when:

- total scores are within 0.3 on a 1-10 scale (3 on 0-100)
- two responses are qualitatively different but numerically similar
- the user asks: “Which is better, A or B?”

Pairwise assessment should answer which response better satisfies the goal and why. Name the decisive criteria, weigh them by the rubric weights, and use the result as a tie-breaker rather than a replacement for the rubric. Judge each pair in both orders (A vs B, then B vs A) when possible to reduce position bias.

## Stability and uncertainty

Flag these cases explicitly:

- criteria are vague or underspecified
- repeated runs produce different winners (compare runs only when the user provides several evaluations, or asks you to re-evaluate)
- the score spread is narrow and could be noise
- evidence is insufficient to justify a high score
- the task is subjective and sensitive to judgment style

Never present a score as objective truth. Position it as a structured evaluation under the chosen rubric.

## Quality guardrails

Follow these rules:

- separate subjective judgment from deterministic validation
- do not infer requirements that were never given
- keep scoring anchors explicit
- preserve the original prompt and response for auditability
- report uncertainty honestly
- for code or structured output, prefer executable or schema checks when available
- for high-stakes tasks, require human review or domain-specific evaluation

## Example

Goal: Generate a professional product description.

Rubric:
- Accuracy 25%
- Relevance 20%
- Instruction following 20%
- Clarity 15%
- Tone 20%

Output:

```text
Goal: Generate a professional product description.
Scale: 1-10
Rubric: Accuracy 25%, Relevance 20%, Instruction following 20%, Clarity 15%, Tone 20%

Prompt B — 9.2/10 (Winner)
- Accuracy: 9/10 — correctly describes product features without unsupported claims
- Relevance: 9/10 — stays tightly focused on the requested product
- Instruction following: 10/10 — follows required structure and tone
- Clarity: 9/10 — easy to follow and well organized
- Tone: 9/10 — polished and professional

Strengths: follows requested structure, stays relevant, avoids unsupported claims.
Weaknesses: slightly more verbose than necessary.
Recommendation: keep the structure and reduce unnecessary wording.
```

## Supporting files

Load these when you need more detail:

- [references/evaluation-rubrics.md](references/evaluation-rubrics.md) — full rubric definitions per task type
- [references/scoring-methodology.md](references/scoring-methodology.md) — weighting rules, anchors, and score aggregation
- [references/judge-guidelines.md](references/judge-guidelines.md) — evaluator behavior and bias avoidance
- [examples/](examples/) — worked evaluations (basic, pairwise, custom rubric)
- [tests/](tests/) — test cases and expected behavior for validating the skill

## Final recommendation

prompt-score should be lightweight, transparent, and reusable. The skill succeeds when it helps people compare candidate responses consistently, justify the ranking, and improve prompts based on explicit evidence instead of intuition.
