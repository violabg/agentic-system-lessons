[Corso](../README.md) › [Principi](README.md) › **6. Composizione e ciclo di vita**

# 6. Composizione e ciclo di vita

> **In breve:** ogni regola vive in un solo posto, quello che la possiede. Le altre parti del sistema rimandano a quel posto invece di copiarla. Si migliora il sistema partendo da un errore reale, con una modifica piccola e una prova che potrebbe smentirla.

[Slide](../slides/06-composizione-e-ciclo-di-vita.md) · [Caso guida](../caso-guida.md)

## Il problema

La stessa regola viene copiata nelle istruzioni generali, in un agent, in una skill e nella documentazione. Poi una correzione aggiorna solo una copia. Oppure si reagisce a un errore aggiungendo altri file e altre istruzioni, senza capire quale controllo è mancato.

## Il principio

Ogni tipo di regola ha un posto preciso:

| Superficie | Che cosa contiene |
| --- | --- |
| Istruzioni generali (root instructions) | Regole sempre attive e indicazioni su dove trovare il resto |
| Agent | Mandato, limiti e consegna di un ruolo |
| Skill | Una procedura ripetibile |
| Knowledge | Fatti e regole da leggere solo quando servono |

Per ogni regola bisogna sapere anche chi può modificarla, quali file vanno riallineati dopo la modifica e quale verifica segnala una divergenza.

## Nel sistema di riferimento

La [mappa del sistema](../reference/mappa-del-sistema.md) mostra come si compongono istruzioni, ruoli, knowledge, gate e artifact. Il [glossario canonical](../system/canonical/CONTEXT.md) distingue questi elementi; le [regole sulla knowledge](../system/canonical/instructions/knowledge-guard.instructions.md) stabiliscono come si aggiungono e si mantengono i documenti. La skill [Author Repo Skill](../role-maps/skills/author-repo-skill.md) aiuta a decidere quando una procedura merita una skill propria e come scriverla.

Il sistema canonical è un esempio di questa separazione, non una struttura da copiare.

**Un ciclo di miglioramento piccolo e verificabile:**

1. Descrivi l'errore e raccogli un caso reale.
2. Stabilisci quale principio è mancato: autorità, gate, prova, artifact o knowledge.
3. Cambia la regola minima nella superficie che la possiede, e dichiara chi la mantiene.
4. Ripeti un task che potrebbe smentire il miglioramento.
5. Registra il risultato e il limite; poi mantieni, correggi o rimuovi la modifica.

## Nel caso guida

L'agente chiude la richiesta correttamente dall'interfaccia, ma l'API la chiude anche senza motivazione. La stessa conseguenza può avere cause diverse, e ogni causa richiede un intervento diverso:

| Causa | Principio mancato | Dove intervenire |
| --- | --- | --- |
| La story non diceva che il vincolo vale per l'API | [Autorità delimitata](01-autorita-delimitata.md): chiarire prima di pianificare | Ticket, [User Story Analysis](../role-maps/skills/user-story-analysis.md), gate del [Planner](../role-maps/agents/planner.md) |
| La regola API esisteva ma non è stata letta | [Conoscenza selettiva](05-conoscenza-selettiva.md) | Indice della knowledge e trigger “When to read” |
| Il piano corretto non è stato recuperato | [Artifact durevoli](04-artifact-durevoli.md) | Sessione di pianificazione e intake dell'[Implementor](../role-maps/agents/implementor.md) |
| Il codice compilava, ma il comportamento restava sbagliato | [Validazione come prova](03-validazione-come-prova.md) | Scenari di copertura del Planner e test dell'Implementor |

Prima la diagnosi, poi la modifica. [Leggi il caso](../caso-guida.md#applicare-il-ciclo-al-tuo-repository).

## Nel tuo repository

Puoi partire da un sistema creato con lo skill di bootstrap o da uno costruito in altro modo: il ciclo è lo stesso.

- Quale errore reale del tuo agente sapresti spiegare oggi come la mancanza di un controllo preciso?
- Quale prova ti farebbe cambiare idea sulla correzione che proponi?

---

[← Precedente: 5. Conoscenza selettiva](05-conoscenza-selettiva.md) · [↑ Principi](README.md) · [Fine del corso: torna all'inizio →](../README.md)
