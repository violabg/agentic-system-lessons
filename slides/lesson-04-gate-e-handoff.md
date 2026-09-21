# Lezione 4: gate e handoff

[Indice](README.md) · [Lettura](../lesson-04-gate-e-handoff.md) · [Flusso dettagliato](reference-flow.md)

## 1. Il principio

Un [gate](../system/canonical/CONTEXT.md) blocca una transizione finché scope, evidenza, approvazione o prova richiesta non bastano.

Domande: che cosa blocca? Che cosa sblocca? Chi può accettare?

---

## 2. Automatico o umano

Molti gate del [Planner](../system/canonical/agents/planner.agent.md) avanzano quando l'evidenza è completa.

L'intervista e l'approvazione del piano richiedono una decisione umana. [Elenco dei gate](reference-flow.md).

---

## 3. Tre transizioni decisive

Requisito ambiguo → chiarimento verificato.

Design → regole di knowledge allineate.

Piano → approvazione esplicita.

[Contratto Planner](../system/canonical/agents/planner.agent.md).

---

## 4. Che cosa resta nella sessione

Ticket, chiarimenti, inventario normativo, piano, approvazione e stato.

Le [planning session rules](../system/canonical/instructions/planning-sessions.instructions.md) preservano l'evidenza necessaria al prossimo ruolo.

---

## 5. Il piano non è solo un riassunto

Lo [schema](../system/canonical/templates/plan-schema.md) vincola file, dettagli, operazioni e scenari di coverage.

Il [Planner](../system/canonical/agents/planner.agent.md) lo fa validare prima dell'handoff.

---

## 6. Nuova conversazione, stessa sessione

Contesto di chat pulito. ID della planning session noto.

L'[Implementor](../system/canonical/agents/implementor.agent.md) carica il piano approvato e gli artifact pertinenti. Se manca una decisione, l'handoff è incompleto.

---

## 7. Nel tuo repository

Quale approvazione deve sopravvivere alla chat? Quale record permette a un altro ruolo di riprendere senza indovinare?

[Diagrammi dei ruoli](../role-maps/README.md).
