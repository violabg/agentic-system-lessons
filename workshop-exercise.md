# Caso condiviso: chiudere una richiesta di assistenza

[Corso](README.md) · [Slide](slides/README.md)

**Tutto il caso è fittizio:** documenti, frammenti e tracce sono preparati per ragionare, non provengono da un’esecuzione reale. Non occorrono installazioni. Il docente mostra una tappa alla volta; evita di leggere in anticipo le evidenze successive.

Si lavora in coppia per 13 minuti: 2 per leggere, 7 per confrontarsi, 4 per scrivere. A ogni lezione aggiungi soltanto il risultato richiesto. Alterna chi propone e chi cerca una possibile smentita. Le risposte motivate possono differire; non si valuta il nome del ruolo scelto.

## Tappa 1

**A1 — Richiesta del responsabile prodotto:** «Impedire la chiusura delle richieste di assistenza senza motivazione».

**A2 — Risposta dell’agente:** «Aggiunto il campo obbligatorio nella schermata di chiusura. Build completata. Il requisito è soddisfatto».

**A3 — Unica traccia allegata:** `Build: SUCCESS`. Nessun risultato comportamentale allegato.

Accetteresti la modifica? Distingui ciò che sai da ciò che stai supponendo.

Completa:

- L’agente afferma che il requisito è soddisfatto perché la build passa.
- Questo mostra … ma non mostra …
- Prima di accettare vorrei … perché potrebbe rivelare …

## Tappa 2

**B1 — Estratto dalla knowledge di dominio, versione corrente, approvata dal responsabile di dominio:** «La validità di una chiusura è controllata dal servizio di dominio per tutti i chiamanti. La motivazione non può essere vuota o composta solo da spazi». L’estratto non specifica la politica delle chiusure automatiche.

**B2 — Vecchia schermata, pseudocodice:**

```text
onCloseClick(reason):
    if trim(reason) == "": showError("Motivazione richiesta")
    else: api.closeTicket(ticketId, reason)
```

**B3 — Mockup testuale ricevuto dal prodotto:**

```text
Chiudi richiesta #42
Motivazione: [________________]
[Annulla] [Chiudi]
```

**B4 — Indice di conoscenza del progetto fittizio:**

| Fonte | Quando leggere |
| --- | --- |
| Regole di chiusura (B1) | Modifiche alla chiusura, qualunque sia il chiamante |
| Glossario | Quando un termine di dominio è ambiguo |
| Guida colori UI | Modifiche ai colori o al contrasto |

Nel glossario: “richiesta” = ticket di assistenza; “chiusura” = transizione allo stato chiuso.

Completa il mandato:

- Output richiesto: modifica che rispetti …
- Fonti da leggere: … perché …
- L’agente può modificare l’implementazione entro il mandato; non può decidere …
- Il mockup dimostra …; non può stabilire …
- Fonte non pertinente al task attuale: …

**Variante facoltativa, dopo l’esercizio:** A richiede un piano da approvare e passare a un altro esecutore; B richiede implementazione da requisiti, senza documento di piano intermedio. Confronta i [due percorsi canonical](role-maps/README.md). Quale output distingue i contratti? Non scegliere soltanto in base alla dimensione del task e non saltare i gate del percorso scelto.

## Tappa 3

**C1 — Nuova informazione dal team:** un processo notturno chiude automaticamente le richieste scadute. Non esiste una persona che compili il campo.

Prima di leggere C2, formula la domanda da porre al responsabile prodotto e indica quale decisione resta bloccata.

<details>
<summary>C2 — Aprire dopo aver formulato la domanda</summary>

**Risposta simulata del responsabile prodotto:** «Anche la chiusura automatica richiede una motivazione non vuota. Il processo deve inviare “Chiusura automatica per scadenza”. Nessuna eccezione al controllo nel servizio».

</details>

Scrivi un record comprensibile senza la chat:

- Decisione e fonte:
- Responsabile della decisione e proprietario del record:
- Condizione che ora consente di procedere:
- Stato della modifica e delle verifiche:
- Prossima prova e destinatario dell’handoff:
- Condizione che bloccherebbe il passaggio:

È una scheda didattica, non un nuovo artifact runtime obbligatorio. Nell’esecuzione reale si usano i record e i gate previsti dal contratto adottato.

## Tappa 4

**D1 — Stato disponibile:** build riuscita; la schermata rifiuta il campo vuoto. Il requisito include la decisione C2.

Prima di leggere D2, specifica input, prerequisiti, risultato atteso e osservazione necessaria per una chiamata che evita la UI. Nessun comando deve essere inventato: descrivi il controllo, poiché non abbiamo un repository eseguibile.

<details>
<summary>D2 — Aprire dopo aver proposto la prova</summary>

**Traccia simulata:**

```text
Ambiente: fixture didattica, ticket 42 aperto, chiamante autorizzato
Azione: chiamata diretta closeTicket(42, "")
Risposta: successo
Stato persistito dopo la chiamata: chiuso
```

</details>

Scrivi:

- La traccia smentisce …
- Il risultato corretto atteso sarebbe …
- Restano da verificare …
- La prova ulteriore richiede … e un ruolo autorizzato a …

Distingui il risultato osservato nella traccia da controlli soltanto proposti. Non dichiarare eseguiti test del tuo progetto.

## Tappa 5

**E1 — Fonte di dominio:** B1 e la decisione C2 sono ancora correnti.

**E2 — Nota locale copiata in un prompt:** «Per la chiusura basta rendere obbligatorio il campo nel browser».

**E3 — Secondo task:** l’agente riutilizza E2. Nel report non cita B1. Non sappiamo ancora se l’indice non instradi correttamente o se la fonte richiesta sia stata ignorata.

Proponi una correzione minima. Distingui il difetto osservato dall’ipotesi sulla causa: che cosa ispezioneresti prima di scegliere dove intervenire? Non aggiungere automaticamente una nuova regola globale.

- Fonte o procedura proprietaria da correggere e responsabile:
- Copia da rimuovere o sostituire con un riferimento:
- Prova sul prossimo task:
- Risultato che giustificherebbe mantenere o rivedere la correzione:

Infine scegli un errore reale del tuo repository e compila le stesse quattro righe. Se non hai un caso, usa E1–E3 come esercizio e rimanda l’esperimento al prossimo task reale.

## Chiusura individuale

Alla fine di ogni lezione scrivi: **decisione iniziale → decisione rivista → evidenza che l’ha cambiata → limite ancora aperto**. Non è necessario cambiare idea: puoi motivare perché l’evidenza conferma la decisione.

Il feedback guarda la decisione, la fonte o prova citata e il limite riconosciuto. Non premia la quantità di termini tecnici usati.

Dopo il corso, sul task scelto, registra l’esito reale e decidi se mantenere, correggere o rimuovere il controllo proposto.
