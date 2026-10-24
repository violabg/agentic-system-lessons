# Canonical Agentic System Context

The vocabulary of the canonical Agentic System under `system/canonical/`. Canonical roles, workflow instructions, skills, contracts and the runtime use these terms; update this glossary first, or in the same change, when one of them changes meaning.

This is not a knowledge index. The knowledge catalogue selects which project knowledge to read; this glossary keeps names and ownership boundaries stable.

## System

**Agentic System**
A repository-local operating system for AI coding work: roles, workflows, skills, the runtime, the session store, knowledge and validation rules.
_Avoid_: prompt collection, agent folder, generic automation bundle

**Runtime**
The local program (`runtime/`) that serves the workflows and owns the session store, the design and the mechanical gates. It replaces the company's private workflow server. Every operation it serves is a runtime capability token, and the token is also its command name.
_Avoid_: server, MCP, tool server

**Capability Token**
`#capability:<token>` — the name of an operation canonical text relies on, declared in `capabilities.yaml`. A runtime token is served by the runtime; a host token is provided by the client or an approved integration chosen at Bootstrap.
_Avoid_: tool name, MCP tool, integration

**Operation**
One of the abstract abilities a role is granted in its frontmatter: `read`, `search`, `write`, `terminal`, `question`, `runtime`, and delegation through its `delegates` list. Bootstrap maps operations to each client's tools. `runtime` grants the runtime commands and nothing else.
_Avoid_: tool, permission map

**Fallback**
The contract procedure an agent follows by hand when a runtime operation is unavailable. Gates run this way are recorded as instruction-only.
_Avoid_: degraded mode, workaround

## Roles

**Role**
A canonical agent contract in `agents/`. Its `invocation` is `user` (started by the developer as the main conversation of a session) or `delegate` (started only by another role).
_Avoid_: agent file, persona, mode

**Orchestrator**
The user role that drives the workflow the developer chooses. It follows the served instructions to the letter, never writes production code, and delegates the code and the verifications.
_Avoid_: planner, main agent, router

**Delegate**
A role the orchestrator starts in a fresh context with a fixed prompt that carries identifiers only (session, job, operation ids, knowledge bundle, image artifact names). The delegate reads its specification itself, reports back in the same conversation, and can be resumed by its delegate id; without resume the same role is started again with a complete correction prompt. The delegates are `code-implementor`, `design-verifier`, `implementation-verifier` and `documentation-reviewer`.
_Avoid_: subagent handoff, second conversation, helper agent

**Verdict**
The first line of a verifier report: exactly `VERDICT: PASS` or `VERDICT: FAIL`. Any other first line counts as `FAIL`.
_Avoid_: approval, score, status

## Workflow

**Workflow**
An ordered set of instructions the runtime serves for one workflow type: `DESIGN` (9 instructions), `FAST_IMPLEMENTATION` (7) or `DOCUMENTATION` (8). The developer always chooses the type explicitly.
_Avoid_: plan, pipeline, mode

**Instruction**
One served step of a workflow, headed `Instruction N/M.`. It names the operations the step may use. The orchestrator never sees a future instruction.
_Avoid_: gate, prompt, phase

**Halt Point**
An explicit stop inside an instruction (a review awaiting approval, an interview question, a required decision) where the orchestrator presents what is required and waits for the developer before requesting the next instruction.
_Avoid_: checkpoint, pause, confirmation

**Job**
One run of a workflow inside a session, identified by a job id. A DESIGN job owns or reuses a design.
_Avoid_: task, ticket, run

**Session**
The durable working record of one piece of work: memory, event log, artifacts, jobs and designs under the session store. Created or resumed only on the developer's request.
_Avoid_: planning session, conversation, chat history

**User Instruction Register**
The session artifact `user_instruction_register_<jobId>`: the developer's particular requests from the first prompt, recorded verbatim with their effects as conditions. The runtime appends it to every instruction after the first.
_Avoid_: preferences, prompt notes

**R-Lock**
The session artifact `requirement_R_lock`: the functional requirement R, byte-for-byte. R is read from it, never from conversation recall.
_Avoid_: requirement summary, story copy

## Design

**Design**
The structured artifact a DESIGN job builds and the developer approves: obligations, open points, overview, file references, decisions and the path (contracts, APIs, filesystem, operations), plus the iteration history. Rendered as a review document.
_Avoid_: implementation plan, plan file, spec document

**Obligation**
`O#` — one atomic, independently falsifiable behavior R imposes (or the developer decided, origin `Developer`), with its necessary elements `O#.k`.
_Avoid_: requirement line, acceptance criterion, task

**Element**
`O#.k` — a necessary condition of an obligation that demands a distinct realization: `Direction`, `Conjunct`, `Quantifier`, `Guard`, `Effect`, `StateSemantics` or `Exception`.
_Avoid_: sub-requirement, bullet

**Open Point**
`OP#` — an internal question the design raises. Open points become decisions; the developer never sees their ids.
_Avoid_: question for the user, blocker

**Decision**
`D#` — a settled answer to an open point: the chosen option first plus comparable alternatives. A blocking decision is highlighted for the developer's judgment at the review.
_Avoid_: choice log, ADR

**Operation (design)**
`IM#` — one ordered unit of implementation work in the design path, with its kind, instructions that name every element it carries out as `{{O#.k}}`, and its failure arms (branches, negatives, exceptions).
_Avoid_: step, task, ticket

**Iteration**
`IT#` — one implementation round recorded in the design history: the request, the files changed (computed by the runtime), the verifications, the blocks and the notes.
_Avoid_: sprint, attempt

**Approval**
The developer's verdict on the design, recorded by `#capability:design-approve` and refused while a mechanical check fails. It is permanent; later modifications are marked as made after approval.
_Avoid_: sign-off by the agent, auto-approval

## Knowledge

**Knowledge Catalogue**
The tiered list of project knowledge documents (`MustHave`, `PerContext`, `PerComponent`) with file ids valid for the current index. Every `MustHave` document is read in full.
_Avoid_: glossary, documentation index, bulk-load list

**Knowledge Bundle**
The merged rules the orchestrator passes, unchanged, to the implementor and the verifier of the same step.
_Avoid_: knowledge dump, summary
