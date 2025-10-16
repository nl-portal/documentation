# NL-Portal 2.0.0

## Features

- Diverse dependencies geüpgraded
- Nieuwe module `haalcentraal2` geïmplementeerd — biedt ondersteuning voor interactie met `HaalCentraal` BRP 2.0 en `Bewoningen` API’s
- Volledige ondersteuning toegevoegd voor NL Portal Configuratiepaneel 1.0
- Nieuwe feature toggle toegevoegd in de frontend om te schakelen tussen OpenKlant 1 en OpenKlant 2 `(OPEN_KLANT_VERSION)`
- OpenKlant2 uitgebreid met extra functionaliteiten:
    - Zoeken op een specifiek `DigitaleAdres`
    - Zoeken naar alle `KlantContactmomenten` van een `Partij`
    - Mogelijkheid om een notitie toe te voegen aan een `DigitaleAdres`
    - Een `Partij` wordt automatisch aangemaakt als deze nog niet bestaat bij het aanmaken van een `DigitaleAdres`
- OpenZaak uitgebreid:
    - Zaken kunnen nu worden uitgesloten op basis van ZaakType. Nieuwe configuratie-optie: `zaakTypesIdsExcluded` (lijst van UUID’s om uit te sluiten in de getZaken-query)
- Idle timer en logout-waarschuwing toegevoegd aan de frontend
- UI-verbeteringen:
    - De gebruikersinformatiepagina is herontworpen om gegevens te tonen uit `OpenKlant` 2.0, `HaalCentraal` BRP 2.0 en `HaalCentraal Bewoningen`
    - Verschillende componenten zijn verbeterd in vormgeving en gebruiksvriendelijkheid

## Bugfixes

Er zijn geen bugfixes

## Breaking changes

- Configuratie-eigenschappen voor NL Portal zijn gewijzigd. De configuratie is nu gegroepeerd per feature en bevat een toggle. Zie [#393](https://github.com/nl-portal/nl-portal-backend-libraries/pull/393/files) voor een voorbeeld.
- Authenticatie is overgezet van de Keycloak JS-adapter naar react-oidc-context [#276](https://github.com/nl-portal/nl-portal-frontend-libraries/pull/276). Hierdoor kan NL Portal nu gebruikt worden met elke OIDC-compatibele identity provider.

## Deprecations

Er zijn geen deprecations

## Bekende problemen

Er zijn geen bekende problemen
