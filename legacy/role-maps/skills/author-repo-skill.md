[Corso](../../README.md) › [Mappe di agent e skill](../README.md) › **Author Repo Skill**

# Author Repo Skill

**File sorgente:** [skills/author-repo-skill/SKILL.md](../../system/canonical/skills/author-repo-skill/SKILL.md)

## In 30 secondi

**Fa:** decide se una procedura ripetibile merita una repository-local skill e, dopo approvazione, la rende un contratto con input, output, failure mode e validazione.

**Non fa:** non usa una skill per un'azione una tantum, per una regola globale o per un vincolo proprio di un agent. Non inventa tool, path o comandi non trovati nella discovery.

**Consegna:** una skill approvata e validata, con artifact finale deterministico e chiamanti compatibili.

## Flusso, controlli e output

```mermaid
flowchart TD
    Procedure[Input: procedura proposta] --> G0{Controllo: e ripetibile,<br/>deliberata e con output?}
    G0 -->|no| Home[Output: prompt, istruzione<br/>o contratto agent corretto]
    G0 -->|sì| G1[Passo: cerca skill esistente]
    G1 --> Duplicate{Esiste un duplicato<br/>o estensione adatta?}
    Duplicate -->|sì| Evolve[Analisi: caller e impatto<br/>di evoluzione]
    Duplicate -->|no| Gather[Passo: raccogli fatti repository]
    Evolve --> Gather
    Gather --> Facts[Fonti: ruoli, convenzioni<br/>ed esempio reale]
    Facts --> Shape[Passo: definisci trigger, passi,<br/>output e failure mode]
    Shape --> Proposal[Proposta: file plan della skill]
    Proposal --> Approval{Approvazione esplicita?}
    Approval -->|no| Shape
    Approval -->|sì| Write[Scrivi o aggiorna skill]
    Write --> Validate[Controllo: frontmatter, riferimenti,<br/>contratti e validazione]
    Validate --> Skill[Artifact: skill completa<br/>e report di validazione]
    Skill --> Handoff[Handoff: agent e caller autorizzati]
```

## Lettura del diagramma

| Passaggio o controllo | Decisione che protegge | Artifact o output | Handoff successivo |
| --- | --- | --- | --- |
| Casa giusta | La procedura e davvero una skill? | Redirect a prompt, istruzione o agent contract | Proprietario corretto |
| Duplicazione | Si estende un contratto esistente? | Analisi di caller e compatibilità | Raccolta fatti |
| Raccolta | Quali fatti repository-specific rendono valida la skill? | Fonti, ruoli, convenzioni e caso reale | Definizione |
| Definizione e approvazione | Trigger, passi e output sono verificabili e approvati? | File plan approvato | Scrittura |
| Validazione | Tutti i riferimenti esistono e l'artifact e deterministico? | Skill e report di validazione | Agent/caller autorizzati |

**Da ricordare:** la richiesta diventa una skill solo quando il suo output e riconoscibile e ripetibile. L'approvazione precede sempre la scrittura.

---

**Nei principi:** [6. Composizione e ciclo di vita](../../principi/06-composizione-e-ciclo-di-vita.md)

[← Precedente: Integration Test Knowledge Checklist](integration-test-knowledge-checklist.md) · [↑ Mappe di agent e skill](../README.md) · [Successivo: Manage Work Item →](manage-work-item.md)
