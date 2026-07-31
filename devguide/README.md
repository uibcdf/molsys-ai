# MolSys-AI Development Guide

> **Design status**
>
> These documents describe the intended architecture of MolSys-AI. Some elements are confirmed by existing repositories; others recover earlier discussions or introduce new proposals. Items based on memory must be verified against the codebase and project history before being treated as established decisions.

## Mission

MolSys-AI is the intelligent interaction and orchestration layer of MolSysSuite. Its long-term goal is a reproducible scientific copilot for molecular modeling and computational drug design.

MolSys-AI should help users operate a growing ecosystem that includes:

- MolSysMT for molecular-system handling,
- MolSysViewer for interactive visualization,
- TopoMT for pockets and molecular topography,
- PharmacophoreMT for pharmacophore modeling,
- future MolSysSuite tools.

Natural language is one input modality. The durable core is a typed, validated and reproducible protocol for scientific actions.

## Primary user experiences

1. An interactive CLI inspired by modern coding copilots.
2. Live AI assistance embedded in MolSysViewer, acting directly on the active canvas.
3. Notebook and Python assistance.
4. Multi-tool scientific workflows.
5. Exportable scripts, notebooks and workflow manifests.

## Documents

- [VISION.md](VISION.md): product vision and guiding principles.
- [ARCHITECTURE.md](ARCHITECTURE.md): target components and repository boundaries.
- [MOLSYSVIEWER_COPILOT.md](MOLSYSVIEWER_COPILOT.md): live assistance over the viewer canvas.
- [ROADMAP.md](ROADMAP.md): phased implementation plan.

## Non-negotiable principles

- Scientific execution is local by default.
- Natural language does not directly execute arbitrary code.
- Commands and results are typed and validated.
- Every action should be inspectable, reversible where possible and reproducible.
- The language model is replaceable; the protocol, state and provenance are the core product.
