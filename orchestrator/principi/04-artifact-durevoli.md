[Corso](../README.md) › [Principi](README.md) › **4. Artifact durevoli**

# 4. Artifact durevoli

> **In breve:** ciò che un altro ruolo deve sapere non può restare nella chat. Requisito, decisioni, approvazioni e stato vanno salvati in file stabili, con un responsabile e una ragione per esistere.

[Slide](../slides/04-artifact-durevoli.md) · [Caso guida](../caso-guida.md)

## Il problema

Requisito, decisioni e risultati delle verifiche restano nella memoria di una conversazione. Dopo qualche ora di lavoro l'agente ricorda il requisito “a modo suo”. Quando il lavoro passa a un altro ruolo, nessuno può ricostruire **perché** una scelta è stata fatta. Il lavoro non si può riprendere né controllare.

## Il principio

Salva in artifact stabili le informazioni che un altro ruolo deve poter verificare: requisito, decisioni, fonti, approvazioni, rischi, stato e criterio di completamento. Ogni artifact ha un proprietario e una ragione per esistere.

La chat può contenere un'approvazione, ma l'artifact ne conserva la traccia. L'handoff si basa sull'artifact, non sulla chat.

## Nel sistema di riferimento

**La sessione è il registro del lavoro.** Il [session store](../system/canonical/contracts/session-store.md) tiene, per ogni sessione, la memoria, il log degli eventi, gli artifact, i job e i design. Memoria ed eventi sono separati: la memoria conserva fatti validati e puntatori agli artifact, mai una loro copia; il log conserva azioni, decisioni ed errori. Una sessione si crea o si riprende solo su richiesta esplicita dello sviluppatore.

**Il requisito diventa obbligazioni durevoli.** L'orchestrator scompone il requisito in obbligazioni atomiche salvate nel design; ogni obbligazione porta la citazione esatta della frase da cui deriva (`sourceRef` e `sourceSpan`). Da lì in poi requisito e verifica si leggono da quelle obbligazioni, non dal ricordo della conversazione, e cambiano solo se lo sviluppatore rivede il requisito.

**Le richieste particolari diventano un registro.** Le istruzioni dello sviluppatore sul processo (“salta l'intervista”, “rispondi in italiano”) finiscono nel `user_instruction_register_<jobId>`, parola per parola, con i loro effetti scritti come condizioni. Il runtime lo allega a ogni istruzione successiva, così non si perde a metà workflow.

**Il design è un artifact strutturato, non un documento libero.** Obbligazioni, decisioni, contratti, file, operazioni e iterazioni vivono nel [modello del design](../system/canonical/contracts/design-model.md) e cambiano solo attraverso le operazioni del runtime. Gli id (`O1`, `D2`, `IM3`) non vengono mai rinumerati: una decisione citata ieri è la stessa oggi. Una modifica manuale del file viene rifiutata da ogni operazione successiva finché non viene annullata o rivista e risigillata.

**Il documento di review è una vista.** Il runtime rigenera il documento HTML del design a ogni scrittura: è ciò che lo sviluppatore legge per approvare, non un file da modificare. L'approvazione è permanente; una modifica successiva viene registrata nella storia e il documento mostra “Approved, modified after approval”. [Come si legge il documento](../reference/documento-di-design.md).

**L'implementazione lascia una traccia propria.** Ogni round di implementazione è un'iterazione. Quando si apre, il runtime fotografa il workspace; quando si chiude, calcola lui i file aggiunti, modificati ed eliminati. L'elenco dei file non dipende da ciò che l'agente ricorda di aver toccato.

**Il contesto pulito è un test dell'handoff.** I delegate partono senza la conversazione dell'orchestrator e ricevono solo identificatori: leggono obbligazioni, design e immagini dalla sessione. Se un dettaglio esisteva solo nella chat, il delegate non lo trova, e l'handoff era incompleto.

**Non tutto diventa un artifact.** `FAST_IMPLEMENTATION` non produce un documento di design né un'approvazione, ma tiene obbligazioni, punti aperti e riferimenti alla knowledge in un job design; il panorama del codice finisce nella memoria della sessione e la knowledge in un bundle passato ai delegate. `DOCUMENTATION` salva come artifact il documento finale.

Il tuo repository non deve usare gli stessi nomi di file. Deve rendere durevoli le stesse informazioni.

## Nel caso guida

La decisione su “solo spazi” è la decisione `D1` del design, con la risposta scelta e le alternative. La regola “una richiesta chiusa non si modifica” è un'obbligazione con origine `Developer`. Il code implementor, che non ha mai visto la conversazione, le trova entrambe nel design. L'iterazione `IT1` registra i file cambiati e le verifiche eseguite. [Leggi la traccia](../caso-guida.md#traccia-4-implementazione-e-prove).

## Nel tuo repository

- Quale traccia permetterebbe a una persona nuova di capire perché una modifica è stata approvata e che cosa resta da verificare?
- Il tuo agente rilegge il requisito da un file, o dal ricordo della conversazione?

---

[← Precedente: 3. Validazione come prova](03-validazione-come-prova.md) · [↑ Principi](README.md) · [Successivo: 5. Conoscenza selettiva →](05-conoscenza-selettiva.md)
