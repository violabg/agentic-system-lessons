[Corso](../README.md) › [Principi](README.md) › **5. Conoscenza selettiva**

# 5. Conoscenza selettiva

> **In breve:** l'agente legge le regole che valgono per il task, nel momento in cui servono. Conta la scelta motivata delle fonti, non la quantità di testo letto.

[Slide](../slides/05-conoscenza-selettiva.md) · [Caso guida](../caso-guida.md)

## Il problema

L'agente cerca ovunque e adotta il primo pattern simile che trova nel codice. Oppure carica tutta la documentazione e mescola regole che valgono per componenti diversi. In entrambi i casi segue una regola sbagliata, o ne ignora una giusta.

## Il principio

Scegli fonti autorevoli e proporzionate al task, e registra quali bastano e perché. Due strumenti hanno ruoli diversi:

- **il glossario** stabilizza i nomi, i confini e le fonti di verità;
- **il catalogo della knowledge** indica i pochi documenti da leggere per un certo tipo di lavoro.

## Nel sistema di riferimento

**Il catalogo divide la knowledge in tre livelli.** Ogni documento dichiara il proprio livello e il suo *intent*, cioè quando leggerlo. Il [contratto del catalogo](../system/canonical/contracts/knowledge-catalog.md) li definisce:

| Livello | Quando si legge | Esempio nel caso guida |
| --- | --- | --- |
| `MustHave` | Sempre, per intero, prima di ragionare sul task | Regola sul changelog |
| `PerContext` | Quando il tipo di lavoro lo richiede | Regola per le modifiche alle API |
| `PerComponent` | Quando il task tocca quel componente | Regola del servizio Richieste |

**Prima le regole, poi il codice.** In ogni workflow lo step di knowledge legge solo la knowledge: non apre file di codice. Le regole decidono come scrivere il codice; il codice esistente serve per i contratti e il comportamento, non come modello da imitare.

**La knowledge è vincolante.** Una regola della knowledge prevale sul buon senso, sulle best practice e sul codice esistente. Un design che realizza il requisito ma viola una regola viene rifiutato. Se la knowledge contraddice il requisito, l'orchestrator non sceglie in silenzio: nel workflow `DESIGN` registra il conflitto, la regola e la scelta che lo risolve, e applica la regola; in `FAST_IMPLEMENTATION` registra un blocco e non cambia il comportamento richiesto.

**Si registra la regola, non il file.** In `DESIGN` e in `FAST_IMPLEMENTATION` ogni lettura di knowledge è seguita dalla registrazione delle sole prescrizioni che valgono per questo requisito: ogni [riferimento](../system/canonical/contracts/design-model.md#knowledge-references) è un intervallo di righe di un documento, con un ambito (`Production` o `Test`). Un documento può dare zero, una o molte prescrizioni; registrarlo intero perché è stato letto non è ammesso. Nel `DESIGN` le prescrizioni vincolano anche il design stesso: contratti, file, operazioni e decisioni dichiarano le regole su cui si fondano. In `FAST_IMPLEMENTATION` la tabella dei riferimenti è l'unica fonte della knowledge del job: ciò che non è registrato lì non conta come regola applicata.

**Leggere il codice è selettivo quanto leggere le regole.** In `DESIGN` e in `FAST_IMPLEMENTATION` l'orchestrator non cerca nel codice: legge direttamente solo i file di cui conosce già il percorso, perché li nomina il requisito, la knowledge, un artifact o il design. Ogni altro fatto lo chiede agli [Explorer](../role-maps/agents/explorer.md). Prima elenca i fatti che gli servono e li divide nei perimetri più piccoli e indipendenti; poi avvia un explorer per perimetro, tutti insieme, e passa a ciascuno ciò che già sa. Ogni explorer ha un limite di otto chiamate e restituisce posizioni verificate: percorso, riga ed estratto del codice. Un perimetro troppo grande si divide ancora, una risposta parziale non vale come fatto, e un fatto non trovato è una lacuna dichiarata, non un'ipotesi. Nel `DESIGN` ogni simbolo usato diventa un riferimento, con il file che lo definisce e i punti in cui è usato: un riferimento non letto non si inventa. In `DOCUMENTATION` l'orchestrator esplora da sé: comincia dalla mappa dei cluster e legge dichiarazioni e firme prima dei corpi. In tutti i casi la somiglianza non è pertinenza.

**La stessa knowledge per chi scrive e per chi giudica.** Nel workflow `DESIGN` ogni operazione elenca le prescrizioni che le servono, e il runtime le consegna al [Code Implementor](../role-maps/agents/code-implementor.md) con l'operazione: nessun bundle nel prompt. L'orchestrator rivede l'unità di lavoro con le stesse prescrizioni e chiede che il report dica quale regola è stata applicata e dove. In `FAST_IMPLEMENTATION` l'orchestrator unisce le regole lette in un *knowledge bundle*, registra le prescrizioni applicabili e implementa da quelle; prima di chiudere le rilegge una per una contro il codice.

**Si legge solo il delta.** Quando serve una regola nuova, l'agente legge solo i documenti che non ha ancora letto e annota quali ha ricordato e quali ha letto adesso. Una decisione presa su una knowledge non letta non è una decisione.

**Glossario e catalogo sono oggetti diversi.** Il [glossario canonical](../system/canonical/CONTEXT.md) dice che cosa significano i termini; il catalogo decide quali documenti leggere. Il [router del repository](../system/canonical/instructions/AGENTS.md) li tiene separati.

**La knowledge si mantiene.** Il [Knowledge Builder](../role-maps/agents/knowledge-builder.md) ricava una regola dal codice letto davvero, intervista lo sviluppatore su contenuto, struttura e uso, prepara una bozza, la fa approvare e la salva con un intent chiaro. Quando il codice cambia, un fatto non più vero va corretto.

## Nel caso guida

Il catalogo contiene quattro documenti: la regola sul changelog, la regola API, la regola del servizio Richieste e una guida per il componente Fatture. La guida Fatture sembra utile, ma non riguarda il servizio Richieste: resta fuori. La regola API aggiunge un comportamento funzionale al requisito e diventa un riferimento del design; l'orchestrator la usa per trovare, nel codice, una risposta di errore sbagliata. [Leggi la traccia](../caso-guida.md#traccia-2-knowledge).

## Nel tuo repository

- Quali documenti devono essere letti sempre, quali dipendono dal tipo di lavoro e quali appartengono a un solo componente?
- Chi verifica il lavoro del tuo agente lo fa con le stesse regole che hanno guidato chi lo ha scritto? Riesce a dire quale regola è stata applicata, e dove?

---

[← Precedente: 4. Artifact durevoli](04-artifact-durevoli.md) · [↑ Principi](README.md) · [Successivo: 6. Composizione e ciclo di vita →](06-composizione-e-ciclo-di-vita.md)
