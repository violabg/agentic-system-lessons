# Lezione 6: migliorare il sistema

[Indice](README.md) · [Lettura](../lesson-06-migliorare-il-sistema.md)

## 1. Il principio

Una regola deve vivere nella superficie che la possiede e restare verificabile nel tempo.

[Principi canonical spiegati nel corso](../principles.md).

---

## 2. Partire da un errore

Nel [caso guida](../workshop-exercise.md) la UI blocca la chiusura, ma l'API no.

Il sintomo non dice ancora quale controllo manca.

---

## 3. Diagnosticare il controllo

Story incompleta? Knowledge non letta? Gate saltato? Handoff incompleto? Prova non pertinente?

Ogni causa porta a una correzione diversa. [Mappa del sistema](../system-map.md).

---

## 4. Trovare la superficie

Ruolo e autorità: [agent](../system/canonical/agents/planner.agent.md).

Procedura ripetibile: [skill](../system/canonical/skills/author-repo-skill/SKILL.md).

Knowledge selettiva: [indice e guard](../system/canonical/instructions/knowledge-guard.instructions.md).

---

## 5. Cambiare il minimo

Una regola proprietaria, un trigger di lettura o una prova mirata.

Evitare copie divergenti in più file. [Ciclo di manutenzione](../system-map.md).

---

## 6. Provare il miglioramento

Ripetere un task che potrebbe mostrare lo stesso errore.

Registrare risultato osservato e limite. Mantenere, correggere o rimuovere la modifica.

---

## 7. Portarlo nel proprio repository

Un sistema avviato con bootstrap o creato autonomamente può migliorare con lo stesso ciclo.

Quale failure mode reale affronteresti per primo?
