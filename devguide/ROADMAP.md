# Implementation Roadmap

## Phase 0 — Design baseline

- Keep these documents as the target architecture.
- Review remembered ideas against repository history.
- Record disagreements between existing code and intended design explicitly.

## Phase 1 — Protocol before model

- Define command, selection, result, error and state schemas.
- Implement schema versioning and serialization.
- Execute commands manually without an LLM.
- Add provenance and replay tests.

## Phase 2 — MolSysViewer vertical slice

- Implement a viewer-state observation API.
- Implement the initial MolSysViewer command executor.
- Add command history and undo.
- Demonstrate the same command from Python, CLI and the live canvas assistant.

Acceptance scenario:

> Load 1TCD, hide water, show chain A as an orange cartoon and focus on the ligand.

The scenario must execute through typed commands and export reproducible Python.

## Phase 3 — Interactive CLI

- Add an interactive `molsys-ai` session.
- Support explicit commands and natural-language requests.
- Display active project, systems, viewer connections and execution profile.
- Add approval modes and readable command previews.
- Verify earlier profile and token concepts before finalizing configuration design.

## Phase 4 — Knowledge integration

- Connect through `molsys-ai-client` to documentation and inference services.
- Add documentation, API-signature and recipe tools.
- Prefer runtime observations for questions about active systems and static knowledge for questions about APIs and methods.

## Phase 5 — MolSysMT and TopoMT

- Add bounded system-management capabilities.
- Add pocket detection and characterization.
- Visualize TopoMT artifacts in MolSysViewer.
- Export cross-tool workflows.

## Phase 6 — PharmacophoreMT

- Add pharmacophore feature and model operations.
- Connect pockets, ligands, pharmacophore hypotheses and viewer overlays.

## Phase 7 — Controlled multi-step copilot

- Add plan review, iterative observations and correction.
- Introduce budgets for tool calls, time and computation.
- Evaluate scientific correctness, not only conversational quality.

## Deferred

- unrestricted autonomous execution,
- arbitrary shell execution as a normal tool,
- server-side execution of private molecular systems,
- fine-tuning before stable protocol and evaluation baselines exist.
