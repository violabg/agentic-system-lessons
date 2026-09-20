# Direct Implementor

[Indice mappe](../README.md) · [Contratto canonical](../../system/canonical/agents/direct-implementor.agent.md) · [Confronto con Implementor](implementor.md)

## In 30 Secondi

**Fa:** analizza una richiesta di implementazione, valida requisiti e design contro la conoscenza, modifica la produzione e registra build e review.

**Non fa:** non produce né richiede un piano di implementazione, non delega al Planner e non crea test unitari o di integrazione. Una richiesta di pianificazione esce dal suo mandato.

**Consegna:** modifiche di produzione, inventario delle regole, execution report, memoria e log della sessione, riepilogo delle verifiche e degli eventuali blocchi.

La scomposizione dei requisiti al Gate 3 è solo in chat: quel gate vieta file, artifact e scritture in memoria. La persistenza avviene nei passaggi previsti: inventario normativo al Gate 4, risposte verbatim in memoria al Gate 8, report e log durante l’esecuzione. Non insegnare un documento di requisiti obbligatorio che il contratto non richiede.

**Autorità:** le decisioni architetturali e di design restano sotto controllo umano esplicito nell'intervista. “Diretto” elimina il documento di piano intermedio; non elimina chiarimenti, gate o prove.

## Flusso, Gate E Artifact

I gruppi nel diagramma servono alla lettura: ogni gate del contratto va eseguito singolarmente, in ordine.

```mermaid
flowchart TD
    Input[Richiesta di implementazione] --> G0{0: scope valido?}
    G0 -->|no| Stop[Rifiuto o chiarimento con utente]
    G0 -->|si| G1[1: attiva o riprendi la sessione nota]
    G1 --> G2[2: intake artifact e immagini]
    G2 --> G3[3: scomponi requisiti e criteri di accettazione]
    G3 --> G4[4: knowledge e inventario regole]
    G4 --> G5[5-6: comprensione e ricognizione del codice]
    G5 --> G7[7-8: intervista e validazione risposte]
    G7 --> G9[9: allineamento knowledge e design]
    G9 --> G10[10: implementazione completa]
    G10 --> G11{11: build riuscita?}
    G11 -->|errore recuperabile| Fix[Correzione secondo compiler recovery policy]
    Fix --> G11
    G11 -->|blocco non risolvibile| Stop
    G11 -->|si| G12[12: review requisiti e regole]
    G12 -->|blocco non risolvibile| Stop
    G12 -->|verifica completata| G13[13: riepilogo e handoff all'utente]
    G13 --> G14{14: richiesta di refinement?}
    G14 -->|si| G0
    G14 -->|no| End[Fine]
```

## Lettura Del Diagramma

| Gate | Decisione protetta | Evidenza e destinatario |
| --- | --- | --- |
| 0-2 | Il mandato è implementare e la sessione è quella indicata? | Scope, stato e artifact; eventuale evidenza Vision per il ruolo consumatore. Nessuna enumerazione di altre sessioni. |
| 3-6 | Cosa deve funzionare e quali regole governano il design? | Requisiti e criteri in chat, inventario normativo persistito e riferimenti al codice per l'intervista. |
| 7-9 | Ambiguità e decisioni sono risolte contro evidenza e risposte umane? | Risposte validate e design conforme per l'implementazione. |
| 10-12 | Modifiche, build e review soddisfano i requisiti? | Report aggiornato con prove effettive o blocchi per l'utente. Una build verde non prova la copertura funzionale. |
| 13-14 | Si chiude o arriva un nuovo requisito? | Riepilogo; se richiesto, nuovo ciclo completo 0-13 nella stessa sessione con riuso dello stato e caricamento del delta di knowledge. |

Un requisito molto diverso richiede prima la decisione esplicita dell'utente se proseguire nella stessa chat. Nel restart, i riferimenti al codice si riverificano; l'intervista si ripete quando nuove ambiguità o gap lo richiedono, altrimenti si registra la conferma. Un binding necessario indisponibile blocca l'operazione.

**Da ricordare:** scegliere questo ruolo non autorizza a saltare gate né a dichiarare test mai eseguiti. Se servono nuovi test, assegnarli a un workflow autorizzato; non estendere silenziosamente questo contratto.
