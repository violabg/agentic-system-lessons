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
One of the abstract abilities a role is granted in its frontmatter: `read`, `search`, `write`, `terminal`, `question`, `runtime`, and delegation through its `delegates` list. Bootstrap maps operations to each client's tools. `runtime` grants the runtime commands and nothing else. A role body names an operation as `#operation:<op>` (for example `#operation:question`, the role's question tool); it runs through the client's own tools and is never a runtime command.
_Avoid_: tool, permission map

**Fallback**
The contract procedure an agent follows by hand when a runtime operation is unavailable. Gates run this way are recorded as instruction-only.
_Avoid_: degraded mode, workaround

## Roles

**Role**
A canonical agent contract in `agents/`. Its `invocation` is `user` (started by the developer as the main conversation of a session) or `delegate` (started only by another role).
_Avoid_: agent file, persona, mode

**Orchestrator**
The user role that drives the workflow the developer chooses. It follows the served instructions to the letter. In DESIGN it never writes production code: it delegates the code to the implementor and reviews every work unit itself. In FAST_IMPLEMENTATION it implements the requirement directly, with its build and tests.
_Avoid_: planner, main agent, router

**Delegate**
A role the orchestrator starts in a fresh context with a fixed prompt that carries identifiers only (session, job, operation ids, image artifact names, and for a verifier the knowledge bundle). The delegate reads its specification itself, reports back in the same conversation, and can be resumed by its delegate id; without resume the same role is started again with a complete correction prompt. The delegates are `code-implementor`, `design-verifier`, `implementation-verifier` and `documentation-reviewer`. Since 3.0.3 the served steps start only `code-implementor` and `documentation-reviewer`; the two verifier roles are still shipped upstream and kept.
_Avoid_: subagent handoff, second conversation, helper agent

**Verdict**
The first line of a verifier report: exactly `VERDICT: PASS` or `VERDICT: FAIL`. Any other first line counts as `FAIL`.
_Avoid_: approval, score, status

## Workflow

**Workflow**
An ordered set of instructions the runtime serves for one workflow type: `DESIGN` (11 instructions), `FAST_IMPLEMENTATION` (5) or `DOCUMENTATION` (8). The developer always chooses the type explicitly.
_Avoid_: plan, pipeline, mode

**Instruction**
One served step of a workflow, headed `Instruction N/M.`. It names the operations the step may use. The orchestrator never sees a future instruction.
_Avoid_: gate, prompt, phase

**Part**
One slice of a long runtime answer (an instruction, knowledge, the snapshot, the verification view, or any other response longer than the limit, served from a stored copy), no larger than the client's limit and starting at a whole unit where one fits. It ends by naming the call that returns the next part, run as a shell command of its own; every part is read before acting.
_Avoid_: page, chunk, truncated output

**Halt Point**
An explicit stop inside an instruction (a review awaiting approval, an interview question, a required decision) where the orchestrator presents what is required and waits for the developer before requesting the next instruction.
_Avoid_: checkpoint, pause, confirmation

**Job**
One run of a workflow inside a session, identified by a job id. A DESIGN job owns or reuses a design; FAST_IMPLEMENTATION and DOCUMENTATION jobs have none.
_Avoid_: task, ticket, run

**Session**
The durable working record of one piece of work: memory, event log, artifacts, jobs and designs under the session store. Created or resumed only on the developer's request.
_Avoid_: planning session, conversation, chat history

**User Instruction Register**
The session artifact `user_instruction_register_<jobId>`: the developer's particular requests from the first prompt, recorded verbatim with their effects as conditions. The runtime appends it to every instruction after the first.
_Avoid_: preferences, prompt notes

## Design

**Design**
The structured artifact a DESIGN job builds and the developer approves: obligations, overview, file references, knowledge references, decisions and the path (contracts, APIs, filesystem, operations), plus the iteration history. Rendered as a review document.
_Avoid_: implementation plan, plan file, spec document

**Obligation**
`O#` — one atomic, independently falsifiable behavior R imposes (or the developer decided, origin `Developer`), written as one closed claim with its class, boundaries and source in R. The obligations are the requirement of the job: every later step reads R from them, never from a separate copy of R. Since 3.0.3 an obligation has no elements.
_Avoid_: requirement line, acceptance criterion, task, requirement lock, element

**Decision**
`D#` — a fork the design settled from the accumulated context: the chosen option first plus comparable alternatives. A highlighted decision (`highlight`, formerly `blocking`) is where the developer's judgment is most needed: it is read first at the review, and one about the situation is not realized by code. A breaking-change decision records a break the design introduces (a contract signature, a public API, a persisted schema) instead of where the question came from.
_Avoid_: choice log, ADR, open point

**Operation (design)**
`IM#` — one ordered unit of implementation work in the design path: a semantic unit with every file it needs, its kind (`Production`, `Documentation` or `Testing`), complete instructions an implementor can execute from an empty context, the obligations, contracts, APIs and decisions it realizes, the knowledge and file references it consumes (or the reason it needs none), and its failure arms (branches, negatives, exceptions).
_Avoid_: step, task, ticket

**Batch**
When an operation is served: the production batch, then the documentation batch, without the developer's selection. A `Testing` operation, or one with destructive side effects, is served only when the developer selects it. The plan keeps the order it was declared in, and `dependsOn` is the only precedence constraint.
_Avoid_: priority, phase, weight class

**Work Unit**
What one implementor delegation realizes: the operations the runtime serves it one at a time (the production and documentation batches, or the operations the developer selected), ending at a terminator — `batch-complete` or `complete` — and reviewed by the orchestrator as one unit. An operation is `Implemented` when the implementor closes it and `Completed` once the orchestrator's review of the work unit passes.
_Avoid_: sprint, task list, whole plan

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

**Knowledge Grounding**
The knowledge a design is judged against: every `MustHave` document, every document read in the design's session and every document the design names. The verification view lists it, with the `knowledge-read` call that reads it, so the verifier reads it.
_Avoid_: cited knowledge, references

**Knowledge Reference**
`kid` — one prescription of a project knowledge document the design applies: the document's file id, the inclusive line range that carries it, and a scope (`Production` or `Test`). Every knowledge read in a job with a design is followed by registering its applicable prescriptions, which also bind the design's own sections; an operation lists the kids it needs, and the runtime serves their text with the operation.
_Avoid_: citation, whole-file reference, knowledge link

**Scope**
Whether a knowledge reference or a file reference governs the production code (`Production`, the default) or the tests (`Test`).
_Avoid_: tier, category

**Knowledge Bundle**
The merged rules of the project knowledge that govern one implementation. In FAST_IMPLEMENTATION the orchestrator builds it and implements from it itself. In DESIGN no bundle goes into a delegate prompt: the implementor receives the knowledge references of each served operation.
_Avoid_: knowledge dump, summary
