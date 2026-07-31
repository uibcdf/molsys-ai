# Typed Scientific Protocol

## Status

**Proposed baseline.** This document defines the stable control plane between natural-language interfaces, scientific sessions and MolSysSuite execution adapters.

## Principle

Language models may interpret intent and propose actions, but scientific execution proceeds only through typed, versioned and validated messages.

## Core envelopes

### Command

A `Command` requests one bounded capability.

Required fields:

- `protocol_version`
- `command_id`
- `tool`
- `tool_version`
- `arguments`
- `session_id`
- `created_at`
- `requested_by`
- `approval_policy`
- `provenance`

Optional fields include `parent_command_id`, `timeout`, `idempotency_key` and `expected_state_revision`.

### CommandBatch

A batch contains ordered commands plus an execution policy:

- stop on first error,
- continue independent commands,
- transactional when every adapter supports rollback,
- require plan approval before execution.

### Selection

Selections must be explicit, serializable and independent of UI wording. Initial selectors should cover system, component, chain, residue, atom, ligand, pocket, pharmacophore feature and current canvas selection.

A selector may contain stable object identifiers, semantic predicates or both. Ambiguous selectors must fail or request clarification; they must not silently choose an object.

### Observation

An `Observation` is a structured statement about current state or execution output. It includes:

- `observation_id`
- `kind`
- `source`
- `state_revision`
- typed payload
- provenance
- warnings and limitations

### Result

A `Result` links to one command and records:

- success, failure, cancellation or partial completion,
- changed state revisions,
- observations,
- artifacts,
- warnings,
- execution metrics,
- reversible operation metadata.

### Error

Errors must be machine-readable. Initial categories:

- schema error,
- unsupported capability,
- invalid state,
- unresolved or ambiguous selection,
- permission denied,
- approval required,
- dependency unavailable,
- execution failure,
- timeout,
- cancellation,
- version incompatibility.

### Artifact

Artifacts represent durable outputs such as structures, tables, images, scenes, notebooks, scripts and workflow manifests. Every artifact carries a URI or project-relative path, media type, checksum, producer, parameters and provenance.

### Event

Events support streaming and UI synchronization. Initial event classes:

- command proposed,
- approval requested,
- command started,
- progress updated,
- observation emitted,
- artifact created,
- state changed,
- command completed,
- command failed,
- command cancelled.

## State revisions and concurrency

Mutable scientific state uses monotonic revisions. Commands may declare `expected_state_revision`. A stale command must be rejected or explicitly rebased; it must not be applied silently to a different canvas or molecular state.

## Versioning

- Protocol versions use semantic versioning.
- Additive optional fields may be backward compatible.
- Removing fields, changing meanings or changing defaults requires a major version.
- Capability manifests declare supported protocol and command-schema versions.

## Serialization

JSON is the baseline interchange format. Python models may use dataclasses or Pydantic, but wire contracts must not depend on Python-specific serialization.

## Validation order

1. Envelope validation.
2. Protocol compatibility.
3. Capability availability.
4. Argument-schema validation.
5. Session and state validation.
6. Selection resolution.
7. permission and approval checks.
8. execution.
9. result and provenance validation.

## Non-goals

The protocol is not a general remote shell, an arbitrary Python execution format or a hidden prompt language.