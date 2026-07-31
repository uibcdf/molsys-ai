# MolSysViewer Live Copilot

## Status

**Proposed and strategic.** Live AI assistance over the MolSysViewer canvas is a first-class MolSys-AI experience and an early implementation target.

## Vision

The user and the copilot share the same molecular scene. The copilot can inspect the viewer state, understand references to visible objects and perform validated visual actions while the user observes the result immediately.

Example interaction:

> Load 1TCD, hide water, show chain A as an orange cartoon and focus on the ligand.

The request becomes a sequence of typed commands executed through the public MolSysViewer API. The model must not generate Mol* internals directly.

## Canvas-aware context

The copilot needs structured observations rather than screenshots alone. MolSysViewer should expose a compact state model containing, where applicable:

- loaded systems and components,
- chains, residues, atoms and ligands,
- current selections,
- visible and hidden representations,
- colors and labels,
- camera and focus target,
- overlays, pockets, pharmacophores and measurements,
- identifiers that allow dialogue to refer to visible objects.

Examples:

> Color this chain red.

> Hide the residues around the selected ligand.

> Compare this pocket with pocket 2.

Deictic references such as “this”, “that residue” or “the selected pocket” require explicit selection and interaction events from the canvas.

## Interaction model

```text
user text or canvas interaction
→ MolSys-AI session
→ viewer-state observation
→ typed command proposal
→ schema and state validation
→ MolSysViewer executor
→ updated viewer state
→ structured result
→ conversational explanation
```

The chat panel may live beside or over the canvas, but it communicates with MolSys-AI through the same protocol used by the CLI and notebooks.

## Initial command set

The first milestone should remain deliberately small:

- load,
- show,
- hide,
- isolate,
- focus,
- select,
- color,
- label,
- reset,
- undo.

Subsequent capabilities may add:

- measurements,
- surfaces and shapes,
- pocket overlays from TopoMT,
- pharmacophore features from PharmacophoreMT,
- image and scene export,
- comparison of systems or states.

## Safety and user control

- Every command is validated against the current viewer state.
- Destructive or expensive actions require explicit confirmation.
- Visual changes should be reversible through command history.
- The user can inspect the exact command before or after execution.
- Failure results must be structured and explain what state or argument was invalid.

## Reproducibility

An interactive canvas operation should be exportable as Python or as a workflow fragment. A session such as:

```text
load 1TCD
hide waters
show chain A as cartoon
color chain A orange
focus ligand
```

must be convertible into a deterministic MolSysViewer script or notebook cell sequence.

## Architectural boundary

MolSysViewer owns visualization state and executes viewer operations. MolSys-AI owns interpretation, session-level orchestration and provenance. MolSys-AI must not bypass the supported MolSysViewer API to manipulate Mol* directly.
