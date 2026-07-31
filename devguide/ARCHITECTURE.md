# Target Architecture

## System view

```text
User interfaces
├── interactive CLI
├── MolSysViewer live copilot
├── notebooks and Python
└── future graphical applications
        │
        ▼
MolSys-AI local core
├── agent/session
├── typed command protocol
├── tool registry
├── validation and policy
├── execution adapters
├── observation model
├── provenance and history
└── export and replay
        │
        ├── MolSysMT
        ├── MolSysViewer
        ├── TopoMT
        ├── PharmacophoreMT
        └── future MolSysSuite tools
        │
        ▼ optional remote services
molsys-ai-client
        │
        ▼
molsys-ai-server
├── model inference
├── documentation assistants
└── knowledge services
```

## Core responsibilities

### Session

A session owns the active scientific context:

- loaded molecular systems,
- active system and selections,
- connected viewers,
- tool outputs and artifacts,
- command and observation history,
- project metadata,
- user confirmations and policy decisions.

### Typed protocol

The model proposes commands; it does not emit arbitrary executable code as the primary control path.

```json
{
  "tool": "molsysviewer.show",
  "arguments": {
    "selection": {"chain_id": "A"},
    "representation": "cartoon",
    "color": "orange"
  }
}
```

Each command must have:

- a stable identifier,
- a versioned schema,
- validated arguments,
- declared side effects,
- a structured result,
- provenance information.

### Tools and adapters

MolSysSuite packages expose bounded capabilities through adapters. The agent should not infer internal library behavior when an adapter can provide a typed operation.

A future capability manifest may allow tools to advertise:

- commands,
- input and output schemas,
- requirements,
- side effects,
- reversibility,
- documentation references.

### Planning loop

The eventual agent loop is:

```text
intent
→ inspect current state
→ propose plan or command
→ validate
→ request confirmation when required
→ execute
→ observe
→ decide whether to continue
→ report and export
```

Multi-step autonomy should only be introduced after single-command execution, state inspection and provenance are reliable.

## Repository boundaries

### `molsys-ai`

Owns the local scientific copilot, sessions, protocol, tool adapters, CLI and MolSysViewer integration.

### `molsys-ai-server`

Owns remote inference, public documentation assistants, static knowledge services, corpus/index construction and server deployment.

### `molsys-ai-client`

Owns only the typed transport SDK for remote MolSys-AI services. It must not contain the scientific agent or MolSysSuite execution logic.

## Profiles and credentials

**Remembered — verify:** earlier plans may have included tokenized user profiles or persistent endpoint profiles.

**Proposed interpretation:** profiles should describe connection and execution environments, not scientific identity embeddings. A profile may select:

- server endpoint,
- authentication token reference,
- preferred model,
- local or remote inference,
- default project location,
- execution policy,
- telemetry and privacy settings.

Credentials must be stored using operating-system facilities or protected configuration, never committed to project files.
