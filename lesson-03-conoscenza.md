# 3. Conoscenza selettiva e governata

[Corso](README.md) · [Slide](slides/lesson-03-conoscenza.md) · [Caso guida](workshop-exercise.md)

**Principio: l'agente legge la conoscenza applicabile al task, nel momento in cui serve.** Caricare ogni documento mescola regole incompatibili e aumenta il rumore; cercare soltanto codice simile può ripetere un pattern vietato. Il [Planner Gate 4](system/canonical/agents/planner.agent.md) usa il catalogo per scegliere le fonti normative prima di decidere il design.

## Tre ambiti di lettura

| Ambito | Quando si legge | Nel caso guida |
| --- | --- | --- |
| MustHave | Sempre, prima del ragionamento governato dalla knowledge | Regola comune sui work item |
| PerContext | Quando il tipo di lavoro o il contesto lo richiede | Regola per modifiche API |
| PerComponent | Quando il task tocca il componente indicato | Regola del servizio Richieste |

Questi nomi sono usati dal [Planner canonical](system/canonical/agents/planner.agent.md). La guida del componente Fatture può sembrare simile ma non governa il servizio Richieste. Quando il contesto cambia, il Planner rivaluta le fonti PerContext e PerComponent e aggiorna l'inventario delle regole. Il principio è **selezione motivata**, non quantità di testo letto.

Il [Context Glossary](system/canonical/CONTEXT.md) stabilizza i termini; il knowledge index instrada verso documenti da leggere. Sono oggetti diversi. Il [knowledge guard](system/canonical/instructions/knowledge-guard.instructions.md) richiede a ogni nuova voce un trigger “When to read” specifico, un solo soggetto per file e fatti con una fonte verificabile. Se una fonte approvata non è disponibile, il workflow si ferma invece di inventare una regola.

## Come nasce e si mantiene una knowledge

La [Knowledge Builder](system/canonical/agents/knowledge-builder.agent.md) raccoglie aspettative ed evidenza del repository, prepara una knowledge focalizzata, chiede review e la salva nella fonte approvata con un intent che dica quando usarla. Il documento descrive regole applicabili, non un elenco di file copiato dal codice. Una nuova o rinominata knowledge deve essere registrata nell'indice secondo il [knowledge guard](system/canonical/instructions/knowledge-guard.instructions.md).

Quando codice, componenti o convenzioni cambiano, un fatto non più vero va corretto o rimosso. Il trigger di lettura va rivisto se carica task non pertinenti o esclude task pertinenti. Questo collega la qualità dell'output alla manutenzione della conoscenza, non solo alla bravura del modello.

## Una selezione controllabile

Per ogni fonte chiedere: “Quale decisione del task governa? Quale trigger la rende applicabile? Quale fonte più autorevole conferma il fatto?” Nel [caso guida](workshop-exercise.md) la regola API entra perché il requisito riguarda anche client esterni; la guida Fatture resta fuori perché non è coinvolta.

**Domanda di trasferimento:** quali documenti del tuo repository devono essere sempre letti, quali dipendono dal contesto e quali appartengono a un solo componente?
