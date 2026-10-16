[Corso](../README.md) › [Principi](README.md) › **3. Validazione come prova**

# 3. Validazione come prova

> **In breve:** “fatto” non è una prova. Ogni affermazione sul risultato deve poggiare su una verifica precisa, e ogni verifica dichiara anche che cosa non copre.

[Slide](../slides/03-validazione-come-prova.md) · [Caso guida](../caso-guida.md)

## Il problema

L'agente dichiara che il lavoro è corretto perché il codice compila. Ma una build verde dice solo che il progetto si compila: non dice che la user story è soddisfatta. Senza una verifica che possa smentire l'errore più probabile, “funziona” è un'opinione.

## Il principio

Scegli la prova più piccola e pertinente per ogni passaggio: un test mirato, una build, un lint, una revisione o una verifica manuale. Per ogni prova, distingui sempre tre cose:

1. **quale rischio controlla**;
2. **che cosa è stato eseguito davvero**;
3. **quale rischio resta aperto**.

Un comando verde è una prova del rischio che controlla, non un giudizio generale sulla qualità.

## Nel sistema di riferimento

L'[Implementor](../role-maps/agents/implementor.md) parte da un piano approvato, applica solo le modifiche previste, poi verifica il risultato. Ogni prova ha un limite:

| Prova | Che cosa controlla | Che cosa non controlla |
| --- | --- | --- |
| Build | Sintassi, riferimenti e compilazione nell'ambiente eseguito | Le regole di business |
| Comandi del piano | I controlli richiesti per quella modifica | Ciò che non è stato eseguito |
| Revisione | La corrispondenza fra piano, modifiche e regole | Il comportamento a runtime |
| Test unitari | Gli scenari di logica previsti dal piano | I casi non rappresentati e le integrazioni |

**Pianificare un test non è eseguirlo.** Il [Planner](../role-maps/agents/planner.md) descrive gli scenari di copertura, uno per ogni ramo di logica, ma non scrive i test. L'Implementor li crea solo dopo un'approvazione esplicita, poi li esegue e registra l'esito.

**Il report finale separa i fatti.** Modifiche fatte, comandi eseguiti, risultati osservati, test non eseguiti e rischio residuo restano voci distinte.

Altri ruoli mostrano altri tipi di prova:

- [Business Logic Gap Detector](../role-maps/skills/business-logic-gap-detector.md) scrive test che falliscono *prima* della correzione, per dimostrare che un difetto esiste davvero.
- [Integration Tester](../role-maps/agents/integration-tester.md) ha un mandato distinto per i test di integrazione.
- [Direct Implementor](../role-maps/agents/direct-implementor.md) esegue build e revisione ma non crea test. È un limite del ruolo, non un invito a rinunciare ai test: la prova mancante va dichiarata e assegnata a un workflow autorizzato.

## Nel caso guida

La build passa. La revisione conferma che l'API rifiuta una motivazione vuota. Con l'approvazione dell'utente, l'Implementor crea i tre test pianificati (motivazione valida, motivazione vuota o di soli spazi, richiesta già chiusa) e tutti passano. Il report può affermare che questi tre scenari funzionano nell'ambiente eseguito. Non può affermare che ogni client esterno sia stato provato. [Leggi la traccia](../caso-guida.md#traccia-4-prove).

## Nel tuo repository

- Quale prova potrebbe smentire rapidamente una modifica che compila ma non soddisfa il requisito?
- Nei report del tuo agente, è chiaro che cosa *non* è stato verificato?

---

[← Precedente: 2. Gate e controllo umano](02-gate-e-controllo-umano.md) · [↑ Principi](README.md) · [Successivo: 4. Artifact durevoli →](04-artifact-durevoli.md)
