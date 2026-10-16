[Corso](../README.md) › [Slide](README.md) › **Riferimento rapido**

# Riferimento rapido: agent e skill

Una guida alla scelta, non un elenco di elementi obbligatori per ogni repository. Il nome porta alla mappa del ruolo, con diagramma e descrizione breve; la mappa rimanda al file sorgente. Tutti i gate del percorso principale sono nel [flusso Planner → Implementor](reference-flow.md).

## Agent

| Agent | Usalo quando | Sorgente |
| --- | --- | --- |
| [Planner](../role-maps/agents/planner.md) | Serve un piano da far approvare prima di toccare il codice | [planner.agent.md](../system/canonical/agents/planner.agent.md) |
| [Implementor](../role-maps/agents/implementor.md) | Esiste un piano approvato da eseguire | [implementor.agent.md](../system/canonical/agents/implementor.agent.md) |
| [Direct Implementor](../role-maps/agents/direct-implementor.md) | Si implementa da requisiti e design validati, senza piano intermedio | [direct-implementor.agent.md](../system/canonical/agents/direct-implementor.agent.md) |
| [Ask](../role-maps/agents/ask.md) | Serve una risposta tecnica, senza modifiche | [ask.agent.md](../system/canonical/agents/ask.agent.md) |
| [Integration Tester](../role-maps/agents/integration-tester.md) | Servono test di integrazione nel suo ambito | [integration-tester.agent.md](../system/canonical/agents/integration-tester.agent.md) |
| [Knowledge Builder](../role-maps/agents/knowledge-builder.md) | Una regola del progetto va ricavata e salvata come knowledge | [knowledge-builder.agent.md](../system/canonical/agents/knowledge-builder.agent.md) |

## Skill

| Skill | Usala quando | Sorgente |
| --- | --- | --- |
| [Plan User Story From Id](../role-maps/skills/plan-user-story-from-id.md) | Si parte dall'ID di una user story | [SKILL.md](../system/canonical/skills/plan-user-story-from-id/SKILL.md) |
| [Plan Bug From Id](../role-maps/skills/plan-bug-from-id.md) | Si parte dall'ID di un bug e bisogna scegliere la causa da pianificare | [SKILL.md](../system/canonical/skills/plan-bug-from-id/SKILL.md) |
| [User Story Analysis](../role-maps/skills/user-story-analysis.md) | Bisogna rendere esplicite lacune e ambiguità prima del design | [SKILL.md](../system/canonical/skills/user-story-analysis/SKILL.md) |
| [Business Logic Gap Detector](../role-maps/skills/business-logic-gap-detector.md) | Si cercano test che falliscono per esporre un difetto reale | [SKILL.md](../system/canonical/skills/business-logic-gap-detector/SKILL.md) |
| [Integration Test Knowledge Checklist](../role-maps/skills/integration-test-knowledge-checklist.md) | Manca la knowledge per scrivere test di integrazione | [SKILL.md](../system/canonical/skills/integration-test-knowledge-checklist/SKILL.md) |
| [Author Repo Skill](../role-maps/skills/author-repo-skill.md) | Una procedura ripetibile va creata o aggiornata come skill | [SKILL.md](../system/canonical/skills/author-repo-skill/SKILL.md) |
| [Manage Work Item](../role-maps/skills/manage-work-item.md) | Si vuole creare o aggiornare un ticket, fuori dal percorso di pianificazione | [SKILL.md](../system/canonical/skills/manage-work-item/SKILL.md) |

---

[← Precedente: 6. Composizione e ciclo di vita](06-composizione-e-ciclo-di-vita.md) · [↑ Slide](README.md) · [Successivo: flusso Planner → Implementor →](reference-flow.md)
