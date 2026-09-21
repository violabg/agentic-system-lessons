# Lezione 4: Validazione come evidenza

[Corso](README.md) · [Slide da usare in aula](slides/lesson-04-validazione.md)

**Domanda:** Quale prova rivelerebbe che la modifica è sbagliata?

**Obiettivo:** Scegliere un controllo comportamentale e dichiararne i limiti.

## Idea da ricordare

Una build verde non dimostra che il requisito funzioni.

## Il caso

Il browser rifiuta una motivazione vuota, ma una chiamata diretta può evitare quel controllo. La compilazione non esercita necessariamente questo percorso.

## Il controllo

Prima della verifica definisci comportamento atteso, input, prerequisiti e risultato osservabile. Dopo, distingui eseguito, passato, fallito e non verificato. Le prove si producono entro il mandato del ruolo; una copertura mancante richiede un workflow autorizzato.

## Attività e risultato

Apri soltanto la [tappa 4 del caso condiviso](workshop-exercise.md#tappa-4). Prima di aprire D2, progetta la prova. Poi confrontala con la traccia fornita: quale affermazione puoi smentire e quale resta non dimostrata?

**Da consegnare:** Una verifica con prerequisiti, risultato atteso, risultato osservato e limite.

**Domanda finale:** Che cosa non potresti affermare anche se il tuo controllo passasse?

## Dopo la lezione, facoltativo

[Approfondimento](principles.md) · [Riferimenti e contratti](reference/README.md). Non è necessaria la lettura prima della prossima lezione.
