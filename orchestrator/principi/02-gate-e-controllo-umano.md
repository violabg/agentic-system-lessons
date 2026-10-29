[Corso](../README.md) › [Principi](README.md) › **2. Gate e controllo umano**

# 2. Gate e controllo umano

> **In breve:** un gate è un punto di controllo su un passaggio. Dice che cosa blocca il lavoro, quale prova lo sblocca e chi può accettarla. Nei passaggi decisivi, quella persona è un essere umano.

[Slide](../slides/02-gate-e-controllo-umano.md) · [Caso guida](../caso-guida.md)

## Il problema

L'agente inizia a modificare il codice quando lo scope non è ancora chiaro, il rischio non è stato valutato e nessuno ha approvato la soluzione. Oppure salta un passaggio perché “sembrava ovvio”. Quando l'errore emerge, è già nel codice e costa di più correggerlo.

## Il principio

Un gate risponde a tre domande:

1. **Che cosa blocca?** La condizione che impedisce di proseguire.
2. **Che cosa sblocca?** La prova che permette di andare avanti.
3. **Chi decide?** Il ruolo o la persona che può accettare quella prova.

Un gate non significa sempre chiedere il permesso. Alcuni gate avanzano da soli quando la prova esiste; altri attendono una persona. Quando progetti un workflow, metti un gate solo dove l'errore costa caro o dove cambia l'autorità. Quando esegui un workflow esistente, tutti i gate previsti restano obbligatori e vanno rispettati in ordine.

## Nel sistema di riferimento

**L'ordine non dipende dall'agente.** Il runtime serve il workflow [un'istruzione alla volta](../system/canonical/contracts/workflow-loop.md): l'orchestrator non apre i file del workflow e non vede le istruzioni future. Non può saltare avanti, perché non sa che cosa c'è dopo.

**Fermarsi è un'eccezione dichiarata.** L'orchestrator continua da solo fino al prossimo *halt point*: una review che attende approvazione, una domanda, una decisione che solo lo sviluppatore può prendere. Lì presenta ciò che serve e aspetta; non chiede l'istruzione successiva finché lo sviluppatore non risponde. In ogni altro punto fermarsi è una violazione: un messaggio senza azione chiude il workflow a metà.

Nel workflow `DESIGN` i passaggi che contano sono questi:

| Passaggio | Che cosa blocca | Che cosa sblocca | Chi decide |
| --- | --- | --- | --- |
| Avvio | Sessione o workflow non indicati | Sessione e workflow scelti esplicitamente | Sviluppatore |
| Presentazione del design | Errori dei controlli meccanici, verdict diverso da `PASS` | Nessun errore e `VERDICT: PASS` | Runtime e [Design Verifier](../role-maps/agents/design-verifier.md) |
| Approvazione | Design non approvato | Risposta “1. Approva” dello sviluppatore | Sviluppatore; il runtime rifiuta l'approvazione finché un controllo fallisce |
| Fine implementazione | Verdict diverso da `PASS` | `VERDICT: PASS` dell'[Implementation Verifier](../role-maps/agents/implementation-verifier.md) | Verificatore; dopo quattro round falliti il blocco è registrato nell'iterazione e riportato nello handoff |

L'approvazione la dà solo lo sviluppatore: [l'orchestrator](../role-maps/agents/orchestrator.md) la registra con un'operazione del runtime, che la rifiuta finché il design ha errori. Approvare un design che lo sviluppatore non ha approvato è un difetto.

**I cicli di correzione hanno un limite.** Verifica del design e verifica dell'implementazione fanno al massimo quattro round. Se il problema persiste e la causa non è dell'orchestrator (un'ambiguità del requisito, una decisione dello sviluppatore), il design non viene indebolito per far passare la verifica: la verifica del design si ferma e porta il report allo sviluppatore; un blocco dell'implementazione viene registrato nell'iterazione e arriva allo sviluppatore con l'handoff.

**Non ogni lavoro merita lo stesso gate.** `FAST_IMPLEMENTATION` non ha un documento di design né un'approvazione: le obbligazioni del job design sono il requisito, e la verifica dell'implementazione resta. Scegliere quel workflow è una decisione dello sviluppatore sul rischio, non una scorciatoia che l'agente può prendere da solo. Il [riferimento dei workflow](../slides/reference-flow.md) elenca tutte le istruzioni e i loro halt point.

**Lo sviluppatore può cambiare il processo, non le garanzie.** Nel primo step di ogni workflow le richieste particolari dello sviluppatore (saltare l'intervista, partire da un certo punto, aggiungere un controllo) diventano effetti vincolanti. Uno skip che toglierebbe un gate o un artifact richiesto dal requisito o dalla knowledge è un conflitto: il workflow si ferma e chiede.

Anche fuori dai workflow vale la stessa regola: [Manage Work Item](../role-maps/skills/manage-work-item.md) non crea né modifica un ticket finché l'utente non approva la proposta finale.

## Nel caso guida

L'orchestrator presenta il design solo dopo che i controlli meccanici non segnalano errori e il design verifier ha risposto `PASS`. Lo sviluppatore chiede una modifica: l'orchestrator la applica, ripete controlli e verifica e ripresenta. Il design passa all'implementazione solo dopo la risposta “approva”. [Leggi la traccia](../caso-guida.md#traccia-3-design-verifica-e-approvazione).

## Nel tuo repository

- In quale punto il tuo team deve approvare prima che un agente modifichi il codice?
- Il tuo agente potrebbe saltare quel punto, oppure non sa nemmeno che esiste finché non ci arriva?

---

[← Precedente: 1. Autorità delimitata](01-autorita-delimitata.md) · [↑ Principi](README.md) · [Successivo: 3. Validazione come prova →](03-validazione-come-prova.md)
