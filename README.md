# PromptScore

PromptScore is a reusable Agent Skill for evaluating and ranking AI prompt/response pairs using explicit criteria, weighted scoring, evidence-based justifications, and winner selection.

Tagline: Measure prompts. Compare responses. Find the winner.

## Why this skill exists

AI engineers often compare multiple prompt versions manually. That leads to inconsistent evaluations, subjective judgment, and repeated configuration overhead. PromptScore gives the workflow a simple, reusable structure:

- define a task goal
- choose a rubric
- score candidates consistently
- explain the reasoning
- rank the results
- recommend the strongest prompt

## What the skill does

PromptScore can:

- evaluate multiple prompt/response pairs
- support built-in or custom evaluation criteria
- score on a 1-10 or 0-100 scale
- apply weighted criteria
- provide criterion-level explanations
- rank candidates by total score
- identify a winner and justify it
- suggest prompt improvements
- flag unstable or ambiguous evaluations

## Installation

Clone the repository into your agent's skills directory. For Claude Code:

```bash
# Personal (available in all projects)
git clone https://github.com/Maria-07/promptscore.git ~/.claude/skills/promptscore

# Or project-level (shared with your team via the repo)
git clone https://github.com/Maria-07/promptscore.git .claude/skills/promptscore
```

The skill loads automatically when you ask the agent to compare, score, or rank prompt/response pairs.

## Repository structure

```text
promptscore/
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
    ├── test-cases.md
    └── expected-behavior.md
```

## Quick usage concept

Use this skill with a structured input like:

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

The skill then returns:

- criterion-level scores
- weighted totals
- ranked candidates
- winner explanation
- improvement recommendations

## Project scope

This MVP stays focused on:

- multiple prompt-response comparisons
- built-in and custom rubrics
- weighted scoring
- evidence-based explanations
- ranking and winner selection
- prompt improvement suggestions

Future enhancements can include pairwise comparison, repeated-run stability analysis, and automated prompt optimization loops.

## Design principles

- model-agnostic evaluation
- explicit scoring anchors
- auditable evidence
- transparent uncertainty
- no claim of objective ground truth for subjective evaluator decisions

## Risks and limitations

PromptScore is useful, but it is not a replacement for human review or deterministic validation in high-stakes tasks. LLM-based grading can be biased, unstable, or poorly aligned if the rubric is vague. The skill should therefore encourage clear criteria, explicit anchors, and honest uncertainty reporting.

## Metadata

- **Category:** AI / Evaluation / Developer Tools
- **Tags:** prompt-engineering, evaluation, llm, ai-engineering, benchmarking, testing, prompt-optimization, llm-evaluation

## Contributing

Issues and pull requests are welcome — especially new rubrics, examples, and test cases.

## License

[MIT](LICENSE)
