# MolSys-AI Development Guide

> **Design status**
>
> These documents describe the intended architecture of MolSys-AI. Some elements are confirmed by existing repositories; others recover earlier discussions or introduce new proposals. Items based on memory must be verified against the codebase and project history before being treated as established decisions.

## Mission

MolSys-AI is the intelligent interaction and orchestration layer of MolSysSuite. Its long-term goal is a reproducible scientific copilot for molecular modeling and computational drug design.

MolSys-AI should help users operate a growing ecosystem that includes MolSysMT, MolSysViewer, TopoMT, PharmacophoreMT and future MolSysSuite tools.

Natural language is one input modality. The durable core is a typed, validated and reproducible protocol for scientific actions.

## Primary user experiences

1. An interactive CLI inspired by modern coding copilots.
2. Live AI assistance embedded in MolSysViewer, acting directly on the active canvas.
3. Notebook and Python assistance.
4. Multi-tool scientific workflows.
5. Exportable scripts, notebooks and workflow manifests.

## Vision and architecture

- [VISION.md](VISION.md)
- [ARCHITECTURE.md](ARCHITECTURE.md)
- [ROADMAP.md](ROADMAP.md)

## Core contracts

- [PROTOCOL.md](PROTOCOL.md): typed commands, observations, results, errors, artifacts and events.
- [SESSION_MODEL.md](SESSION_MODEL.md): projects, sessions, persistence, history and recovery.
- [TOOL_PROTOCOL.md](TOOL_PROTOCOL.md): capability manifests and MolSysSuite adapters.
- [ARTIFACTS_AND_PROVENANCE.md](ARTIFACTS_AND_PROVENANCE.md): workflow manifests, exports and replay.

## User experiences

- [CLI.md](CLI.md): interactive and automated command-line use.
- [MOLSYSVIEWER_COPILOT.md](MOLSYSVIEWER_COPILOT.md): product vision for live canvas assistance.
- [VIEWER_PROTOCOL.md](VIEWER_PROTOCOL.md): state, events and synchronization with MolSysViewer.

## Policy and quality

- [MODEL_AND_INFERENCE_POLICY.md](MODEL_AND_INFERENCE_POLICY.md)
- [USER_PROFILES_AND_MEMORY.md](USER_PROFILES_AND_MEMORY.md)
- [SECURITY_AND_PRIVACY.md](SECURITY_AND_PRIVACY.md)
- [EVALUATION.md](EVALUATION.md)

## Non-negotiable principles

- Scientific execution is local by default.
- Natural language does not directly execute arbitrary code.
- Commands and results are typed and validated.
- Every action should be inspectable, reversible where possible and reproducible.
- The language model is replaceable; the protocol, state and provenance are the core product.
