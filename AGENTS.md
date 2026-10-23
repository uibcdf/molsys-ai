# MolSys-AI repository coordination

MolSys-AI is a governed specialist subsystem of MolSysSuite.

Before cross-repository, architectural, migration, or governance work:

1. read `MOLSYSSUITE_GUIDE.md` for MolSysSuite member governance and its MOLI platform boundary;
2. read `MOLSYS_AI_GUIDE.md` for MolSys-AI subsystem boundaries and routing.

This umbrella repository owns subsystem architecture, internal registry, cross-repository contracts, and migration coordination. Server, Client, and Agent retain their own implementation ownership.

Escalate modeling-domain contracts to `uibcdf/molsyssuite` and MOLI platform-boundary contracts to `uibcdf/moli`.

Before filing or closing a durable subsystem report, follow
`devguide/reporting_protocol.md`: open the owning GitHub issue first, use
`devguide/templates/report.md`, and run the commands in
`devguide/reporting_protocol.md` before committing. Do not edit synchronized
guide copies in child repositories.

## Release and package-publication notices

For every new component release, with or without a published package, and every
new package version/build/distribution route, open or update a release-specific
issue in `uibcdf/molsyssuite` as part of closeout. Include exact version/tag/source,
actual package availability and verification evidence, and ecosystem follow-up.
Follow [the notice policy](MOLSYSSUITE_GUIDE.md#release-and-package-publication-notices).

## Public release titles

When preparing, publishing or intentionally editing a public GitHub Release, use
exactly `X.Y.Z` as its title/name, matching the canonical tag and package/project
version. Put descriptions in the body/notes. Read
[the local release-title guide](devguide/release_titles.md) and
[the canonical rule](MOLSYSSUITE_GUIDE.md#github-release-titles).

## Modular reusable tools

Before adding a feature, inspect existing tools and identify the owning module or
component. Implement or extend independently useful operations as documented reusable
tools in that owner, with their own contracts and tests; have consumers call them.
Keep task-specific decisions local and report missing sibling capabilities to the
provider with linked consumer evidence. Follow
[MOLSYSSUITE_GUIDE.md#modular-reusable-tools](MOLSYSSUITE_GUIDE.md#modular-reusable-tools)
for applicability, compatibility, performance and tracked exceptions.

## Durable working instructions

Keep technical findings in owning issues, fixes, tests and maintained guidance.
Place only accepted lasting contributor actions in root or appropriately scoped
instructions, following
[the common policy](MOLSYSSUITE_GUIDE.md#durable-working-instructions).
For work under `devguide/`, also read [devguide/AGENTS.md](devguide/AGENTS.md)
and its local reporting protocol. Shared instruction proposals belong in
`uibcdf/molsyssuite`; cross-MOLI contracts belong in `uibcdf/moli`.

## Human-facing issue feedback

Surface actionable suspected defects, inconsistencies, missing analyses and
improvements, including uncertain or nonblocking findings. When working with a
human, offer an owning issue at a natural pause; retain existing reporting
authorization and respect declined/deferred disclosure. Follow
[the accepted feedback route](MOLSYSSUITE_GUIDE.md#human-facing-issue-feedback)
for ownership, uncertainty, privacy and exceptions.
