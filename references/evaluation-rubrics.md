# Evaluation rubrics

The quality of an evaluation depends on how well the rubric matches the task. A single generic rubric is rarely enough for all use cases.

## General rubric

Use this when the task is broad or not highly specialized.

- Accuracy: Is the output factually and contextually correct?
- Relevance: Does it address the goal without rambling or off-topic material?
- Instruction following: Does it obey explicit constraints, structure, and requested format?
- Completeness: Does it cover all meaningful requirements without material omissions?
- Clarity: Is it readable, organized, and easy to understand?
- Conciseness: Does it avoid unnecessary verbosity while preserving essential information?
- Consistency: Does it maintain logic, terminology, and formatting coherently?
- Safety: Does it avoid harmful, prohibited, or inappropriate content where relevant?

## Code task rubric

Use this when evaluating code or technical outputs.

- Correctness: Does the solution satisfy the task and behave as expected?
- Requirement coverage: Does it address all required behaviors or constraints?
- Security: Does it avoid common vulnerabilities or unsafe patterns?
- Maintainability: Is the code readable, modular, and understandable?
- Efficiency: Is it reasonably optimized for the stated constraints?
- Error handling: Are edge cases addressed when relevant?

Readability can be folded into Maintainability to avoid double-counting.

## Communication task rubric

Use this when evaluating writing, support content, or conversational responses.

- Accuracy: Are claims and recommendations reliable?
- Empathy: Is the tone respectful and considerate?
- Policy compliance: Does the answer avoid banned or risky guidance?
- Resolution quality: Does it solve the user problem effectively?
- Clarity: Is it easy for the intended audience to understand?
- Tone: Is the emotional register appropriate to the context?

## Rubric design guidance

- Prefer 5 to 8 criteria for most tasks.
- Keep criteria independent and observable.
- Use weights to reflect business or task priorities.
- Add deterministic checks when a criterion can be measured objectively.
- If the task is ambiguous, clarify the rubric before scoring.

## Example rubric weighting

```text
Accuracy: 25%
Relevance: 20%
Instruction following: 20%
Clarity: 15%
Tone: 20%
```

This is a good starting point for general writing tasks because it emphasizes correctness and goal alignment without ignoring style.
