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

Revisione dell'[orchestrator](../role-maps/agents/orchestrator.md): il design realizza davvero il requisito?

---

## Nominare non è realizzare

Un'obbligazione citata senza meccanismo non è coperta.

Un nome di test non è una prova.

---

## Cercare di smentire

Chi rivede dà per sbagliato il lavoro e cerca il difetto più forte.

Una revisione che conferma non è una verifica.

---

## Il report porta le prove

Comandi eseguiti, esiti, regole di knowledge applicate e dove.

Un'affermazione senza prova non passa.

---

## Test che possono fallire

Se un test rivela un difetto, si corregge il codice, non il test.

---

## Il limite

Il design lo rivede chi l'ha scritto.

La prova indipendente è lo sviluppatore che lo approva.

---

## Nel tuo repository

Nei report del tuo agente, è chiaro che cosa *non* è stato verificato?

---

[← Precedente: 2. Gate e controllo umano](02-gate-e-controllo-umano.md) · [↑ Slide](README.md) · [Successivo: 4. Artifact durevoli →](04-artifact-durevoli.md)
