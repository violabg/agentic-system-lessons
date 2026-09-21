# 1. Orientarsi nel sistema canonical

[Corso](README.md) · [Slide](slides/lesson-01-introduzione.md) · [Caso guida](workshop-exercise.md)

**Domanda:** quali ruoli e procedure sono disponibili, e come passa il lavoro da una richiesta a una prova ispezionabile?

Un Agentic System è un insieme locale al repository di istruzioni, agent, skill, knowledge, gate, artifact e regole di validazione. Il suo valore è rendere il lavoro dell'agente ispezionabile e correggibile: una persona può vedere chi ha deciso, su quali fonti, con quale approvazione e quale risultato. Il [glossario canonical](system/canonical/CONTEXT.md) definisce questi termini; i [principi](principles.md) spiegano i controlli.

## Agent disponibili

| Agent | Quando usarlo, in breve | Fonte |
| --- | --- | --- |
| Planner | Preparare e far approvare un piano senza modificare codice | [Contratto Planner](system/canonical/agents/planner.agent.md) |
| Implementor | Eseguire un piano approvato, costruire, verificare e riferire | [Contratto Implementor](system/canonical/agents/implementor.agent.md) |
| Direct Implementor | Implementare da requisiti validati senza piano intermedio | [Contratto Direct Implementor](system/canonical/agents/direct-implementor.agent.md) |
| Ask | Rispondere a domande tecniche usando knowledge e riscontro mirato | [Contratto Ask](system/canonical/agents/ask.agent.md) |
| Integration Tester | Pianificare e realizzare prove di integrazione nel proprio mandato | [Contratto Integration Tester](system/canonical/agents/integration-tester.agent.md) |
| Knowledge Builder | Ricavare e salvare knowledge supportata da evidenza del repository | [Contratto Knowledge Builder](system/canonical/agents/knowledge-builder.agent.md) |
| Vision | Convertire un'immagine in un artifact leggibile dai ruoli successivi | [Contratto Vision](system/canonical/agents/vision.agent.md) |

## Skill disponibili

| Skill | Quando usarla, in breve | Fonte |
| --- | --- | --- |
| Plan User Story From Id | Recuperare una user story tramite ID per la pianificazione | [Skill canonical](system/canonical/skills/plan-user-story-from-id/SKILL.md) |
| Plan Bug From Id | Raccogliere un bug, esporre cause probabili e far scegliere la causa da pianificare | [Skill canonical](system/canonical/skills/plan-bug-from-id/SKILL.md) |
| User Story Analysis | Trovare ambiguità, gap e domande prima del design | [Skill canonical](system/canonical/skills/user-story-analysis/SKILL.md) |
| Business Logic Gap Detector | Cercare un difetto di logica con test che falliscono prima della correzione | [Skill canonical](system/canonical/skills/business-logic-gap-detector/SKILL.md) |
| Integration Test Knowledge Checklist | Definire la knowledge necessaria per test di integrazione del progetto | [Skill canonical](system/canonical/skills/integration-test-knowledge-checklist/SKILL.md) |
| Author Repo Skill | Creare o evolvere una procedura ripetibile del repository | [Skill canonical](system/canonical/skills/author-repo-skill/SKILL.md) |

Le [mappe di agent e skill](role-maps/README.md) aggiungono mandato, diagramma e handoff. Qui basta saper scegliere la voce pertinente; non si memorizzano i contratti.

## Il percorso principale, una volta intero

1. La richiesta arriva come user story o bug. La skill pertinente raccoglie il ticket e l'evidenza tramite ID.
2. Il [Planner](system/canonical/agents/planner.agent.md) apre una sessione nota, espone ciò che manca, seleziona knowledge, chiarisce i punti bloccanti, prepara il piano e chiede approvazione.
3. La sessione conserva ticket, chiarimenti, regole selezionate, piano e decisione. Il [contratto delle planning session](system/canonical/instructions/planning-sessions.instructions.md) definisce cosa deve sopravvivere alla chat.
4. L'implementazione parte in una **nuova conversazione con contesto pulito**. L'[Implementor](system/canonical/agents/implementor.agent.md) recupera la sessione e il piano approvato, applica le modifiche previste, esegue build, comandi e review, poi registra i risultati.
5. Se il piano contiene scenari di test unitari, l'Implementor chiede approvazione prima di crearli; quando autorizzati, li esegue e registra l'esito.

La [mappa approfondita](slides/reference-flow.md) espone ogni gate del percorso e collega i due contratti. [Direct Implementor](system/canonical/agents/direct-implementor.agent.md) resta un percorso alternativo con requisiti e design validati, ma senza documento di piano intermedio.

## Che cosa osservare

Nel [caso guida](workshop-exercise.md) la story “chiudere una richiesta solo con motivazione” sembra semplice. Il percorso rende visibile chi chiarisce che il vincolo vale anche per l'API, quale conoscenza governa il servizio, dove resta l'approvazione e quali prove sostengono il risultato. Le lezioni successive spiegano il principio dietro ciascuna scelta.
