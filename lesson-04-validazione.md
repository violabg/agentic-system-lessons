# Lezione 4: Validazione Come Evidenza

[Torna al corso](README.md) · [Lezione 3](lesson-03-gate-e-artifact.md) · [Principi](principles.md)

## Obiettivo

Scegliere una prova che possa smentire il risultato piu' probabilmente errato e descrivere con precisione cio' che la prova non dimostra.

## Failure Mode

L'agente dichiara corretto il lavoro perche' la modifica sembra plausibile, la build e' verde o una review ripete la stessa assunzione dei requisiti. Il team confonde un controllo parziale con una garanzia generale.

## Controlli

Prima dell'handoff, definire il comportamento atteso, il rischio controllato, il comando o l'osservazione necessaria e i prerequisiti. La prova puo' essere un test mirato, un controllo di schema, un'analisi statica, una build, una review competente o una verifica manuale proporzionata al rischio.

Il record deve distinguere cosa e' stato eseguito, cosa e' passato, cosa e' fallito e cosa non e' stato verificato. Un test verde prova solo il comportamento coperto. Una review dello stesso agente non e' automaticamente indipendente. Se mancano accesso, ambiente o copertura, il lavoro resta parzialmente verificato e il limite diventa parte dell'handoff.

Le restrizioni di ruolo contano: Direct Implementor puo' eseguire build e review secondo il proprio contratto, ma non crea test unitari o di integrazione. La copertura mancante richiede il workflow autorizzato e non puo' essere sostituita da una frase di fiducia.

## Evidenza Nel Sistema

Le [istruzioni root](system/canonical/instructions/AGENTS.md) definiscono la validazione prima dell'handoff. Il [percorso Direct Implementor](role-maps/agents/direct-implementor.md) rende visibili le restrizioni del ruolo. La sezione [validazione in introduction](introduction.md#dare-allagente-un-modo-di-scoprire-che-ha-sbagliato) distingue prova, risultato e rischio residuo.

## Esercizio

Nel [workshop](workshop-exercise.md), parti da una build verde e prova a falsificare l'affermazione “una richiesta senza motivazione non puo' essere chiusa”. Indica la prova minima, il suo risultato atteso, il prerequisito e cio' che rimane non dimostrato.

## Domanda Di Trasferimento

Quale controllo potrebbe dimostrare rapidamente che il tuo prossimo piano o la tua prossima modifica e' sbagliata? Chi ha il mandato di produrre una prova ulteriore?

[Prossima: composizione e ciclo di vita](lesson-05-composizione-e-ciclo-di-vita.md)
