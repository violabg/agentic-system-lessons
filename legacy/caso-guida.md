[Corso](README.md) › **Caso guida**

# Caso guida: chiudere una richiesta con motivazione

Questo caso è **inventato per il corso**: le tracce non sono log reali del sistema canonical. Ogni pagina dei principi ne usa un frammento per rendere concreta un'idea. Le domande brevi sono facoltative.

## La richiesta

> Come operatore, voglio chiudere una richiesta solo dopo aver inserito una motivazione.

Sembra semplice, ma la story non dice:

- se il vincolo vale solo nell'interfaccia o anche per le chiamate API;
- quale testo conta come motivazione;
- che cosa succede a una richiesta già chiusa;
- quale risposta riceve un client rifiutato.

Sono decisioni di prodotto. Il Planner non può inventarle.

## Traccia 1: richiesta e chiarimento

Principio: [1. Autorità delimitata](principi/01-autorita-delimitata.md)

- La skill [Plan User Story From Id](role-maps/skills/plan-user-story-from-id.md) recupera dal ticket descrizione, criteri di accettazione, commenti e relazioni, e li salva nella sessione.
- Il [Planner](role-maps/agents/planner.md) mostra le lacune del requisito e chiede quale comportamento è atteso.
- Lo stakeholder risponde: il vincolo vale per interfaccia e API; una motivazione di soli spazi non è valida; una richiesta già chiusa non si modifica.

**Domanda breve:** quale di queste risposte sarebbe pericoloso lasciare solo nella chat?

## Traccia 2: knowledge

Principio: [5. Conoscenza selettiva](principi/05-conoscenza-selettiva.md)

Il catalogo contiene una regola MustHave sui work item, una regola PerContext per le modifiche alle API e una regola PerComponent sul servizio Richieste. Contiene anche una guida per il componente Fatture: plausibile, ma non applicabile. Il [Planner](role-maps/agents/planner.md) sceglie le fonti in base al task (Gate 4).

**Domanda breve:** se la soluzione aggiunge un processo batch che usa lo stesso servizio, quali fonti vanno rivalutate?

## Traccia 3: piano e handoff

Principi: [2. Gate e controllo umano](principi/02-gate-e-controllo-umano.md) · [4. Artifact durevoli](principi/04-artifact-durevoli.md)

Il Planner salva nella sessione il ticket, i chiarimenti, l'elenco delle regole e il piano. Il piano descrive la modifica al servizio e tre scenari di copertura: chiusura valida, motivazione vuota, richiesta già chiusa. L'utente approva il piano in modo esplicito. Poi una nuova conversazione con l'[Implementor](role-maps/agents/implementor.md) riceve l'ID della sessione, carica il piano approvato e legge gli artifact pertinenti.

**Domanda breve:** se l'Implementor non riesce a capire perché “solo spazi” non è valido, che cosa manca nell'handoff?

## Traccia 4: prove

Principio: [3. Validazione come prova](principi/03-validazione-come-prova.md)

La build passa. La revisione conferma che l'API rifiuta una motivazione vuota. L'utente approva la creazione dei test unitari pianificati; l'Implementor li scrive ed esegue la suite pertinente: i tre scenari passano. Il report registra comandi, risultati e limiti. Non dichiara provati i client esterni, che nessuno ha eseguito.

**Domanda breve:** quale affermazione sostiene la build, e quale sostengono i test?

## Applicare il ciclo al tuo repository

Principio: [6. Composizione e ciclo di vita](principi/06-composizione-e-ciclo-di-vita.md)

Davanti a un errore reale: descrivilo, individua il controllo mancante, trova la superficie che lo possiede, fai una modifica minima e cerca una prova che potrebbe smentire il miglioramento. Il [ciclo di manutenzione](reference/mappa-del-sistema.md#ciclo-di-manutenzione) mostra questo percorso.

---

[↑ Torna al corso](README.md)
