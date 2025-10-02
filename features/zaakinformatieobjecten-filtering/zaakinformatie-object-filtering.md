# Zaak informatieobjecten filtering

Het is mogelijk om te bepalen welke Documenten een gebruiker te zien krijgt op een zaak pagina. Zaak Informatieobjecten worden gefilterd voor dat ze geretourneerd worden.

## Configuratie

Deze functionalitiet maakt gebruik van twee whitelists in de spring properties van jouw applicatie. Beide properties 
hebben zijn eigen [opties en standaardwaardes](#opties). Standaardwaardes worden gebruikt als deze properties niet 
configureerd zijn.

1. `nl-portal.zgw.zakenapi.zaak-documenten.status-whitelist`
2. `nl-portal.zgw.zakenapi.zaak-documenten.vertrouwelijkheidsaanduiding-whitelist`

### Opties

De volgende opties zijn van toepassing bij de whitelists en zijn gebaseerd op de 
[enkelvoudiginfromatieobject](https://openzaak.ritense.opengem.nl/documenten/api/v1/schema/#tag/enkelvoudiginformatieobjecten)
Documenten API specificatie.

| Status           | Standaardwaarde |
|------------------|:---------------:|
| ter_vaststelling |                 |
| in_bewerking     |                 |
| definitief       |        X        |
| gearchiveerd     |        X        |

| Vertrouwelijkheidaanduiding | Standaardwaarde |
|-----------------------------|:---------------:|
| openbaar                    |        X        |
| beperkt_openbaar            |        X        |
| intern                      |        X        |
| zaakvertrouwelijk           |        X        |
| vertrouwelijk               |                 |
| confidentieel               |                 |
| geheim                      |                 |

### Voorbeeld

De volgende spring properties zorgen ervoor dat alle Informatieobjecten die bij jouw Zaak horen worden geretourneerd.
```yaml
nl-portal:
    zgw:
        zakenapi:
            zaak-documenten:
                vertrouwelijkheidsaanduiding-whitelist:
                    - openbaar
                    - beperkt_openbaar
                    - intern
                    - vertrouwelijk
                    - zaakvertrouwelijk
                    - confidentieel
                    - geheim
                    - zeer_geheim
                status-whitelist:
                    - ter_vaststelling
                    - in_bewerking
                    - definitief
                    - gearchiveerd
```
