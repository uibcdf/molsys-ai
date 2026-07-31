# Interactive CLI

## Status

**Proposed product specification; earlier Codex-like CLI ideas remain pending repository verification.**

## Modes

- Interactive REPL: `molsys-ai`
- One-shot natural language: `molsys-ai ask "..."`
- Explicit typed command execution: `molsys-ai run workflow.json`
- Machine-readable mode: `--output json`

## Session experience

The prompt should display a compact active context: project, session, active molecular system, connected viewer and execution profile. Natural-language input and explicit slash commands share the same session.

Candidate commands:

```text
/help /status /project /session /systems /viewer
/profile /model /policy /plan /approve /reject
/history /undo /checkpoint /export /quit
```

Exact names remain provisional.

## Approval modes

- `ask`: confirm commands with meaningful side effects.
- `plan`: approve a complete multi-step plan before execution.
- `safe-auto`: automatically execute bounded reversible operations.
- `manual`: propose commands but never execute automatically.

Arbitrary shell execution is excluded from the normal scientific toolset.

## Viewer connection

The CLI can attach to one or more active MolSysViewer instances registered in the session. Commands must identify the target when more than one viewer is connected.

## Streaming

The interface streams model text, command proposals, approval requests, execution progress, observations and final summaries as distinct events.

## Automation

Non-interactive use must provide stable exit codes, JSON output and no hidden prompts. Workflows can be replayed without an LLM.

## History and privacy

Command history and scientific results are project-local. Conversation history may be retained separately and can be disabled. Secrets and private molecular content must be redacted from logs.

## First acceptance flow

From an empty project, the user can start the CLI, connect a viewer, request the 1TCD demonstration, inspect the generated command batch, approve it, observe the canvas changes and export equivalent Python.