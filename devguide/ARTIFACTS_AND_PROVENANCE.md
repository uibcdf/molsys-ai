# Artifacts and Provenance

## Principle

The conversation is temporary; the reproducible scientific record is durable.

## Workflow manifest

Every exportable workflow records:

- workflow and schema version,
- ordered typed commands,
- exact arguments and selections,
- package, adapter, protocol and model versions,
- input artifact checksums,
- outputs and checksums,
- random seeds,
- environment and execution profile,
- warnings, approvals and limitations,
- parent workflow or checkpoint when derived.

## Artifact model

Artifacts include molecular files, trajectories, tables, images, viewer scenes, reports, scripts, notebooks and logs. Each artifact has a stable ID, project-relative location or URI, media type, checksum, producer command, timestamps and provenance.

## Export targets

Initial targets:

- deterministic Python,
- Jupyter notebook cells,
- protocol-native JSON workflow,
- MolSysViewer scene or image exports.

Generated Python should use public MolSysSuite APIs rather than reproducing adapter internals.

## Replay semantics

- **Repeat:** execute the same commands against the same declared inputs.
- **Resume:** continue from a recorded checkpoint.
- **Reproduce:** recreate outputs under a declared compatible environment.
- **Branch:** derive a new workflow while preserving lineage.

Reproducibility claims must state environmental assumptions and tolerances for stochastic or platform-dependent computation.

## Immutability

Completed manifests are append-only. Corrections create a new revision linked to the previous record; they do not erase history.