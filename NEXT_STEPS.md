# MolSys-AI — Temporary Implementation Checkpoint

> **Temporary implementation checkpoint.**
>
> This document is not part of the frozen MolSys-AI architecture. It records the next implementation/migration steps after the repository boundaries were aligned with MOLI Platform Architecture 1.0. Remove this file once the migration is complete and durable documentation has absorbed any still-relevant information.

## Current baseline

The project-level structure is now:

    MolSys-AI
    ├── molsys-ai          umbrella / architecture
    ├── molsys-ai-server   inference + MolSysSuite Software Knowledge + docs assistants
    ├── molsys-ai-client   lightweight typed SDK
    └── molsys-ai-agent    local-first MolSysSuite specialist agent

The documentation chatbot is the first operational MolSys-AI capability.

Two migration rules apply throughout:

> **Preserve working capabilities, not legacy implementations.**

> **Restructuring the repositories must not turn a working chatbot into a future promise.**

The chatbot therefore acts as a regression anchor while its internal implementation remains free to evolve.

## Phase 1 — Chatbot regression gate

Before moving legacy code:

- separate server-owned tests from the current mixed smoke tests;
- establish an executable baseline for the documentation-assistant capability;
- verify grounded answers, Software Knowledge retrieval, citations/sources, supported multi-turn behavior, API/symbol guardrails, and the documentation UI → API → model path;
- retain compatibility for current consumers such as POST /v1/chat while they remain in use.

The gate protects capability, not endpoint or RAG implementation details.

## Phase 2 — MolSys-AI Client

Turn molsys-ai-client into the real lightweight typed SDK.

Initial migration sources from molsys-ai-server:

- client/cli/config.py;
- client/cli/http_api.py;
- transport-related portions of other legacy modules where appropriate.

Goals:

- endpoint/configuration handling;
- authentication;
- typed requests/responses;
- sync/async and streaming contracts as justified;
- compatibility negotiation;
- stable exceptions/timeouts;
- tests against the current server.

The Client must remain usable without MolSysSuite installed.

## Phase 3 — MolSys-AI Agent

Turn molsys-ai-agent into the real MolSysSuite specialist-agent package.

Migration/refactoring candidates:

- client/agent/core.py;
- client/agent/planner.py;
- client/agent/executor.py;
- client/agent/notebook.py;
- client/agent/tools/*.

Important changes during migration:

- remove direct ownership/import of server RAG from the Agent;
- consume MolSysSuite Software Knowledge through stable contracts when remote services are used;
- preserve backend independence: Server/Client is an available path, not a mandatory topology;
- strengthen tool validation, API introspection, authorization, and execution safety;
- establish Agent-owned tests.

## Phase 4 — CLI split

The current client/cli/main.py mixes remote-service UX and local specialist-agent UX and must be decomposed rather than moved wholesale.

Preserve a coherent user-facing experience even if implementation is distributed across packages.

## Phase 5 — Server cleanup

Only after Client and Agent replacement paths are functional:

- mark legacy server-side client/agent modules deprecated;
- remove obsolete client/agent and client/cli code;
- simplify server packaging and pyproject.toml;
- leave only server-owned tests and dependencies;
- run the chatbot regression gate after each cleanup step.

The operational chatbot must remain available throughout.

## Phase 6 — Legacy devguide audit

Audit older design material in molsys-ai/devguide, including session model, tool protocol, MolSysViewer copilot, CLI, artifacts/provenance, model/inference policy, user profiles/memory, security/privacy, and evaluation.

For each document or concept classify it as KEEP, MIGRATE, REINTERPRET, or SUPERSEDE.

Do not delete historical design material before determining whether it contains useful requirements not yet represented in the new repositories.

## Completion condition

This temporary checkpoint can be removed when:

- Server, Client, and Agent physical code ownership matches the documented boundaries;
- legacy server client/agent code has been safely retired;
- the documentation chatbot remains operational;
- Software Knowledge is reusable beyond the chatbot;
- repository-specific tests enforce the new boundaries;
- durable devguide documents contain any remaining architectural or operational decisions.
