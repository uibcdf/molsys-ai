# Vision

## Long-term goal

MolSys-AI should become a scientific copilot for MolSysSuite and for computational drug-design projects. It should help a researcher move from an objective expressed in scientific language to a transparent, validated and reproducible workflow.

Example long-term request:

> Prepare this protein, identify relevant pockets, characterize the best candidate, derive a pharmacophore hypothesis and visualize the evidence.

The copilot should be able to coordinate MolSysMT, TopoMT, PharmacophoreMT and MolSysViewer while exposing intermediate decisions and preserving all parameters and outputs.

## Product family

MolSys-AI is not a single chatbot. The same infrastructure should support several levels of access:

- public documentation assistants for each MolSysSuite tool,
- code and notebook assistants,
- an interactive CLI,
- live assistance inside MolSysViewer,
- the complete scientific copilot.

Users who cannot access the complete copilot should still benefit from derived tools such as documentation chatbots and code-generation assistants.

## Scientific contract

A useful answer is not enough. Scientific actions must produce durable artifacts:

- typed commands,
- structured observations,
- exact parameters,
- tool and model versions,
- generated files,
- decision history,
- Python or notebook exports,
- warnings and limitations.

The conversation is an interface. The reproducible workflow is the scientific product.

## Design-status vocabulary

These documents use the following labels:

- **Confirmed**: verified in an existing repository or accepted design record.
- **Remembered — verify**: recalled from prior design discussions but not yet verified.
- **Proposed**: a new architectural proposal.
- **Superseded**: retained for historical context but replaced by a newer design.

## Recovered ideas pending verification

- **Remembered — verify:** an interactive CLI experience comparable in spirit to Codex CLI.
- **Remembered — verify:** persistent user or environment profiles.
- **Remembered — verify:** token-based access to remote MolSys-AI services.
- **Remembered — verify:** multiple endpoints or execution environments such as local, laboratory and cluster profiles.

These ideas should be preserved for discussion without being represented as confirmed facts until repository archaeology is completed.
