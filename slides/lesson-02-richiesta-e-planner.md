# Lezione 2: dalla richiesta al piano

[Indice](README.md) · [Lettura](../lesson-02-richiesta-e-planner.md)

## 1. Il principio

Un ruolo ha autorità e output delimitati.

Il [Planner](../system/canonical/agents/planner.agent.md) produce un piano approvato; non modifica l'applicazione.

---

## 2. La qualità della story conta

“Chiudere solo con motivazione” non decide il comportamento dell'API, degli spazi vuoti o delle richieste già chiuse.

Un piano dettagliato non ripara una decisione mai chiarita. [Caso guida](../workshop-exercise.md).

---

## 3. Il ticket entra con evidenza

[Plan User Story From Id](../system/canonical/skills/plan-user-story-from-id/SKILL.md) raccoglie il work item e le sue relazioni.

[Plan Bug From Id](../system/canonical/skills/plan-bug-from-id/SKILL.md) esamina cause probabili e chiede quale pianificare.

[User Story Analysis](../system/canonical/skills/user-story-analysis/SKILL.md) espone gap e domande.

---

## 4. Il Planner non inventa

Il [Gate 3](../system/canonical/agents/planner.agent.md) scompone il requisito e segnala lacune. Il suo output è in chat.

Il [Gate 7](../system/canonical/agents/planner.agent.md) chiede le risposte che bloccano il piano.

---

## 5. Una domanda utile

“Gli spazi vuoti contano come motivazione nell'API?”

Spiegare perché la risposta cambia design, acceptance criteria e coverage.

---

## 6. La separazione protegge

Il [Planner](../system/canonical/agents/planner.agent.md) prepara una decisione ispezionabile.

L'[Implementor](../system/canonical/agents/implementor.agent.md) riceve un piano approvato; non eredita autorità illimitata dalla chat.

---

## 7. Nel tuo repository

Quale ambiguità ricorrente nei ticket dovrebbe fermare la pianificazione prima del codice?

[Dettaglio dei gate](reference-flow.md).
