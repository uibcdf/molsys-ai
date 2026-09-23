# MolSys-AI Development Guide

## Current project boundary

MolSys-AI is the MolSysSuite-specialized AI subsystem. The project is organized as:

- `molsys-ai` — umbrella architecture and cross-repository coordination;
- `molsys-ai-server` — remote inference and software-knowledge services;
- `molsys-ai-client` — lightweight typed remote-service SDK;
- `molsys-ai-agent` — MolSysSuite specialist agent and local scientific execution.

Older documents in this directory were written before this repository split. Their scientific/tooling ideas remain useful, but ownership references such as “local copilot belongs to molsys-ai” should now be read as “MolSys-AI Agent belongs to molsys-ai-agent”.

## Mission

MolSys-AI helps humans and higher-level agents understand and operate MolSysSuite. Natural language is one input modality; durable value lies in grounded software knowledge, typed contracts, verified tool use, reproducible execution, and explicit provenance.

## Non-negotiable boundaries

- MolSys-AI ≠ MOLI Agent.
- Server-side inference/software knowledge ≠ local MolSysSuite execution.
- Client SDK ≠ specialist agent.
- The agent may use the client; the client must remain usable without MolSysSuite.
- Legacy code is migrated by responsibility, not by directory.
- Working server behavior must be preserved during extraction.

## Existing design material

The existing VISION, ARCHITECTURE, protocol, session, tool, provenance, CLI, viewer, policy, and evaluation documents remain design inputs. They should be progressively aligned with the current four-repository ownership model rather than rewritten or discarded wholesale.
