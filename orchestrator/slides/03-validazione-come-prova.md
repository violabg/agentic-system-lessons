[Corso](../README.md) › [Slide](README.md) › **3. Validazione come prova**

# 3. Validazione come prova

Lettura completa: [principio 3](../principi/03-validazione-come-prova.md)

## Il problema

“Compila e i miei test passano.”

Ma i test li ha scritti lo stesso agente, con la stessa idea del codice.

---

## Il principio

Per ogni prova: **quale rischio controlla**, **che cosa è stato eseguito**, **che cosa resta aperto**.

---

## Struttura e significato

Controlli meccanici: l'artifact è completo e coerente?

[Design Verifier](../role-maps/agents/design-verifier.md): il design realizza davvero il requisito?

---

## Nominare non è realizzare

Un elemento citato senza meccanismo non è coperto.

Una realizzazione parziale non è copertura.

---

## Il verdict è meccanico

`VERDICT: PASS` o `VERDICT: FAIL`.

Qualsiasi altra prima riga vale `FAIL`.

---

## Non condizionare chi giudica

Il verificatore riceve solo identificatori. Nessun riassunto, nessun verdict suggerito.

---

## Test che possono fallire

Il [Code Implementor](../role-maps/agents/code-implementor.md) scrive prima il codice, poi i test.

Test tautologici vietati.

---

## Nel tuo repository

Nei report del tuo agente, è chiaro che cosa *non* è stato verificato?

---

[← Precedente: 2. Gate e controllo umano](02-gate-e-controllo-umano.md) · [↑ Slide](README.md) · [Successivo: 4. Artifact durevoli →](04-artifact-durevoli.md)
