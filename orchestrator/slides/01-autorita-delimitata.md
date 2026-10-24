[Corso](../README.md) › [Slide](README.md) › **1. Autorità delimitata**

# 1. Autorità delimitata

Lettura completa: [principio 1](../principi/01-autorita-delimitata.md)

## Il problema

Un solo agente interpreta, progetta, scrive il codice e dichiara concluso.

Chi ha scritto il codice è anche chi lo giudica.

---

## Il principio

Un ruolo è un contratto: **mandato**, **limiti**, **consegna**.

Quando cambia l'autorità, cambia il ruolo.

---

## Dirigere, eseguire, giudicare

[Orchestrator](../role-maps/agents/orchestrator.md): segue il workflow. Non scrive codice di produzione.

[Code Implementor](../role-maps/agents/code-implementor.md): scrive codice e test.

[Design Verifier](../role-maps/agents/design-verifier.md) e [Implementation Verifier](../role-maps/agents/implementation-verifier.md): giudicano. Non correggono.

---

## Il workflow lo sceglie lo sviluppatore

`DESIGN`, `FAST_IMPLEMENTATION` o `DOCUMENTATION`: sempre in modo esplicito.

Dedurlo dalla richiesta è una violazione.

---

## Scegliere il come, non il che cosa

L'orchestrator sceglie come realizzare il requisito e scrive le alternative.

Solo lo sviluppatore cambia che cosa il requisito chiede.

---

## Identificatori, non riassunti

I delegate ricevono id di sessione e job, e leggono la specifica da soli.

---

## Altri ruoli

[Ask](../role-maps/agents/ask.md) · [Knowledge Builder](../role-maps/agents/knowledge-builder.md) · [Documentation Reviewer](../role-maps/agents/documentation-reviewer.md) · [User Story Analysis](../role-maps/skills/user-story-analysis.md)

---

## Nel tuo repository

Nel tuo flusso, chi produce il codice è anche chi dichiara che è corretto?

---

[← Indice slide](README.md) · [↑ Slide](README.md) · [Successivo: 2. Gate e controllo umano →](02-gate-e-controllo-umano.md)
