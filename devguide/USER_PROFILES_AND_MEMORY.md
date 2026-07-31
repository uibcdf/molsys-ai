# User Profiles and Memory

## Status

This document preserves several remembered ideas without assuming what “profiles” or “tokenized profiles” meant in earlier designs. Repository archaeology must verify the original intent.

## Separate concepts

### Connection profile

Selects endpoint, model defaults, credential reference and network behavior.

### Execution profile

Describes local, workstation, laboratory or cluster execution policy and available resources.

### Identity and authorization profile

Represents authenticated identity, organization, roles, quotas and permitted services. It is controlled by server-side authorization, not hidden prompts.

### Preference profile

Stores explicit user preferences such as verbosity, default representations, approval mode and export format. Preferences must be inspectable and editable.

### Scientific working profile

A possible future layer for declared expertise, preferred terminology or recurring scientific conventions. It must be transparent, optional and never silently substitute for project evidence.

### Project memory

Durable facts, decisions, aliases, workflows and artifacts belonging to one scientific project.

### Conversation memory

Summaries used to continue dialogue. It is separate from scientific provenance and may be disabled or deleted without invalidating workflows.

## “Tokenized profile” ambiguity

The phrase may have referred to authentication tokens, compressed context tokens, encoded user preferences or another mechanism. Until verified, no architecture decision should treat one interpretation as historical fact.

## Rules

- Secrets are not profile content; profiles reference secure secret stores.
- Memory is scoped and inspectable.
- Project state never leaks between projects implicitly.
- Inferred personal traits are not stored as scientific profile data.
- Deleting conversational memory must not delete scientific commands or artifacts.
- Any model-facing personalization is visible in effective context or policy summaries.

## Initial recommendation

Implement connection and execution profiles first. Defer scientific working profiles and long-term conversational memory until requirements, privacy policy and evaluation criteria are clear.