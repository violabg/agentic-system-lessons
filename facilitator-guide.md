# Guida del Facilitatore

[Torna alla lettura principale](README.md) · [Principi](principles.md) · [Scaletta slide](slide-outline.md) · [Demo](live-demo-script.md)

## Prima del Corso

Ricordare in massimo cinque minuti i prerequisiti: agent, skill e custom instructions. Il corso inizia quando la domanda diventa: quali controlli trasformano questi blocchi in un sistema affidabile?

Mostrare un repository dimostrativo solo quando serve un'evidenza concreta, per non più di cinque minuti per lezione. Non modificare il repository demo durante il corso.

## Struttura di Ogni Sessione

| Minuti | Attività |
| --- | --- |
| 0-5 | Domanda di rischio: cosa può andare storto se questo controllo manca? |
| 5-15 | Spiegazione dell'obiettivo di controllo. |
| 15-22 | Mappa o diagramma Mermaid del principio. |
| 22-27 | Evidenza breve dal sistema canonical o dal demo. |
| 27-40 | Esercizio decisionale in coppia o gruppo. |
| 40-45 | Debrief: decisione, prova richiesta e trade-off. |

## Lezione 1: Ruoli e Autorità Delimitata

- Obiettivo: distinguere responsabilità da capacità generica del modello.
- Evidenza: [confronto dei percorsi](role-maps/README.md) e [Direct Implementor](role-maps/agents/direct-implementor.md).
- Esercizio: scegliere il percorso nelle due varianti del [caso condiviso](workshop-exercise.md), dichiarando output richiesto e azioni vietate.
- Debrief: analizzare e implementare nello stesso ruolo è possibile con autorità delimitata; Direct Implementor mantiene i gate e non crea test. Un piano approvato è il prerequisito di Implementor, non una regola universale.

## Lezione 2: Conoscenza Selettiva e Governata

- Obiettivo: distinguere glossario, knowledge index e documenti di conoscenza.
- Evidenza: [system/canonical/CONTEXT.md](../system/canonical/CONTEXT.md) e [knowledge guard](../system/canonical/instructions/knowledge-guard.instructions.md).
- Esercizio: selezionare fonti per un task di autorizzazione e giustificare quali restano escluse.
- Debrief: leggere tutto non equivale a sapere cosa governa una decisione.

## Lezione 3: Gate e Controllo Umano

- Obiettivo: progettare gate proporzionati al rischio.
- Evidenza: un gate di approvazione nel demo o in un workflow canonical.
- Esercizio: aggiungere due gate minimi a un flusso ambiguo.
- Debrief: un gate governa il momento del passaggio, non sostituisce la prova.

## Lezione 4: Artifact, Provenienza e Ownership

- Obiettivo: rendere il lavoro riprendibile e ispezionabile fuori dalla chat.
- Evidenza: [artifact e session instructions canonical](../system/canonical/instructions/planning-sessions.instructions.md).
- Esercizio: trasformare un'approvazione verbale in un record di handoff completo.
- Debrief: approvazione e immutabilità non sono implicite.

## Lezione 5: Validazione Come Evidenza

- Obiettivo: associare ogni handoff a una prova verificabile.
- Evidenza: validation commands del demo e contratti canonical.
- Esercizio: associare modifiche a artifact lint, controllo mirato, test, build o review.
- Debrief: la fiducia dell'agente non è un risultato di validazione.

## Lezione 6: Composizione e Ciclo di Vita

- Obiettivo: collocare ogni regola nella sua superficie proprietaria.
- Evidenza: root instructions come router, agent come contratti, skill come workflow e knowledge index come selettore.
- Esercizio: classificare sei modifiche nella superficie proprietaria e indicare l'output da aggiornare.
- Debrief: correggere un output generato non corregge la fonte.

## Lezione 7: Bootstrap e Adattamento Controllato

- Obiettivo: adattare un sistema al repository target senza cancellarne i controlli, poi ispezionare criticamente cio' che e' stato generato.
- Evidenza: slot registry, overlay policy, manifest e Bootstrap workflow public-safe.
- Esercizio: completare il record del [caso condiviso](workshop-exercise.md) con un binding senza MCP, una scelta di modello Vision e la verifica del contratto generato. Un fallback senza prerequisiti funzionanti resta bloccante.
- Debrief: Bootstrap e' un processo di progettazione e provenienza, non un installer. Un sistema generato va letto contro l'evidenza del repository prima di essere considerato adeguato.

## Criteri di Qualità

Una lezione è riuscita se gli studenti producono una decisione motivata da un obiettivo di controllo. Non valutare l'abilità di ricordare nomi di file, agent o comandi.

## Conduzione Del Caso Condiviso

Usare [Una richiesta, due percorsi](workshop-exercise.md) nei 13 minuti già previsti per ogni esercizio: 2 minuti di lettura, 7 di confronto, 4 per scrivere decisione e prova. Le soluzioni attese e la rubrica sono nella scheda; nel debrief chiedere prima la motivazione, poi mostrare la soluzione. Il caso non aggiunge una lezione e non richiede accesso a un repository privato.

Correggere esplicitamente questi equivoci:

- “Diretto significa senza controlli”: far individuare intervista, inventario normativo, build e review nella nuova mappa.
- “Ogni gate chiede conferma”: distinguere il controllo automatico dalla decisione umana prevista dal contratto; non saltare gate già prescritti.
- “Senza piano non resta nulla”: chiedere il record durevole di requisiti, risposte e verifiche.
- “Build verde significa requisito provato”: chiedere quale comportamento potrebbe ancora fallire e chi produce la prova mancante.
- “Serve sempre un MCP”: richiedere input, output e prerequisiti di un binding nativo o locale approvato.
- “L'upgrade copia i tool di un altro ruolo”: far cercare l'entry esatta del file nelle answers; se manca, serve una decisione.

Per lezione 7, far verificare anche lo schema YAML di test se Integration Tester è selezionato, la ripresa per ID noto senza enumerare sessioni, e il modello Vision se selezionato. I default ordinari basati su evidenza possono essere approvati insieme; le decisioni materiali irrisolte restano esplicite. Non usare una raccomandazione come se fosse approvazione.

[Torna alla lettura principale](README.md)
