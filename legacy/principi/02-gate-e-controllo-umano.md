[Corso](../README.md) › [Principi](README.md) › **2. Gate e controllo umano**

# 2. Gate e controllo umano

> **In breve:** un gate è un punto di controllo su un passaggio. Dice che cosa blocca il lavoro, quale prova lo sblocca e chi può accettarla. Nei passaggi decisivi, quella persona è un essere umano.

[Slide](../slides/02-gate-e-controllo-umano.md) · [Caso guida](../caso-guida.md)

## Il problema

L'agente inizia a modificare il codice quando lo scope non è ancora chiaro, il rischio non è stato valutato e nessuno ha approvato la soluzione. Quando l'errore emerge, è già nel codice e costa di più correggerlo.

## Il principio

Un gate risponde a tre domande:

1. **Che cosa blocca?** La condizione che impedisce di proseguire.
2. **Che cosa sblocca?** La prova che permette di andare avanti.
3. **Chi decide?** Il ruolo o la persona che può accettare quella prova.

Un gate non significa sempre chiedere il permesso. Alcuni gate avanzano da soli quando la prova esiste; altri attendono una persona. Quando progetti un workflow, metti un gate solo dove l'errore costa caro o dove cambia l'autorità. Quando esegui un workflow esistente, invece, tutti i gate previsti restano obbligatori e vanno rispettati in ordine.

## Nel sistema di riferimento

Il [glossario canonical](../system/canonical/CONTEXT.md) definisce il gate come un punto di controllo su prove, approvazione, scope, handoff o validazione.

Il [Planner](../role-maps/agents/planner.md) ha quattordici gate, dal Gate 0 al Gate 13, e non può saltarli, unirli o cambiarne l'ordine. La maggior parte avanza da sola quando la prova richiesta è disponibile. Il contratto ammette solo quattro punti di attesa: la conferma della sessione (Gate 1) e la scelta del piano o delle immagini (Gate 2), solo quando servono; l'intervista per chiarire le lacune (Gate 7); l'approvazione del piano (Gate 11). Tre passaggi mostrano bene l'idea:

| Passaggio | Che cosa blocca | Che cosa sblocca |
| --- | --- | --- |
| Dal requisito al design | Un'ambiguità che cambia il comportamento | Una risposta chiarita e verificata |
| Dalle regole al piano | Una regola applicabile ignorata o violata | L'elenco delle regole e un design allineato |
| Dal piano all'implementazione | Un piano non revisionato o non approvato | Un piano validato e un'approvazione registrata |

Anche l'[Implementor](../role-maps/agents/implementor.md) si ferma per una decisione umana: prima di creare test unitari chiede un'approvazione esplicita (Gate 8). La skill [Manage Work Item](../role-maps/skills/manage-work-item.md) applica la stessa regola fuori dal codice: non crea né modifica un ticket finché l'utente non approva la proposta finale.

Il [flusso Planner → Implementor](../slides/reference-flow.md) elenca tutti i gate, uno per riga.

## Nel caso guida

Il Planner prepara un piano per la chiusura con motivazione. Il piano non passa all'Implementor finché l'utente non lo approva in modo esplicito. Se l'utente chiede una modifica, il Planner registra la decisione, rivede il piano e lo ripresenta. [Leggi la traccia](../caso-guida.md#traccia-3-piano-e-handoff).

## Nel tuo repository

- In quale punto il tuo team deve approvare prima che un agente modifichi il codice o configuri un'integrazione?
- Per quel punto, sai dire che cosa blocca, che cosa sblocca e chi decide?

---

[← Precedente: 1. Autorità delimitata](01-autorita-delimitata.md) · [↑ Principi](README.md) · [Successivo: 3. Validazione come prova →](03-validazione-come-prova.md)
