# prompt-score

prompt-score is a reusable Agent Skill for evaluating and ranking AI prompt/response pairs using explicit criteria, weighted scoring, evidence-based justifications, and winner selection.

Tagline: Measure prompts. Compare responses. Find the winner.

## Why this skill exists

AI engineers often compare multiple prompt versions manually. That leads to inconsistent evaluations, subjective judgment, and repeated configuration overhead. prompt-score gives the workflow a simple, reusable structure:

- define a task goal
- choose a rubric
- score candidates consistently
- explain the reasoning
- rank the results
- recommend the strongest prompt

## What the skill does

- evaluates multiple prompt/response pairs
- supports built-in or custom evaluation criteria
- scores on a 1-10 or 0-100 scale
- applies weighted criteria
- provides criterion-level explanations with evidence
- ranks candidates and identifies a winner
- uses pairwise comparison when scores are close
- handles ties, failed deterministic checks, and ambiguous rubrics explicitly
- suggests prompt improvements
- flags uncertainty and unstable evaluations

## Installation

Clone the repository into your agent's skills directory. For Claude Code:

```bash
# Personal (available in all projects)
git clone https://github.com/Maria-07/prompt-score.git ~/.claude/skills/prompt-score

# Or project-level (shared with your team via the repo)
git clone https://github.com/Maria-07/prompt-score.git .claude/skills/prompt-score
```

The skill loads when you ask the agent to compare, score, or rank prompt/response pairs.

## Quick usage

```text
Goal: Generate a professional product description.
Candidates:
- Prompt A -> Response A
- Prompt B -> Response B
- Prompt C -> Response C
Rubric: Accuracy, Relevance, Instruction following, Clarity, Tone
Scale: 1-10
Weights: Accuracy 25%, Relevance 20%, Instruction following 20%, Clarity 15%, Tone 20%
```

The skill returns criterion-level scores with evidence, weighted totals, a ranking, the winner and why it won, weaknesses, and concrete prompt improvements. See [examples/](examples/) for full worked outputs.

## Repository structure

```text
prompt-score/
├── SKILL.md                     # Skill definition (entry point)
├── README.md
├── LICENSE
├── references/
│   ├── evaluation-rubrics.md    # Rubrics per task type
│   ├── scoring-methodology.md   # Weighting, anchors, aggregation
│   └── judge-guidelines.md      # Evaluator behavior rules
├── examples/
│   ├── basic-evaluation.md
│   ├── pairwise-comparison.md
│   └── custom-rubric.md
└── tests/
    ├── test-cases.md            # 10 scenarios with concrete inputs
    └── expected-behavior.md
```

## Design principles

- model-agnostic evaluation
- explicit scoring anchors
- auditable evidence
- transparent uncertainty
- deterministic checks kept separate from judged criteria
- no claim of objective ground truth

## Testing

[tests/test-cases.md](tests/test-cases.md) defines ten scenarios (basic, close, custom rubric, instruction following, code, hallucination, structured output, ambiguous rubric, tie, stability), each with concrete inputs and the expected behavior. [tests/expected-behavior.md](tests/expected-behavior.md) lists the acceptance checks.

## Limitations

prompt-score is not a replacement for human review or deterministic validation in high-stakes tasks. LLM-based grading can be biased, unstable, or poorly aligned if the rubric is vague, and a single judge should not be treated as ground truth. Repeated-run stability analysis is manual: the skill flags instability when you supply multiple runs, but it does not execute repeated runs itself.

## Roadmap

- Automated test-set evaluation across many examples
- Pass/fail assertions for structured outputs
- Prompt optimization loop: evaluate, diagnose, improve, retest

## Contributing

Issues and pull requests are welcome, especially new rubrics, examples, and test cases.

## Metadata

- **Category:** AI/ML Development
- **Tags:** prompt-engineering, evaluation, llm, ai-engineering, benchmarking, testing, prompt-optimization, llm-evaluation

## License

[MIT](LICENSE)
