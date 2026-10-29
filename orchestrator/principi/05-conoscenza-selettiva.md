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

**Prima le regole, poi il codice.** In ogni workflow lo step di knowledge legge solo la knowledge: non apre file di codice. Solo dopo arriva la ricognizione del codice. Le regole decidono come scrivere il codice; il codice esistente serve per i contratti e il comportamento, non come modello da imitare.

**La knowledge è vincolante.** Una regola della knowledge prevale sul buon senso, sulle best practice e sul codice esistente. Un design che realizza il requisito ma viola una regola viene rifiutato. Se la knowledge contraddice il requisito, l'orchestrator non sceglie in silenzio: nel workflow `DESIGN` il conflitto diventa una domanda da decidere, in `FAST_IMPLEMENTATION` un blocco.

**Leggere il codice è selettivo quanto leggere le regole.** La ricognizione del codice costruisce un panorama dei soli componenti coinvolti e delle lacune rispetto al requisito. Legge dichiarazioni e firme prima dei corpi, non segue catene di dipendenze e non sceglie un file perché “sembra simile”: la somiglianza non è pertinenza.

**La stessa knowledge per chi scrive e per chi giudica.** In `FAST_IMPLEMENTATION` l'orchestrator unisce le regole lette in un *knowledge bundle* e lo passa invariato al [Code Implementor](../role-maps/agents/code-implementor.md) e all'[Implementation Verifier](../role-maps/agents/implementation-verifier.md). Nel workflow `DESIGN` l'implementor riceve i riferimenti alla knowledge di ogni operazione servita, mentre il verificatore riceve il bundle. In entrambi i casi il verificatore giudica il codice con le stesse regole che lo hanno governato.

**Si legge solo il delta.** Quando serve una regola nuova, l'agente legge solo i documenti che non ha ancora letto e annota quali ha ricordato e quali ha letto adesso. Una decisione presa su una knowledge non letta non è una decisione.

**Glossario e catalogo sono oggetti diversi.** Il [glossario canonical](../system/canonical/CONTEXT.md) dice che cosa significano i termini; il catalogo decide quali documenti leggere. Il [router del repository](../system/canonical/instructions/AGENTS.md) li tiene separati.

**La knowledge si mantiene.** Il [Knowledge Builder](../role-maps/agents/knowledge-builder.md) ricava una regola dal codice letto davvero, intervista lo sviluppatore su contenuto, struttura e uso, prepara una bozza, la fa approvare e la salva con un intent chiaro. Quando il codice cambia, un fatto non più vero va corretto.

## Nel caso guida

Il catalogo contiene quattro documenti: la regola sul changelog, la regola API, la regola del servizio Richieste e una guida per il componente Fatture. La guida Fatture sembra utile, ma non riguarda il servizio Richieste: resta fuori. La regola API aggiunge un comportamento funzionale al requisito, e l'implementation verifier la usa per trovare una risposta di errore sbagliata. [Leggi la traccia](../caso-guida.md#traccia-2-knowledge).

## Nel tuo repository

- Quali documenti devono essere letti sempre, quali dipendono dal tipo di lavoro e quali appartengono a un solo componente?
- Chi verifica il lavoro del tuo agente lo fa con le stesse regole che hanno guidato chi lo ha scritto?

---

[← Precedente: 4. Artifact durevoli](04-artifact-durevoli.md) · [↑ Principi](README.md) · [Successivo: 6. Composizione e ciclo di vita →](06-composizione-e-ciclo-di-vita.md)
