[Corso](../README.md) › [Slide](README.md) › **4. Artifact durevoli**

# 4. Artifact durevoli

Lettura completa: [principio 4](../principi/04-artifact-durevoli.md)

## Il problema

Dopo ore di lavoro l'agente ricorda il requisito “a modo suo”.

Nessuno sa perché una scelta è stata fatta.

---

## Il principio

Requisito, decisioni, approvazioni e stato vivono in file stabili, con un proprietario.

---

## La sessione

Memoria, log, artifact, job e design.

La memoria tiene puntatori, non copie. [Session store](../system/canonical/contracts/session-store.md).

---

## Il requisito si congela

`requirement_R_lock`: il requisito parola per parola.

Si rilegge da lì, non dal ricordo della chat.

---

## Il design è strutturato

Obbligazioni, decisioni, operazioni: cambiano solo tramite il runtime.

Gli id non si rinumerano mai.

---

## Le iterazioni

Il runtime fotografa il workspace e calcola lui i file cambiati.

---

## Il contesto pulito come test

Il delegate non vede la chat. Se un dettaglio manca nella sessione, l'handoff era incompleto.

---

## Nel tuo repository

Il tuo agente rilegge il requisito da un file o dal ricordo della conversazione?

---

[← Precedente: 3. Validazione come prova](03-validazione-come-prova.md) · [↑ Slide](README.md) · [Successivo: 5. Conoscenza selettiva →](05-conoscenza-selettiva.md)
