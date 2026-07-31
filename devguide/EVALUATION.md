# Evaluation Framework

## Scope

MolSys-AI must be evaluated as a scientific control system, not only as a conversational assistant.

## Evaluation layers

1. **Knowledge grounding:** source relevance, citation correctness and documented-symbol accuracy.
2. **Protocol generation:** schema validity, correct capability choice and argument accuracy.
3. **State understanding:** correct interpretation of active systems, selections and canvas references.
4. **Execution:** successful tool invocation, structured failures and side-effect correctness.
5. **Reproducibility:** equivalence between interaction history, exported workflow and replayed result.
6. **Scientific validity:** domain-specific correctness of analyses and derived conclusions.
7. **Safety and privacy:** permissions, approval behavior, redaction and transmission policy.
8. **Product quality:** latency, usability, recovery and explanation clarity.

## Canonical benchmark families

- single viewer commands,
- deictic canvas references,
- ambiguous selection handling,
- MolSysMT transformations,
- pocket detection and visualization,
- pharmacophore workflows,
- documentation and API questions,
- multi-step plans with checkpoints,
- failure, cancellation and restart recovery.

## First golden scenario

The 1TCD viewer scenario is the initial vertical benchmark. It must produce equivalent typed commands and observable state from Python, CLI and canvas chat, and export deterministic Python.

## Test records

Each case stores input state, user request, allowed capabilities, expected command constraints, expected observations, tolerated alternatives, prohibited behavior and replay checks.

## Model-independent testing

Protocol, adapters, viewer synchronization and replay are tested without an LLM. Model evaluations are layered on top so infrastructure failures are not confused with reasoning failures.

## Regression policy

A model, prompt, adapter or protocol change cannot be promoted when it causes unexplained regression in scientific or safety benchmarks, even if conversational scores improve.