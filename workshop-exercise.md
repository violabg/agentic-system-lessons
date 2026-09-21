# Caso guida: chiusura di una richiesta

[Corso](README.md) · [Principi](principles.md)

Queste tracce sono **inventate per la lezione**. Non sono log prodotti dal sistema canonical. Ogni lezione usa solo un frammento, poi torna al principio che quel frammento illustra. Le brevi domande sono facoltative e non richiedono lavoro di gruppo.

## Richiesta iniziale

> Come operatore, voglio chiudere una richiesta solo dopo aver inserito una motivazione.

La story non specifica se il vincolo vale solo nell'interfaccia o anche per chiamate API, quale testo conta come motivazione, come si trattano richieste già chiuse e quale risposta deve ricevere un client rifiutato. Sono decisioni di prodotto, non dettagli che il Planner può inventare.

## Traccia 1: intake e chiarimento

- La [skill Plan User Story From Id](role-maps/skills/plan-user-story-from-id.md) recupera descrizione, acceptance criteria, commenti e relazioni dal ticket ID in un artifact di sessione.
- Il [Planner](role-maps/agents/planner.md) espone le lacune del requisito e chiede quali comportamenti sono attesi.
- Risposta fittizia dello stakeholder: il vincolo vale per UI e API; spazi vuoti non sono una motivazione; una richiesta già chiusa non si modifica.

**Domanda breve:** quale di queste risposte sarebbe pericoloso lasciare soltanto nella chat?

## Traccia 2: knowledge

Il catalogo fittizio contiene una regola MustHave sulla gestione dei work item, una regola PerContext per le modifiche API e una regola PerComponent sul servizio Richieste. Una guida per il componente Fatture è plausibile ma non applicabile. Il [Planner Gate 4](system/canonical/agents/planner.agent.md) seleziona le fonti in base al task; il [knowledge guard](system/canonical/instructions/knowledge-guard.instructions.md) richiede un trigger “When to read” specifico.

**Domanda breve:** se la soluzione aggiunge un flusso batch che usa lo stesso servizio, quale contesto va rivalutato?

## Traccia 3: piano e handoff

Il Planner conserva l'evidenza del ticket, i chiarimenti, l'inventario normativo e il piano nella sessione nota. Il piano descrive la modifica al servizio e scenari di coverage per motivazione vuota, richiesta già chiusa e chiusura valida. Dopo approvazione esplicita, un nuovo dialogo con [Implementor](role-maps/agents/implementor.md) riceve l'ID della sessione, carica il piano approvato e legge gli artifact pertinenti.

**Domanda breve:** se l'Implementor non può ricostruire perché “solo spazi” è invalido, quale evidenza manca nell'handoff?

## Traccia 4: prove

La build fittizia passa. La review rileva che l'API rifiuta la motivazione vuota. Con approvazione esplicita del lavoro opzionale sui test, l'Implementor crea i test unitari pianificati ed esegue la suite pertinente: tre scenari passano. Il report registra comandi, risultati e limiti; non dichiara provati i client esterni mai eseguiti.

**Domanda breve:** quale affermazione sostiene la build e quale sostengono i test?

## Trasferimento

Davanti a un errore reale nel proprio repository: nominare il failure mode, scegliere il controllo mancante, trovare la superficie che lo possiede, fare una modifica minima e osservare una prova che potrebbe smentire il miglioramento. La [mappa del ciclo di manutenzione](system-map.md) mostra questo percorso.
