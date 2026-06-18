# Module afhankelijkheden

Overzicht van welke NL Portal modules geconfigureerd moeten zijn per feature.

> **Let op:** Dit overzicht is gebaseerd op de laatst beschikbare major/minor release en geldt voor de standaard nl-portal-app configuratie. Eigen implementaties kunnen andere frontend-vereisten hebben, maar backend module-afhankelijkheden (zoals taak → objectenapi) blijven van toepassing.

## Afhankelijkheidsgrafiek

```mermaid
flowchart TB
    subgraph features["Features"]
        zaken["Zaken"]
        taken["Taken"]
        berichten["Berichten"]
        account["Account"]
    end

    subgraph modules["Modules"]
        zakenapi["zakenapi"]
        catalogiapi["catalogiapi"]
        documentenapis["documentenapis"]
        objectenapi["objectenapi"]
        taak["taak"]
        berichtenmod["berichten"]
        openklant2["openklant2"]
        haalcentraal2["haalcentraal2"]
    end

    zaken --> zakenapi
    zaken --> catalogiapi
    zaken --> documentenapis
    zaken --> objectenapi
    zaken --> taak
    zaken -.->|"showContactTimeline"| openklant2
    
    taken --> objectenapi
    taken --> taak
    taken --> documentenapis
    
    berichten --> objectenapi
    berichten --> berichtenmod
    berichten --> documentenapis
    
    account --> haalcentraal2
    account --> openklant2
```

## Afhankelijkheidsmatrix

| Feature | zakenapi | catalogiapi | documentenapis | objectenapi | taak | berichten | openklant2 | haalcentraal2 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Zaken | ✓ | ✓ | ✓ | ✓ | ✓ | | ¹ | |
| Taken | | | ✓ | ✓ | ✓ | | | |
| Berichten | | | ✓ | ✓ | | ✓ | | |
| Account | | | | | | | ✓ | ✓ |

¹ Alleen vereist als `showContactTimeline` aan staat
