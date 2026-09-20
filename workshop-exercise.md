# Esercizio Trasversale: Una Richiesta, Due Percorsi

[Torna al corso](README.md) · [Conduzione](facilitator-guide.md) · [Scelta dei ruoli](role-maps/README.md)

**Caso fittizio:** un portale deve impedire la chiusura di una richiesta di assistenza senza motivazione. La knowledge assegna la regola al servizio di dominio. Una vecchia schermata controlla solo il browser. Lo screenshot mostra il campo, ma non definisce quando sia obbligatorio. Non serve un repository demo per svolgere l'esercizio.

**Obiettivo:** spiegare chi può decidere, quale evidenza lo autorizza e quale prova rende il risultato controllabile. Riutilizzare il caso nelle sette lezioni; ogni gruppo aggiunge una riga al proprio record.

| Lezione | Consegna in 13 minuti | Ragionamento atteso per il facilitatore |
| --- | --- | --- |
| 1. Ruoli | Scegliere il percorso per due varianti: A richiede un piano approvabile da un altro team; B richiede implementazione dai requisiti senza documento di piano. | A: Planner → Implementor. B: Direct Implementor, mantenendo intervista e gate. Se la richiesta include nuovi test, assegnare un workflow autorizzato separato. |
| 2. Conoscenza | Scegliere fonti, indicare cosa lo screenshot non può provare. | Knowledge per la responsabilità di dominio; codice per wiring e firme; immagine per evidenza visiva. Il pattern legacy non prevale sulla regola. |
| 3. Gate | Risolvere se la motivazione serve anche per chiusure automatiche; indicare il gate che blocca. | La risposta cambia il requisito e va chiarita prima della modifica. Nel percorso diretto, intervista e validazione del design svolgono questo controllo senza inventare un piano. |
| 4. Artifact | Compilare il record sotto; indicare cosa riusare al cambio di collega. | Fonti, risposta, regole, stato e prove devono sopravvivere alla chat anche nel percorso senza piano. Riprendere solo la sessione nota. |
| 5. Validazione | La build è verde: si può dichiarare impossibile una chiusura senza motivazione? | No: servono prove del comportamento, inclusa una chiamata che evita la UI. Registrare cosa è stato davvero verificato e chi produce le prove mancanti; Direct Implementor non crea test. |
| 6. Composizione | Collocare la regola di dominio e un nuovo limite del ruolo. | Regola nel documento di knowledge proprietario; limite nel contratto del ruolo. Le altre superfici instradano. Registrare le personalizzazioni per la manutenzione. |
| 7. Bootstrap | La piattaforma non ha subagent o MCP; Vision è richiesto per lo screenshot. Proporre binding, modello e verifica. | Valutare strumenti nativi o fallback approvati e operazioni inline previste, verificandone i prerequisiti. Decidere modello Vision supportato o default approvato; bloccare ciò che resta indisponibile. |

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
- Binding di capability, prerequisiti e scelta approvata:
- Contratto generato da ispezionare e criterio di correzione:

## Valutazione E Trasferimento

Attribuire 0 (assente), 1 (dichiarato) o 2 (motivato con evidenza) a: confine di autorità, qualità delle fonti, gate e record, validazione e rischio residuo. Il punteggio guida il debrief; non certifica un sistema di produzione.

**Domanda finale:** nel vostro repository quale evidenza cambierebbe questa scelta, e chi dovrebbe approvare il cambiamento? Far rispondere ogni gruppo con una decisione concreta, non con il nome di un agente.
