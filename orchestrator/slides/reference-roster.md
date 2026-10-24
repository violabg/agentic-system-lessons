[Corso](../README.md) › [Slide](README.md) › **Riferimento rapido**

# Riferimento rapido: agent e skill

Una guida alla scelta, non un elenco di elementi obbligatori per ogni repository. Il nome porta alla mappa del ruolo, con diagramma e descrizione breve; la mappa rimanda al file sorgente. Tutte le istruzioni dei workflow sono nel [riferimento dei workflow](reference-flow.md).

## Agent avviati dallo sviluppatore

Ognuno è la conversazione principale della propria sessione.

| Agent | Usalo quando | Sorgente |
| --- | --- | --- |
| [Orchestrator](../role-maps/agents/orchestrator.md) | Vuoi progettare e implementare (`DESIGN`), implementare un cambiamento semplice (`FAST_IMPLEMENTATION`) o scrivere documentazione (`DOCUMENTATION`) | [orchestrator.agent.md](../system/canonical/agents/orchestrator.agent.md) |
| [Ask](../role-maps/agents/ask.md) | Serve una risposta tecnica, senza modifiche | [ask.agent.md](../system/canonical/agents/ask.agent.md) |
| [Knowledge Builder](../role-maps/agents/knowledge-builder.md) | Una regola del progetto va ricavata dal codice e salvata come knowledge | [knowledge-builder.agent.md](../system/canonical/agents/knowledge-builder.agent.md) |

## Delegate avviati dall'orchestrator

Ognuno parte in un contesto pulito e riferisce nella stessa conversazione. Non si avviano a mano.

| Delegate | Quando lo avvia l'orchestrator | Sorgente |
| --- | --- | --- |
| [Code Implementor](../role-maps/agents/code-implementor.md) | Per scrivere codice e test, in `DESIGN` e in `FAST_IMPLEMENTATION` | [code-implementor.agent.md](../system/canonical/agents/code-implementor.agent.md) |
| [Design Verifier](../role-maps/agents/design-verifier.md) | Prima di presentare il design per l'approvazione | [design-verifier.agent.md](../system/canonical/agents/design-verifier.agent.md) |
| [Implementation Verifier](../role-maps/agents/implementation-verifier.md) | Dopo ogni round di implementazione | [implementation-verifier.agent.md](../system/canonical/agents/implementation-verifier.agent.md) |
| [Documentation Reviewer](../role-maps/agents/documentation-reviewer.md) | Dopo la stesura di un documento in `DOCUMENTATION` | [documentation-reviewer.agent.md](../system/canonical/agents/documentation-reviewer.agent.md) |

## Skill

| Skill | Usala quando | Sorgente |
| --- | --- | --- |
| [Plan User Story From Id](../role-maps/skills/plan-user-story-from-id.md) | Si parte dall'ID di una user story | [SKILL.md](../system/canonical/skills/plan-user-story-from-id/SKILL.md) |
| [Plan Bug From Id](../role-maps/skills/plan-bug-from-id.md) | Si parte dall'ID di un bug e bisogna scegliere la causa da affrontare | [SKILL.md](../system/canonical/skills/plan-bug-from-id/SKILL.md) |
| [User Story Analysis](../role-maps/skills/user-story-analysis.md) | Bisogna rendere esplicite lacune e ambiguità di una story | [SKILL.md](../system/canonical/skills/user-story-analysis/SKILL.md) |
| [Manage Work Item](../role-maps/skills/manage-work-item.md) | Si vuole creare o aggiornare un ticket, fuori dai workflow | [SKILL.md](../system/canonical/skills/manage-work-item/SKILL.md) |
| [Author Repo Skill](../role-maps/skills/author-repo-skill.md) | Una procedura ripetibile va creata o aggiornata come skill | [SKILL.md](../system/canonical/skills/author-repo-skill/SKILL.md) |

---

[← Precedente: 6. Composizione e ciclo di vita](06-composizione-e-ciclo-di-vita.md) · [↑ Slide](README.md) · [Successivo: i tre workflow →](reference-flow.md)
