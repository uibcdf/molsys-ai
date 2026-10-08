# Umbrella governance coverage

This repository owns MolSys-AI architecture and coordination. Its coverage
percentage measures the Python governance scripts in `scripts/`, using the
existing reporting-protocol tests. All three maintained scripts remain in the
denominator, including resource validation paths not exercised by these tests.
Server, Client and Agent runtime code, scientific execution, third-party modules
and child-process execution are outside this report. No subsystem runtime
coverage is inferred from the umbrella percentage.

`reporting-governance.yml` measures branches and lines on Linux/Python 3.14 after
checking the generated report indexes. It preserves the existing reporting test
selection and has no minimum coverage threshold. A failed check or test keeps
the reporting job failed and prevents publication of an incomplete report.
The successful job retains its XML for fourteen days.

A dependent, independent job downloads that run's XML and automatically uploads
it using the same pinned, signature-verifying Codecov action as MolSysSuite.
Only a non-PR run on this repository's `main` receives OIDC publication permission.
PRs execute the reporting checks and retain their measurement without uploading.
No scientific suite, child repository or package build is added to this workflow.

Pushes to `main` and explicit manual reporting runs produce reports; skip-CI
pushes do not. The live badge describes the last report independently accepted
by Codecov and may lag later commits. A successful upload alone is insufficient:
before adding the badge, verify the complete report's source SHA and numeric SVG
using MolSysSuite's read-only `coverage_audit.py`. Coverage does not certify
runtime capability, scientific correctness or a package release.

Local measurement in the qualified MolSysSuite development environment:

```bash
python scripts/devguide_index.py --check
python -m coverage run --branch --source=scripts -m unittest discover -s tests -p test_reporting_protocol.py
python -m coverage xml -o coverage.xml
```

Work and acceptance evidence belong to `uibcdf/molsys-ai#3`, coordinated by
`uibcdf/molsyssuite#69`. A future change of executable ownership or reporting
scope needs its own review; it must not silently relabel this percentage as
coverage of the three runtime repositories.
