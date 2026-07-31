# Session and Project Model

## Status

**Proposed baseline.** Sessions provide the durable scientific context shared by the CLI, notebooks, MolSysViewer and future interfaces.

## Project versus session

A **project** is durable. It owns inputs, generated artifacts, workflow manifests, configuration and long-term provenance.

A **session** is an active interaction with a project. It owns current systems, active selections, connected viewers, conversation context, execution history and temporary observations.

A project may contain many sessions. A session belongs to exactly one project, although import and export between projects may be supported explicitly.

## Session contents

- session identifier and schema version,
- project identifier,
- loaded molecular systems and stable handles,
- active system and active selection,
- connected viewer instances,
- tool outputs and artifacts,
- command, result and observation history,
- approval and policy decisions,
- model and inference choices,
- compact conversational context,
- current state revision and checkpoints.

## Persistence

Sessions should be restorable after process or kernel restart. Durable state is stored in project-local manifests; large molecular objects remain in explicit files or caches referenced by checksum.

Suggested project layout:

```text
.molsys-ai/
├── project.toml
├── sessions/
├── workflows/
├── artifacts/
├── cache/
└── logs/
```

The exact layout remains provisional and must be reviewed against earlier repository ideas.

## History layers

Keep separate histories for:

1. conversation messages,
2. typed scientific commands,
3. execution results and observations,
4. viewer-state changes,
5. durable workflow checkpoints.

Scientific replay must not depend on retaining the full conversational transcript.

## Checkpoints, undo and branching

A checkpoint records references to all durable state required to restore a meaningful scientific point. Undo should use adapter-supported inverse commands or checkpoint restoration. It must never be represented as guaranteed when an operation is irreversible.

Branching from a checkpoint creates a new session lineage rather than rewriting provenance.

## Multiple systems and viewers

A session may contain multiple molecular systems and multiple viewers. Every command must identify its target explicitly or resolve it through an unambiguous active target. Viewer connections have stable IDs and report their state revisions.

## Context sent to models

Only the minimum required context should be sent to inference:

- user request,
- compact session summary,
- relevant state observations,
- allowed capabilities,
- selected documentation fragments.

Private files, full trajectories and unrelated project history remain local unless the user and policy explicitly allow transmission.

## Lifecycle

```text
create or open project
→ create or restore session
→ attach interfaces and tools
→ execute and checkpoint
→ export or suspend
→ resume, branch or close
```

Closing a session finalizes manifests but does not delete project artifacts.