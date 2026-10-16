[Corso](../README.md) › [Slide](README.md) › **Flusso Planner → Implementor**

# Flusso Planner → Implementor

Mappe dei ruoli: [Planner](../role-maps/agents/planner.md) · [Implementor](../role-maps/agents/implementor.md)

Questa pagina serve quando vuoi seguire **ogni gate**. Il [contratto del Planner](../system/canonical/agents/planner.agent.md) e il [contratto dell'Implementor](../system/canonical/agents/implementor.agent.md) restano la fonte normativa. La sequenza riassume il percorso ordinario con piano approvato. Durante l'esecuzione i gate numerati non si uniscono e non si saltano.

```mermaid
flowchart TD
    Ticket[Ticket ID o richiesta] --> Intake[Skill di intake<br/>ticket e artifact]
    Intake --> Planner[Planner<br/>sessione e gate 0-10]
    Planner --> Approval{Gate 11-12<br/>Piano approvato?}
    Approval -->|no| Planner
    Approval -->|sì| Record[Sessione di pianificazione<br/>piano, prove e approvazione]
    Record --> Fresh[Nuova conversazione<br/>contesto pulito, stessa sessione]
    Fresh --> Implementor[Implementor<br/>recupera il piano, gate 2-7]
    Implementor --> Tests{Gate 8<br/>Test unitari autorizzati?}
    Tests -->|sì| TestRun[Gate 9-11<br/>knowledge, test e verifica]
    Tests -->|no| Report[Gate 12<br/>report finale]
    TestRun --> Report
    Report --> Handoff[Handoff ispezionabile]
```

L'intake di una user story può usare [Plan User Story From Id](../role-maps/skills/plan-user-story-from-id.md); quello di un bug [Plan Bug From Id](../role-maps/skills/plan-bug-from-id.md). Le [regole delle sessioni di pianificazione](../system/canonical/instructions/planning-sessions.instructions.md) definiscono che cosa passa da una conversazione all'altra. Il [Direct Implementor](../role-maps/agents/direct-implementor.md) segue un percorso diverso, senza piano intermedio.

## Gate del Planner

| Gate | Scopo in una frase | Prova o decisione |
| --- | --- | --- |
| 0. Request Scope | Verificare che la richiesta sia pianificabile | Scope valido o rifiuto |
| 1. Session Activation | Creare o riprendere la sessione nota | ID e stato di sessione |
| 2. Process Request and Handle Artifacts | Risolvere piano e materiali di ingresso | Artifact del requisito e immagini, se presenti |
| 3. Requirement Decomposition | Esporre capacità, scenari e lacune senza inventare | Output in chat, non artifact |
| 4. Knowledge Catalog | Leggere MustHave e PerContext/PerComponent applicabili | Inventario normativo persistito |
| 5. Codebase cold start understanding | Pianificare una ricognizione mirata | Piano di esplorazione |
| 6. Codebase Reconnaissance | Verificare fatti e collocazione nel codice | Riferimenti concreti al codice |
| 7. Structured Interview | Chiedere solo chiarimenti che bloccano il piano | Risposte dello stakeholder |
| 8. Answer Validation | Verificare risposte e ambiguità residue | Risposte valide o nuova domanda |
| 9. Knowledge Alignment | Controllare il design contro ogni regola applicabile | Allineamento ed eventuale discovery mirata |
| 10. Plan Drafting | Scrivere il piano e gli scenari di coverage secondo schema | Bozza verificata del piano |
| 11. Validation Request | Presentare il piano alla review umana | Attesa di approvazione |
| 12. Decision Processing | Registrare approvazione o richiesta di modifica | Stato di approvazione e piano salvato |
| 13. Final Handoff | Consegnare solo il piano approvato | Sessione pronta per Implementor |

Fonte: [contratto Planner](../system/canonical/agents/planner.agent.md) · [schema del piano](../system/canonical/templates/plan-schema.md). I gate 1, 2, 7 e 11 attendono l'utente solo nelle condizioni definite dal contratto; gli altri avanzano da soli.

## Gate dell'Implementor

| Gate | Scopo in una frase | Prova o decisione |
| --- | --- | --- |
| 0. Process user request | Valutare la richiesta speciale Business Logic Gap Detector, se invocata | Scope della richiesta speciale |
| 1. Business logic gap triage and repair | Gestire test rossi e correzione stretta nel percorso speciale | Esiti e report |
| 2. Session-managed plan resolution | Risolvere e caricare un piano approvato nel percorso ordinario | Piano selezionato o blocco |
| 3. Session artifacts and plan intake | Leggere piano e artifact pertinenti | Scope di esecuzione noto |
| 4. Code implementation | Applicare le modifiche autorizzate dal piano | File modificati e report |
| 5. Build and fix loop | Compilare e correggere errori in scope | Esito build |
| 6. Execute required commands | Eseguire i comandi del piano | Output dei comandi |
| 7. Review and validate | Confrontare lavoro e piano | Review e limiti |
| 8. Optional unit-test request | Chiedere approvazione esplicita per i test opzionali | Sì, no o assenza di scenari |
| 9. Knowledge refresh | Rileggere convenzioni di test applicabili | Fonti aggiornate |
| 10. Unit-test scope resolution | Decidere file e scope dei test autorizzati | Piano di test mirato |
| 11. Unit-test implementation and verification | Scrivere, eseguire e triagiare i test | Risultati e report |
| 12. Final summary | Distinguere modifiche, prove e rischio residuo | Handoff all'utente |
| 13. Refinements | Gestire eventuale ulteriore richiesta nel mandato | Nuova decisione o chiusura |

Fonte: [contratto Implementor](../system/canonical/agents/implementor.agent.md) · [Business Logic Gap Detector](../role-maps/skills/business-logic-gap-detector.md). I gate 0–1 sono condizionali alla richiesta speciale; i gate 8–11 dipendono dagli scenari di coverage e dall'approvazione richiesta dal contratto. La tabella non modifica l'ordine o le condizioni runtime.

---

[← Precedente: riferimento rapido](reference-roster.md) · [↑ Slide](README.md) · [Torna al corso →](../README.md)
