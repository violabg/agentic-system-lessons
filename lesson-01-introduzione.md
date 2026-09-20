# Lezione 1: Perche' Un Sistema Agentico

[Torna al corso](README.md) · [Introduzione](introduction.md) · [Principi](principles.md)

## Obiettivo

Capire il problema prima di scegliere strumenti, ruoli o file. Un sistema agentico locale al repository aiuta il team a rendere visibili tre decisioni: **chi puo' decidere, su quale evidenza, con quale verifica**.

## Il Problema

Nel lavoro quotidiano un agente puo' produrre una modifica plausibile senza conoscere le regole del dominio, i confini architetturali o il modo in cui il team verifica un risultato. Se queste informazioni restano implicite, il team ricostruisce le stesse assunzioni in ogni chat. Un pattern legacy puo' sembrare una regola, una build verde puo' sembrare una prova completa e una decisione puo' sparire quando termina la conversazione.

Il sistema non rende deterministico il modello. Rende invece piu' espliciti il contesto, l'autorita', i passaggi di controllo, le prove e i record che permettono di riprendere il lavoro.

## Il Vibe Coding Con Un Sistema

Il vibe coding puo' essere un modo rapido e conversazionale di esplorare un'idea, trasformarla in una modifica e imparare dal feedback del repository. La velocita' e' utile quando il percorso resta osservabile: l'agente riceve il contesto pertinente, opera entro un mandato, incontra controlli nei punti rischiosi e lascia evidenza di cio' che ha fatto.

Senza questi limiti, la stessa velocita' amplifica assunzioni sbagliate. Il punto non e' sostituire l'esplorazione con burocrazia, ma dare al team un modo leggero per distinguere una proposta plausibile da un risultato accettabile.

## Le Sei Leve, In Sintesi

- **Autorita' delimitata:** ogni ruolo ha responsabilita', input, output e azioni vietate riconoscibili.
- **Conoscenza selettiva:** il task carica fonti autorevoli e pertinenti, non tutta la documentazione.
- **Gate e controllo umano:** le transizioni rischiose richiedono condizioni, evidenza o approvazione esplicite.
- **Artifact durevoli:** decisioni, fonti, stato e handoff sopravvivono alla chat.
- **Validazione come evidenza:** ogni prova dimostra un rischio specifico e lascia visibile il rischio residuo.
- **Composizione e ciclo di vita:** ogni regola ha una superficie proprietaria e un percorso di manutenzione.

Queste leve non prescrivono lo stesso numero di agent, directory o comandi per ogni repository. Il [modello di evidenza](principles.md) e la [mappa del sistema](system-map.md) mostrano come possono collaborare.

## Prima Applicazione

Scegli un errore ricorrente nel tuo repository. Scrivi quale informazione manca, chi dovrebbe poter decidere, quale prova potrebbe smentire il risultato e quale record dovrebbe rimanere dopo la chat. Riprenderemo lo stesso caso nelle lezioni successive con il [workshop trasversale](workshop-exercise.md).

## Fonti

- [Perche' un sistema agentico](introduction.md)
- [Principi di sviluppo agentico](principles.md)
- [Vocabolario canonical](system/canonical/CONTEXT.md)
- [Mappa del sistema](system-map.md)

[Prossima: autorita' e conoscenza](lesson-02-autorita-e-conoscenza.md)
