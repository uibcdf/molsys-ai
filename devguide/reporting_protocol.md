# MolSys-AI reporting protocol

MolSys-AI implements `uibcdf/molsyssuite`'s `devguide/reporting_protocol.md`
for the umbrella repository. Report subsystem contracts and coordination here;
server, client and agent implementation issues belong to their owning child
repositories. MolSysSuite and MOLI retain the higher-level boundaries defined
by `MOLSYS_AI_GUIDE.md`.

Open `uibcdf/molsys-ai#<number>` before creating a durable report. Copy
`devguide/templates/report.md`, remove `severity` for proposals, and write
analysis and evidence in the document. The issue holds public state and
settled facts.

- `devguide/pending_bugs/` contains open subsystem defects;
- `devguide/pending_proposals/` contains open subsystem proposals;
- `devguide/archive/` permanently retains resolved, withdrawn and superseded
  reports.

Broader architecture and migration material in `devguide/` remains outside
the issue queue until split into independently closable themes.

To close a report, set its closed status and date, cite a relevant durable
`guard` or `normative` document, move it to the archive and regenerate the
indexes. Close the GitHub issue with the decision, evidence and archive path.
Preserve archived claims; append a dated correction if one later proves false.

The default guard is a pytest selector under `tests/` or `devtools/tests/`.
The offline validator checks that a named test function, class method or
module exists. A reviewer must also check relevance to the reported
mechanism. This repository uses the Python standard library for its
reporting scripts and workflow; that does not give the umbrella a
`python-package` capability or package-release obligation.

Run these offline checks after changing a report:

```bash
python scripts/devguide_index.py
python scripts/devguide_index.py --check
python -m unittest discover -s tests -p test_reporting_protocol.py
```

The reporting-governance workflow runs the index check and reporting tests
without package or scientific dependencies.
