# Lezione 2: Autorita' E Conoscenza

[Torna al corso](README.md) · [Lezione 1](lesson-01-introduzione.md) · [Principi](principles.md)

## Obiettivo

Imparare a delimitare chi puo' decidere e a scegliere la conoscenza sufficiente per il task.

## Failure Mode

Un agente analizza, decide e modifica senza un confine osservabile. Per colmare le lacune cerca ovunque, adotta il primo pattern simile e tratta documentazione generale o codice legacy come regola applicabile.

## Controlli

Un ruolo e' un contratto, non un titolo: dichiara responsabilita', input, output, autorita', strumenti e azioni vietate. Il cambio di autorita' o di contesto deve essere riconoscibile, anche quando lo stesso agente puo' eseguire piu' passaggi.

La conoscenza va selezionata in base al rischio e alla domanda. Il **Context Glossary** stabilizza termini, confini e fonti di verita'. Il **Knowledge Index** indica quali documenti leggere e quando. I due oggetti non sono intercambiabili: il primo definisce il vocabolario, il secondo instrada la lettura.

Se una fonte obbligatoria o pertinente non e' disponibile, il ruolo non deve indovinare. Deve rendere visibile la lacuna, chiedere la decisione necessaria o fermarsi secondo il proprio contratto.

## Evidenza Nel Sistema

Il confronto tra [Planner e Implementor](role-maps/README.md) e [Direct Implementor](role-maps/agents/direct-implementor.md) mostra due percorsi con confini diversi. Il [vocabolario canonical](system/canonical/CONTEXT.md) distingue glossario e knowledge index; il [knowledge guard](system/canonical/instructions/knowledge-guard.instructions.md) mostra come rendere operativo il caricamento selettivo.

## Esercizio

Nel caso del [workshop](workshop-exercise.md), scegli due o tre fonti autorevoli per il cambiamento. Indica quale decisione puo' prendere il ruolo, quale azione resta fuori dalla sua autorita' e quale fonte plausibile deve essere esclusa. Scrivi cosa cambierebbe la tua decisione.

## Domanda Di Trasferimento

Nel tuo repository, quale passaggio non dovrebbe poter essere completato dalla stessa conversazione senza un handoff o una review? Quale fonte governa davvero quella decisione?

[Prossima: gate e artifact](lesson-03-gate-e-artifact.md)
