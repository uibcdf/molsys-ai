The offline reporting guard lives in `devguide_reports.py` and the generated
queue/archive index command in `devguide_index.py`. Run
`python scripts/devguide_index.py --check` from the repository root after
changing a durable report. See `devguide/reporting_protocol.md`.

The reporting workflow measures these Python governance scripts with the
existing reporting tests. The source scope, trusted-main publisher and local
measurement commands are documented in `devguide/coverage_reporting.md`.
