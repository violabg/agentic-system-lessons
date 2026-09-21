# Perché un sistema agentico

[Corso](README.md) · [Inizia dalla lezione 1](lesson-01-introduzione.md)

Un agente può scrivere una modifica plausibile ignorando una regola del dominio. Può copiare un pattern vecchio, interpretare una richiesta ambigua o dichiarare successo dopo una build che non verifica il comportamento richiesto.

Quando regole e decisioni restano implicite, ogni chat ricomincia da capo. Un sistema agentico locale al repository rende più chiari il mandato, le fonti da consultare, i controlli e le informazioni necessarie per riprendere il lavoro.

Non rende deterministico il modello. Permette al team di chiedere: **chi può decidere, su quale evidenza, con quale verifica?**

## Un esempio

Il portale deve impedire la chiusura di una richiesta senza motivazione. Il browser segnala il campo vuoto e la build passa. Basta per accettare la modifica? Non sappiamo ancora che cosa accade se un altro programma chiama il servizio direttamente.

Nelle cinque lezioni seguiremo questo caso, aggiungendo fonti, decisioni e prove. Alla fine ogni partecipante sceglierà un errore reale del proprio progetto e una modifica minima al workflow da sperimentare.

I sei principi sono leve da adattare, non sei strumenti da installare. Per un task piccolo può bastare un percorso leggero; le regole di un workflow già adottato continuano comunque a valere.

[Approfondimenti facoltativi](reference/README.md)
