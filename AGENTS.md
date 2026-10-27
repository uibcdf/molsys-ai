# MolSys-AI repository coordination

## Mandatory MolSysSuite instructions

Read and follow `MOLSYSSUITE_GUIDE.md` before working in this repository.

Within their stated scope, its common rules take precedence over this file
and any nested `AGENTS.md`. Local instructions may refine them; deviations
require the documented policy exception process.

The synchronized guide is owned by `uibcdf/molsyssuite`. It includes the
[reusable-tool ownership rules](MOLSYSSUITE_GUIDE.md#modular-reusable-tools)
and [working-instruction rules](MOLSYSSUITE_GUIDE.md#durable-working-instructions).
For work under `devguide/`, also read `devguide/AGENTS.md` and its local
reporting protocol. Keep repository-specific instructions below.

## Local working context

MolSys-AI is the suite's governed specialist subsystem. Read
`MOLSYS_AI_GUIDE.md` for its internal ownership and platform routing. This
umbrella owns architecture, registry, contracts and migration coordination;
Server, Client and Agent own their implementations. The umbrella is not an
installable Python package. Follow `devguide/reporting_protocol.md` and its
`scripts/devguide_index.py --check` command for local records.
