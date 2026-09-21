# 2. Dalla richiesta al piano

[Corso](README.md) · [Slide](slides/lesson-02-richiesta-e-planner.md) · [Caso guida](workshop-exercise.md)

**Principio: autorità delimitata.** Un ruolo riceve un mandato, fonti, output e limiti. Il [Planner canonical](system/canonical/agents/planner.agent.md) può indagare, chiedere e produrre un piano approvato; non modifica l'applicazione. Il [contratto Implementor](system/canonical/agents/implementor.agent.md) assume un mandato diverso soltanto dopo l'handoff.

## Il problema prima del piano

Una story di bassa qualità può avere una frase convincente e lasciare aperte decisioni decisive. Nel [caso guida](workshop-exercise.md) “solo dopo aver inserito una motivazione” non dice se il controllo vale per l'API, cosa fare con spazi vuoti o con una richiesta già chiusa. Un piano che sceglie da solo queste risposte sembra completo ma contiene requisiti inventati.

La [skill Plan User Story From Id](system/canonical/skills/plan-user-story-from-id/SKILL.md) parte dall'ID e raccoglie titolo, descrizione, criteri di accettazione, commenti e relazioni in un artifact. La [skill Plan Bug From Id](system/canonical/skills/plan-bug-from-id/SKILL.md) aggiunge indagine delle cause e scelta umana della causa da pianificare. La [skill User Story Analysis](system/canonical/skills/user-story-analysis/SKILL.md) aiuta a rendere visibili gap, ambiguità, assunzioni e domande; non decide al posto dello stakeholder.

## Perché il Planner è un ruolo separato

Il Planner lavora su requisiti e prove prima che esistano modifiche. Il suo [Gate 3](system/canonical/agents/planner.agent.md) scompone il requisito senza inventare funzionalità e mostra il ragionamento in chat; il gate non salva ancora un artifact della scomposizione. Nei gate successivi legge knowledge e codice, poi al [Gate 7](system/canonical/agents/planner.agent.md) pone soltanto domande motivate da lacune che bloccano il piano. Al [Gate 8](system/canonical/agents/planner.agent.md) verifica le risposte prima di continuare.

La domanda di chiarimento deve spiegare **quale decisione del piano dipende dalla risposta**. “Come deve reagire l'API a una motivazione fatta di soli spazi?” è una domanda utile; “Hai altri dettagli?” non delimita il rischio. La [sessione di pianificazione](system/canonical/instructions/planning-sessions.instructions.md) conserva le risposte e le decisioni nei punti prescritti, così il prossimo ruolo non dipende dalla memoria della chat.

## Che cosa dimostra il principio

Separare il Planner dall'Implementor consente una revisione del design e dello scope prima di autorizzare modifiche. Non impone questi nomi o questo numero di ruoli a ogni repository: richiede che i cambi di autorità siano visibili. Il [Direct Implementor](system/canonical/agents/direct-implementor.agent.md) è l'alternativa canonical senza piano intermedio, ma mantiene chiarimenti, conoscenza e gate propri.

**Domanda di trasferimento:** quale ambiguità ricorrente nei ticket del tuo team produce decisioni di implementazione che lo stakeholder non ha mai preso?
