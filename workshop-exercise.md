# Esercizio Trasversale: Una Richiesta, Due Percorsi

[Torna al corso](README.md) · [Scelta dei ruoli](role-maps/README.md)

**Caso fittizio:** un portale deve impedire la chiusura di una richiesta di assistenza senza motivazione. La knowledge assegna la regola al servizio di dominio. Una vecchia schermata controlla solo il browser. Lo screenshot mostra il campo, ma non definisce quando sia obbligatorio. Non serve un repository demo per svolgere l'esercizio.

**Obiettivo:** spiegare chi può decidere, quale evidenza lo autorizza e quale prova rende il risultato controllabile. Riutilizzare il caso nelle cinque lezioni; ogni gruppo aggiunge una riga al proprio record.

| Lezione | Consegna in 13 minuti | Ragionamento atteso per il facilitatore |
| --- | --- | --- |
| 1. Introduzione | Nominare il failure mode del caso e le tre domande del corso. | Chi decide, quale evidenza autorizza la decisione e quale prova rende il risultato controllabile. |
| 2. Autorità e conoscenza | Scegliere il percorso per le due varianti, le fonti e ciò che lo screenshot non può provare. | Ruolo delimitato; knowledge per la responsabilità di dominio; codice per wiring e firme; immagine per evidenza visiva. Il pattern legacy non prevale sulla regola. |
| 3. Gate e artifact | Risolvere se la motivazione serve anche per chiusure automatiche e trasformare l'approvazione in un record durevole. | La risposta cambia il requisito e va chiarita prima della modifica. Indicare gate, responsabile, stato, fonti e handoff; senza piano non scompaiono gli artifact. |
| 4. Validazione | La build è verde: si può dichiarare impossibile una chiusura senza motivazione? | No: servono prove del comportamento, inclusa una chiamata che evita la UI. Registrare cosa è stato verificato e chi produce le prove mancanti; Direct Implementor non crea test. |
| 5. Composizione | Collocare la regola di dominio, un limite del ruolo e la verifica che segnala drift. | Regola nel documento di knowledge proprietario; limite nel contratto del ruolo; le altre superfici instradano. Registrare la personalizzazione per la manutenzione. |

Il record seguente è un esercizio didattico, non un nuovo artifact obbligatorio del runtime. Direct Implementor espone i requisiti del Gate 3 solo in chat e persiste regole, risposte e stato nei gate dedicati.

## Record Del Gruppo

- Richiesta e variante:
- Ruolo scelto, output e azione vietata:
- Fonti e regole applicabili:
- Decisione ancora aperta, responsabile e risposta:
- Gate ed evidenza che ne consente il passaggio:
- Artifact durevole e proprietario:
- Verifica effettuata, risultato e cosa non dimostra:
- Prova mancante, rischio residuo e prossimo responsabile:

## Valutazione E Trasferimento

Attribuire 0 (assente), 1 (dichiarato) o 2 (motivato con evidenza) a: confine di autorità, qualità delle fonti, gate e record, validazione e rischio residuo. Il punteggio guida il debrief; non certifica un sistema di produzione.

**Domanda finale:** nel vostro repository quale evidenza cambierebbe questa scelta, e chi dovrebbe approvare il cambiamento? Far rispondere ogni gruppo con una decisione concreta, non con il nome di un agente.

## Prima, Dopo E Nel Proprio Repository

Prima della spiegazione, scrivere individualmente: “Deciderei … perché …; cambierei idea se …”. Dopo l'esercizio, annotare quale evidenza ha confermato o corretto la decisione e quale rischio resta aperto. Riutilizzare la stessa rubrica per confrontare le due risposte; non premiare il solo uso dei termini del corso.

Per trasferire il metodo, scegliere un task reale futuro e completare: failure mode osservato, fonte autorevole, modifica minima entro la propria autorità, verifica eseguibile e prerequisiti, esito atteso, risultato che farebbe rivedere la modifica. Dopo quel task aggiungere risultato effettivo, limite della prova e decisione di mantenimento. È una proposta di apprendimento, non un artifact runtime obbligatorio.
