# Baseline dei Principi Didattici

[Torna alla lettura principale](README.md)

Questo baseline stabilisce cosa il corso può insegnare come principio stabile. Protegge i materiali didattici dal drift verso una singola versione di agent o un esempio locale.

## Fonti Consentite

| Fonte | Uso didattico |
| --- | --- |
| [../system/canonical/CONTEXT.md](../system/canonical/CONTEXT.md) | Vocabolario di Agentic System, Gate, Artifact, Context Glossary e Knowledge Index. |
| [../system/canonical/agents/](../system/canonical/agents/) | Evidenza di ruoli, autorità, input e output delimitati. |
| [../system/canonical/skills/](../system/canonical/skills/) | Evidenza di workflow ripetibili e gate. |
| [../system/canonical/instructions/](../system/canonical/instructions/) | Evidenza di instradamento, scope e knowledge guard. |
| [../public-package/](../public-package/) | Evidenza public-safe per Bootstrap, slot, rendering e distribuzione. |

Il corso usa il sistema canonical e il Bootstrap public-safe come fonti didattiche. Non usare un repository dimostrativo per definire i principi: puo' soltanto dimostrare come un repository li applica.

## Principi Stabili

1. Ruoli con autorità delimitata.
2. Conoscenza selettiva e governata.
3. Gate nelle transizioni dove cambiano rischio o autorità.
4. Artifact, provenienza e ownership durevoli.
5. Validazione come evidenza, non come affermazione.
6. Composizione modulare con ownership e ciclo di vita espliciti.
7. Bootstrap come adattamento controllato, basato su evidenza e approvazione.

Ogni lezione, slide, demo o esercizio deve indicare uno di questi principi e non deve introdurre un ottavo principio senza aggiornare prima questo baseline e [principles.md](principles.md).

## Regole di Allineamento

- Insegnare l'obiettivo di controllo prima del file o della tecnologia che lo implementa.
- Distinguere sempre un glossario da un knowledge index.
- Non presentare una lista di ruoli, directory o comandi come obbligatoria per tutti i repository.
- Usare un esempio solo per verificare un principio osservabile.
- Ogni esercizio deve chiedere una decisione, una prova o un trade-off; non solo un richiamo mnemonico.
- Per Bootstrap, chiedere sempre quale contratto generato va ispezionato, quale assunzione deve essere verificata nel repository target e quale correzione manuale potrebbe rendersi necessaria.
- Quando un contratto canonical cambia, classificare l'impatto su principio, facilitatore, slide, demo e skill `teach`.

## Mappa di Tracciabilità

| Principio | Evidenza canonical primaria | Materiale didattico proprietario |
| --- | --- | --- |
| Ruoli | Canonical agents | `principles.md`, Lezione 1 |
| Conoscenza | Canonical context e knowledge guard | `principles.md`, Lezione 2 |
| Gate | Canonical context e workflow skills | `principles.md`, Lezione 3 |
| Artifact | Canonical context e planning instructions | `principles.md`, Lezione 4 |
| Validazione | Root instructions e contratti workflow | `principles.md`, Lezione 5 |
| Composizione | Root instructions, agents, skills e instructions | `system-map.md`, Lezione 6 |
| Bootstrap | Public-safe package, overlay e slot registry | `principles.md`, Lezione 7 |

## Allineamento Al 17 Settembre 2026

Riferimento pubblico: [changelog](../public-package/CHANGELOG.md), Bootstrap **4.1.0**, Maintainer **2.1.0**. Sono versioni delle fonti, non del corso né una prova dello stato di installazione dei repository dei partecipanti.

| Cambiamento verificato | Fonte | Impatto didattico primario |
| --- | --- | --- |
| Direct Implementor, percorso senza piano e senza creazione di test | [Contratto](../system/canonical/agents/direct-implementor.agent.md) | Lezione 1: [nuova mappa](role-maps/agents/direct-implementor.md); rimandi a gate, artifact e validazione. |
| Binding approvati per ruolo, strumenti nativi e fallback locali, esecuzione inline senza subagent, tracker condizionale e default raggruppabili | [Discovery e decisioni](../public-package/skills/agentic-system/bootstrap-agentic-system/contracts/discovery-and-decisions.md), [changelog 4.0.0](../public-package/CHANGELOG.md) | Lezione 7: portabilità come conservazione delle operazioni, non obbligo di MCP. |
| Schema YAML di test compatibile e resume della sola sessione nota | [Audit](../public-package/skills/agentic-system/bootstrap-agentic-system/contracts/audit-and-handoff.md) | Lezione 7, rimandi a provenienza e validazione. |
| Scelta esplicita del modello Vision | [Decisioni](../public-package/skills/agentic-system/bootstrap-agentic-system/contracts/discovery-and-decisions.md) | Lezione 7 e [mappa Vision](role-maps/agents/vision.md). |
| Risposte di manutenzione risolte per file generato, senza copiare tool da un altro ruolo | [Changelog Maintainer 2.1.0](../public-package/CHANGELOG.md) | Lezione 6: preservare ownership e personalizzazioni. |

I sette principi restano invariati. Il nuovo agente è evidenza di un diverso confine di autorità, non un ottavo principio. Il catalogo contiene il suo template; la generazione resta subordinata al file plan approvato. I nomi dei modelli non diventano obiettivi mnemonici del corso.

[Torna alla lettura principale](README.md)
