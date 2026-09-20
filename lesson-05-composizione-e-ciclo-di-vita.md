# Lezione 5: Composizione, Ownership E Ciclo Di Vita

[Torna al corso](README.md) · [Lezione 4](lesson-04-validazione.md) · [Principi](principles.md)

## Obiettivo

Decidere dove vive una regola, come le superfici collaborano senza duplicarla e come il sistema migliora dopo un errore osservato.

## Failure Mode

La stessa regola viene copiata nelle istruzioni root, negli agent, nelle skill e nella documentazione. Una correzione aggiorna solo una copia; nel frattempo il sistema produce comportamenti diversi e nessuno sa quale versione possieda davvero la regola.

## Controlli

La **composizione** assegna ogni responsabilita' alla superficie che la possiede. Le istruzioni root instradano le regole sempre attive; gli agent definiscono ruoli e autorita'; le skill organizzano workflow ripetibili; la knowledge documenta fatti o indica fonti selettive. Le altre superfici devono collegare o applicare la regola, non riscriverla senza ownership.

Il **ciclo di vita** parte da un failure mode osservato: identificare se manca conoscenza, autorita' o verifica; modificare la superficie proprietaria; provare il caso reale; conservare il risultato e il rischio residuo; mantenere, correggere o rimuovere la modifica. Ogni cambiamento deve rendere chiaro quale output derivato o controllo deve essere riallineato.

La struttura canonical e' una reference implementation di questa separazione, non una directory obbligatoria per il tuo repository.

## Evidenza Nel Sistema

La [mappa del sistema](system-map.md) mostra router, ruoli, knowledge, gate, artifact e validazione. Il [vocabolario canonical](system/canonical/CONTEXT.md) stabilisce i confini dei termini. Le [istruzioni AGENTS](system/canonical/instructions/AGENTS.md) mostrano una superficie di instradamento; le [planning-session instructions](system/canonical/instructions/planning-sessions.instructions.md) mostrano una superficie di workflow.

## Esercizio

Classifica nel [caso condiviso](workshop-exercise.md) una nuova regola di dominio, un limite di autorita' e una verifica. Per ciascuna indica la superficie proprietaria, quale file o workflow deve solo instradare e quale prova segnalerebbe drift.

## Domanda Di Trasferimento

Qual e' la modifica minima che il tuo repository dovrebbe provare dopo il prossimo errore osservato? Quale risultato ti farebbe mantenerla, rivederla o rimuoverla?

## Chiusura

Il corso torna alla domanda iniziale: **chi puo' decidere, su quale evidenza, con quale verifica?** Adattare il controllo al rischio reale del repository, non copiare il numero di ruoli o di documenti del sistema canonical.

[Torna alla lezione introduttiva](lesson-01-introduzione.md) · [Torna al corso](README.md)
