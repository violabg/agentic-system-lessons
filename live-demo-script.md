# Script per Demo Brevi

[Torna alla lettura principale](README.md) · [Guida del facilitatore](facilitator-guide.md) · [Mappa del sistema](system-map.md)

Le demo confermano un principio già spiegato. Non diventano un tour di repository e non modificano il repository dimostrativo.

## Regola Comune

Prima della demo, dire: "Cerchiamo una prova del controllo, non il modo corretto di organizzare tutti i repository." Dopo cinque minuti, fermare la navigazione e passare all'esercizio.

## Lezione 1: Ruoli

Aprire il [confronto dei percorsi](role-maps/README.md). In cinque minuti: 1 minuto sulla richiesta del [caso condiviso](workshop-exercise.md), 2 minuti sui vincoli di [Implementor](../system/canonical/agents/implementor.agent.md) e [Direct Implementor](../system/canonical/agents/direct-implementor.agent.md), 2 minuti per scegliere output, azione vietata e prova necessaria. Non invocare gli agenti: si confrontano contratti, non risultati di una live execution.

## Lezione 2: Conoscenza

Mostrare il router [AGENTS.md](../system/canonical/instructions/AGENTS.md), il [glossario canonical](../system/canonical/CONTEXT.md) e il [knowledge guard](../system/canonical/instructions/knowledge-guard.instructions.md). Chiedere quale file stabilizza termini, quale seleziona fonti e perché i due compiti non sono intercambiabili.

## Lezione 3: Gate

Mostrare una transizione da piano ad implementazione e i requisiti di approvazione. Confrontarla con intervista e validazione del design di Direct Implementor. Chiedere quale stato blocca ciascun percorso, quale prova lo sblocca e chi può approvare; non presentare il piano come l’unico gate possibile.

## Lezione 4: Artifact

Usare uno schema fittizio di inventario regole, risposte in memoria, log ed execution report. Chiedere cosa sopravvive alla chat senza un piano e quale record cambia dopo un refinement. Spiegare la ripresa della sola sessione nota per ID, senza enumerare altre sessioni.

## Lezione 5: Validazione

Mostrare i comandi di validation dichiarati dal sistema, senza eseguirli durante la lezione. Chiedere quale rischio controlla ogni comando e quale prova ulteriore può ancora mancare. Per Direct Implementor distinguere build e review dalla creazione di test, esclusa dal suo mandato; non mostrare esiti verdi inventati.

## Lezione 6: Composizione

Mostrare la mappa di [system-map.md](system-map.md) e il manifest del demo. Chiedere quale superficie possiede una regola e dove correggere il drift. Su un record fittizio, mostrare baseline, personalizzazione corrente e nuova versione: le answers si risolvono per il file del ruolo interessato, non prendendo i tool da un altro ruolo.

## Lezione 7: Bootstrap

Mostrare le [decisioni Bootstrap](../public-package/skills/agentic-system/bootstrap-agentic-system/contracts/discovery-and-decisions.md) e un record fittizio: capability necessaria → binding nativo o locale approvato → prerequisiti e prova. Aggiungere la scelta Vision tra modello esatto supportato e default della piattaforma approvato. Far leggere il contratto generato collegato alla scelta. Chiedere quale evidenza giustifica la scelta, cosa richiede conferma, quale assunzione va verificata nel repository target e quale record rende la generazione rivedibile.

[Torna alla lettura principale](README.md)
