# Lezione 5: implementare e provare

[Indice](README.md) · [Lettura](../lesson-05-implementazione-e-prove.md) · [Gate dettagliati](reference-flow.md)

## 1. Il principio

Una prova sostiene una dichiarazione specifica.

L'[Implementor](../system/canonical/agents/implementor.agent.md) registra ciò che ha modificato, eseguito e osservato.

---

## 2. Piano approvato

Il [Gate 2](../system/canonical/agents/implementor.agent.md) risolve e carica un piano approvato.

Nessun piano leggibile e approvato: il percorso ordinario si ferma.

---

## 3. Build e review

La build verifica la compilazione nelle condizioni eseguite.

La review controlla il rapporto tra piano, codice e regole. Sono entrambe richieste dal [contratto Implementor](../system/canonical/agents/implementor.agent.md).

---

## 4. Coverage nel piano

Il [Planner](../system/canonical/agents/planner.agent.md) descrive gli scenari dei rami di business: successo, guardie, errori e stati quando presenti.

Scenari pianificati non sono test eseguiti.

---

## 5. Test con approvazione

Il [Gate 8](../system/canonical/agents/implementor.agent.md) chiede autorizzazione esplicita prima di creare o cambiare unit test.

Se autorizzato: knowledge di test, implementazione, suite pertinente, risultati e report.

---

## 6. Tre prove del caso

Nel [caso guida](../workshop-exercise.md), build e tre unit test passano.

È supportata la dichiarazione sui tre scenari eseguiti. I client esterni non eseguiti restano un limite.

---

## 7. Oltre questo ruolo

[Business Logic Gap Detector](../system/canonical/skills/business-logic-gap-detector/SKILL.md) cerca test rossi utili.

[Integration Tester](../system/canonical/agents/integration-tester.agent.md) possiede un percorso distinto per test di integrazione.
