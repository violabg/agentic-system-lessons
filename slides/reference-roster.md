# Riferimento rapido: agent e skill

[Indice slide](README.md) · [Mappe complete](../role-maps/README.md)

Questa è una mappa di scelta, non un elenco di elementi obbligatori per ogni repository. Ogni voce porta alla sua [mappa didattica](../role-maps/README.md) e al contratto canonical. I dettagli dei gate del percorso principale sono nel [flusso approfondito](reference-flow.md).

## Agent

| Agent | Usalo quando | Approfondisci |
| --- | --- | --- |
| Planner | Serve un piano da far approvare prima del codice | [Mappa](../role-maps/agents/planner.md) · [Contratto](../system/canonical/agents/planner.agent.md) |
| Implementor | Esiste un piano approvato da eseguire | [Mappa](../role-maps/agents/implementor.md) · [Contratto](../system/canonical/agents/implementor.agent.md) |
| Direct Implementor | Si implementa da requisiti e design validati senza piano intermedio | [Mappa](../role-maps/agents/direct-implementor.md) · [Contratto](../system/canonical/agents/direct-implementor.agent.md) |
| Ask | Occorre una risposta tecnica senza modifiche | [Mappa](../role-maps/agents/ask.md) · [Contratto](../system/canonical/agents/ask.agent.md) |
| Integration Tester | Servono prove di integrazione nel suo scope | [Mappa](../role-maps/agents/integration-tester.md) · [Contratto](../system/canonical/agents/integration-tester.agent.md) |
| Knowledge Builder | Una regola di progetto va ricavata e salvata come knowledge | [Mappa](../role-maps/agents/knowledge-builder.md) · [Contratto](../system/canonical/agents/knowledge-builder.agent.md) |
| Vision | Una immagine va trasformata in evidenza strutturata | [Mappa](../role-maps/agents/vision.md) · [Contratto](../system/canonical/agents/vision.agent.md) |

## Skill

| Skill | Usala quando | Approfondisci |
| --- | --- | --- |
| Plan User Story From Id | Si parte dall'ID di una user story | [Mappa](../role-maps/skills/plan-user-story-from-id.md) · [Contratto](../system/canonical/skills/plan-user-story-from-id/SKILL.md) |
| Plan Bug From Id | Si parte dall'ID di un bug e si deve scegliere la causa da pianificare | [Mappa](../role-maps/skills/plan-bug-from-id.md) · [Contratto](../system/canonical/skills/plan-bug-from-id/SKILL.md) |
| User Story Analysis | Occorre rendere espliciti gap e ambiguità prima del design | [Mappa](../role-maps/skills/user-story-analysis.md) · [Contratto](../system/canonical/skills/user-story-analysis/SKILL.md) |
| Business Logic Gap Detector | Si cercano test rossi che espongano una debolezza reale | [Mappa](../role-maps/skills/business-logic-gap-detector.md) · [Contratto](../system/canonical/skills/business-logic-gap-detector/SKILL.md) |
| Integration Test Knowledge Checklist | Manca knowledge applicabile ai test di integrazione | [Mappa](../role-maps/skills/integration-test-knowledge-checklist.md) · [Contratto](../system/canonical/skills/integration-test-knowledge-checklist/SKILL.md) |
| Author Repo Skill | Una procedura ripetibile va creata o aggiornata come skill | [Mappa](../role-maps/skills/author-repo-skill.md) · [Contratto](../system/canonical/skills/author-repo-skill/SKILL.md) |
