# Model and Inference Policy

## Principle

Models are replaceable execution dependencies. Protocol, session state, validation and provenance remain independent of any provider.

## Roles

Different tasks may use different model roles:

- intent interpretation,
- command or plan generation,
- documentation answering,
- code explanation or generation,
- summarization and context compression,
- critique or verification.

A single model may fill several roles initially, but APIs should not assume that permanently.

## Routing

Routing considers:

- task complexity,
- required structured-output reliability,
- context size,
- privacy policy,
- local hardware availability,
- latency,
- cost or quota,
- model capability and health.

Automatic routing must be inspectable and overridable. The chosen model and reason are recorded in provenance.

## Local and remote inference

Profiles may select local, institutional or external inference. Project policy may prohibit remote inference. Failover must never move private data to a less trusted provider without explicit permission.

## Structured output

Command generation requires schema-constrained output and validation. Invalid model output is corrected, retried within a bounded budget or returned as a visible failure; it is never executed as best-effort free text.

## Context construction

Context is assembled from compact session state, capability manifests and relevant knowledge results. Full conversation replay is not the default. Context construction and truncation decisions should be observable for debugging.

## Budgets

Sessions may define limits for model calls, tokens, wall time and cost. Multi-step agents stop when budgets are exhausted and return partial, reproducible state.

## Evaluation and fallback

Models are admitted to roles through task-specific benchmarks. Fallback models must meet the same schema and privacy requirements. A cheaper model may handle simple classification or formatting while more capable models handle planning, but scientific validity is enforced outside the model.