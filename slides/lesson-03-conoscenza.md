# Lezione 3: conoscenza selettiva

[Indice](README.md) · [Lettura](../lesson-03-conoscenza.md)

## 1. Il principio

L'agente deve leggere **fonti autorevoli applicabili**, non ogni documento disponibile.

Il [Planner Gate 4](../system/canonical/agents/planner.agent.md) sceglie le knowledge prima del design.

---

## 2. Tre ambiti

**MustHave:** sempre.

**PerContext:** quando il tipo di lavoro lo richiede.

**PerComponent:** quando il task tocca quel componente.

[Regola canonical](../system/canonical/agents/planner.agent.md).

---

## 3. Scegliere e scartare

Nel [caso guida](../workshop-exercise.md), la regola API e quella del servizio Richieste servono. La guida Fatture non governa il task.

Il motivo della selezione deve essere spiegabile.

---

## 4. Due oggetti diversi

Il [glossario](../system/canonical/CONTEXT.md) stabilizza i termini.

Il knowledge index instrada verso documenti da leggere. Il [knowledge guard](../system/canonical/instructions/knowledge-guard.instructions.md) richiede un trigger “When to read” specifico.

---

## 5. Se il contesto cambia

Un nuovo componente o un flusso batch può cambiare le fonti applicabili.

Il [Planner](../system/canonical/agents/planner.agent.md) rivaluta PerContext e PerComponent e aggiorna l'inventario normativo.

---

## 6. Creare e mantenere

[Knowledge Builder](../system/canonical/agents/knowledge-builder.agent.md) raccoglie evidenza, chiede review e salva una knowledge con intent.

Il [knowledge guard](../system/canonical/instructions/knowledge-guard.instructions.md) richiede un soggetto per file, fonte dei fatti e trigger mirato.

---

## 7. Nel tuo repository

Quali regole sono sempre applicabili? Quali hanno bisogno di un contesto o di un componente per essere caricate?
