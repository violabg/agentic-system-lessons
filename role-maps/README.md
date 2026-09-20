# Mappe Visuali Dei Ruoli

[Torna alla lettura principale](../README.md) · [Slide](../slides/README.md) · [Principi](../principles.md)

Mappe didattiche di mandato, confine e handoff. Non prescrivono ruoli, nomi o tool per un repository target.

## Come Leggerle

Ogni pagina contiene una lettura rapida e un flusso Mermaid dettagliato. Il flusso usa sempre la stessa catena:

```mermaid
flowchart LR
	Input[Input] --> Gate{Gate e criterio di uscita}
	Gate -->|non soddisfatto| Stop[Stop, rifiuto o chiarimento]
	Gate -->|soddisfatto| Artifact[Artifact o output]
	Artifact --> Handoff[Handoff al prossimo ruolo]
```

La tabella sotto ogni diagramma spiega quattro domande: quale decisione protegge il gate, quale prova produce, chi riceve l'handoff e cosa accade se il criterio non e soddisfatto. Seguire le frecce non assegna autorita: il contratto canonical collegato resta la fonte di verita.

## Agent

- [Ask](agents/ask.md)
- [Implementor](agents/implementor.md)
- [Direct Implementor](agents/direct-implementor.md)
- [Integration Tester](agents/integration-tester.md)
- [Knowledge Builder](agents/knowledge-builder.md)
- [Planner](agents/planner.md)
- [Vision](agents/vision.md)

## Skill

- [Author Repo Skill](skills/author-repo-skill.md)
- [Business Logic Gap Detector](skills/business-logic-gap-detector.md)
- [Integration Test Knowledge Checklist](skills/integration-test-knowledge-checklist.md)
- [Plan Bug From Id](skills/plan-bug-from-id.md)
- [Plan User Story From Id](skills/plan-user-story-from-id.md)
- [User Story Analysis](skills/user-story-analysis.md)

## Quale Percorso Scegliere?

| Esigenza | Percorso | Evidenza prima di modificare |
| --- | --- | --- |
| Capire o spiegare | [Ask](agents/ask.md) | Fonti verificabili; nessuna implementazione implicita. |
| Preparare un piano da approvare e passare di mano | [Planner](agents/planner.md) → [Implementor](agents/implementor.md) | Piano approvato e scope leggibile. |
| Implementare dai requisiti senza documento di piano | [Direct Implementor](agents/direct-implementor.md) | Requisiti, regole e decisioni di design validate nei gate. |
| Produrre prove di integrazione | [Integration Tester](agents/integration-tester.md) | Intake e piano di test propri del ruolo; nessun handoff automatico che salti i suoi gate. |

La scelta dipende da autorità e output richiesti, non soltanto dalla dimensione del task. Direct Implementor è disponibile nel catalogo dei template; la sua presenza non significa che ogni installazione lo generi o che sostituisca il Core System.
