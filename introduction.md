# Perché un Sistema Agentico

[Lettura principale](README.md) · [Le cinque lezioni](lesson-01-introduzione.md) · [I sei principi](principles.md)

## Il Problema Prima Della Soluzione

Un agente può produrre una modifica plausibile senza conoscere le regole del dominio, i confini architetturali o il modo in cui il team verifica un risultato. Se queste informazioni restano implicite, ogni conversazione deve ricostruirle. Un pattern legacy può diventare una regola per errore; una build verde può essere scambiata per la prova che il requisito sia soddisfatto; una decisione può sparire quando termina la chat.

Il problema che vogliamo controllare è questo modo di lavorare: assunzioni non dichiarate, autorità ambigua e risultati accettati senza evidenza. Non promettiamo di rendere deterministico un LLM. Vogliamo rendere espliciti e ispezionabili il contesto, i confini delle azioni e le condizioni per accettarne il risultato, anche quando il percorso seguito dal modello varia.

Un sistema agentico locale al repository organizza questi controlli. Il sistema canonical ne mostra un'implementazione; il corso ne estrae principi da capire e adattare, non una lista di file da copiare.

## Cosa Deve Restare Dopo Le Lezioni

Per ogni task, saper rispondere: quale problema stiamo risolvendo, chi può decidere, quali fonti governano la decisione, quale prova potrebbe smentire il risultato e cosa rimane incerto?

I sei principi (ruoli delimitati, conoscenza governata, gate, artifact durevoli, validazione e composizione) danno le leve per rispondere. Non sono strumenti obbligatori da installare né richiedono lo stesso numero di agent in ogni progetto.

## Dare All'Agente Le Informazioni Giuste

Rendere disponibile la conoscenza necessaria non significa caricare tutta la documentazione in ogni task. Servono fonti autorevoli, aggiornate e selezionabili: terminologia del dominio, invarianti, confini architetturali, convenzioni applicabili e modalità di verifica.

Il glossario chiarisce il significato dei termini. Il knowledge index indica quando leggere un documento. I documenti di conoscenza riportano fatti e fonti verificabili nel repository. Se un fatto è superato, va corretto; se manca un'informazione decisiva, va resa esplicita, non indovinata. Questa distinzione deriva dal [vocabolario canonical](system/canonical/CONTEXT.md) e dal [knowledge guard](system/canonical/instructions/knowledge-guard.instructions.md).

Selezionare non significa saltare conoscenza obbligatoria: il contratto del ruolo può prescrivere tutte le voci `MustHave` e quelle pertinenti al contesto o al componente. Vanno lette nel gate previsto, rispettando anche i limiti alla ricerca e le regole di riuso del ruolo.

## Dare All'Agente Un Modo Di Scoprire Che Ha Sbagliato

«Ricontrolla il tuo lavoro» non basta come criterio di completamento. Prima di implementare, definire il comportamento atteso e la prova che può rilevare un errore: test mirato, controllo di schema, analisi statica, build, osservazione del comportamento o review competente, secondo il rischio.

L'agente deve conoscere come eseguire il controllo, i prerequisiti e come interpretarne l'esito. Entro l'autorità del suo ruolo può eseguirlo, correggere un errore e ripeterlo. Il record deve distinguere cosa è stato eseguito, cosa è passato, cosa è fallito e cosa non è stato verificato. Se mancano accessi, ambiente o copertura, non dichiarare il lavoro verificato: rendere visibile il limite e il passaggio necessario.

Le [istruzioni canonical](system/canonical/instructions/AGENTS.md) richiedono la validazione configurata prima dell'handoff. Creare test richiede l'autorità prevista dal ruolo; Direct Implementor non crea test unitari o di integrazione. Se manca una capability necessaria o un gate resta insoddisfatto, il lavoro resta bloccato in quel punto: una review generica non lo sblocca automaticamente.

Anche un test verde dimostra solo ciò che il test controlla. Una review dello stesso agente non è una prova indipendente; requisiti e controlli possono condividere la stessa assunzione sbagliata. La responsabilità di scegliere criteri adeguati e accettare il rischio residuo rimane del team. La [lezione sulla validazione](lesson-04-validazione.md) spiega anche le restrizioni dei singoli ruoli canonical.

## Trasferire Nel Proprio Repository

Partire da un problema ricorrente e circoscritto, non dall'intera struttura canonical. Questo esempio è un esercizio didattico, non un nuovo contratto canonical:

| Decisione | Esempio: modifica alle autorizzazioni |
| --- | --- |
| Errore da evitare | Un utente legge dati di un altro ambito. |
| Conoscenza necessaria | Regola di isolamento, punto di applicazione e test esistenti, verificati nel progetto. |
| Risultato atteso | L'accesso consentito resta valido; l'accesso fuori ambito viene negato. |
| Confine di autorità | Il ruolo modifica l'implementazione; una variazione della politica richiede la decisione del responsabile. |
| Prova | Un controllo comportamentale distingue accesso consentito e negato; la sola compilazione non basta. |
| Evidenza conservata | Regola usata, esito effettivo dei controlli, limiti e decisioni di review. |

Nel tuo progetto scegli fonti, comandi realmente eseguibili, responsabilità e artifact proporzionati. Non inventare un comando o un'integrazione perché compare nell'esempio; non saltare un gate prescritto da un contratto già adottato.

## Non È Una Soluzione Universale Né Definitiva

Stack, dominio, dimensione del team e costo degli errori cambiano i controlli necessari. Per un'attività piccola e reversibile può bastare un percorso leggero con istruzioni e una verifica mirata. Moltiplicare ruoli, documenti e approvazioni senza un problema osservato aggiunge manutenzione, non evidenza di affidabilità.

Il lavoro quotidiano è il banco di prova: osserva l'errore o l'attrito, identifica se dipende da conoscenza mancante, responsabilità ambigua o verifica insufficiente; correggi la fonte proprietaria; riprova il caso; conserva o rivedi la correzione in base al risultato. Aggiorna o rimuovi regole obsolete e duplicazioni. Non trasformare ogni incidente in una nuova istruzione universale.

Questo ciclo sviluppa la [composizione e il ciclo di vita](lesson-05-composizione-e-ciclo-di-vita.md), senza aggiungere un nuovo principio.

## Prima Domanda Per I Colleghi

Scegli un errore ricorrente del tuo repository. Quale conoscenza avrebbe aiutato a evitarlo? Quale verifica lo avrebbe rilevato? Qual è la modifica minima al workflow da provare sul prossimo task, e quale risultato ti farebbe mantenerla o cambiarla?

[Inizia dalla prima lezione](lesson-01-introduzione.md) · [Prosegui con i principi](principles.md) · [Torna al corso](README.md)
