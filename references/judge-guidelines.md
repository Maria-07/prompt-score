# Judge guidelines

This document defines how the evaluator should behave when scoring prompt/response pairs.

## Core principles

1. Judge the response, not the model name or brand.
2. Evaluate the output against the specified goal and constraints.
3. Prefer explicit requirements over inferred assumptions.
4. Score against the rubric, not against a hidden preference.
5. Explain the score with evidence from the actual response.
6. Be honest about uncertainty when the evidence is thin.

## What to avoid

- Do not invent unstated requirements.
- Do not reward style if correctness is the main objective.
- Do not treat a numerical score as objective truth.
- Do not hide weak evidence behind a high overall number.
- Do not confuse verbosity with quality.
- Do not discount safety requirements in favor of tone or polish.

## Evidence standards

Good evidence is specific and grounded. Examples:

- “It includes the required three features and omits the unsupported claim.”
- “The answer follows the exact output format in the brief.”
- “The language is clear, but one requirement was not fully addressed.”

Weak evidence looks like:

- “It seems good.”
- “This is likely better.”
- “The response is polished.”

When evidence is weak, the score should be modest or the evaluation should flag uncertainty.

## Criteria independence

Avoid scoring the same issue under multiple labels.

For example:

- Do not count “clear formatting” under both clarity and instruction following if the same issue is being judged twice.
- Do not let tone dominate correctness unless the task explicitly values tone.

## High-stakes tasks

For code generation, medical advice, legal advice, compliance-critical analysis, or other high-risk domains:

- use deterministic validation where possible
- require human oversight when the decision matters
- avoid overconfidence in a single judge model

## Recommended evaluator language

When writing the final evaluation, use grounded language such as:

- “The response is strong on X because it does Y.”
- “The main weakness is Z, which affects score for criterion A.”
- “This result is close to the winner, but it loses on instruction following.”

Avoid language like:

- “This is obviously the best answer.”
- “The model is clearly superior.”
- “This score is objective.”

## Final expectation

A credible evaluation is a transparent, evidence-based comparison under a known rubric. The goal is not to create the illusion of certainty; it is to make the decision process understandable and reusable.
