[Corso](../README.md) › [Approfondimenti](README.md) › **Mappa del sistema**

# Mappa del sistema

Questa mappa mostra come si collegano gli elementi di un Agentic System. Non prescrive nomi di file, agent o cartelle per il tuo repository.

## Come scorre un'attività

```mermaid
flowchart TD
    Request[Richiesta] --> Router[Istruzioni sempre attive<br/>indirizzano la richiesta]
    Router --> Role[Ruolo delimitato]
    Human[Decisione umana] --> Workflow
    Role --> Workflow[Workflow servito<br/>un'istruzione alla volta]
    Workflow --> Knowledge[Glossario e catalogo della knowledge]
    Knowledge --> Evidence[Fonti selezionate]
    Evidence --> Delegate[Delegate in contesto pulito]
    Delegate --> Validation[Validazione e verdict]
    Validation --> Gate[Gate o halt point]
    Human --> Gate
    Gate --> Artifact[Artifact nella sessione]
    Artifact --> Next[Istruzione successiva o esito]
```

| Elemento | Che cosa fa | Principio |
| --- | --- | --- |
| Istruzioni sempre attive | Indirizzano verso i contratti necessari | [6. Composizione e ciclo di vita](../principi/06-composizione-e-ciclo-di-vita.md) |
| Ruolo | Limita autorità, strumenti e output | [1. Autorità delimitata](../principi/01-autorita-delimitata.md) |
| Workflow e runtime | Impongono l'ordine dei passaggi | [2. Gate e controllo umano](../principi/02-gate-e-controllo-umano.md) |
| Gate e halt point | Controllano il passaggio | [2. Gate e controllo umano](../principi/02-gate-e-controllo-umano.md) |
| Delegate e verificatori | Separano chi produce da chi giudica | [3. Validazione come prova](../principi/03-validazione-come-prova.md) |
| Sessione e design | Conservano requisito, decisioni, prove e stato | [4. Artifact durevoli](../principi/04-artifact-durevoli.md) |
| Glossario e catalogo | Stabilizzano i termini e selezionano le fonti | [5. Conoscenza selettiva](../principi/05-conoscenza-selettiva.md) |

## Tre workflow, un orchestrator

```mermaid
flowchart TD
    Request[Richiesta e output desiderato] --> Choice{Lo sviluppatore sceglie<br/>il workflow}
    Choice -->|scelte da giudicare| Design[DESIGN]
    Design --> Approved[Design verificato<br/>e approvato]
    Approved --> Impl1[Code implementor<br/>e implementation verifier]
    Choice -->|cambiamento semplice| Fast[FAST_IMPLEMENTATION]
    Fast --> Impl2[Code implementor<br/>e implementation verifier]
    Choice -->|documentare l'esistente| Doc[DOCUMENTATION]
    Doc --> Review[Documento compilato<br/>e documentation reviewer]
    Impl1 --> Handoff[Handoff con le prove<br/>e i blocchi aperti]
    Impl2 --> Handoff
    Review --> Artifact[Documento salvato<br/>nella sessione]
```

Mappe dei ruoli: [Orchestrator](../role-maps/agents/orchestrator.md) · [Code Implementor](../role-maps/agents/code-implementor.md) · [Implementation Verifier](../role-maps/agents/implementation-verifier.md) · [Documentation Reviewer](../role-maps/agents/documentation-reviewer.md) · [Come scegliere](../role-maps/README.md#quale-percorso-scegliere).

Il diagramma riassume i percorsi: non permette di unire o saltare istruzioni. Tutte le istruzioni sono nel [riferimento dei workflow](../slides/reference-flow.md).

## Ciclo di manutenzione

```mermaid
flowchart TD
    Failure[Errore osservato] --> Cause[Controllo mancante:<br/>autorità, gate, prova, artifact o knowledge]
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

[← Precedente: Approfondimenti](README.md) · [↑ Approfondimenti](README.md)
