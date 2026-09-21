# Lezione 1: orientarsi nel sistema

[Indice](README.md) · [Lettura](../lesson-01-introduzione.md) · [Tutti gli agent e le skill](reference-roster.md)

## 1. Perché esiste

Un sistema agentico rende il lavoro **ispezionabile e correggibile**.

Chi decide? Che cosa legge? Quale prova permette di continuare? Che cosa resta per il prossimo ruolo?

---

## 2. I ruoli principali

[Planner](../system/canonical/agents/planner.agent.md): prepara e fa approvare il piano.

[Implementor](../system/canonical/agents/implementor.agent.md): esegue il piano e registra le prove.

[Direct Implementor](../system/canonical/agents/direct-implementor.agent.md): percorso alternativo senza piano intermedio.

---

## 3. Gli altri agent

[Ask](../system/canonical/agents/ask.agent.md): Q&A tecnico. [Integration Tester](../system/canonical/agents/integration-tester.agent.md): prove di integrazione.

[Knowledge Builder](../system/canonical/agents/knowledge-builder.agent.md): knowledge del repository. [Vision](../system/canonical/agents/vision.agent.md): evidenza visiva strutturata.

[Elenco completo con quando usarli](reference-roster.md).

---

## 4. Le skill disponibili

Intake: [Plan User Story From Id](../system/canonical/skills/plan-user-story-from-id/SKILL.md), [Plan Bug From Id](../system/canonical/skills/plan-bug-from-id/SKILL.md), [User Story Analysis](../system/canonical/skills/user-story-analysis/SKILL.md).

Altri bisogni: [Business Logic Gap Detector](../system/canonical/skills/business-logic-gap-detector/SKILL.md), [Integration Test Knowledge Checklist](../system/canonical/skills/integration-test-knowledge-checklist/SKILL.md), [Author Repo Skill](../system/canonical/skills/author-repo-skill/SKILL.md).

[Quando usarle](reference-roster.md).

---

## 5. Il percorso in una riga

Ticket ID → skill di intake → Planner → chiarimenti e knowledge → piano approvato nella sessione → nuova conversazione → Implementor recupera piano e artifact → modifica, build, review, test autorizzati → report.

[Flusso e gate dettagliati](reference-flow.md).

---

## 6. Il caso guida

“Chiudere una richiesta solo con motivazione” lascia aperte decisioni su API, spazi vuoti e richieste già chiuse.

Il sistema rende quelle decisioni visibili prima della modifica. [Traccia fittizia](../workshop-exercise.md).

---

## 7. Che cosa studieremo

Ogni passaggio controlla un failure mode: requisito inventato, fonte sbagliata, autorità implicita, approvazione persa, prova insufficiente.

Le lezioni successive spiegano il principio dietro il passaggio. [Principi](../principles.md).
