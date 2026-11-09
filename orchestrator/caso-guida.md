[Corso](README.md) › **Caso guida**

# Caso guida: chiudere una richiesta con motivazione

Questo caso è **inventato per il corso**: le tracce sono materiale preparato, non log reali del sistema canonical. Ogni pagina dei principi ne usa un frammento per rendere concreta un'idea. Le domande brevi sono facoltative.

## La richiesta

> Come operatore, voglio chiudere una richiesta solo dopo aver inserito una motivazione.

Sembra semplice, ma la story non dice:

- quale testo conta come motivazione (una stringa di soli spazi vale?);
- che cosa succede a una richiesta già chiusa;
- quale risposta riceve un client che prova a chiudere senza motivazione.

Una parte invece è già decisa: “solo dopo” vale per **ogni** chiusura, dall'interfaccia e dall'API. Non è una scelta da fare, è un obbligo da realizzare.

## Traccia 1: workflow, requisito e decisioni

Principio: [1. Autorità delimitata](principi/01-autorita-delimitata.md)

- Lo sviluppatore apre una sessione nuova, `richieste_chiusura`, e chiede all'[orchestrator](role-maps/agents/orchestrator.md) di lavorare sulla story con il workflow `DESIGN`. Il nome del workflow lo dà lui: l'orchestrator non lo deduce dalla richiesta.
- La skill [Plan User Story From Id](role-maps/skills/plan-user-story-from-id.md) fa recuperare il ticket da un delegate e lo salva come artifact della sessione.
- L'orchestrator scompone la story in obbligazioni verificabili, lavorando solo sul testo della story: non legge il codice e non decide nulla che la story lasci aperto. Ogni obbligazione è un'affermazione chiusa, con le sue condizioni e la frase da cui deriva. Estratto preparato:

  ```text
  O1 | Quando un operatore chiude una richiesta, dall'interfaccia o dall'API,
     | la richiesta passa a "Chiusa" solo se la chiusura porta una motivazione.
     | classe: guard · confini: ogni canale di chiusura
     | fonte: "chiudere una richiesta solo dopo aver inserito una motivazione"
  ```

- Gli aspetti che la story non fissa diventano decisioni, in uno step che non si ferma a chiedere. Per “soli spazi” l'orchestrator **sceglie** una risposta (una motivazione deve contenere almeno un carattere che non sia uno spazio) e scrive accanto tre alternative complete. Segna la decisione come `highlight`: è quella su cui vuole il giudizio dello sviluppatore alla review.

**Domanda breve:** perché l'orchestrator può scegliere come trattare gli spazi, ma non può decidere che il vincolo valga solo per l'interfaccia?

## Traccia 2: knowledge

Principio: [5. Conoscenza selettiva](principi/05-conoscenza-selettiva.md)

Il catalogo contiene una regola `MustHave` sul changelog, una regola `PerContext` per le modifiche alle API e una regola `PerComponent` sul servizio Richieste. Contiene anche una guida per il componente Fatture: plausibile, ma non applicabile. Nello step di knowledge l'orchestrator legge per intero la regola `MustHave`, sceglie le altre dai metadati del catalogo e non apre file di codice. Dopo ogni lettura registra solo le prescrizioni che valgono per la story, ciascuna come intervallo di righe: dalla regola API, per esempio, solo le righe sulle risposte di errore. Quella prescrizione aggiunge un comportamento funzionale: un rifiuto risponde con un errore di validazione che indica il campo mancante. L'orchestrator lo aggiunge alle obbligazioni, citando la fonte.

**Domanda breve:** se la soluzione aggiunge un processo batch che chiude le richieste scadute, quali fonti vanno rivalutate?

## Traccia 3: design, revisione e approvazione

Principi: [2. Gate e controllo umano](principi/02-gate-e-controllo-umano.md) · [3. Validazione come prova](principi/03-validazione-come-prova.md)

