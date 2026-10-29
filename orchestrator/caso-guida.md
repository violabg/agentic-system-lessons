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
- L'orchestrator scompone la story in obbligazioni verificabili; ogni obbligazione cita la frase da cui deriva con `sourceRef` e `sourceSpan`. Estratto preparato:

  ```text
  O1 | Una richiesta passa a "Chiusa" solo se la chiusura porta una motivazione,
     | per ogni canale di chiusura (interfaccia e API).
     | elementi: O1.1 (guard) motivazione presente · O1.2 (quantifier) ogni canale
     |           O1.3 (effect) senza motivazione lo stato non cambia
  ```

- Gli aspetti che la story non fissa diventano decisioni. Per “soli spazi” l'orchestrator **sceglie** una risposta (una motivazione deve contenere almeno un carattere che non sia uno spazio) e scrive accanto tre alternative complete. Segna la decisione come `highlight`: è quella su cui vuole il giudizio dello sviluppatore alla review.

**Domanda breve:** perché l'orchestrator può scegliere come trattare gli spazi, ma non può decidere che il vincolo valga solo per l'interfaccia?

## Traccia 2: knowledge

Principio: [5. Conoscenza selettiva](principi/05-conoscenza-selettiva.md)

Il catalogo contiene una regola `MustHave` sul changelog, una regola `PerContext` per le modifiche alle API e una regola `PerComponent` sul servizio Richieste. Contiene anche una guida per il componente Fatture: plausibile, ma non applicabile. Nello step di knowledge l'orchestrator legge per intero la regola `MustHave`, sceglie le altre dai metadati del catalogo e non apre file di codice. La regola API aggiunge un comportamento funzionale: un rifiuto risponde con un errore di validazione che indica il campo mancante. L'orchestrator lo aggiunge alle obbligazioni, citando la fonte.

**Domanda breve:** se la soluzione aggiunge un processo batch che chiude le richieste scadute, quali fonti vanno rivalutate?

## Traccia 3: design, verifica e approvazione

Principi: [2. Gate e controllo umano](principi/02-gate-e-controllo-umano.md) · [3. Validazione come prova](principi/03-validazione-come-prova.md)

- L'orchestrator scrive contratti, file e operazioni del design. Il primo controllo meccanico segnala `operation-without-failures`: l'operazione che realizza la guardia non dice che cosa succede quando la motivazione manca. L'orchestrator aggiunge il ramo negativo e ripete il controllo finché non restano errori.
- Il [design verifier](role-maps/agents/design-verifier.md) riceve solo l'id della sessione e l'id del job; quando lo stesso verificatore riprende dopo un `FAIL`, il prompt aggiunge solo l'elenco delle correzioni fatte. Il primo report inizia con `VERDICT: FAIL`: `O1` non è coperta, perché il controller API chiama il servizio senza passare la motivazione. L'orchestrator corregge il design; il secondo round restituisce `VERDICT: PASS`.
- L'orchestrator apre la review con il [documento del design](reference/documento-di-design.md) e la decisione `highlight` sugli spazi. Lo sviluppatore chiede una modifica: una richiesta già chiusa non si modifica. Diventa un'obbligazione con origine `Developer`, che prevale sul requisito; l'orchestrator la realizza, ripete controlli e verifica e ripresenta il design.
- Lo sviluppatore approva. Il runtime registra l'approvazione con il nome `chiusura_con_motivazione`.

**Domanda breve:** che cosa dice il controllo meccanico verde, e che cosa dice il `PASS` del design verifier?

## Traccia 4: implementazione e prove

Principi: [3. Validazione come prova](principi/03-validazione-come-prova.md) · [4. Artifact durevoli](principi/04-artifact-durevoli.md)

- L'orchestrator apre l'iterazione `IT1`, segna le operazioni di codice `InProgress` e avvia il [code implementor](role-maps/agents/code-implementor.md). Il prompt contiene identificatori e knowledge, non il testo del design: il delegate legge il design dalla sessione.
- Il code implementor realizza le operazioni servite: scrive il codice e, nell'operazione di test unitari autorizzata, i test; compila ed esegue: quattro scenari passano (motivazione valida, motivazione vuota, soli spazi, richiesta già chiusa).
- L'[implementation verifier](role-maps/agents/implementation-verifier.md) risponde `VERDICT: FAIL`: la risposta di errore dell'API non nomina il campo mancante, come chiede la regola API. L'orchestrator riprende lo **stesso** code implementor con il report del verifier; il secondo round è `VERDICT: PASS`.
- Le operazioni passano a `Completed` e l'iterazione si chiude: l'elenco dei file cambiati lo calcola il runtime confrontando il workspace con lo stato all'apertura.
- Il messaggio finale mostra file, test, verdict e blocchi. Non dichiara provati i client esterni dell'API, che nessuno ha eseguito.

**Domanda breve:** se domani una persona nuova riapre la sessione, dove trova il motivo per cui “solo spazi” non è una motivazione valida?

## Applicare il ciclo al tuo repository

Principio: [6. Composizione e ciclo di vita](principi/06-composizione-e-ciclo-di-vita.md)

Davanti a un errore reale: descrivilo, individua il controllo mancante, trova la superficie che lo possiede, fai una modifica minima e cerca una prova che potrebbe smentire il miglioramento. Il [ciclo di manutenzione](reference/mappa-del-sistema.md#ciclo-di-manutenzione) mostra questo percorso.

---

[↑ Torna al corso](README.md)
