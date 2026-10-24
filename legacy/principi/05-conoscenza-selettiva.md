[Corso](../README.md) › [Principi](README.md) › **5. Conoscenza selettiva**

# 5. Conoscenza selettiva

> **In breve:** l'agente legge le regole che valgono per il task, nel momento in cui servono. Conta la scelta motivata delle fonti, non la quantità di testo letto.

[Slide](../slides/05-conoscenza-selettiva.md) · [Caso guida](../caso-guida.md)

## Il problema

L'agente cerca ovunque e adotta il primo pattern simile che trova. Oppure carica tutta la documentazione e mescola regole che valgono per componenti diversi. In entrambi i casi segue una regola sbagliata, o ne ignora una giusta.

## Il principio

Scegli fonti autorevoli e proporzionate al task, e registra quali bastano e perché. Due strumenti hanno ruoli diversi:

- **il glossario** stabilizza i nomi, i confini e le fonti di verità;
- **l'indice della knowledge** indica i pochi documenti da leggere per un certo tipo di lavoro.

## Nel sistema di riferimento

Il [Planner](../role-maps/agents/planner.md) sceglie le regole prima di decidere il design (Gate 4). Il catalogo della knowledge divide i documenti in tre gruppi:

| Gruppo | Quando si legge | Esempio nel caso guida |
| --- | --- | --- |
| MustHave | Sempre, prima di ragionare sul task | Regola comune sui work item |
| PerContext | Quando il tipo di lavoro lo richiede | Regola per le modifiche alle API |
| PerComponent | Quando il task tocca quel componente | Regola del servizio Richieste |

Quando il contesto del task cambia, il Planner rivaluta le fonti PerContext e PerComponent e aggiorna l'elenco delle regole.

Il [glossario canonical](../system/canonical/CONTEXT.md) e l'indice della knowledge sono oggetti diversi. Le [regole sulla knowledge](../system/canonical/instructions/knowledge-guard.instructions.md) chiedono che ogni documento abbia un solo argomento, fatti con una fonte verificabile e un trigger “When to read” abbastanza preciso da non caricarlo per task non pertinenti. Se una fonte approvata non è disponibile, il workflow si ferma invece di inventare una regola.

**La knowledge si mantiene.** Il [Knowledge Builder](../role-maps/agents/knowledge-builder.md) ricava una regola dal repository, prepara una bozza, la fa approvare e la salva con un trigger chiaro. Quando il codice cambia, un fatto non più vero va corretto o rimosso. La skill [Integration Test Knowledge Checklist](../role-maps/skills/integration-test-knowledge-checklist.md) applica lo stesso approccio ai test di integrazione: guida la scrittura di una knowledge specifica del progetto, invece di affidarsi a consigli generici.

## Nel caso guida

Il catalogo contiene quattro documenti: la regola comune sui work item, la regola API, la regola del servizio Richieste e una guida per il componente Fatture. La guida Fatture sembra utile, ma non riguarda il servizio Richieste: resta fuori. La regola API entra perché il requisito vale anche per i client esterni. [Leggi la traccia](../caso-guida.md#traccia-2-knowledge).

## Nel tuo repository

- Quali documenti devono essere letti sempre, quali dipendono dal tipo di lavoro e quali appartengono a un solo componente?
- Per un cambiamento rischioso, quali due o tre fonti sono autorevoli e quali, pur plausibili, devono restare escluse?

---

[← Precedente: 4. Artifact durevoli](04-artifact-durevoli.md) · [↑ Principi](README.md) · [Successivo: 6. Composizione e ciclo di vita →](06-composizione-e-ciclo-di-vita.md)
