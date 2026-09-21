# 4. Gate, piano e handoff

[Corso](README.md) · [Slide](slides/lesson-04-gate-e-handoff.md) · [Gate uno per uno](slides/reference-flow.md)

**Principi: gate e artifact durevoli.** Un gate controlla una transizione. Deve dire che cosa impedisce di proseguire, quale evidenza sblocca il passaggio e chi può accettarla. Il [glossario canonical](system/canonical/CONTEXT.md) definisce il gate come checkpoint di evidenza, approvazione, scope, handoff o validazione.

## Perché i gate servono

Il [Planner](system/canonical/agents/planner.agent.md) non può dichiarare pronto un piano quando il requisito è ambiguo, la knowledge applicabile manca o il design non è allineato. I suoi gate sono ordinati. Alcuni avanzano automaticamente quando la prova richiesta esiste; altri attendono una risposta umana, come il chiarimento e l'approvazione finale. Un gate non equivale sempre a chiedere permesso.

| Transizione | Condizione che blocca | Evidenza che consente di proseguire |
| --- | --- | --- |
| Dal requisito al design | Ambiguità che cambia il comportamento | Risposta chiarita e verificata |
| Dalla knowledge al piano | Regola applicabile ignorata o violata | Inventario normativo e design allineato |
| Dal piano all'Implementor | Piano non revisionato o non approvato | Piano validato e approvazione registrata |

Il [riferimento ai gate](slides/reference-flow.md) offre una riga per ciascun gate di Planner e Implementor, i diagrammi verticali e i link ai contratti. In aula si spiega brevemente ogni passaggio, poi si approfondiscono le transizioni che cambiano autorità.

## Perché il piano è un artifact

Il [Planner Gate 10](system/canonical/agents/planner.agent.md) scrive un piano secondo lo [schema canonical](system/canonical/templates/plan-schema.md). Il piano collega file, cambiamenti, operazioni e scenari di coverage. La sua utilità è permettere all'Implementor di lavorare su una decisione ispezionata, non di indovinare la decisione dalla conversazione.

La [planning session](system/canonical/instructions/planning-sessions.instructions.md) conserva anche ticket, dipendenze, regole, chiarimenti, approvazioni e stato. L'artifact ha valore quando un altro ruolo può recuperare il **perché**, non solo il **cosa**. Chat e artifact possono entrambi contenere una risposta, ma l'handoff si fonda sul record durevole previsto dal contratto.

## Il passaggio a un contesto pulito

Dopo approvazione e [handoff del Planner](system/canonical/agents/planner.agent.md), l'implementazione inizia in una nuova conversazione. L'[Implementor](system/canonical/agents/implementor.agent.md) riceve l'ID della sessione, carica il piano approvato e gli artifact pertinenti. Il contesto pulito rende osservabile se il piano basta davvero: dettagli presenti soltanto nella vecchia chat non sono un handoff affidabile. La nuova conversazione non crea una nuova planning session; recupera quella nota.

Nel [caso guida](workshop-exercise.md), la decisione “spazi vuoti non valgono come motivazione” deve essere ritrovabile nel requisito chiarito e nel piano. Se l'Implementor non può ricostruirla, il passaggio è incompleto.

**Domanda di trasferimento:** quale decisione del tuo workflow deve essere approvata prima di cambiare codice, e dove resta leggibile dopo la chat?
