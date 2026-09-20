# Slide 6: Composizione

[Indice slide](README.md) · [Principi](../principles.md)

**Failure mode:** una regola e duplicata in istruzioni, agent, skill e documentazione, poi diverge.

**Controllo:** scrivi una regola nella superficie che la possiede e instrada le altre superfici verso quella fonte.

```mermaid
flowchart TD
    Rule[Nuova regola] --> Owner{Chi la possiede?}
    Owner --> Instruction[Istruzione: regola sempre attiva]
    Owner --> Agent[Agent: limite di ruolo]
    Owner --> Skill[Skill: procedura ripetibile]
    Owner --> Knowledge[Knowledge: fonte selettiva]
    Instruction --> Verify[Verifica drift]
    Agent --> Verify
    Skill --> Verify
    Knowledge --> Verify
```

**Evidenza:** Author Repo Skill decide dove collocare una procedura. Maintainer confronta baseline, nuova resa e personalizzazioni; risolve le answers per il file esatto, senza prendere i tool di un altro ruolo.

**Esercizio:** assegna una nuova regola di review a una sola superficie proprietaria.

**Decisione trasferibile:** correggi la fonte, poi propaga gli output.