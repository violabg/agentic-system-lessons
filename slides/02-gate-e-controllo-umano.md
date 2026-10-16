[Corso](../README.md) › [Slide](README.md) › **2. Gate e controllo umano**

# 2. Gate e controllo umano

Lettura completa: [principio 2](../principi/02-gate-e-controllo-umano.md)

## Il problema

Il codice cambia prima che scope, rischio e approvazione siano chiari.

---

## Il principio

Un [gate](../system/canonical/CONTEXT.md) risponde a tre domande:

Che cosa blocca? Che cosa sblocca? Chi decide?

---

## Automatico o umano

Molti gate del [Planner](../role-maps/agents/planner.md) avanzano da soli quando la prova esiste.

Altri attendono una persona: per esempio l'intervista (Gate 7) e l'approvazione del piano (Gate 11).

---

## Tre passaggi decisivi

Requisito ambiguo → chiarimento verificato.

Design → regole applicabili rispettate.

Piano → approvazione esplicita.

---

## Anche dopo il piano

L'[Implementor](../role-maps/agents/implementor.md) chiede un'approvazione esplicita prima di creare test unitari (Gate 8).

---

## Tutti i gate

[Flusso Planner → Implementor](reference-flow.md): un gate per riga.

---

## Nel tuo repository

Dove il tuo team deve approvare prima che un agente modifichi il codice?

---

[← Precedente: 1. Autorità delimitata](01-autorita-delimitata.md) · [↑ Slide](README.md) · [Successivo: 3. Validazione come prova →](03-validazione-come-prova.md)
