# Scaletta Slide

[Torna alla lettura principale](README.md) · [Principi](principles.md) · [Guida del facilitatore](facilitator-guide.md)

Ogni lezione usa una slide di sintesi già disponibile e una sequenza narrativa di sette momenti. Non sono sette deck completi: il facilitatore sviluppa i momenti con evidenza ed esercizio. Usare una mappa Mermaid quando chiarisce una relazione; evitare slide che elencano file, tool o prompt senza una decisione da prendere.

## Struttura Ricorrente

1. Titolo del principio.
2. Failure mode quando il controllo manca.
3. Obiettivo di controllo.
4. Diagramma o modello decisionale.
5. Evidenza breve dal sistema.
6. Esercizio.
7. Decisione trasferibile.

Le slide pronte sono in [slides/README.md](slides/README.md). Ogni file rappresenta una slide e contiene un diagramma Mermaid leggibile anche senza presentazione.

## Lezione 1: Ruoli e Autorità

Failure mode: un agente amplia la propria autorità senza un contratto osservabile. Esercizio: confrontare Planner → Implementor e Direct Implementor nelle due varianti del caso condiviso. Takeaway: la specializzazione protegge responsabilità, non il prestigio di un ruolo. [Apri slide](slides/01-ruoli-e-autorita.md).

## Lezione 2: Conoscenza

Failure mode: ricerca larga e pattern legacy adottati come norma. Esercizio: scegliere fonti per un task e spiegare le esclusioni. Takeaway: la conoscenza giusta è selezionata, non massima. [Apri slide](slides/02-conoscenza.md).

## Lezione 3: Gate

Failure mode: implementazione prima di scope e approvazione verificabili. Esercizio: disegnare due gate proporzionati al rischio. Takeaway: un gate rende esplicito quando il sistema può avanzare. [Apri slide](slides/03-gate.md).

## Lezione 4: Artifact

Failure mode: una decisione vive solo nella memoria della chat. Esercizio: completare un handoff e, per la variante con piano, controllare navigazione e coverage dei rami distinti senza scambiarla per test eseguiti. Takeaway: la provenienza rende il lavoro riprendibile. [Apri slide](slides/04-artifact.md).

## Lezione 5: Validazione

Failure mode: una dichiarazione dell'agente sostituisce una prova. Esercizio: scegliere la prova più piccola che falsifica un esito errato. Takeaway: validare il rischio, non la fiducia. [Apri slide](slides/05-validazione.md).

## Lezione 6: Composizione

Failure mode: la stessa regola viene duplicata in tutte le superfici. Esercizio: assegnare una modifica alla sua ownership. Takeaway: correggere la fonte, poi propagare gli output. [Apri slide](slides/06-composizione.md).

## Lezione 7: Bootstrap

Failure mode: template installato senza evidenza, approvazione o lettura dei contratti generati. Esercizio: due ambienti target, binding approvato senza MCP e scelta Vision; distinguere preservazione deterministica, caricamento completo e verifica runtime, lasciando esplicito il client non verificato. Takeaway: adattare non significa riscrivere arbitrariamente; generare non significa aver finito di progettare. [Apri slide](slides/07-bootstrap.md).

Tutti gli esercizi possono usare il [caso condiviso con soluzioni attese](workshop-exercise.md). Collegare ogni decisione a una prova; i nomi dei ruoli servono a leggere il contratto, non a superare un quiz.

[Torna alla lettura principale](README.md)
