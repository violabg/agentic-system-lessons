# User Story Analysis

[Indice mappe](../README.md) · [Contratto canonical](../../system/canonical/skills/user-story-analysis/SKILL.md)

## In 30 Secondi

**Fa:** analizza criticamente una user story prima del design, esponendo ciò che manca, e le conseguenze di ambiguita, assunzioni, casi limite e rischi.

**Non fa:** non inventa requisiti. Quando mancano dettagli, li trasforma in domande per stakeholder e suggerimenti di miglioramento.

**Consegna:** un'analisi strutturata che rende il requisito piu verificabile prima che un Planner lo trasformi in piano.

## Flusso, Controlli E Output

```mermaid
flowchart TD
    Story[Input: user story<br/>o work item ID] --> Retrieve[Passo: recupera descrizione,<br/>criteri, relazioni e commenti]
    Retrieve --> Evidence[Dati della story recuperati]
    Evidence --> Gaps[Analizza gap funzionali<br/>e comportamenti non definiti]
    Gaps --> Ambiguity[Analizza ambiguita,<br/>incoerenze e assunzioni]
    Ambiguity --> Scenarios[Analizza edge case,<br/>rischi e dipendenze]
    Scenarios --> Questions[Output: domande<br/>per stakeholder]
    Questions --> Improve[Output: suggerimenti e<br/>acceptance criteria migliorati]
    Improve --> G1{Controllo didattico<br/>Le lacune restano esplicite?}
    G1 -->|no| Gaps
    G1 -->|si| Handoff[Handoff: stakeholder chiarisce;<br/>Planner usa requisito migliorato]
```

## Lettura Del Diagramma

| Passaggio o controllo | Decisione che protegge | Output | Handoff successivo |
| --- | --- | --- | --- |
| Recupero | Quale evidenza definisce davvero la story? | Descrizione, criteri, commenti e relazioni | Analisi |
| Gap e ambiguita | Cosa manca, e cosa puo avere piu interpretazioni? | Gap, incoerenze e assunzioni esplicite | Scenari |
| Scenari e rischi | Quali casi limite, dipendenze e rischi richiedono decisione? | Inventario di scenari e rischi | Domande |
| Domande e miglioramenti | Come si ottiene un requisito piu preciso senza inventarlo? | Domande stakeholder e proposte di AC | Controllo dell'output |
| Controllo dell'output | Le lacune restano esplicite senza requisiti inventati? | Analisi strutturata | Stakeholder e Planner |

**Da ricordare:** il valore della skill e rendere esplicita l'incertezza. Un requisito migliore nasce da domande tracciabili, non da dettagli aggiunti dall'analista.
