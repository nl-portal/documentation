# NL-Portal 3.0.0

## Functionaliteiten

* Verschillende afhankelijkheden zijn geüpgraded.
* Verbeteringen aan bestaande functionaliteiten:
    * OpenKlant 2:
        * Nieuwe zoekfilters toegevoegd voor Klantcontactmomenten om te kunnen zoeken op Onderwerpobject-criteria.
    * OpenZaak:
        * Ondersteuning toegevoegd voor het opvragen van ZaakResultaten.
        * Nieuwe feature toggle-configuratie-eigenschap toegevoegd:
          `nl-portal.config.zakenapi.useNnpKvkQueryIdentificators`
          om de nieuwe `kvkNummer`-eigenschap van een `Rol` (beschikbaar sinds OpenZaak 1.20.0) te gebruiken bij het
          opvragen van Zaken als een Bedrijf.
        * Mogelijkheid toegevoegd om de SubStatussen van een Zaak op te vragen. Alleen SubStatussen met doelgroep
          betrokkenen of geen doelgroep worden aan de gebruiker getoond.
    * Direct
        * Nieuwe eigenschap `customTemplateUrl` toegevoegd voor het instellen van de
          [variant](https://docs.direct.worldline-solutions.com/en/integration/basic-integration-methods/hosted-checkout-page#createhostedcheckoutrequest:~:text=Method%202%3A%20Customise%20the%20Template%20in%20the%20Merchant%20Portal)
          van een HostedCheckout.
    * Berichten
        * De `getBericht`-query retourneert nu ook het Bericht-ID voor eenvoudiger verwerking in de frontend.
        * Mogelijkheid toegevoegd om de bijlagen van een Bericht te downloaden. Hiervoor moet de Documenten API
          geconfigureerd zijn.
* Mogelijkheid toegevoegd om een applicatielogo en stijlen te definiëren via configuratie-eigenschappen of het NL Portal
  Configuratiepaneel.
* Mogelijkheid toegevoegd om extra OIDC-parameters te definiëren in de NL Portal Frontend
  ([#426](https://github.com/nl-portal/nl-portal-frontend-libraries/pull/426)).
* Ondersteuning geïntroduceerd voor [Open Product](https://github.com/maykinmedia/open-product) via de `openproduct` NL
  Portal Backend-module. Dit is bedoeld om de op Objecten API gebaseerde `product`-module te vervangen.
* Formio-componenten zijn vervangen door maatwerkcomponenten die de stijlen van de applicatie volgen, waardoor Formio-formulieren prettiger zijn om mee te werken.

## Bugfixes

Er zijn geen bugfixes.

## Breaking changes

* OpenKlant 2:
    * Een typefout gecorrigeerd door de query `getUserDigitaleAdresen` te hernoemen naar `getUserDigitaleAdressen`.
* `graphql-kotlin` vervangen door [Spring for GraphQL](https://spring.io/projects/spring-graphql) voor een meer uniforme
  manier van werken en fijnmazige controle over querydefinities.

## Verwijderingen en afschrijvingen

* De volgende backend-modules zijn verwijderd:
    * `haalcentraal-all` - De HaalCentraal BRP 1.0 API is verlaten en al geruime tijd niet meer in gebruik. Alle
      functionaliteit is vervangen door de `haalcentraal2`-module, die BRP 2.0 en Bewoningen API-functionaliteit biedt.
      De HaalCentraal HR-functionaliteit is verplaatst naar een eigen module, omdat deze nog in gebruik is.
    * `klant`, `klant-generiek` en `klantcontactmomenten` - De Klantinteracties API-specificatie wordt al lange tijd
      niet meer ondersteund door de VNG. Deze module is vervangen door de `openklant`-module,
      die [Open Klant](https://github.com/maykinmedia/open-klant) implementeert.
* Taak V1-functionaliteit verwijderd ten gunste van Taak V2, die het
  [Externe Klanttaak](https://dienstverleningsplatform.gitbook.io/platform-generieke-dienstverlening-public/patronen/taken/externe-klanttaak)
  patroon implementeert.

## Bekende problemen

Er zijn geen bekende problemen.
