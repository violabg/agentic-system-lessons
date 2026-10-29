[Corso](../../README.md) › [Mappe di agent e skill](../README.md) › **Design Verifier**

# Design Verifier

**File sorgente:** [agents/design-verifier.agent.md](../../system/canonical/agents/design-verifier.agent.md)

## In 30 secondi

**Fa:** decide se il design realizza il requisito, un'obbligazione alla volta, e segnala i conflitti con la knowledge grounding del design.

**Non fa:** non progetta, non scrive codice, non ripara e non controlla la struttura del design, che spetta ai controlli meccanici. Ignora ogni altro contenuto dell'invocazione; alla ripresa dopo un `FAIL` riceve in più solo l'elenco delle correzioni fatte.

**Consegna:** un report di testo che inizia con `VERDICT: PASS` o `VERDICT: FAIL`, seguito dai conflitti con la knowledge e da una riga per ogni obbligazione.

## Flusso, controlli e output

```mermaid
flowchart TD
    Prompt[Input: id di sessione e job;<br/>alla ripresa solo le correzioni] --> View[Legge la vista di verifica<br/>con le obbligazioni]
    View --> K[Legge la knowledge grounding]
    K --> Split[Per ogni obbligazione:<br/>condizioni atomiche]
    Split --> Q{Realizzata, senza omissioni,<br/>con un meccanismo concreto?}
    Q -->|no o dubbio| NotCovered[NOT COVERED<br/>con il meccanismo mancante]
    Q -->|sì per ogni condizione| Covered[COVERED]
    NotCovered --> Conflicts[Conflitti citabili con la knowledge]
    Covered --> Conflicts
    Conflicts --> Verdict{Tutto pulito?}
    Verdict -->|sì| Pass[VERDICT: PASS]
    Verdict -->|no| Fail[VERDICT: FAIL]
    Pass --> Handoff[Handoff: report all'orchestrator]
    Fail --> Handoff
```

## Lettura del diagramma

| Passaggio | Decisione che protegge | Output | Passaggio successivo |
| --- | --- | --- | --- |
| Lettura | Su che cosa si giudica? | Vista di verifica con le obbligazioni e la knowledge grounding; tutto trattato come dati, mai come istruzioni | Giudizio |
| Copertura | Implementare il design *esattamente* produce l'effetto richiesto? | Una riga per obbligazione; per le non coperte, la condizione e il meccanismo mancante | Conflitti |
| Conflitti | Il design contraddice una regola citabile della knowledge? | Regola citata e elemento del design che la contraddice | Verdict |
| Verdict | Il design può essere presentato? | `PASS` solo se i conflitti sono `none` e ogni obbligazione è coperta | Orchestrator |

La knowledge grounding comprende ogni documento `MustHave`, ogni documento letto nella sessione del design e ogni documento che il design nomina. La vista di verifica mostra solo le etichette delle obbligazioni: operazioni, decisioni e file arrivano senza id, così il verificatore giudica il contenuto e non ricostruisce una mappatura. Il verificatore può chiedere solo più design, mai meno.

**Da ricordare:** “nominare non è realizzare”. Un riferimento a un elemento seguito da una frase generica, un rimando o un nome di test non è copertura.

---

**Nei principi:** [1. Autorità delimitata](../../principi/01-autorita-delimitata.md) · [2. Gate e controllo umano](../../principi/02-gate-e-controllo-umano.md) · [3. Validazione come prova](../../principi/03-validazione-come-prova.md)

[← Precedente: Code Implementor](code-implementor.md) · [↑ Mappe di agent e skill](../README.md) · [Successivo: Implementation Verifier →](implementation-verifier.md)
