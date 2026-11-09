[Corso](../README.md) › [Slide](README.md) › **2. Gate e controllo umano**

# 2. Gate e controllo umano

Lettura completa: [principio 2](../principi/02-gate-e-controllo-umano.md)

## Il problema

L'agente modifica il codice prima che qualcuno abbia approvato la soluzione.

Oppure salta un passaggio perché “sembrava ovvio”.

---

## Il principio

Un gate dice **che cosa blocca**, **che cosa sblocca** e **chi decide**.

---

## Un'istruzione alla volta

Il runtime serve il workflow un passo per volta.

L'orchestrator non vede i passi futuri: non può saltarli.

---

## Halt point

Review, domanda, decisione: il workflow si ferma e aspetta lo sviluppatore.

Altrove, fermarsi è una violazione.

---

## L'approvazione è dello sviluppatore

Il runtime la rifiuta finché un controllo del design fallisce.

L'[orchestrator](../role-maps/agents/orchestrator.md) la registra, non la decide.

---

## Test su richiesta

I batch automatici: prima la produzione, poi la documentazione.

Le operazioni `Testing` e quelle distruttive partono solo quando lo sviluppatore le seleziona.

---

## Correggere, non indebolire

La revisione si ripete finché un giro completo non trova difetti.

Una contraddizione si corregge nel design; solo un difetto non correggibile diventa un blocco.

---

## Gate proporzionati

`FAST_IMPLEMENTATION`: niente design, niente approvazione, niente delegate. L'orchestrator implementa e lo sviluppatore giudica alla fine.

La scelta è dello sviluppatore. [Tutti i workflow](reference-flow.md).

---

## Nel tuo repository

In quale punto il tuo team deve approvare prima che l'agente modifichi il codice?

---

[← Precedente: 1. Autorità delimitata](01-autorita-delimitata.md) · [↑ Slide](README.md) · [Successivo: 3. Validazione come prova →](03-validazione-come-prova.md)
