# Corso: Sistemi Agentici Enterprise

Questo è il documento di lettura principale del corso.

**Inizia da [Perché un sistema agentico](introduction.md) e dalla [Lezione 1](lesson-01-introduzione.md):** il problema da risolvere, cosa imparare, limiti e trasferimento nel proprio progetto. Questa cartella è la fonte per preparare le lezioni, non un sistema da installare integralmente.

Questo corso insegna a sviluppatori esperti come riconoscere, usare e adattare i principi di un sistema agentico enterprise. Agent, skill e custom instructions sono esempi dei contratti che compongono il sistema.

Il corso è principle-first. Il sistema canonical è una reference implementation, non una forma da copiare. Un repository dimostrativo può essere mostrato per pochi minuti come prova concreta di un principio, ma non è il centro della lezione.

## Idea Da Portare Al Team

Per ogni modifica devono essere ricostruibili tre risposte: **chi può decidere, su quale evidenza, con quale verifica**. I sei principi sviluppano queste tre domande. Un piano è uno degli artifact possibili; il controllo non scompare quando il percorso non lo prevede.

Usare l'[esercizio trasversale](workshop-exercise.md) per collegare le lezioni allo stesso caso. Il [confronto dei percorsi](role-maps/README.md) distingue Planner → Implementor da Direct Implementor.

## Risultati Attesi

Al termine, ogni partecipante sa:

- spiegare perché un sistema agentico enterprise è un sistema operativo locale al repository, non una raccolta di prompt;
- individuare controlli mancanti in un workflow non affidabile;
- distinguere la variabilità del modello dalla verificabilità del lavoro, senza promettere determinismo;
- distinguere ruoli, conoscenza, gate, artifact, validazione e ownership;
- valutare se una personalizzazione preserva il principio che la giustifica;
- trasferire i principi a un repository target senza copiare meccanicamente una struttura;
- affinare conoscenza, regole e verifiche a partire dagli errori osservati nel lavoro quotidiano.

## Percorso

| Lezione | Principio | Decisione che gli studenti imparano a prendere |
| --- | --- | --- |
| 1 | Introduzione: il problema e le sei leve | Quali controlli rendono il vibe coding osservabile e trasferibile? |
| 2 | Autorità delimitata e conoscenza selettiva | Chi può decidere e quali fonti governano questo task? |
| 3 | Gate, controllo umano e artifact durevoli | Quale evidenza consente il passaggio e quale record deve sopravvivere? |
| 4 | Validazione come evidenza | Quale prova può smentire il risultato e quale rischio resta aperto? |
| 5 | Composizione, ownership e ciclo di vita | Dove vive la regola e come si corregge il drift? |

Ogni lezione dura 45 minuti e termina con un esercizio breve. Le lezioni sono ordinate per costruire il modello, ma ogni principio resta trasferibile a un repository diverso.

## Materiali

- [introduction.md](introduction.md): motivazione, obiettivi, limiti e primo trasferimento al proprio progetto.
- [lesson-01-introduzione.md](lesson-01-introduzione.md): quadro introduttivo e modello del corso.
- [lesson-02-autorita-e-conoscenza.md](lesson-02-autorita-e-conoscenza.md): ruoli e conoscenza selettiva.
- [lesson-03-gate-e-artifact.md](lesson-03-gate-e-artifact.md): gate, controllo umano e artifact.
- [lesson-04-validazione.md](lesson-04-validazione.md): prove, limiti e rischio residuo.
- [lesson-05-composizione-e-ciclo-di-vita.md](lesson-05-composizione-e-ciclo-di-vita.md): ownership e manutenzione.
- [principles.md](principles.md): riferimento sintetico per i sei principi.
- [slides/README.md](slides/README.md): materiali visuali di supporto alle cinque lezioni.
- [role-maps/README.md](role-maps/README.md): mappe visuali di agent e skill canonical.
- [system-map.md](system-map.md): mappe Mermaid del modello e delle sue superfici.

## Confini

Il corso non modifica codice applicativo e non insegna workflow privati come verita' universali. Per contenuti nuovi o modificati, usare i riferimenti canonical pubblicati accanto a questo corso come evidenza. Il sistema del repository target resta soggetto a lettura, verifica e manutenzione del team.

_Navigazione: sei nella lettura principale._
