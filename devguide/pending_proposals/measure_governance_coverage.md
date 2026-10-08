---
summary: Measure and publish coverage of the MolSys-AI umbrella governance scripts.
issue: uibcdf/molsys-ai#3
status: partial
opened: 2026-10-01
closed:
verification: inspected
area: [governance, ci, coverage]
guard:
normative: devguide/coverage_reporting.md
blocked_by: []
supersedes: []
---

# Umbrella governance coverage

## What

The umbrella has executable reporting and resource governance scripts but no
accepted coverage report. Runtime responsibilities belong to Server, Client and
Agent; incubation does not make the umbrella's own tested tooling non-applicable.

## How / evidence

Extend the existing reporting workflow with coverage.py measurement of all
`scripts/` Python files using its existing three reporting tests. Retain XML in
the producing run and publish automatically in a dependent trusted-main OIDC job.
The action and signature-verifying route match the existing central producer.
No extra scientific tests or new package dependencies are introduced.

## Why

A narrowly described umbrella percentage is useful and honest. Reporting/upload
success, independent service acceptance, README delivery and runtime coverage
remain distinct; the last is outside this work.

## Alternatives

Do not combine child repository percentages or infer their runtime coverage.
Do not remove untested resource validation from the denominator, introduce a
coverage floor or launch a scientific suite to obtain a badge.

## Acceptance criteria

- Existing reporting checks pass and retain a measured governance-only XML.
- The exact source's independent publisher runs automatically after the checks;
  untrusted PRs do not receive upload permission.
- Codecov independently confirms a complete source-linked report and numeric SVG.
- README scope/cadence and live badge are delivered only after that acceptance.
- Archive this record, keep the normative reporting contract and reconcile #69.

## Resolution

Local Python 3.14.7 reporting checks pass: three tests, no failures or skips,
current indexes and valid workflow publication boundaries. Coverage.py 7.16.2
measures 106/443 lines and 43/224 branches across exactly the three maintained
governance scripts. The hosted measurement uses the central producer's fixed
coverage.py 7.16.0; its XML and service percentage will be checked independently.
No uncovered resource-validator paths are removed from the denominator.

Exact native upload and independent service acceptance remain to be recorded.
The primary clone and caller environment remain preserved.
