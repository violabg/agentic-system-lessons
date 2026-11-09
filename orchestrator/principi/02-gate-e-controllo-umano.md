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
| Presentazione del design | Errori dei [controlli meccanici](../system/canonical/contracts/design-checks.md); difetti trovati dalla revisione avversariale | Un giro completo della revisione senza difetti, poi un controllo finale senza errori | Runtime e [orchestrator](../role-maps/agents/orchestrator.md) |
| Approvazione | Design non approvato | Risposta “1. Approva” dello sviluppatore | Sviluppatore; il runtime rifiuta l'approvazione finché un controllo fallisce |
| Unità di lavoro | Operazioni realizzate ma non riviste | Revisione dell'orchestrator senza difetti: le operazioni passano a `Completed` | Orchestrator; un difetto che non si può correggere diventa un blocco registrato nell'iterazione |
| Test e operazioni distruttive | Operazioni `Testing` o con effetti distruttivi non selezionate | Scelta esplicita delle operazioni | Sviluppatore; dopo ogni unità di lavoro l'orchestrator elenca ciò che manca e chiede come procedere |

L'approvazione la dà solo lo sviluppatore: l'orchestrator la registra con un'operazione del runtime, che la rifiuta finché il design ha errori. Approvare un design che lo sviluppatore non ha approvato è un difetto.

**Le correzioni non hanno scorciatoie.** La revisione del design si ripete finché un giro completo non trova più difetti, e l'[istruzione](../system/canonical/workflows/design/09-design-review.md) se ne aspetta almeno tre; la revisione di un'unità di lavoro si ripete finché è pulita. Una contraddizione nel design non è un blocco da segnalare: è un difetto che l'orchestrator corregge nel design prima di continuare. Solo un difetto che non si può correggere diventa un blocco: l'iterazione lo registra, l'istruzione resta incompleta e il blocco arriva allo sviluppatore.

**Non ogni lavoro merita lo stesso gate.** `FAST_IMPLEMENTATION` non ha un documento di design, un'approvazione né un delegate: l'orchestrator prende il requisito dal prompt così com'è scritto, implementa, esegue build e test e riferisce. Lo sviluppatore giudica il risultato alla fine. Scegliere quel workflow è una decisione dello sviluppatore sul rischio, non una scorciatoia che l'agente può prendere da solo. Il [riferimento dei workflow](../slides/reference-flow.md) elenca tutte le istruzioni e i loro halt point.

**Lo sviluppatore può cambiare il processo, non le garanzie.** Nel primo step di ogni workflow le richieste particolari dello sviluppatore (saltare l'intervista, partire da un certo punto, aggiungere un controllo) diventano effetti vincolanti. Uno skip che toglierebbe un gate o un artifact richiesto dal requisito o dalla knowledge è un conflitto: il workflow si ferma e chiede.

Anche fuori dai workflow vale la stessa regola: [Manage Work Item](../role-maps/skills/manage-work-item.md) non crea né modifica un ticket finché l'utente non approva la proposta finale.

## Nel caso guida

L'orchestrator presenta il design solo dopo che la sua revisione non trova più difetti e il controllo finale non segnala errori. Lo sviluppatore chiede una modifica: l'orchestrator la applica, ripete controlli e revisione e ripresenta. Il design passa all'implementazione solo dopo la risposta “approva”. [Leggi la traccia](../caso-guida.md#traccia-3-design-revisione-e-approvazione).

## Nel tuo repository

- In quale punto il tuo team deve approvare prima che un agente modifichi il codice?
- Il tuo agente potrebbe saltare quel punto, oppure non sa nemmeno che esiste finché non ci arriva?

---

[← Precedente: 1. Autorità delimitata](01-autorita-delimitata.md) · [↑ Principi](README.md) · [Successivo: 3. Validazione come prova →](03-validazione-come-prova.md)
