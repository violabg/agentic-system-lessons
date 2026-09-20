# Lezione 3: Gate, Controllo Umano E Artifact

[Torna al corso](README.md) · [Lezione 2](lesson-02-autorita-e-conoscenza.md) · [Principi](principles.md)

## Obiettivo

Rendere controllabili le transizioni rischiose e conservare le decisioni necessarie per riprendere il lavoro fuori dalla chat.

## Failure Mode

Una modifica parte prima che scope, rischio, approvazione o definizione di pronto siano verificabili. In seguito nessuno sa quali fonti siano state usate, chi abbia approvato, cosa sia ancora aperto o quale handoff sia stato completato.

## Controlli

Un **gate** e' un checkpoint che blocca una transizione finche' non sono soddisfatte condizioni osservabili. Un gate utile risponde a tre domande: cosa blocca il passaggio, quale evidenza lo sblocca e chi ha l'autorita' di accettarla? Non ogni passaggio richiede approvazione umana, ma i gate prescritti da un contratto esistente restano obbligatori e ordinati.

Un **artifact** e' un record durevole di requisiti, fonti, decisioni, approvazioni, rischi, stato, validazioni o handoff. Deve avere un proprietario e una ragione per esistere. La chat puo' contenere una decisione, ma l'artifact ne conserva il contesto e rende possibile l'ispezione successiva.

Il piano non e' l'unico artifact possibile. Un percorso diretto puo' conservare requisiti, risposte, regole e report nei propri gate. Il controllo richiesto dipende dal workflow, non dal nome del file.

## Evidenza Nel Sistema

Le [planning-session instructions](system/canonical/instructions/planning-sessions.instructions.md) mostrano come rendere riprendibile un lavoro. La [mappa del percorso](system-map.md) collega gate, artifact e handoff. Il [confronto dei percorsi](role-maps/README.md) mostra che senza piano intermedio non scompare l'obbligo di conservare evidenza.

## Esercizio

Trasforma un'approvazione verbale del [caso condiviso](workshop-exercise.md) in un record: richiesta, decisione, fonte, responsabile, gate superato, stato, prova richiesta e rischio residuo. Aggiungi una condizione che dovrebbe bloccare l'handoff.

## Domanda Di Trasferimento

Quale record permetterebbe a una persona nuova di capire perche' una modifica e' stata approvata e cosa resta da verificare? Chi possiede quel record?

[Prossima: validazione](lesson-04-validazione.md)
