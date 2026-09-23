# MolSys-AI

**MolSys-AI is the AI subsystem specialized in understanding and operating MolSysSuite.**

It is part of the MolSysSuite domain and is distinct from **MOLI Agent**, the scientific agent of the wider MOLI Platform.

This repository is the **umbrella and architecture repository** for MolSys-AI. Implementations are split across three focused repositories:

- [molsys-ai-server](https://github.com/uibcdf/molsys-ai-server) — remote inference, MolSysSuite software-knowledge/RAG, citations, and documentation-assistant services.
- [molsys-ai-client](https://github.com/uibcdf/molsys-ai-client) — lightweight typed SDK for remote MolSys-AI services.
- [molsys-ai-agent](https://github.com/uibcdf/molsys-ai-agent) — MolSysSuite specialist agent for planning, API inspection, tool execution, and recovery in the scientific environment.

## System view

```text
                    MolSys-AI
                  umbrella / architecture
                         │
          ┌──────────────┼──────────────┐
          ▼              ▼              ▼
       Server          Client          Agent
 inference +         typed SDK       MolSysSuite
 software knowledge      │          specialist
          ▲              │              │
          └──────────────┘              ▼
                                    MolSysSuite
```

MolSys-AI Agent may be used directly by scientists or receive delegated modeling tasks from [MOLI Agent](https://github.com/uibcdf/moli-agent).

> **MolSys-AI knows how to use MolSysSuite. MOLI reasons about why, when, and what for.**

## Migration

This repository and `molsys-ai-server` predate the current four-repository structure. Existing material is retained as project history and migration input. New implementation ownership should follow the boundaries above; legacy agent/CLI code in the server should be migrated incrementally rather than removed destructively.

See `devguide/` for project-level design material. Some documents predate the current repository split and should be interpreted in light of this README and the frozen [MOLI Platform Architecture 1.0](https://github.com/uibcdf/moli/tree/main/architecture_1.0).
