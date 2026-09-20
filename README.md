# Corso: Sistemi Agentici Enterprise

Questo è il documento di lettura principale del corso.

**Inizia da [Perché un sistema agentico](introduction.md):** il problema da risolvere, cosa imparare, limiti e trasferimento nel proprio progetto. Questa cartella è la fonte per preparare le lezioni, non un sistema da installare integralmente.

Questo corso insegna a sviluppatori esperti come riconoscere, usare e adattare un sistema agentico enterprise. Agent, skill e custom instructions sono prerequisiti richiamati dal facilitatore fuori dalle sette lezioni.

Il corso è principle-first. Il sistema canonical è una reference implementation, non una forma da copiare. Il Bootstrap public-safe produce un punto di partenza che va letto, verificato e adattato al repository target; non sostituisce il giudizio del team. Un repository dimostrativo può essere mostrato per pochi minuti come prova concreta di un principio, ma non è il centro della lezione.

## Idea Da Portare Al Team

Per ogni modifica devono essere ricostruibili tre risposte: **chi può decidere, su quale evidenza, con quale verifica**. I sette principi sviluppano queste tre domande. Un piano è uno degli artifact possibili; il controllo non scompare quando il percorso non lo prevede.

Usare l'[esercizio trasversale](workshop-exercise.md) per collegare le lezioni allo stesso caso. Il [confronto dei percorsi](role-maps/README.md) distingue Planner → Implementor da Direct Implementor; la [baseline](core-principles-baseline.md) riporta le release considerate e le fonti delle novità.

## Risultati Attesi

Al termine, ogni partecipante sa:

- spiegare perché un sistema agentico enterprise è un sistema operativo locale al repository, non una raccolta di prompt;
- individuare controlli mancanti in un workflow non affidabile;
- distinguere la variabilità del modello dalla verificabilità del lavoro, senza promettere determinismo;
- distinguere ruoli, conoscenza, gate, artifact, validazione e ownership;
- valutare se una personalizzazione preserva il principio che la giustifica;
- preparare un Bootstrap decision record basato su evidenza del repository target;
- ispezionare i contratti generati, verificare le loro assunzioni e individuare il lavoro manuale necessario per rendere il sistema adatto al repository.
- affinare conoscenza, regole e verifiche a partire dagli errori osservati nel lavoro quotidiano.

## Percorso

| Lezione | Principio | Decisione che gli studenti imparano a prendere |
| --- | --- | --- |
| 1 | Ruoli e autorità delimitata | Quale responsabilità non può cambiare autorità in silenzio? |
| 2 | Conoscenza selettiva e governata | Quale fonte è necessaria e autorevole per questo task? |
| 3 | Gate e controllo umano | Dove il rischio richiede prova o approvazione prima di avanzare? |
| 4 | Artifact, provenienza e ownership | Quale record deve sopravvivere alla conversazione e chi lo possiede? |
| 5 | Validazione come evidenza | Quale prova dimostra davvero che il handoff è affidabile? |
| 6 | Composizione e ciclo di vita | Dove vive una regola e come si evita drift fra superfici? |
| 7 | Bootstrap e adattamento controllato | Quali decisioni possono essere inferite e quali richiedono approvazione? |

Ogni lezione dura 45 minuti e termina con un esercizio breve. Le lezioni sono ordinate per costruire il modello, ma ogni principio resta trasferibile a un repository diverso.

## Materiali

- [introduction.md](introduction.md): motivazione, obiettivi, limiti e primo trasferimento al proprio progetto.
- [principles.md](principles.md): fonte didattica per i sette principi.
- [core-principles-baseline.md](core-principles-baseline.md): fonti canonical consentite e regole di allineamento.
- [facilitator-guide.md](facilitator-guide.md): conduzione delle sette sessioni.
- [slide-outline.md](slide-outline.md): struttura dei deck.
- [slides/README.md](slides/README.md): sette slide pronte per la lezione.
- [role-maps/README.md](role-maps/README.md): mappe visuali di agent e skill canonical.
- [live-demo-script.md](live-demo-script.md): demo brevi basate su evidenza, non su spettacolo.
- [system-map.md](system-map.md): mappe Mermaid del modello e delle sue superfici.
- [skills/teach/SKILL.md](skills/teach/SKILL.md): contratto per mantenere il corso allineato al sistema canonical.

## Confini

Il corso non modifica codice applicativo e non insegna workflow privati come verita' universali. Per contenuti nuovi o modificati, usare il sistema canonical e il public-safe package come evidenza. Il sistema generato nel repository target resta soggetto a lettura, verifica e manutenzione del team.

_Navigazione: sei nella lettura principale._
