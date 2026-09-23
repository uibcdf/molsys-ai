# MolSys-AI Governance

MolSys-AI is governed as a subsystem of MolSysSuite.

The umbrella repository owns subsystem-level architecture, contracts, reporting coordination, and migration boundaries. Server, Client, and Agent retain implementation ownership.

Inherited governance flows:

```text
MOLI engineering/platform baseline
        ↓
MolSysSuite modeling-domain governance
        ↓
MolSys-AI subsystem governance
        ↓
repository-local rules
```

The canonical child-facing guide is `MOLSYS_AI_GUIDE.md`. The machine-readable subsystem registry is `molsys-ai.toml`.

GitHub issues are stable work identities. Durable reports use `pending_bugs/`, `pending_proposals/`, and `archive/`.
