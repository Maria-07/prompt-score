# Custom rubric example

## Scenario

Evaluate a code-generation response for a Python helper function that must validate email addresses.

## Goal

Write a Python function that validates a list of emails and returns only the valid ones.

## Custom rubric

- Correctness 35%
- Requirement coverage 25%
- Security 15%
- Readability 15%
- Error handling 10%

## Candidate summary

```text
Candidate X — 8.9/10
- Correctness: 9/10 — the function correctly filters valid emails by a reasonable regex.
- Requirement coverage: 9/10 — includes the validation and filtering behavior expected by the task.
- Security: 8/10 — avoids obvious issues but does not explicitly handle edge cases like malformed input types.
- Readability: 9/10 — clear and easy to follow.
- Error handling: 8/10 — handles empty inputs but could be more defensive.

Winner: Candidate X
Reason: It meets the core behavior and remains readable, even though it could be more robust around edge cases.

Recommendation: Add input-type checks and explain the regex in a comment for maintainability.
```

## What this demonstrates

A custom rubric can prioritize correctness and requirements over prose quality. This is especially important for technical tasks where output quality must be judged on functional behavior, not style alone.
