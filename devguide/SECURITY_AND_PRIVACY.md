# Security and Privacy

## Default posture

Scientific execution and private molecular data remain local by default. Remote services receive only the minimum context required for inference or knowledge retrieval.

## Data classes

- public documentation,
- project metadata,
- private molecular structures and trajectories,
- proprietary pharmacological or industrial data,
- credentials and secrets,
- conversation and telemetry data.

Policies must distinguish these classes rather than treating all session context alike.

## Permissions

Capabilities declare filesystem, network, external-process, GPU and mutation permissions. The session policy determines which may run automatically, require approval or remain disabled.

## Remote inference

Before remote transmission, MolSys-AI should make the payload inspectable and apply project policy. Full structures, trajectories and local files must not be uploaded implicitly. Offline mode disables remote calls completely.

## Secrets

Tokens are resolved through environment variables, OS keyrings or protected configuration. They never appear in workflows, logs, prompts, exported notebooks or project repositories.

## Logging and telemetry

Scientific command logs are local and redact secrets. Remote operational logs should avoid payload retention by default. Telemetry is opt-in or institutionally configured and must state exactly what is collected.

## Prompt and tool safety

Retrieved documents and molecular metadata are untrusted inputs, not instructions. Models cannot grant themselves permissions, bypass schemas or invoke undeclared tools.

## Data retention

Conversation retention, server request retention and artifact retention are separate policies. Users must be able to operate without retaining conversation text while preserving scientific commands and provenance.

## Auditability

Security-relevant events include authentication, approval decisions, capability invocation, remote transmission, file access and policy changes. Audit records must avoid recording secret values.