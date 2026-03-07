# instruction-hierarchy-evals

Evaluation suite for testing instruction precedence, context separation, and instruction-following failures in LLM systems.

## Overview

`instruction-hierarchy-evals` is a structured evaluation project focused on a narrow but important question:

**When multiple instructions compete, why does a language model follow the wrong one?**

The repository is designed to study failures in instruction integrity under controlled conditions. It emphasizes reproducible evaluation over anecdotal examples and concentrates on how models handle:

- competing instructions across priority levels
- confusion between data and commands
- prompt injection and context contamination
- multi-turn erosion of correct instruction-following
- instability under prompt mutation and formatting variation

This project is intended for defensive research, evaluation design, and regression tracking.

## Scope

The repository focuses on instruction-handling failures such as:

- system vs user instruction conflicts
- developer-level constraints being ignored or weakened
- quoted text being treated as operative instructions
- retrieved or contextual text overriding higher-priority instructions
- indirect prompt injection through inserted content
- role confusion in multi-message conversations
- formatting-based confusion about which text is instructional
- degradation of correct behavior across paraphrases or repeated turns

It does not aim to be a general benchmark for all aspects of model quality.

## Objectives

The project has five primary goals:

1. Define a clear taxonomy of instruction hierarchy failures.
2. Build high-quality, reusable evaluation cases for each failure class.
3. Measure robustness under prompt variation and adversarial reformulation.
4. Support comparison across models, prompts, and system configurations.
5. Enable regression testing over time as models or wrappers change.

## Design Principles

This repository is built around the following principles:

- **Narrow scope**: depth over breadth
- **Reproducibility**: every evaluation should be runnable and inspectable
- **Controlled variation**: isolate the cause of failure wherever possible
- **Clear taxonomy**: distinguish genuinely different failure modes
- **Defensive use**: support safety research and system hardening, not misuse

## Repository Structure

```text
instruction-hierarchy-evals/
├── README.md
├── LICENSE
├── CONTRIBUTING.md
├── pyproject.toml
├── requirements.txt
├── .gitignore
├── data/
│   ├── cases/
│   │   ├── direct_conflicts/
│   │   ├── quoted_text_confusion/
│   │   ├── injected_context/
│   │   ├── multi_turn_erosion/
│   │   └── formatting_variants/
│   ├── mutations/
│   └── expected_behavior/
├── docs/
│   ├── taxonomy.md
│   ├── methodology.md
│   ├── scoring.md
│   └── limitations.md
├── scripts/
│   ├── run_eval.py
│   ├── score_outputs.py
│   ├── generate_mutations.py
│   └── compare_runs.py
├── notebooks/
│   └── exploratory_analysis.ipynb
├── results/
│   ├── sample_run/
│   └── regression_baselines/
└── tests/
    └── test_schema.py
