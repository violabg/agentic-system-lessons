[Corso](../README.md) › [Principi](README.md) › **4. Artifact durevoli**

# 4. Artifact durevoli

> **In breve:** ciò che un altro ruolo deve sapere non può restare nella chat. Decisioni, approvazioni e stato vanno salvati in file stabili, con un responsabile e una ragione per esistere.

[Slide](../slides/04-artifact-durevoli.md) · [Caso guida](../caso-guida.md)

## Il problema

Decisioni, domande aperte e risultati delle verifiche restano nella memoria di una conversazione. Quando la conversazione finisce, o quando il lavoro passa a un altro ruolo, nessuno può ricostruire **perché** una scelta è stata fatta. Il lavoro non si può riprendere né controllare.

## Il principio

Salva in artifact stabili le informazioni che un altro ruolo deve poter verificare: decisioni, fonti, approvazioni, rischi, stato e criterio di completamento. Ogni artifact ha un proprietario e una ragione per esistere.

La chat può contenere un'approvazione, ma l'artifact ne conserva la traccia. L'handoff si basa sull'artifact, non sulla chat.

## Nel sistema di riferimento

**La sessione di pianificazione** raccoglie ticket, chiarimenti, regole selezionate, piano, approvazione e stato. Le [regole delle sessioni di pianificazione](../system/canonical/instructions/planning-sessions.instructions.md) stabiliscono che cosa deve sopravvivere alla chat.

**Il piano è un artifact.** Il [Planner](../role-maps/agents/planner.md) lo scrive secondo lo [schema del piano](../system/canonical/templates/plan-schema.md): file, modifiche, operazioni e scenari di copertura. Così l'Implementor lavora su una decisione già controllata, invece di ricostruirla dalla conversazione.

**L'implementazione parte da un contesto pulito.** Dopo l'approvazione, l'[Implementor](../role-maps/agents/implementor.md) lavora in una nuova conversazione. Riceve l'ID della sessione, carica il piano approvato e gli artifact pertinenti. Il contesto pulito è un test: se un dettaglio esisteva solo nella vecchia chat, l'handoff era incompleto. La nuova conversazione non crea una nuova sessione: riprende quella esistente.

**Non tutto diventa un artifact.** Nel Planner, la scomposizione del requisito (Gate 3) resta in chat; le decisioni rilevanti vengono salvate nei punti previsti dal contratto. Anche il [Direct Implementor](../role-maps/agents/direct-implementor.md), che non produce un piano, salva l'elenco delle regole, le risposte, il log e il report di esecuzione. Il nome “Planning Session ID” identifica la cartella di lavoro: non garantisce che un piano esista.

Il tuo repository non deve usare gli stessi nomi di file. Deve rendere durevoli le stesse informazioni.

## Nel caso guida

La decisione “una motivazione di soli spazi non è valida” deve comparire nel requisito chiarito e nel piano. Se l'Implementor, in una nuova conversazione, non riesce a ritrovarla, il passaggio è incompleto. [Leggi la traccia](../caso-guida.md#traccia-3-piano-e-handoff).

## Nel tuo repository

- Quale traccia permetterebbe a una persona nuova di capire perché una modifica è stata approvata e che cosa resta da verificare?
- Quale decisione del tuo team oggi vive solo in una chat?

---

[← Precedente: 3. Validazione come prova](03-validazione-come-prova.md) · [↑ Principi](README.md) · [Successivo: 5. Conoscenza selettiva →](05-conoscenza-selettiva.md)
