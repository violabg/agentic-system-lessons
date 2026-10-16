# Capire un Agentic System

Un corso in italiano per sviluppatori che usano già un coding agent.

Un agente può scrivere codice plausibile e sbagliato. Il corso spiega i principi che rendono il suo lavoro **verificabile e correggibile**: chi può decidere, con quali informazioni, quale prova serve per andare avanti e quale traccia resta a chi lavora dopo.

Gli esempi vengono da un sistema di riferimento, il sistema *canonical*. Servono a mostrare i principi in un caso concreto: non devi impararne i file né copiarne la struttura. Puoi applicare gli stessi principi a qualsiasi sistema, anche uno costruito da te.

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
| Agent | Un ruolo con un mandato scritto: cosa può fare, cosa non può fare, cosa consegna. |
| Skill | Una procedura ripetibile che un agente o una persona può richiamare. |
| Gate | Un punto di controllo: il lavoro non prosegue finché la condizione non è soddisfatta. |
| Artifact | Un file che conserva decisioni, prove o stato oltre la conversazione. |
| Handoff | Il passaggio di lavoro da un ruolo al successivo. |
| Knowledge | Documenti con le regole del progetto, da leggere solo quando servono. |
| Sessione di pianificazione | La cartella di lavoro che raccoglie gli artifact di un'attività. |

Le definizioni complete sono nel [glossario del sistema canonical](system/canonical/CONTEXT.md).

---

[Inizia: i sei principi in breve →](principi/README.md)
