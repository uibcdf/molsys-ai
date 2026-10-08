# MolSys-AI

[![MolSysSuite: Specialist Subsystem](https://img.shields.io/badge/MolSysSuite-specialist%20subsystem-8b5cf6?labelColor=24292f)](https://github.com/uibcdf/molsyssuite/blob/main/devguide/repository_badges.md#specialist-subsystem)
[![MolSysSuite policy](https://github.com/uibcdf/molsys-ai/actions/workflows/molsyssuite-policy.yml/badge.svg?branch=main)](https://github.com/uibcdf/molsys-ai/actions/workflows/molsyssuite-policy.yml)
[![License](https://img.shields.io/github/license/uibcdf/molsys-ai)](https://github.com/uibcdf/molsys-ai/blob/main/LICENSE)

**MolSys-AI is the AI subsystem specialized in understanding and operating MolSysSuite.**

It is part of the MolSysSuite domain and is distinct from **MOLI Agent**, the scientific agent of the wider MOLI Platform.

MolSys-AI is a **primary incubating specialist subsystem of MolSysSuite**. This repository receives MolSysSuite governance through `MOLSYSSUITE_GUIDE.md` and governs its internal repositories through `MOLSYS_AI_GUIDE.md`.

This repository is the umbrella, governance, and architecture repository for MolSys-AI:

- [molsys-ai-server](https://github.com/uibcdf/molsys-ai-server) — remote inference and reusable **MolSysSuite Software Knowledge** services, plus documentation assistants.
- [molsys-ai-client](https://github.com/uibcdf/molsys-ai-client) — lightweight typed SDK for remote MolSys-AI services.
- [molsys-ai-agent](https://github.com/uibcdf/molsys-ai-agent) — local-first MolSysSuite specialist agent for planning, API inspection, tool execution, and recovery.

## System view

```text
                         MolSys-AI
                    umbrella / architecture
                             │
          ┌──────────────────┼──────────────────┐
          ▼                  ▼                  ▼
       Server              Client              Agent
 inference +             typed SDK       MolSysSuite specialist
 Software Knowledge          │             /      |      \
          ▲                  │            ▼       ▼       ▼
          └──────────────────┘       MolSysSuite Client  local/other
```

The documentation chatbot is the **first operational MolSys-AI capability**. Its grounded documentation-assistance capability should remain available while its internal implementation is free to evolve.

The server's Software Knowledge capability is reusable: the chatbot is its first consumer, not its architectural owner.

MolSys-AI Agent may be used directly by scientists or receive delegated modeling tasks from [MOLI Agent](https://github.com/uibcdf/moli-agent). It may use Server through Client, but is not architecturally required to do so for every operation.

> **MolSys-AI knows how to use MolSysSuite. MOLI reasons about why, when, and what for.**

## Migration

The project predates the current four-repository structure. Existing material is retained as history and migration input. Legacy code should be migrated incrementally by responsibility, while preserving working capabilities rather than freezing legacy implementation details.

See `devguide/` and the frozen [MOLI Platform Architecture 1.0](https://github.com/uibcdf/moli/tree/main/architecture_1.0).


## Governance

```text
MOLI
  ↓
MolSysSuite
  ↓  MOLSYSSUITE_GUIDE.md
MolSys-AI
  ↓  MOLSYS_AI_GUIDE.md
├── Server
├── Client
└── Agent
```

The MolSys-AI umbrella is the MolSysSuite member. Server, Client, and Agent are internal subsystem repositories rather than independent MolSysSuite members. See `molsys-ai.toml` for the authoritative internal registry.


Governance coverage measures the umbrella's Python scripts using its reporting tests;
Server, Client and Agent runtime code are outside that percentage. The
[scope and automatic publication route](devguide/coverage_reporting.md) describe
its push/manual cadence. The initial report is uploaded, but its live percentage
remains pending independent Codecov processing under `uibcdf/molsys-ai#3`.
