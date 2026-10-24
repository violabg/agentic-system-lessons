[Corso](../../README.md) › [Mappe di agent e skill](../README.md) › **Manage Work Item**

# Manage Work Item

**File sorgente:** [skills/manage-work-item/SKILL.md](../../system/canonical/skills/manage-work-item/SKILL.md)

## In 30 secondi

**Fa:** crea un bug o una user story, oppure aggiorna un work item esistente nel tracker del repository. Parte solo quando l'utente la invoca per nome.

**Non fa:** non attiva sessioni, non avvia job o workflow e non progetta. Non cerca nel tracker per indovinare l'item da aggiornare, non cancella item o commenti e non cambia campi che l'utente non ha chiesto di cambiare.

**Consegna:** modalità, tipo, ID del work item, integrazione usata, link o percorso della fonte, campi cambiati e campi ancora aperti. L'ID serve poi, se l'utente lo vuole, a una skill che avvia il lavoro dell'orchestrator.

**Autorità:** l'invocazione autorizza il workflow della skill, non la scrittura. Ogni creazione o modifica richiede l'approvazione esplicita della proposta finale.

## Flusso, controlli e output

```mermaid
flowchart TD
    Invoke[Input: invocazione esplicita] --> Mode{Modalità indicata?}
    Mode -->|no| AskMode[Output: chiede la modalità]
    AskMode --> Mode
    Mode -->|create-bug o create-user-story| Clarify[Chiarisce tipo, campi,<br/>criteri e tracker]
    Clarify --> Proposal[Output: proposta completa]
    Mode -->|update ID| Read[Legge solo quell'item<br/>e i suoi commenti]
    Read --> Readable{Item leggibile?}
    Readable -->|no| Stop[Stop: segnala il problema<br/>senza modificare nulla]
    Readable -->|sì| Diff[Chiarisce i campi da cambiare<br/>Output: prima e dopo, campo per campo]
    Diff --> Proposal
    Proposal --> Approve{L'utente approva<br/>la proposta finale?}
    Approve -->|no| Clarify
    Approve -->|sì| Reread{Update: l'item è cambiato<br/>dopo la lettura?}
    Reread -->|sì| Diff
    Reread -->|no o create| Write[Crea o aggiorna con<br/>l'integrazione approvata]
    Write --> Handoff[Handoff: ID e riepilogo all'utente]
```

## Lettura del diagramma

| Passaggio | Decisione che protegge | Output | Passaggio successivo |
| --- | --- | --- | --- |
| Modalità | Creare un bug, una story o aggiornare un item? | Modalità scelta | Chiarimento o lettura |
| Chiarimento | La proposta è abbastanza precisa da poter essere rivista? | Tipo, titolo, descrizione, criteri o passi di riproduzione, tracker | Approvazione |
| Lettura (update) | L'item esiste ed è leggibile? Quali commenti contano? | Stato attuale e confronto prima/dopo | Approvazione, oppure stop |
| Approvazione | L'utente accetta esattamente questa proposta? | Approvazione esplicita | Rilettura o scrittura |
| Rilettura (update) | L'item è cambiato nel frattempo? | Differenza e nuova richiesta di approvazione, se serve | Scrittura |
| Scrittura | L'integrazione approvata può eseguire l'operazione? | Item creato o aggiornato, oppure blocco spiegato | Utente |

Se l'integrazione richiesta non è disponibile, la skill spiega il blocco e non crea né modifica nulla. Non la sostituisce con comandi shell, chiamate API o strumenti di altri client.

**Da ricordare:** l'approvazione del workflow o della discussione precedente non vale come approvazione della modifica. Conta solo il sì alla proposta finale.

---

**Nei principi:** [1. Autorità delimitata](../../principi/01-autorita-delimitata.md) · [2. Gate e controllo umano](../../principi/02-gate-e-controllo-umano.md)

[← Precedente: User Story Analysis](user-story-analysis.md) · [↑ Mappe di agent e skill](../README.md) · [Successivo: Author Repo Skill →](author-repo-skill.md)
