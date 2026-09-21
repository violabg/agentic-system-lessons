# 5. Implementazione e prove

[Corso](README.md) · [Slide](slides/lesson-05-implementazione-e-prove.md) · [Gate uno per uno](slides/reference-flow.md)

**Principio: la validazione è evidenza di un rischio specifico.** Una build verde è una prova utile: il progetto si compila nelle condizioni eseguite. La [build gate dell'Implementor](system/canonical/agents/implementor.agent.md) la usa e prevede una correzione circoscritta quando fallisce. La build, da sola, non dimostra che la user story sia soddisfatta.

## Il mandato dell'Implementor

L'[Implementor canonical](system/canonical/agents/implementor.agent.md) parte da sessione e piano approvato, ne rispetta file e operazioni, esegue build, comandi richiesti, review e report. Se vi sono più piani approvati, risolve quale usare prima di applicare modifiche. Se il piano non è approvato, si ferma. Non può trasformare una propria preferenza in nuovo scope.

| Prova | Che cosa controlla | Limite |
| --- | --- | --- |
| Build | Sintassi, riferimenti e compatibilità di compilazione nel contesto eseguito | Non verifica ogni regola di business |
| Comandi del piano | Controlli richiesti per quella modifica | Valgono solo per scope e condizioni effettivamente eseguiti |
| Review | Corrispondenza tra piano, modifiche e regole applicabili | Una review non esegue il comportamento |
| Unit test | Scenari di logica dichiarati nel piano | Restano casi non rappresentati o integrazioni non esercitate |

## Dal test pianificato al test eseguito

Il [Planner canonical](system/canonical/agents/planner.agent.md) descrive gli scenari di coverage derivandoli dai rami di logica del piano; non aggiunge automaticamente file di unit test alla parte operativa. Nel [Gate 8 dell'Implementor](system/canonical/agents/implementor.agent.md), la creazione o modifica di unit test è opzionale e richiede approvazione esplicita. Se autorizzata, l'Implementor aggiorna la knowledge pertinente ai test, realizza i casi e avvia la suite rilevante, registrando esiti e blocchi.

Nel [caso guida](workshop-exercise.md), gli scenari sono: motivazione valida, motivazione vuota o fatta di spazi, richiesta già chiusa. La build passa; i tre test unitari autorizzati passano. Il report può affermare che questi scenari hanno prodotto il risultato atteso nell'ambiente eseguito. Non può affermare che ogni client esterno sia stato provato.

La [skill Business Logic Gap Detector](system/canonical/skills/business-logic-gap-detector/SKILL.md) mostra un altro tipo di prova: costruire test che falliscono prima della correzione per esporre una debolezza reale. L'[Integration Tester](system/canonical/agents/integration-tester.agent.md) ha un mandato distinto per le prove di integrazione.

## Handoff verificabile

Il report finale separa modifiche fatte, comandi eseguiti, risultati osservati, test non eseguiti e rischio residuo. “Fatto” non sostituisce questi dati. La [mappa dell'Implementor](role-maps/agents/implementor.md) conserva il dettaglio dei gate.

**Domanda di trasferimento:** quale prova potrebbe smentire rapidamente che una modifica del tuo repository soddisfi il requisito, anche se compila?
