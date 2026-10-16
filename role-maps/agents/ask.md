[Corso](../../README.md) › [Mappe di agent e skill](../README.md) › **Ask**

# Ask

**File sorgente:** [agents/ask.agent.md](../../system/canonical/agents/ask.agent.md)

## In 30 secondi

**Fa:** risponde a domande di programmazione o IT, ancorando la risposta prima alla conoscenza selezionata e poi, se necessario, a un riscontro mirato nel codice.

**Non fa:** non implementa, non modifica codice, non usa sessioni né memoria di lavoro e rifiuta richieste fuori da Q&A.

**Consegna:** una risposta strutturata che cita le knowledge usate, oppure un rifiuto o una domanda di chiarimento quando il contratto non consente di proseguire.

## Flusso, gate e artifact

```mermaid
flowchart TD
    Request[Input: domanda utente] --> G0{Gate 0<br/>È Q&A tecnica?}
    G0 -->|no| Decline[Output: rifiuto breve<br/>Handoff: nessuno]
    G0 -->|sì| G1[Gate 1<br/>Leggi catalogo knowledge]
    G1 --> KContext[Fonti nel contesto: knowledge<br/>selezionate e lette]
    KContext --> G2{Gate 2<br/>Il codice serve a colmare<br/>un gap concreto?}
    G2 -->|sì| Search[Cross-check mirato<br/>in una ricerca batched]
    Search --> Evidence[Evidenza nel contesto:<br/>riscontro nel codice]
    G2 -->|no| G3
    Evidence --> G3{Gate 3<br/>Fonti coerenti e sufficienti?}
    G3 -->|no, gap| Clarify[Output: chiarimento minimo<br/>Handoff: utente]
    G3 -->|no, conflitto| Stop[Output: stop con conflitto<br/>Handoff: utente]
    G3 -->|sì| G5[Gate 5<br/>Prepara risposta]
    G5 --> G6[Gate 6<br/>Risposta con riferimenti]
    G6 --> Answer[Output: answer, esempi se utili,<br/>knowledge references e follow-up]
```

## Lettura del diagramma

| Gate | Decisione che protegge | Artifact o output | Handoff successivo |
| --- | --- | --- | --- |
| 0. Scope | La richiesta è una domanda tecnica e non una modifica? | Classificazione o rifiuto | Gate 1, oppure utente |
| 1. Knowledge | Quali knowledge sono pertinenti? | Elenco delle knowledge lette | Gate 2 |
| 2. Cross-check | Manca una prova che solo il codice può dare? | Evidenza da ricerca batched, se necessaria | Gate 3 |
| 3-4. Coerenza e chiarimento | Le fonti bastano e non si contraddicono? | Gap, conflitto o chiarimento puntuale | Utente, oppure Gate 5 |
| 5-6. Risposta | La risposta rispetta scope e fonti? | Risposta strutturata con riferimenti | Utente |

**Da ricordare:** il gate di knowledge viene prima del repository. Il codice non sostituisce la conoscenza; serve solo a verificare o a completare un punto ancora aperto.

---

**Nei principi:** [1. Autorità delimitata](../../principi/01-autorita-delimitata.md)

[← Precedente: Direct Implementor](direct-implementor.md) · [↑ Mappe di agent e skill](../README.md) · [Successivo: Integration Tester →](integration-tester.md)
