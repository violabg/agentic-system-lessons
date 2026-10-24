[Lezioni](../README.md) › **Corso orchestrator**

# Capire un Agentic System

Un corso in italiano per sviluppatori che usano già un coding agent.

Un agente può scrivere codice plausibile e sbagliato. Il corso spiega i principi che rendono il suo lavoro **verificabile e correggibile**: chi può decidere, con quali informazioni, quale prova serve per andare avanti e quale traccia resta a chi lavora dopo.

Gli esempi vengono da un sistema di riferimento, il sistema *canonical*, costruito attorno a un solo ruolo che dirige il lavoro: l'**orchestrator**. Servono a mostrare i principi in un caso concreto: non devi impararne i file né copiarne la struttura. Puoi applicare gli stessi principi a qualsiasi sistema, anche uno costruito da te.

## Il percorso

Leggi le pagine in ordine. Ognuna termina con il link alla successiva.

0. [I sei principi in breve](principi/README.md)
1. [Autorità delimitata](principi/01-autorita-delimitata.md)
2. [Gate e controllo umano](principi/02-gate-e-controllo-umano.md)
3. [Validazione come prova](principi/03-validazione-come-prova.md)
4. [Artifact durevoli](principi/04-artifact-durevoli.md)
5. [Conoscenza selettiva](principi/05-conoscenza-selettiva.md)
6. [Composizione e ciclo di vita](principi/06-composizione-e-ciclo-di-vita.md)

## Materiale di supporto

- [Caso guida](caso-guida.md): un esempio inventato, ripreso in tutte le pagine.
- [Slide](slides/README.md): un deck breve per ogni principio.
- [Mappe di agent e skill](role-maps/README.md): per ogni ruolo, un diagramma del flusso e una descrizione breve, con il link al file sorgente.
- [Approfondimenti](reference/README.md): letture facoltative per chi vuole andare oltre.

## Parole che useremo

Alcuni termini restano in inglese perché sono quelli che troverai nei file del sistema.

| Termine | Significato |
| --- | --- |
| Agent (ruolo) | Un contratto scritto: che cosa può fare, che cosa non può fare, che cosa consegna. |
| Orchestrator | Il ruolo che guida il workflow scelto dallo sviluppatore. Non scrive codice di produzione. |
| Delegate | Un ruolo che l'orchestrator avvia in un contesto pulito per un compito preciso: scrivere il codice o verificare. |
| Workflow | Una sequenza ordinata di istruzioni: `DESIGN`, `FAST_IMPLEMENTATION` o `DOCUMENTATION`. Lo sceglie sempre lo sviluppatore. |
| Runtime | Il programma locale che serve le istruzioni una alla volta e custodisce sessioni, design e controlli. |
| Halt point | Un punto in cui il workflow si ferma e attende lo sviluppatore: una review, una domanda, una decisione. |
| Sessione | Il registro durevole di un lavoro: memoria, log, artifact, job e design. |
| Design | L'artifact strutturato che lo sviluppatore rivede e approva prima dell'implementazione. |
| Verdict | La prima riga del report di un verificatore: `VERDICT: PASS` oppure `VERDICT: FAIL`. |
| Knowledge | Documenti con le regole del progetto, da leggere solo quando servono. |
| Skill | Una procedura ripetibile che una persona o un ruolo può richiamare. |

Le definizioni complete sono nel [glossario del sistema canonical](system/canonical/CONTEXT.md).

---

[↑ Lezioni](../README.md) · [Inizia: i sei principi in breve →](principi/README.md)
