---
summary: Restore canonical umbrella identity, policy and license badges.
issue: uibcdf/molsys-ai#4
status: partial
opened: 2026-10-01
closed:
verification: reproduced
area: [governance, documentation, ci]
guard:
normative: MOLSYSSUITE_GUIDE.md
blocked_by: []
supersedes: []
---

# Umbrella repository badge baseline

## What

The README lacks the three canonical badges for this registered specialist
subsystem. No actual `molsyssuite-policy.yml` workflow previously backed the
required policy link; reporting CI alone did not establish the shared baseline.

## How / evidence

Generate the exact identity/policy/license row using MolSysSuite's registered
`repository_badges.py`, then add the real caller of `check-python-repository.yaml`
at published `policy-v1.5.9`. The shared checker returns after umbrella governance
checks because the registered member has no `python-package` capability. Its
ordinary lint/format steps apply to the existing governance Python scripts.
Local Ruff configuration fixes this repository's tool scope and style; it does
not add project metadata, a Python package or a release obligation.

## Why

Role identity, license and executed policy conformance are distinct from AI
runtime capability. Coverage adoption remains separately owned by #3. There is
no fabricated Python support badge or static green CI status.

## Alternatives

Do not copy another member's role or invent a passing workflow URL. No shared
taxonomy, policy change or canonical guide rollout is needed. Keep Server,
Client and Agent ownership and the umbrella's incubation state intact.

## Acceptance criteria

- Registered badge generation and shared repository conformance pass.
- A real exact-source policy workflow executes successfully before closure.
- Reporting/index checks remain successful and the record is archived.

## Resolution

The central generator's canonical row and local full repository checker pass.
All three reporting tests and generated indexes pass. Exact policy Ruff 0.16.5
lint/format checks pass using a task-owned temporary installation; the shared
development environment is preserved. The resource validator needed formatting;
its AST is identical before/after, with no executable logic change. Tool
configuration is explicit at this repository root.

The actual `policy-v1.5.9` caller is prepared. Exact native checks remain to be
recorded before closure. Coverage upload processing is independent.
