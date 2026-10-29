[Corso](../README.md) › [Principi](README.md) › **3. Validazione come prova**

# 3. Validazione come prova

> **In breve:** “fatto” non è una prova. Ogni affermazione sul risultato deve poggiare su una verifica precisa, e ogni verifica dichiara anche che cosa non copre.

[Slide](../slides/03-validazione-come-prova.md) · [Caso guida](../caso-guida.md)

## Il problema

L'agente dichiara che il lavoro è corretto perché il codice compila e i test che ha scritto passano. Ma una build verde dice solo che il progetto si compila, e un test scritto dallo stesso agente può confermare la stessa idea sbagliata del codice. Senza una verifica che possa smentire l'errore più probabile, “funziona” è un'opinione.

## Il principio

Scegli la prova più piccola e pertinente per ogni passaggio: un controllo meccanico, un test mirato, una build, una revisione indipendente. Per ogni prova, distingui sempre tre cose:

1. **quale rischio controlla**;
2. **che cosa è stato eseguito davvero**;
3. **quale rischio resta aperto**.

Un comando verde è una prova del rischio che controlla, non un giudizio generale sulla qualità.

## Nel sistema di riferimento

Il workflow `DESIGN` usa prove diverse, ognuna con il suo limite:

| Prova | Che cosa controlla | Che cosa non controlla |
| --- | --- | --- |
| [Controlli meccanici del design](../system/canonical/contracts/design-checks.md) | Che ogni elemento del requisito abbia un'operazione, che ogni decisione sia realizzata, che il piano sia eseguibile in ordine | Se il design realizza davvero il requisito |
| [Design Verifier](../role-maps/agents/design-verifier.md) | Se ogni obbligazione è realizzata da un meccanismo concreto e se il design contraddice una regola citabile della knowledge grounding | Il codice, che ancora non esiste |
| Build e test del [Code Implementor](../role-maps/agents/code-implementor.md) | Compilazione e scenari di comportamento del codice prodotto | Ciò che i test non rappresentano |
| [Implementation Verifier](../role-maps/agents/implementation-verifier.md) | Se il codice realizza la specifica e applica la knowledge, toccando solo i file previsti | Il comportamento a runtime oltre il codice letto |

**Struttura e significato sono prove diverse.** I controlli meccanici sono fatti sull'artifact: un'operazione dichiara un elemento che le istruzioni non nominano, una decisione non ha un'operazione che la realizzi. Il design verifier risponde a un'altra domanda: se si implementasse il design *esattamente* com'è scritto, l'effetto richiesto si produrrebbe? Nominare un elemento non è realizzarlo; una realizzazione parziale non è copertura; un nome di test non è una prova.

**Il verdict è meccanico.** Il report di un verificatore inizia con `VERDICT: PASS` o `VERDICT: FAIL`. Qualunque altra prima riga vale come `FAIL`. Se il dubbio è reale, il verificatore sceglie “non coperto” e nomina l'elemento irrisolto.

**Il verificatore non va condizionato.** Alla prima invocazione il design verifier riceve solo l'id della sessione e del job: niente riassunto del design, niente verdict suggerito. Legge le obbligazioni e il design dalla vista di verifica, da solo. Quando riprende dopo un `FAIL`, il prompt aggiunge solo l'elenco delle correzioni fatte: descrive ciò che è cambiato, non chiede un verdict. La verifica può chiedere solo *più* design, mai meno: un design che passa perdendo scope ha fallito.

**I test devono poter fallire.** Quando la specifica del lavoro include i test, il code implementor li scrive dopo il codice, ricavando un inventario completo dei comportamenti: percorsi felici, condizioni, input non validi, errori. Nel workflow `DESIGN` l'operazione di test unitari è autorizzata dallo sviluppatore; in `FAST_IMPLEMENTATION` i test fanno parte del lavoro di implementazione. I test tautologici sono vietati: un test che non può fallire, perché asserisce una costante o verifica solo che un mock è stato chiamato, non osserva il codice.

**Il messaggio finale non dichiara più di quello che è successo.** Al termine l'orchestrator mostra file toccati, test eseguiti con il loro esito, verdict del verificatore e blocchi aperti. Se resta un blocco, il messaggio lo dice; non presenta come successo ciò che non è passato.

Anche `DOCUMENTATION` separa le prove: un controllo meccanico cerca segnaposti non risolti nel documento, poi il [Documentation Reviewer](../role-maps/agents/documentation-reviewer.md) lo rilegge come farebbe un lettore nuovo.

## Nel caso guida

I controlli meccanici trovano un'operazione senza ramo negativo; il design verifier trova un'obbligazione non coperta sul canale API. Dopo l'implementazione quattro test passano, ma l'implementation verifier segnala che la risposta di errore viola la regola API: i test verdi non coprivano quella regola. Il messaggio finale afferma che i quattro scenari passano nell'ambiente eseguito. Non afferma che i client esterni siano stati provati. [Leggi la traccia](../caso-guida.md#traccia-4-implementazione-e-prove).

## Nel tuo repository

- Chi verifica il lavoro del tuo agente: lo stesso agente, nella stessa conversazione, con lo stesso contesto?
- Nei report del tuo agente, è chiaro che cosa *non* è stato verificato?

---

[← Precedente: 2. Gate e controllo umano](02-gate-e-controllo-umano.md) · [↑ Principi](README.md) · [Successivo: 4. Artifact durevoli →](04-artifact-durevoli.md)
