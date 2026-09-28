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
