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
| Istruzioni generali (router) | Regole sempre attive e indicazioni su dove trovare il resto |
| Agent | Mandato, limiti e consegna di un ruolo |
| Workflow | La sequenza dei passaggi, con i loro gate e halt point |
| Skill | Una procedura ripetibile, invocata quando serve |
| Knowledge | Fatti e regole del progetto, da leggere solo quando servono |

Per ogni regola bisogna sapere anche chi può modificarla, quali file vanno riallineati dopo la modifica e quale verifica segnala una divergenza.

## Nel sistema di riferimento

La [mappa del sistema](../reference/mappa-del-sistema.md) mostra come si compongono queste superfici. Nel sistema di riferimento ognuna ha un confine netto:

- **Il router è corto.** Le [istruzioni del repository](../system/canonical/instructions/AGENTS.md) restano sotto le ottanta righe: elencano ruoli, runtime, skill, knowledge e validazione, e rimandano ai contratti invece di ripeterli.
- **I ruoli non contengono il workflow.** Il contratto dell'[orchestrator](../role-maps/agents/orchestrator.md) dice come seguire le istruzioni, non quali sono. I passaggi vivono nei file del workflow e arrivano solo dal runtime.
- **Il runtime ha un contratto leggibile.** Ogni operazione del runtime è descritta in un contratto, come il [ciclo del workflow](../system/canonical/contracts/workflow-loop.md). Chi mantiene il sistema può controllare che cosa fa un'operazione senza leggere il codice del runtime, e ogni operazione ha i suoi test.
- **Le capacità hanno un nome, non un prodotto.** Un ruolo dice “recupera il work item” o “avvia un delegate”, non il nome di uno strumento. Ogni repository collega quel nome allo strumento che usa davvero: il contratto del ruolo non cambia quando cambia lo strumento.
- **Le procedure ripetibili sono skill.** [Author Repo Skill](../role-maps/skills/author-repo-skill.md) aiuta a decidere quando una procedura merita una skill e quando appartiene invece a un ruolo, a un'istruzione o a un workflow.

Il sistema canonical è un esempio di questa separazione, non una struttura da copiare.

**Un ciclo di miglioramento piccolo e verificabile:**

1. Descrivi l'errore e raccogli un caso reale.
2. Stabilisci quale principio è mancato: autorità, gate, prova, artifact o knowledge.
3. Cambia la regola minima nella superficie che la possiede, e dichiara chi la mantiene.
4. Ripeti un task che potrebbe smentire il miglioramento.
5. Registra il risultato e il limite; poi mantieni, correggi o rimuovi la modifica.

## Nel caso guida

Supponi che, in un altro lavoro, l'API chiuda una richiesta senza motivazione. La stessa conseguenza può avere cause diverse, e ogni causa richiede un intervento diverso:

| Causa | Principio mancato | Dove intervenire |
| --- | --- | --- |
| Lo sviluppatore ha scelto `FAST_IMPLEMENTATION` per un cambiamento con decisioni aperte | [Gate e controllo umano](02-gate-e-controllo-umano.md) | Le regole del team su quale workflow usare |
| La regola API esisteva ma il suo intent non la faceva scegliere | [Conoscenza selettiva](05-conoscenza-selettiva.md) | L'intent del documento nel catalogo |
| Il prompt del delegate conteneva un riassunto invece degli identificatori | [Autorità delimitata](01-autorita-delimitata.md) | Il contratto che fissa il prompt del delegate |
| I test passavano, ma nessuna verifica confrontava il codice con la regola | [Validazione come prova](03-validazione-come-prova.md) | La verifica dell'implementazione e il bundle che riceve |

Prima la diagnosi, poi la modifica. [Leggi il caso](../caso-guida.md#applicare-il-ciclo-al-tuo-repository).

## Nel tuo repository

Puoi partire da un sistema creato con lo skill di bootstrap o da uno costruito in altro modo: il ciclo è lo stesso.

- Quale errore reale del tuo agente sapresti spiegare oggi come la mancanza di un controllo preciso?
- Quale prova ti farebbe cambiare idea sulla correzione che proponi?

---

[← Precedente: 5. Conoscenza selettiva](05-conoscenza-selettiva.md) · [↑ Principi](README.md) · [Fine del corso: torna all'inizio →](../README.md)
