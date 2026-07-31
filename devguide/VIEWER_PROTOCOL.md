# MolSysViewer Integration Protocol

## Status

**Proposed technical companion to `MOLSYSVIEWER_COPILOT.md`.**

## Boundary

MolSysViewer owns visual state and executes public viewer operations. MolSys-AI owns interpretation, session orchestration, approval and provenance. MolSys-AI never manipulates Mol* internals directly.

## Viewer registration

A viewer registers with a session using:

- stable `viewer_id`,
- supported protocol version,
- capability manifest,
- current state revision,
- transport endpoint or in-process adapter,
- project and session identity.

## State observation

The viewer exposes compact structured snapshots and incremental events. Snapshots include loaded components, stable object handles, selections, representations, visibility, colors, labels, camera, measurements, overlays and active focus.

Large coordinate data is referenced, not embedded, unless explicitly required.

## Interaction events

Initial events:

- object clicked,
- selection changed,
- representation changed,
- camera/focus changed,
- object added or removed,
- overlay added or removed,
- scene reset,
- viewer disposed.

Click and selection events include stable molecular or visual identifiers so deictic language can resolve “this chain” or “that pocket”. Hover is ephemeral and should not become durable session state unless promoted by an explicit action.

## Commands

Viewer commands use the shared typed protocol. Each command declares its target viewer and expected state revision. The first command set is load, show, hide, isolate, focus, select, color, label, reset and undo.

## Synchronization

- Full snapshots establish or repair state.
- Deltas update normal operation.
- Commands against stale revisions are rejected or explicitly rebased.
- User interaction and copilot execution are serialized through revision checks.
- After every mutating command, the viewer returns the resulting revision and normalized state delta.

## Multiple viewers

A session may connect several viewers. They may share a molecular system while maintaining independent scenes. Synchronization between viewers is opt-in and represented as explicit commands, not assumed.

## Restart and recovery

After kernel, widget or frontend restart, the viewer re-registers and reports a fresh snapshot. The session compares durable scene history with actual viewer state and offers restore, accept-current or branch choices.

## Undo

Undo is capability-based. Pure visual changes should normally expose inverse commands. Loads, resets and compound operations may require scene checkpoints. The UI must not claim reversibility when restoration is incomplete.

## Transport

The first implementation may be in-process through Python/anywidget messaging. The protocol must remain transport-neutral so a desktop or remote frontend can later use WebSocket or another event channel.

## Latency target

Simple visual actions should feel immediate. Model inference may stream separately, but once a command is approved, state validation and viewer dispatch should avoid unnecessary remote round trips.