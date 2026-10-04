# Test cases

Each case gives concrete inputs and the behavior the skill must show. Run them by pasting the input into an agent with the skill loaded and checking the output against "Expected".

Shared setup unless stated otherwise: Scale 1-10, general rubric (Accuracy 30%, Relevance 25%, Instruction following 25%, Clarity 20%).

## 1. Basic: obvious quality differences

Goal: Summarize in one sentence: "The city council voted 7-2 on Tuesday to approve a $4M budget for new bike lanes, with construction starting in March."
- A: "The council approved $4M for bike lanes by a 7-2 vote, with construction starting in March."
- B: "The council did something about transportation."
- C: "The council voted unanimously to approve $40M for roads and bike lanes starting in May."

Expected: A > B > C. C is penalized on Accuracy for three wrong facts (unanimous, $40M, May). B is vague, not wrong. Every score has evidence.

## 2. Close case

Goal: Two-sentence welcome email for a new user, friendly tone.
- A and B are both correct, friendly, and two sentences. A is slightly warmer; B names the next step.

Expected: totals within 0.3, so the skill runs a pairwise comparison, names decisive criteria, and warns that the margin may be noise.

## 3. Custom rubric

Goal: Explain recursion to a beginner. Rubric given by user: Analogy quality 50%, Simplicity 30%, Correctness 20%.

Expected: only those three criteria and weights are used. No Completeness, Safety, etc. are added. Weights are applied exactly.

## 4. Instruction following

Goal: Describe a coffee mug. Constraints: exactly 3 bullet points, each under 10 words, no mention of price.
- A: 3 bullets, all under 10 words.
- B: 5 bullets, polished prose.
- C: 3 bullets, one has 14 words.

Expected: A wins. B and C lose points specifically for the violated constraints, named in the evidence.

## 5. Code

Goal: Python function `is_palindrome(s)` ignoring case and non-alphanumerics.
- A: correct, terse, no comments.
- B: well documented, but fails on "A man, a plan, a canal: Panama" because punctuation is not stripped.

Expected: A wins. Correctness outweighs documentation quality. If a runnable test is available, the skill prefers it and reports the result separately.

## 6. Hallucination

Goal: Answer using only this text: "Acme Corp was founded in 2009 in Austin and makes solar inverters."
- A: "Acme makes solar inverters and was founded in Austin in 2009."
- B: "Acme, founded in 2009 by Jane Doe, makes solar inverters and employs 500 people."

Expected: A wins. B is penalized on Accuracy for the unsupported founder and headcount claims, which are quoted as evidence.

## 7. Structured output

Goal: Return JSON with keys "name" (string) and "age" (integer) only.
- A: `{"name": "Ann", "age": 31}`
- B: `{"name": "Ann", "age": "31", "city": "Oslo"}`
- C: `{"name": "Ann", "age": 31,}` (trailing comma)

Expected: A wins. C fails parsing and B fails the schema (string age, extra key). Failed candidates cannot win, their score is capped (4/10), and the failed check is stated separately from judged scores.

## 8. Ambiguous rubric

Goal: "Evaluate these responses, make them good." No criteria, no weights, scale not given.

Expected: the skill asks for the goal and criteria, or states the assumption it is making in Warnings. It does not silently invent a rubric and present the result as authoritative.

## 9. Tie

Goal: Translate "Good morning" to French.
- A: "Bonjour." B: "Bonjour !"

Expected: identical or near-identical totals reported as a tie, with an explanation that the difference is not meaningful. No forced winner.

## 10. Stability

Input: three prior evaluation runs of the same A vs B comparison, where the winners were A, B, A and the totals were within 0.2 each time.

Expected: the skill flags low confidence, states that the winner changed across runs, and recommends tighter anchors, pairwise comparison in both orders, or more runs.

## Success criteria

A successful evaluation should:

- assign scores based on explicit criteria
- provide evidence for each score
- rank candidates sensibly
- explain the winner in plain language
- recommend a concrete prompt improvement
- warn when uncertainty or instability is high
