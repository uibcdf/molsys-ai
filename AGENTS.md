# MolSys-AI repository coordination

MolSys-AI is a governed specialist subsystem of MolSysSuite.

Before cross-repository, architectural, migration, or governance work:

1. read `MOLSYSSUITE_GUIDE.md` for MolSysSuite member governance and its MOLI platform boundary;
2. read `MOLSYS_AI_GUIDE.md` for MolSys-AI subsystem boundaries and routing.

This umbrella repository owns subsystem architecture, internal registry, cross-repository contracts, and migration coordination. Server, Client, and Agent retain their own implementation ownership.

Escalate modeling-domain contracts to `uibcdf/molsyssuite` and MOLI platform-boundary contracts to `uibcdf/moli`.
