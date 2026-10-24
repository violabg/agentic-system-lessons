[Corso](../README.md) › [Slide](README.md) › **3. Validazione come prova**

# 3. Validazione come prova

Lettura completa: [principio 3](../principi/03-validazione-come-prova.md)

## Il problema

“Compila, quindi funziona.”

Una build verde non dimostra che la story sia soddisfatta.

---

## Il principio

Per ogni prova: quale rischio controlla, che cosa è stato eseguito, quale rischio resta.

---

## Ogni prova ha un limite

**Build:** compilazione, non regole di business.

**Revisione:** piano e codice coincidono, ma niente è stato eseguito.

**Test unitari:** gli scenari previsti, non le integrazioni.

---

## Pianificato non è eseguito

Il [Planner](../role-maps/agents/planner.md) descrive gli scenari di copertura.

L'[Implementor](../role-maps/agents/implementor.md) crea i test solo con un'approvazione esplicita, poi li esegue.

---

## Nel caso guida

Build verde, tre test verdi.

Si può dire: i tre scenari funzionano. Non si può dire: ogni client esterno funziona.

---

## Altre prove

[Business Logic Gap Detector](../role-maps/skills/business-logic-gap-detector.md): test che falliscono prima della correzione.

[Integration Tester](../role-maps/agents/integration-tester.md): test di integrazione.

---

## Nel tuo repository

Quale prova smentirebbe rapidamente una modifica che compila ma è sbagliata?

---

[← Precedente: 2. Gate e controllo umano](02-gate-e-controllo-umano.md) · [↑ Slide](README.md) · [Successivo: 4. Artifact durevoli →](04-artifact-durevoli.md)
