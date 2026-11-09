[Corso](../README.md) › [Principi](README.md) › **3. Validazione come prova**

# 3. Validazione come prova

> **In breve:** “fatto” non è una prova. Ogni affermazione sul risultato deve poggiare su una verifica precisa, e ogni verifica dichiara anche che cosa non copre.

[Slide](../slides/03-validazione-come-prova.md) · [Caso guida](../caso-guida.md)

## Il problema

L'agente dichiara che il lavoro è corretto perché il codice compila e i test che ha scritto passano. Ma una build verde dice solo che il progetto si compila, e un test scritto dallo stesso agente può confermare la stessa idea sbagliata del codice. Senza una verifica che possa smentire l'errore più probabile, “funziona” è un'opinione.

## Il principio

Scegli la prova più piccola e pertinente per ogni passaggio: un controllo meccanico, un test mirato, una build, una revisione di chi non ha prodotto il risultato. Per ogni prova, distingui sempre tre cose:

1. **quale rischio controlla**;
2. **che cosa è stato eseguito davvero**;
3. **quale rischio resta aperto**.

Un comando verde è una prova del rischio che controlla, non un giudizio generale sulla qualità.

## Nel sistema di riferimento

Il workflow `DESIGN` usa prove diverse, ognuna con il suo limite:

| Prova | Che cosa controlla | Che cosa non controlla |
| --- | --- | --- |
| [Controlli meccanici del design](../system/canonical/contracts/design-checks.md) | Che ogni obbligazione, contratto, API e decisione abbia un'operazione che la realizza, che ogni file dichiarato abbia un'operazione, che i riferimenti esistano, che il piano sia eseguibile in ordine e abbia al massimo un'operazione `Testing` per tipo di test | Se il design realizza davvero il requisito |
| [Revisione avversariale](../system/canonical/workflows/design/09-design-review.md) dell'[orchestrator](../role-maps/agents/orchestrator.md) | Quattro punti di vista: knowledge applicata, obbligazioni realizzate da un meccanismo concreto, sezioni coerenti tra loro, operazioni eseguibili da chi parte senza contesto | Il codice, che ancora non esiste; e non è uno sguardo indipendente, perché la fa chi ha scritto il design |
| Build e test riportati dal [Code Implementor](../role-maps/agents/code-implementor.md) | Compilazione e scenari di comportamento del codice prodotto, con i comandi eseguiti e il loro esito | Ciò che i test non rappresentano |
| [Revisione dell'unità di lavoro](../system/canonical/workflows/design/10-implementation.md) dell'orchestrator | Se il codice e il report rispettano istruzioni, obbligazioni, contratti, decisioni e knowledge dell'operazione, e se il report porta le prove che dichiara | Il comportamento a runtime oltre il codice letto e i comandi riportati |

**Struttura e significato sono prove diverse.** I controlli meccanici sono fatti sull'artifact: un contratto che nessuna operazione realizza, un file che nessuna operazione dichiara, una dipendenza verso un'operazione successiva. La revisione risponde a un'altra domanda: un'operazione che dichiara di realizzare un'obbligazione ne nomina anche il meccanismo? Citare un'obbligazione non è realizzarla, e un nome di test non è una prova.

**Chi giudica cerca di smentire.** Una revisione che conferma ciò che è stato scritto non è una verifica. L'istruzione chiede all'orchestrator di dare per sbagliato il proprio design e di cercare il difetto più forte da ogni punto di vista: “un punto di vista che non riesci ad attaccare è un punto di vista che non hai esaminato”. Lo stesso vale per il codice: l'orchestrator dà per sbagliata l'unità di lavoro e prova a smentire il report. Un'affermazione senza prova nel report non passa.

**Il report è una prova solo se porta le prove.** Il code implementor consegna l'inventario dei comportamenti con il test che copre ciascuno, le regole di knowledge applicate e dove, i file toccati, i comandi eseguiti e il loro esito. L'orchestrator non ripete la build: giudica quella riportata. Una regola di knowledge che il report non nomina, o che il codice contraddice, è un difetto.

**I test devono poter fallire.** Nel workflow `DESIGN` il piano ha al massimo un'operazione `Testing` per tipo di test (`Unit`, `Integration`, `E2E`, `Harness`), e parte solo quando lo sviluppatore la seleziona. Se un test rivela un difetto reale nel codice di produzione, si corregge il codice e il test resta come prova: aggirare il difetto dentro il test è vietato. In `FAST_IMPLEMENTATION` l'orchestrator scrive i test unitari dopo il codice e ripete build e test finché passano.

**Il messaggio finale non dichiara più di quello che è successo.** Al termine l'orchestrator mostra file toccati, esito delle revisioni e blocchi aperti. Se resta un blocco, il messaggio lo dice; non presenta come successo ciò che non è passato.

**Il limite di questa scelta.** Nel sistema di riferimento il design non ha più un verificatore indipendente prima della review: i contratti del [Design Verifier](../role-maps/agents/design-verifier.md) e dell'[Implementation Verifier](../role-maps/agents/implementation-verifier.md), con il loro verdict meccanico `VERDICT: PASS` o `VERDICT: FAIL`, restano nel sistema ma nessuna istruzione li avvia. La prova indipendente sul design è lo sviluppatore che lo legge e lo approva. Saperlo serve a non attribuire alla revisione dell'autore un valore che non ha.

Anche `DOCUMENTATION` separa le prove: un controllo meccanico cerca segnaposti non risolti nel documento, poi il [Documentation Reviewer](../role-maps/agents/documentation-reviewer.md) lo rilegge come farebbe un lettore nuovo.

## Nel caso guida

I controlli meccanici trovano un'API che nessuna operazione realizza; la revisione dell'orchestrator trova un'operazione che non passa la motivazione dal canale API. Dopo l'implementazione la build è verde, ma la revisione dell'unità di lavoro trova che la risposta di errore viola la regola API: la build non diceva nulla su quella regola. Dopo la correzione lo sviluppatore seleziona l'operazione di test unitari e quattro scenari passano. Il messaggio finale afferma che quei quattro scenari passano nell'ambiente eseguito. Non afferma che i client esterni siano stati provati. [Leggi la traccia](../caso-guida.md#traccia-4-implementazione-e-prove).

## Nel tuo repository

- Chi verifica il lavoro del tuo agente: lo stesso agente, nella stessa conversazione, con lo stesso contesto? Se sì, dove si trova la prova indipendente?
- Nei report del tuo agente, è chiaro che cosa *non* è stato verificato?

---

[← Precedente: 2. Gate e controllo umano](02-gate-e-controllo-umano.md) · [↑ Principi](README.md) · [Successivo: 4. Artifact durevoli →](04-artifact-durevoli.md)
