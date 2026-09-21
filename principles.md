# Principi di Sviluppo Agentico

> Approfondimento facoltativo: [biblioteca](reference/README.md). I contratti di questa implementazione non sono prerequisiti del corso.

[Torna alla lettura principale](README.md) · [Mappa del sistema](system-map.md)

Questa lettura insegna i controlli che rendono affidabile un sistema agentico in un repository. Il sistema canonical è evidenza di questi controlli, non un modello di directory o di file da copiare.

## Il Modello di Evidenza

Un sistema agentico affidabile trasforma una richiesta in una decisione verificabile:

```text
Richiesta -> ruolo autorizzato -> conoscenza selezionata -> decisione o modifica
          -> gate e artifact -> validazione -> handoff ispezionabile
```

La domanda per ogni passaggio e': quale evidenza permette al prossimo ruolo o alla persona responsabile di fidarsi di questo avanzamento?

## 1. Ruoli con Autorita' Delimitata

**Failure mode:** lo stesso agente decide scope, modifica codice e dichiara il proprio risultato senza un confine osservabile.

**Obiettivo di controllo:** assegnare un ruolo quando cambiano autorita', contesto, strumenti, output o responsabilita' di approvazione. Un ruolo non e' un titolo prestigioso: e' un contratto che limita cosa puo' decidere e cosa deve consegnare.

Nel sistema canonical, i contratti di Planner, Implementor, Direct Implementor, Integration Tester, Knowledge Builder, Ask e Vision dimostrano confini diversi. Il repository target puo' usare altri nomi o un numero minore di ruoli, ma non deve lasciare implicito un cambio di autorita' rischioso.

Il [confronto dei percorsi](role-maps/README.md) rende esplicita una distinzione: Planner → Implementor usa un piano approvato; Direct Implementor valida requisiti e design senza produrre quel piano. Entrambi conservano confini osservabili. Un unico ruolo può analizzare e implementare se il suo contratto lo autorizza; non può attribuirsi autorità di approvazione illimitata.

Domanda di trasferimento: quale passaggio nel tuo repository non deve poter essere completato dalla stessa conversazione senza un handoff o una review?

## 2. Conoscenza Selettiva e Governata

**Failure mode:** l'agente cerca ovunque, adotta il primo pattern simile e confonde documentazione generale con regole applicabili al task.

**Obiettivo di controllo:** fare scegliere fonti autorevoli e proporzionate al task. Un context glossary stabilizza nomi, confini e fonti di verita'; un knowledge index instrada verso i pochi documenti da leggere. Non sono intercambiabili.

L'evidenza canonical e' il glossario [system/canonical/CONTEXT.md](system/canonical/CONTEXT.md) insieme al [knowledge guard](system/canonical/instructions/knowledge-guard.instructions.md). Il controllo non chiede di caricare piu' contesto: chiede di registrare quale contesto basta e perche'.

Domanda di trasferimento: per un cambiamento ad alto rischio, quali due o tre fonti sono autorevoli e quali fonti plausibili devono restare escluse?

## 3. Gate e Controllo Umano

**Failure mode:** una modifica parte prima che scope, rischio, approvazione o definizione di pronto siano verificabili.

**Obiettivo di controllo:** fermare il workflow nelle transizioni dove l'errore costa caro o cambia l'autorita'. Un gate puo' richiedere un artifact, un'approvazione esplicita, una prova di qualita' o un handoff completo. Nel progettare un nuovo workflow, non tutti i passaggi richiedono un gate. Quando si esegue un contratto esistente, tutti i gate prescritti restano obbligatori e ordinati; un gate soddisfatto non richiede una pausa umana se il contratto non la prevede.

Un gate utile risponde a tre domande: cosa blocca il passaggio, quale evidenza lo sblocca, chi ha l'autorita' di accettarla? La chat puo' contenere l'approvazione, ma l'artifact deve conservarne il record.

Domanda di trasferimento: dove il tuo team deve approvare prima che un agente modifichi codice o configuri un'integrazione?

## 4. Artifact, Provenienza e Ownership Durevoli

**Failure mode:** decisioni, domande aperte e risultati di validazione rimangono nella memoria di una chat e il lavoro non puo' essere ripreso o controllato.

**Obiettivo di controllo:** conservare in artifact stabili le informazioni che un altro ruolo deve poter ispezionare: decisioni, fonti, approvazioni, rischi, stato e definition of done. Ogni artifact ha un proprietario e una ragione per esistere.

Le planning-session instructions canonical mostrano come un brief, un piano e un handoff rendano il lavoro riprendibile. Direct Implementor espone la scomposizione dei requisiti in chat e conserva inventario normativo, risposte in memoria, log ed execution report nei gate previsti, anche senza piano intermedio. Il nome tecnico Planning Session ID identifica il record di lavoro: non prova che sia stato prodotto un piano. Il tuo repository non deve adottare gli stessi nomi di file: deve rendere durevole la stessa evidenza.

Domanda di trasferimento: quale record permetterebbe a una persona nuova di capire perche' una modifica e' stata approvata e cosa resta da verificare?

## 5. Validazione Come Evidenza

**Failure mode:** l'agente afferma che il lavoro e' corretto senza una prova che possa falsificare l'errore piu' probabile.

**Obiettivo di controllo:** scegliere la prova piu' piccola e rilevante per ogni handoff: controllo di schema, test mirato, lint, build, review o verifica manuale. Un comando verde e' evidenza del rischio che controlla, non una dichiarazione generale di qualita'.

Il sistema canonical mantiene contratti di validazione e richiede prove prima dell'handoff. Per ogni decisione, distinguere sempre: quale rischio e' stato controllato, quale prova e' stata eseguita e quale rischio residuo rimane.

Direct Implementor esegue build e review ma non crea test: questa è una restrizione del ruolo, non una raccomandazione a rinunciare ai test. Il team deve rendere espliciti copertura mancante, rischio residuo e workflow responsabile delle prove ulteriori.

Domanda di trasferimento: quale controllo potrebbe dimostrare rapidamente che il tuo piano o la tua generazione e' sbagliata?

## 6. Composizione e Ciclo di Vita Espliciti

**Failure mode:** la stessa regola viene copiata in root instructions, agent, skill e documentazione; poi una correzione aggiorna solo una copia.

**Obiettivo di controllo:** collocare una regola nella superficie che la possiede e usare le altre superfici per instradare, non duplicare. Le root instructions dichiarano regole sempre attive e indicano dove leggere il resto; agent definiscono ruoli; skill organizzano workflow ripetibili; knowledge documenta o instrada fonti selettive.

Il controllo di ciclo di vita e' altrettanto importante: chi puo' modificare la regola, quale output deve essere riallineato e quale validazione segnala il drift? Il sistema canonical offre una reference implementation di questa separazione, non una struttura obbligatoria.

Domanda di trasferimento: dove dovrebbe vivere una nuova regola di review nel tuo repository, e quale file derivato o workflow dovrebbe essere verificato dopo la modifica?

## Ciclo di Progettazione

1. Nomina il failure mode costoso.
2. Decidi quale ruolo, conoscenza, gate, artifact o validazione lo controlla.
3. Scrivi la regola minima nella superficie proprietaria.
4. Provala in un workflow reale.
5. Conserva il risultato e i rischi residui.
6. Riesamina il sistema mantenuto quando cambiano repository, strumenti o failure mode.

[Torna alla lettura principale](README.md)
