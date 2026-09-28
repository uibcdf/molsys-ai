---
summary: Complete issue-backed reporting validation for the MolSys-AI umbrella.
issue: uibcdf/molsys-ai#2
status: resolved
opened: 2026-09-28
closed: 2026-09-28
verification: inspected
area: [governance, reporting]
guard: tests/test_reporting_protocol.py::TestReportingProtocol::test_existing_reports_have_valid_metadata_and_generated_indexes
normative:
blocked_by: []
supersedes: []
---

# Complete the reporting lifecycle

## What

Complete the umbrella's local reporting machinery required by
`uibcdf/molsyssuite#60`.

## How

Retain the existing queues, archive and template. Add common closure fields
to the template, generated queue/archive indexes, an offline validator with
negative tests, contributor guidance and an independent hosted governance
workflow.

## Why

The current documents describe issue-backed reports, but no local command
or CI job checks metadata, status, guard addressability or index freshness.

## What is measured and what is assumed

Inspection of the umbrella's `main` on 2026-09-28 found the three directories
and a partial template, with no reports, generated index or validator. The
umbrella has no Python package workflow and this change makes no claim about
one.

## Scope and exclusions

This governs the umbrella's subsystem reports. It does not transfer child
implementation ownership or impose Python-package and scientific CI lanes.

## Acceptance criteria

The validator rejects missing issues, false closure and unresolvable guard
selectors; generated indexes are current. The exact published commit passes
its reporting-governance workflow. Close the issue with a durable guard and
archived report path.

## Resolution

Commit `805a2cc` completed the local template, generated indexes, offline
validator, contributor guidance and independent hosted reporting workflow.
The guard checks report metadata and index freshness; two additional negative
tests reject false closure and unresolvable test selectors. Local index,
reporting tests and Ruff checks passed. Hosted Reporting governance run
`36386280283` passed for the implementation commit. The umbrella still makes
no Python-package support or release claim.
