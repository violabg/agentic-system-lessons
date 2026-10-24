[Corso](../../README.md) › [Mappe di agent e skill](../README.md) › **Plan User Story From Id**

# Plan User Story From Id

**File sorgente:** [skills/plan-user-story-from-id/SKILL.md](../../system/canonical/skills/plan-user-story-from-id/SKILL.md)

## In 30 secondi

**Fa:** raccoglie da un user story work item una rappresentazione completa e leggibile dal Planner, delegando il recupero dell'evidenza a un subagent.

**Non fa:** non progetta la soluzione e non sostituisce il workflow del Planner; se manca l'ID, si ferma e lo chiede.

**Consegna:** artifact di sessione con descrizione, acceptance criteria, commenti, immagini e relazioni, pronto per il gate di pianificazione.

## Flusso, controlli e artifact

```mermaid
flowchart TD
    StoryId[Input: user story ID] --> G0{ID presente?}
    G0 -->|no| Ask[Output: chiedi work item ID]
    G0 -->|sì| Delegate[Passo: delega raccolta<br/>al subagent]
    Delegate --> Retrieve[Recupera descrizione, criteri,<br/>commenti, immagini e relazioni]
    Retrieve --> Artifact[Artifact: work item in Markdown<br/>con contenuto preservato]
    Artifact --> G1{Controllo didattico<br/>campi richiesti raccolti?}
    G1 -->|no| Delegate
    G1 -->|sì| Handoff[Handoff: Planner legge artifact<br/>e avvia il proprio Gate 0]
    Handoff --> Plan[Artifact successivo: piano<br/>solo dopo workflow Planner]
```

## Lettura del diagramma

| Passaggio o controllo | Decisione che protegge | Artifact o output | Handoff successivo |
| --- | --- | --- | --- |
| ID | Esiste un work item da recuperare? | ID valido o richiesta all'utente | Raccolta |
| Raccolta delegata | L'evidenza viene recuperata senza progettare? | Descrizione, commenti, criteri, immagini e relazioni | Controllo dei campi richiesti |
| Evidenza | Tutti i campi richiesti sono disponibili e leggibili? | Artifact work item completo | Planner |
| Handoff | Chi può trasformare prova in design? | Artifact di sessione | Planner, poi Implementor dopo approvazione |

**Da ricordare:** questa skill separa il recupero dal giudizio di design. Il Planner riceve una prova completa, non un piano implicito.

## Prove raccolte dal work item

La mappa sopra descrive il contratto canonical. Tracker e persistenza devono avere fonti leggibili e binding verificati; riprendere solo la sessione nota senza enumerare altre sessioni. Recuperare i riferimenti espliciti del work item corrente senza espansione ricorsiva.

---

**Nei principi:** [1. Autorità delimitata](../../principi/01-autorita-delimitata.md)

[← Precedente: Knowledge Builder](../agents/knowledge-builder.md) · [↑ Mappe di agent e skill](../README.md) · [Successivo: Plan Bug From Id →](plan-bug-from-id.md)
