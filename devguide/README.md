# MolSys-AI Development Guide

## Current project boundary

- `molsys-ai` — umbrella architecture and cross-repository coordination;
- `molsys-ai-server` — remote inference, MolSysSuite Software Knowledge, and documentation-assistant services;
- `molsys-ai-client` — lightweight typed remote-service SDK;
- `molsys-ai-agent` — local-first MolSysSuite specialist agent and scientific execution.

## Mission

MolSys-AI helps humans and higher-level agents understand and operate MolSysSuite. Durable value lies in grounded software knowledge, typed contracts, verified tool use, reproducible execution, and explicit provenance.

## First operational capability

The documentation chatbot is the first operational MolSys-AI capability. Preserve the capability during restructuring, not the legacy implementation.

The current RAG/corpus/symbol/recipe/citation stack should evolve as a reusable **MolSysSuite Software Knowledge Service** that can serve the chatbot, MolSys-AI Agent, and future clients.

## Non-negotiable boundaries

- MolSys-AI ≠ MOLI Agent.
- Server-side inference/Software Knowledge ≠ MolSysSuite execution.
- Client SDK ≠ specialist agent.
- Agent may use Client/Server but must not require that topology for every operation.
- Client remains usable without MolSysSuite.
- Agent does not import/own server RAG internals.
- Legacy code migrates by responsibility, not by directory.
- Working capabilities are preserved while implementations may evolve.

## Existing design material

Older design documents remain valuable inputs but may predate the current repository split. Ownership references should be progressively aligned rather than copied blindly.
