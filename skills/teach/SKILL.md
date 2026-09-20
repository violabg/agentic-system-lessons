---
name: teach
version: 1
summary: Maintain the seven-lesson enterprise agentic-system curriculum from canonical evidence.
disable-model-invocation: true
argument-hint: "What teaching material or curriculum change is needed?"
---

# Teach Enterprise Agentic Systems

[Torna alla lettura principale](../../README.md) · [Principi](../../principles.md) · [Baseline](../../core-principles-baseline.md)

Use this skill to create, revise, or review material under `teaching/`. The course teaches transferable controls for enterprise agentic systems, not a copied agent roster, private workflow, or generic learning workspace.

## Course Contract

Use the [introduction](../../introduction.md) to frame why the system exists, expected learning outcomes, limits, and transfer to the learner's repository. Teach controlled, verifiable work rather than deterministic models; relevant maintained knowledge rather than maximum context; executable validation rather than self-confidence; and refinement from observed daily-work failures rather than a universal recipe.

The curriculum has seven 45-minute lessons:

1. Roles and bounded authority.
2. Selective, governed knowledge.
3. Gates and human control.
4. Durable artifacts, provenance, and ownership.
5. Validation as evidence.
6. System composition and lifecycle.
7. Bootstrap and controlled adaptation.

Every lesson must contain an objective of control, a failure mode, a short evidence example, a Mermaid diagram when relationships need clarification, and a short decision exercise. A demo repository may demonstrate an observable control but must not become the course structure or a universal prescription.

## Scope and Sources

- Write only under `teaching/`.
- Read `system/canonical/CONTEXT.md`, canonical agents, skills, instructions, and public-safe material as required by the proposed change.
- Treat `teaching/core-principles-baseline.md` and `teaching/principles.md` as the teaching source of truth.
- Teach the canonical system and the public-safe Bootstrap as the course examples; keep internal Lab workflows and origins out of course material.
- Do not modify any source outside `teaching/`.

## Workflow

### Gate 0: Trigger and Classification

Confirm the request affects a durable principle, lesson objective, exercise, diagram, facilitator guidance, demo, or curriculum maintenance contract. Classify the impact as one or more of: principle, course map, facilitator guidance, slides, demo, system map, or skill contract. If no durable teaching impact exists, report a no-op.

### Gate 1: Canonical Evidence

Identify the smallest canonical or public-safe source that proves the proposed teaching claim. Separate stable principle from local implementation detail. Reject a claim supported only by chat memory or a demo repository.

Check that teaching simplifications retain mandatory knowledge, ordered gates, approvals, validation requirements, capability guards, and role-specific prohibitions. Separate greenfield workflow design from Bootstrap's approved-slot adaptation and preservation of non-slot canonical content. A lesson cannot authorize weakening an adopted contract.

### Gate 2: Curriculum Placement

Map lesson-specific changes to exactly one primary lesson. Course-wide motivation and learning outcomes belong in `introduction.md` with links to the existing principle owners, not an eighth lesson. A related lesson can receive a cross-reference, but do not duplicate the principle. If a new principle is proposed, update `core-principles-baseline.md` and `principles.md` before all derived materials.

### Gate 3: Teach the Control

For every changed lesson, state the failure mode, control objective, learner decision, evidence sample, applied exercise, expected reasoning, and transfer question for a different repository. For Bootstrap material, also state what the learner must inspect in the generated system, which assumption needs repository evidence, and when manual correction is warranted.

Include an individual prediction before explanation, a worked example and plausible counterexample, and an evidence-based revision at the end. Gradually remove exercise scaffolding without weakening runtime controls. Keep these activities inside the existing 45-minute budget and assess transfer using an observed task outcome rather than terminology recall.

Use Mermaid when it explains a relationship or flow better than prose. Do not add diagrams as decoration.

### Gate 4: Synchronize Surfaces

Update the applicable files among `README.md`, `introduction.md`, `principles.md`, `core-principles-baseline.md`, `facilitator-guide.md`, `slide-outline.md`, `live-demo-script.md`, and `system-map.md`. Keep the seven lessons aligned. Do not turn a 45-minute lesson into a file tour or a command tutorial.

### Gate 5: Validate

Check Markdown diagnostics, links, Mermaid fences, lesson numbering, and public-safe language. Confirm that every changed claim has canonical or public-safe evidence and that the `teach` contract still matches the curriculum.

## Release Alignment And Learner Checks

When releases change role boundaries, update the affected role map and compare it with adjacent roles. Propagate changed assumptions to slides, exercises, facilitator guidance, demos, and the system map. Record source versions and links in the teaching baseline; distinguish catalog availability from default installation.

For Direct Implementor, preserve the distinction between validated requirements without an intermediate plan and Implementor's approved-plan handoff. Teach the retained gates, session evidence, prohibition on creating unit or integration tests, and explicit residual verification needs. Do not turn a role-specific restriction into a universal engineering principle.

Use the shared [workshop exercise](../../workshop-exercise.md) to connect lessons. Keep expected reasoning and a small evidence-based rubric available to facilitators. Teach portability through explicitly selected environments, versioned official sources, complete canonical copies and loading adapters, approved operation bindings and verified prerequisites. Separate deterministic preservation checks from native runtime evidence; retain per-environment/role/operation verification states and honest v1-to-v2 migration. For plan-schema changes, teach navigable structure and branch-specific coverage without calling planned scenarios executed tests. Preserve source ownership and shared consumers during maintenance, and keep model choices conditional on the selected role and target-platform support.

[Torna alla lettura principale](../../README.md)
