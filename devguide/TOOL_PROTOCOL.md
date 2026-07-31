# Tool and Capability Protocol

## Status

**Proposed baseline.** MolSysSuite packages expose bounded scientific capabilities to MolSys-AI through adapters and manifests.

## Capability manifest

Each adapter publishes a machine-readable manifest containing:

- tool and package name,
- package and adapter versions,
- supported protocol versions,
- capability identifiers,
- command schemas,
- result and artifact schemas,
- requirements and optional dependencies,
- side effects,
- estimated cost class,
- reversibility,
- progress and cancellation support,
- documentation references.

## Adapter boundary

Adapters translate stable MolSys-AI commands into public package APIs. They must not expose arbitrary internal functions merely because they are callable.

An adapter owns:

- argument validation specific to the package,
- conversion from session handles to package objects,
- execution,
- structured observations and artifacts,
- package-specific provenance,
- rollback or inverse-action metadata when available.

## Capability classes

Initial classes:

- inspection: read state without mutation,
- transformation: modify or derive molecular systems,
- analysis: compute scientific observations,
- visualization: modify a viewer or produce scenes,
- export: create durable files,
- orchestration helper: coordinate bounded package operations without autonomous reasoning.

## Execution properties

Every capability declares:

- synchronous, asynchronous or either,
- deterministic or stochastic,
- required seeds for stochastic work,
- expected resource class,
- whether it touches files, network, GPU or external executables,
- whether confirmation is required,
- whether results can be cached.

## Progress and cancellation

Long-running capabilities emit progress events and support cancellation when the underlying package permits it. Cancellation results must distinguish clean cancellation, partial output and unknown external-process state.

## Discovery

The local core discovers installed adapters through Python entry points or an equivalent explicit registry. Discovery must not import every scientific package into server processes.

## Namespacing

Capability identifiers use stable namespaces, for example:

```text
molsysmt.load
molsysmt.select
topomt.detect_pockets
pharmacophoremt.build_model
molsysviewer.show
```

Names reflect user-facing scientific operations, not internal module paths.

## Compatibility

Adapters declare tested package-version ranges. Unsupported combinations must fail visibly. Compatibility shims belong in adapters, not in prompts.

## Testing contract

Each capability requires:

- schema tests,
- successful execution tests,
- invalid-state and invalid-selection tests,
- provenance tests,
- replay tests when deterministic,
- cancellation and rollback tests when claimed.