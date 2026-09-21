# Corso: capire e migliorare un Agentic System

Questo corso in italiano è per sviluppatori che hanno già usato un coding agent. Presenta il sistema canonical come una soluzione concreta al problema di rendere il lavoro degli agenti **ispezionabile e correggibile**. Gli studenti possono poi usare il bootstrap skill o costruire un sistema proprio; il corso non insegna il funzionamento interno del bootstrap.

La domanda guida è: **chi può decidere, con quale conoscenza, quale prova e quale record per il ruolo successivo?**

## Percorso

| Lezione | Domanda centrale | Principio visibile |
| --- | --- | --- |
| [1. Orientarsi nel sistema](lesson-01-introduzione.md) | Quali agent e skill abbiamo, quando servono e come scorre il lavoro? | Sistema e flusso Planner → Implementor |
| [2. Dalla story al piano](lesson-02-richiesta-e-planner.md) | Perché la qualità della richiesta e il mandato del Planner contano? | Autorità delimitata e chiarimento |
| [3. Conoscenza selettiva](lesson-03-conoscenza.md) | Quale conoscenza leggere, quando e come mantenerla? | MustHave, PerContext, PerComponent |
| [4. Gate e handoff](lesson-04-gate-e-handoff.md) | Che cosa autorizza il passaggio dal piano all'implementazione? | Gate, artifact, sessione e contesto pulito |
| [5. Implementazione e prove](lesson-05-implementazione-e-prove.md) | Quali prove sostengono il risultato? | Build, review, unit test e rischio residuo |
| [6. Migliorare il proprio sistema](lesson-06-migliorare-il-sistema.md) | Come correggere un limite emerso nel lavoro reale? | Composizione, ownership e ciclo di vita |

[Slide](slides/README.md) · [Caso guida breve](workshop-exercise.md) · [Principi](principles.md) · [Biblioteca canonical](reference/README.md)

## Come si usa il materiale

La prima lezione mostra l'intero percorso prima dei dettagli. Le lezioni successive spiegano il failure mode, il principio, la scelta canonical e una domanda di trasferimento. Un unico caso fittizio offre esempi brevi; non è un'esecuzione reale né un esercizio lungo. Le domande in aula richiedono solo interventi brevi.

Quando una lezione nomina un contratto canonical, ne offre il link. Le [mappe di agent e skill](role-maps/README.md) restano riferimenti consultabili, con diagrammi e collegamenti alle fonti. La [mappa approfondita del flusso](slides/reference-flow.md) riassume ogni gate del percorso principale; il contratto collegato resta la fonte normativa.

Il percorso principale segue Planner → Implementor. [Direct Implementor](role-maps/agents/direct-implementor.md) è un percorso canonical diverso, senza piano intermedio; viene presentato come alternativa di ruolo, senza confonderne i gate con quelli del percorso principale.

## Risultato atteso

Lo studente sa spiegare perché il sistema canonical usa ruoli delimitati, conoscenza selettiva, gate, artifact e prove. Davanti a un errore del proprio agente sa individuare il controllo da migliorare, modificarne la superficie proprietaria e verificare se il cambiamento aiuta. La sequenza temporale con cui userà il bootstrap skill resta libera.
