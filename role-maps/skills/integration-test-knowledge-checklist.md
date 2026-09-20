# Integration Test Knowledge Checklist

[Indice mappe](../README.md) · [Contratto canonical](../../../system/canonical/skills/integration-test-knowledge-checklist/SKILL.md)

## In 30 Secondi

**Fa:** guida la costruzione di una knowledge project-specific che permetta di creare e diagnosticare test di integrazione nel confine reale del progetto.

**Non fa:** non sostituisce una convenzione locale con consigli generici e non confonde test di integrazione con unit, system o end-to-end test.

**Consegna:** una knowledge indicizzata con metadata, stack, setup, seeding, mocking, assertion, failure interpretation e checklist verde.

## Flusso, Gate E Artifact

```mermaid
flowchart TD
    Boundary[Input: confine reale<br/>di integrazione] --> G1{Gate scope<br/>Famiglia test e fuori scope chiari?}
    G1 -->|no| Refine[Completa il confine]
    Refine --> G1
    G1 -->|si| Stack[Gate: stack, fixture e metadata]
    Stack --> Setup[Gate: flow, setup e seeding]
    Setup --> Shape[Gate: struttura, mocking<br/>e assertion]
    Shape --> Failures[Gate: negative case<br/>e failure interpretation]
    Failures --> Draft[Artifact: bozza knowledge<br/>con template pratico]
    Draft --> G2{Gate completezza<br/>Un nuovo test e diagnosticabile?}
    G2 -->|no| Refine
    G2 -->|si| Green[Artifact: knowledge pubblicabile<br/>e checklist verde]
    Green --> Handoff[Handoff: Integration Tester<br/>carica la knowledge]
```

## Lettura Del Diagramma

| Gate | Decisione che protegge | Artifact o output | Handoff successivo |
| --- | --- | --- | --- |
| Scope | Quale famiglia test e quale confine reale copre? | Scope e fuori scope espliciti | Stack |
| Stack e setup | Quali fixture, dipendenze, dati e seeding sono necessari? | Regole di stack, setup e seeding | Struttura |
| Struttura e assertion | Come si organizzano test, mock e prove degli effetti? | Template e policy di assertion | Failure interpretation |
| Failure interpretation | Come distinguere setup errato da difetto reale? | Casi negativi e segnali di failure | Completezza |
| Completezza | Un agente puo creare e debuggare un test nuovo? | Knowledge indicizzabile e checklist verde | Integration Tester |

**Da ricordare:** il prodotto non e un elenco di librerie. E una knowledge che permette al tester di ricostruire setup, prova e interpretazione di una failure.