- L'orchestrator scrive il design una sezione per volta: prima i contratti e l'API di chiusura, poi i file, poi le operazioni e una sintesi della situazione di partenza. Prima di ogni sezione rilegge quelle già scritte, le obbligazioni e le decisioni.
- Nella revisione esegue subito i controlli meccanici. Segnalano `api-not-realized`: l'API di chiusura è dichiarata, ma nessuna operazione la realizza. Poi attacca il design da quattro punti di vista. Sulla copertura trova un difetto più serio: l'operazione del controller API chiama il servizio senza passargli la motivazione, quindi `O1` è realizzata solo per l'interfaccia. Corregge l'operazione e collega l'API. Il terzo giro non trova difetti, e il controllo finale non segnala errori.
- L'orchestrator apre la review con il [documento del design](reference/documento-di-design.md), il suo giudizio sui rischi e la decisione `highlight` sugli spazi. Lo sviluppatore chiede una modifica: una richiesta già chiusa non si modifica. Diventa un'obbligazione con origine `Developer`, che prevale sul requisito; l'orchestrator la realizza, ripete controlli e revisione e ripresenta il design.
- Lo sviluppatore approva. Il runtime registra l'approvazione con il nome `chiusura_con_motivazione`.

**Domanda breve:** che cosa dice il controllo meccanico verde, che cosa la revisione dell'orchestrator, e chi ha giudicato il design senza averlo scritto?

## Traccia 4: implementazione e prove

Principi: [3. Validazione come prova](principi/03-validazione-come-prova.md) · [4. Artifact durevoli](principi/04-artifact-durevoli.md)

- L'orchestrator apre l'iterazione `IT1` e avvia il [code implementor](role-maps/agents/code-implementor.md). Il prompt contiene identificatori e il ciclo di lavoro, non il testo del design né la knowledge: il delegate chiede al runtime un'operazione alla volta, e ogni risposta porta con sé obbligazioni, decisioni, contratti, file e il testo delle prescrizioni che la riguardano.
- Il runtime serve il batch di produzione, poi quello di documentazione: la voce di changelog che la regola `MustHave` richiede. Poi risponde `batch-complete` e il delegate restituisce il controllo con il suo report: file toccati, build eseguita con l'esito, regole applicate e dove. L'operazione di test resta fuori dai batch.
- L'orchestrator rivede l'unità di lavoro: legge il report e il codice. La build è verde, ma la risposta di errore dell'API non nomina il campo mancante, come chiedono la regola API e le istruzioni dell'operazione. Manda allo **stesso** code implementor una correzione con il file e la modifica esatti; la seconda revisione è pulita.
- Le operazioni passano a `Completed` e `IT1` si chiude: l'elenco dei file cambiati lo calcola il runtime confrontando il workspace con lo stato all'apertura.
- L'orchestrator elenca allo sviluppatore le operazioni che mancano. Lo sviluppatore seleziona quella `Testing` di tipo `Unit`: l'orchestrator apre `IT2` e lo stesso delegate scrive ed esegue i test. Quattro scenari passano (motivazione valida, motivazione vuota, soli spazi, richiesta già chiusa), e l'orchestrator rivede anche questo lavoro.
- Il messaggio finale mostra documento, file, revisioni e blocchi. Non dichiara provati i client esterni dell'API, che nessuno ha eseguito.

**Domanda breve:** se domani una persona nuova riapre la sessione, dove trova il motivo per cui “solo spazi” non è una motivazione valida?

## Applicare il ciclo al tuo repository

Principio: [6. Composizione e ciclo di vita](principi/06-composizione-e-ciclo-di-vita.md)

Davanti a un errore reale: descrivilo, individua il controllo mancante, trova la superficie che lo possiede, fai una modifica minima e cerca una prova che potrebbe smentire il miglioramento. Il [ciclo di manutenzione](reference/mappa-del-sistema.md#ciclo-di-manutenzione) mostra questo percorso.

---

[↑ Torna al corso](README.md)
