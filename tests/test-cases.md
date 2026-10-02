# Test cases

This test set is meant to exercise the core PromptScore workflow before submitting the skill.

## 1. Basic case: obvious quality differences

- Three responses with clearly different quality levels
- Expected result: correct ranking with a clear winner and a reasoned explanation

## 2. Close case: nearly tied candidates

- Two responses are similar in quality
- Expected result: pairwise comparison resolves the small gap and explains the tradeoff

## 3. Custom rubric case

- User defines a rubric that differs from the default one
- Expected result: the evaluation reflects the custom priorities without inventing extra criteria

## 4. Instruction-following case

- Exact format, word count, or required section structure is enforced
- Expected result: instruction-following criterion drives the score and winner selection

## 5. Code case

- Compare code responses where correctness matters more than prose quality
- Expected result: functional correctness is prioritized and code quality is explained with evidence

## 6. Hallucination case

- One response includes unsupported claims or invented facts
- Expected result: accuracy and trustworthiness are penalized clearly

## 7. Structured-output case

- JSON or schema validation is required
- Expected result: invalid output fails the deterministic requirement and is scored appropriately

## 8. Ambiguous-rubric case

- The rubric is underspecified or contradictory
- Expected result: the skill requests clarification or flags ambiguity instead of silently making assumptions

## 9. Tie case

- Two responses are effectively equivalent
- Expected result: either a tie is reported or the evaluator explains why the margins are not meaningful

## 10. Stability case

- The same evaluation is run repeatedly and ranking differs
- Expected result: the skill flags instability and recommends stronger scoring anchors or repeated evaluation

## Success criteria

A successful evaluation should:

- assign scores based on explicit criteria
- provide evidence for each score
- rank candidates sensibly
- explain the winner in plain language
- recommend a concrete prompt improvement
- warn when uncertainty or instability is high
