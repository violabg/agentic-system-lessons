# Canonical Agentic System Context

This file is the vocabulary glossary for the authored canonical Agentic System under `system/canonical/`. Canonical agents, skills, and docs should use these terms consistently before choosing role names, gates, artifacts, or public-safe wording.

This is not a knowledge index. Use a knowledge index to select which repository knowledge files to load. Use this context glossary to keep names and ownership boundaries stable.

## Terms

**Agentic System**:
A repository-local operating system for AI coding work: instructions, agents, skills, gates, artifacts, knowledge docs, validation rules, and handoff contracts.
_Avoid_: prompt collection, agent folder, generic automation bundle

**Canonical Agent**:
An authored private agent contract in `system/canonical/agents/` that preserves a workflow role after cleanup and adaptation.
_Avoid_: raw source agent, public agent, company-prefixed agent

**Canonical Skill**:
An authored private workflow skill in `system/canonical/skills/` or a Lab-owned public-safe skill source under `public-package/skills/` when classified for export.
_Avoid_: raw prompt copy, one-off chat prompt, direct upstream workflow

**Context Glossary**:
A `CONTEXT.md` file that defines stable domain or system vocabulary, ownership boundaries, and terms to avoid. Agents use it to name things consistently.
_Avoid_: knowledge index, exhaustive documentation, implementation guide

**Knowledge Index**:
A compact routing artifact that tells agents which knowledge files to read for a task and when to skip them.
_Avoid_: glossary, full documentation set, bulk-load checklist

**Gate**:
A named checkpoint where an agent must satisfy evidence, approval, scope, handoff, or validation conditions before continuing.
_Avoid_: informal reminder, optional checklist, hidden preference

**Artifact**:
A durable file or structured record that preserves requirements, questions, decisions, plans, validations, handoffs, or review findings.
_Avoid_: chat-only state, temporary reasoning, unrecorded approval

**Work Item Integration**:
An optional generalized connection to an issue, ticket, planning, or session system supplied by the target repository.
_Avoid_: mandatory private tracker, hard-coded vendor workflow, company-only tool

**Planning Session**:
A single isolated working record created by the Planner for one bug or user-story ID. The Planner chooses the configured session root during bootstrap, creates or resumes only the current session folder, and never enumerates or reads other session folders.
_Avoid_: shared session scan, tracker-creation session, repository-mandated session path

**Work Item Creation**:
A separate workflow that creates a bug or user story through a configured tracker adapter or saves a local Markdown record, then returns the resulting ID without creating a planning session.
_Avoid_: implicit planning, session creation during ticket creation

**Public-Safe Export**:
Material that has been classified, cleaned, versioned, and leakage-checked before leaving Lab staging.
_Avoid_: raw source publication, private canonical dump, unreviewed release

## Flow Rule

When canonical agents or skills define or change workflow language, update this glossary first or in the same batch. Then update teaching and public-safe material only after deciding whether the vocabulary is private canonical, teaching-only, public-safe generic, ignored source noise, or needs maintainer judgment.