[Corso](../README.md) › [Approfondimenti](README.md) › **Mappa del sistema**

# Mappa del sistema

Questa mappa mostra come si collegano gli elementi di un Agentic System. Non prescrive nomi di file, agent o cartelle per il tuo repository.

## Come scorre un'attività

```mermaid
flowchart TD
    Request[Richiesta] --> Router[Istruzioni sempre attive<br/>indirizzano la richiesta]
    Router --> Role[Ruolo delimitato]
    Role --> Selector[Glossario e indice della knowledge]
    Selector --> Evidence[Fonti selezionate]
    Evidence --> Gate[Gate]
    Gate --> Artifact[Artifact e handoff]
    Artifact --> Validation[Validazione]
    Validation --> Next[Ruolo successivo o esito]
    Human[Decisione umana] --> Gate
    Human --> Next
```

| Elemento | Che cosa fa | Principio |
| --- | --- | --- |
| Istruzioni sempre attive | Indirizzano verso i contratti necessari | [6. Composizione e ciclo di vita](../principi/06-composizione-e-ciclo-di-vita.md) |
| Ruolo | Limita autorità, strumenti e output | [1. Autorità delimitata](../principi/01-autorita-delimitata.md) |
| Gate | Controlla il passaggio | [2. Gate e controllo umano](../principi/02-gate-e-controllo-umano.md) |
| Validazione | Smentisce gli esiti non affidabili | [3. Validazione come prova](../principi/03-validazione-come-prova.md) |
| Artifact | Conserva prove, stato e handoff | [4. Artifact durevoli](../principi/04-artifact-durevoli.md) |
| Glossario | Stabilizza i termini | [5. Conoscenza selettiva](../principi/05-conoscenza-selettiva.md) |
| Indice della knowledge | Seleziona le fonti da leggere | [5. Conoscenza selettiva](../principi/05-conoscenza-selettiva.md) |

## Due percorsi di implementazione

```mermaid
flowchart TD
    Request[Richiesta e output desiderato] --> Choice{Quale contratto serve?}
    Choice -->|un piano da passare di mano| Planner[Planner]
    Planner --> Approved[Piano approvato]
    Approved --> Implementor[Implementor]
    Choice -->|implementazione dai requisiti| Direct[Direct Implementor]
    Direct --> Requirements[Requisiti, knowledge, intervista<br/>e design validati]
    Requirements --> Code[Modifiche senza piano intermedio]
    Implementor --> Evidence[Build, revisione e report<br/>delle prove effettive]
    Code --> Evidence
    Evidence --> Handoff[Utente: rischio residuo<br/>e prossimo workflow autorizzato]
```

Mappe dei ruoli: [Planner](../role-maps/agents/planner.md) · [Implementor](../role-maps/agents/implementor.md) · [Direct Implementor](../role-maps/agents/direct-implementor.md) · [Come scegliere](../role-maps/README.md#quale-percorso-scegliere).

Il diagramma riassume i percorsi: non permette di unire o saltare i gate. Il Direct Implementor non crea test; una verifica successiva richiede il ruolo incaricato, con il suo intake.

## Ciclo di manutenzione

```mermaid
flowchart TD
    Failure[Errore osservato] --> Cause[Controllo mancante:<br/>conoscenza, autorità o verifica]
    Cause --> Owner[Superficie che possiede la regola]
    Owner --> Change[Modifica minima]
    Change --> Check[Verifica eseguibile]
    Check --> Decide{Il risultato giustifica<br/>la modifica?}
    Decide -->|sì| Keep[Mantieni e documenta]
    Decide -->|no| Revise[Rivedi o rimuovi]
    Keep --> Observe[Osserva il lavoro successivo]
    Revise --> Observe
    Observe --> Failure
```

Ogni regola resta nella superficie che la possiede; le altre superfici rimandano a lei invece di copiarla. Il risultato della verifica distingue ciò che è stato controllato dal rischio che resta aperto.

---

[↑ Approfondimenti](README.md)
