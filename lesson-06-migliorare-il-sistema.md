# 6. Migliorare il proprio Agentic System

[Corso](README.md) · [Slide](slides/lesson-06-migliorare-il-sistema.md) · [Principi](principles.md)

**Principio: composizione e ciclo di vita espliciti.** Una regola funziona quando vive nella superficie che la possiede, viene caricata nel momento giusto e può essere aggiornata senza lasciare copie divergenti. Il [glossario canonical](system/canonical/CONTEXT.md) distingue ruoli, knowledge index, gate e artifact; il [knowledge guard](system/canonical/instructions/knowledge-guard.instructions.md) disciplina le fonti di conoscenza.

## Diagnosi prima della modifica

Partire da un errore osservato, non dal desiderio di aggiungere file. Nel [caso guida](workshop-exercise.md) un agente chiude la richiesta dalla UI ma lascia aperta la chiamata API. Le possibili cause richiedono interventi diversi:

| Causa osservata | Controllo da migliorare | Superficie probabile |
| --- | --- | --- |
| La story non diceva che il vincolo vale per l'API | Chiarimento prima del piano | Ticket, [skill di analisi](system/canonical/skills/user-story-analysis/SKILL.md), gate del [Planner](system/canonical/agents/planner.agent.md) |
| La regola API esisteva ma non è stata letta | Selezione della knowledge | Knowledge index e [guard](system/canonical/instructions/knowledge-guard.instructions.md) |
| Il piano corretto non è stato recuperato | Handoff durevole | [Planning session](system/canonical/instructions/planning-sessions.instructions.md) e [Implementor](system/canonical/agents/implementor.agent.md) |
| La modifica compilava ma il comportamento errato restava | Validazione pertinente | Coverage del [Planner](system/canonical/agents/planner.agent.md) e prove dell'[Implementor](system/canonical/agents/implementor.agent.md) |

Una root instruction ospita regole sempre attive. Un agent delimita mandato e autorità. Una skill ordina una procedura ripetibile. Una knowledge contiene fatti o regole da leggere selettivamente. Una modifica nella superficie sbagliata può creare duplicazione o lasciare il task successivo senza la regola necessaria. La [mappa del sistema](system-map.md) mostra come questi elementi si compongono; [Author Repo Skill](system/canonical/skills/author-repo-skill/SKILL.md) esplicita quando una procedura merita una skill.

## Un ciclo piccolo e verificabile

1. Nominare il failure mode e raccogliere un caso reale.
2. Stabilire se il difetto riguarda autorità, knowledge, gate, artifact o prova.
3. Cambiare la regola minima nella superficie proprietaria; dichiarare chi la mantiene.
4. Ripetere un task che potrebbe falsificare il miglioramento.
5. Registrare risultato e limite; mantenere, correggere o rimuovere la modifica.

Il sistema prodotto dal bootstrap skill è un possibile punto di partenza. Questo ciclo funziona anche per un sistema costruito in altro modo. Il sistema canonical è una reference implementation di controlli, non un elenco obbligatorio di nomi e directory.

**Domanda di trasferimento:** quale errore reale del tuo agente sapresti spiegare oggi come mancanza di un controllo, e quale prova ti farebbe cambiare idea?
