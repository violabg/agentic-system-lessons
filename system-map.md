# Mappa del Sistema Agentico Enterprise

[Torna alla lettura principale](README.md) · [Principi](principles.md)

Questa mappa mostra relazioni didattiche. Non prescrive nomi di file, agent o directory per il repository target.

## Controlli Operativi

```mermaid
flowchart TD
    Request[Richiesta] --> Router[Router e istruzioni sempre attive]
    Router --> Role[Ruolo delimitato]
    Role --> Selector[Glossario e knowledge index]
    Selector --> Evidence[Evidenza selezionata]
    Evidence --> Gate[Gate]
    Gate --> Artifact[Artifact e handoff]
    Artifact --> Validation[Validazione]
    Validation --> Next[Prossimo ruolo o esito]
    Human[Autorità umana] --> Gate
    Human --> Next
```

| Elemento | Responsabilità | Principio |
| --- | --- | --- |
| Router | Indirizza verso i contratti necessari | Composizione |
| Ruolo | Limita autorità, strumenti e output | Ruoli |
| Glossario | Stabilizza termini | Conoscenza |
| Knowledge index | Seleziona fonti operative | Conoscenza |
| Gate | Controlla la transizione | Gate |
| Artifact | Conserva prova, stato e handoff | Provenienza |
| Validation | Falsifica esiti non affidabili | Validazione |

## Due Percorsi Di Implementazione

```mermaid
flowchart TD
    Request[Richiesta e output desiderato] --> Choice{Quale contratto serve?}
    Choice -->|piano da passare di mano| Planner[Planner]
    Planner --> Approved[Piano approvato]
    Approved --> Implementor[Implementor]
    Choice -->|implementazione dai requisiti| Direct[Direct Implementor]
    Direct --> Requirements[Requisiti, knowledge, intervista e design validati]
    Requirements --> Code[Modifiche senza piano intermedio]
    Implementor --> Evidence[Build, review e report delle prove effettive]
    Code --> Evidence
    Evidence --> Handoff[Utente: rischio residuo e prossimo workflow autorizzato]
```

[Confronto e scelta](role-maps/README.md) · [Gate del percorso diretto](role-maps/agents/direct-implementor.md). Il diagramma riassume i percorsi, non consente di accorpare i gate esecutivi. Direct Implementor non crea test; una successiva verifica richiede il mandato e l'intake del ruolo incaricato.

## Ciclo Di Manutenzione

```mermaid
flowchart TD
    Failure[Failure mode osservato] --> Cause[Conoscenza, autorità o verifica mancante]
    Cause --> Owner[Superficie proprietaria]
    Owner --> Change[Modifica minima]
    Change --> Check[Verifica eseguibile]
    Check --> Decide{Il risultato sostiene la modifica?}
    Decide -->|si| Keep[Mantieni e documenta]
    Decide -->|no| Revise[Rivedi o rimuovi]
    Keep --> Observe[Osserva il lavoro successivo]
    Revise --> Observe
    Observe --> Failure
```

Il ciclo mantiene le regole nella superficie che le possiede e usa le altre superfici per instradare, non duplicare. Il risultato della verifica deve distinguere ciò che è stato controllato dal rischio che resta aperto.

[Torna alla lettura principale](README.md)
