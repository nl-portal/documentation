# NL Portal

NL Portal is een open source Mijn Omgeving voor overheden. NL Portal is gebouwd volgens de principes van [Common Ground](https://vng.nl/artikelen/common-ground). NL Portal is gebruikt de API's van [VNG Zaakgericht werken](https://vng-realisatie.github.io/gemma-zaken/standaard/). De portal is open source en kan door elke (overheids-) organisatie gebruikt en verbeterd worden zonder enige restricties.

De basis principes van NL Portal zijn:
- Open standaarden, open source licentie EUPL 1.2;
- Compatible met diverse formulierapplicaties;
- Frontend UI gebaseerd op [NL Design System](https://nldesignsystem.nl/);
- Voldoet aan alle web toegankelijkheidsrichtlijnen (WCAG);
- Onafhankelijk van proces- of zaak management systemen;
- Horizontal schaalbaar;

## Functionaliteiten

Op dit moment kent NL Portal de volgende functionaliteiten
- Bezoekers kunnen nieuwe zaken aanmaken;
- Bezoekers kunnen altijd de actuele status van hun zaken zien (track and trace);
- Behandelaars van zaken kunnen taken aan de gebruikers geven om uit te voeren (bijvoorbeeld extra informatie toevoegen aan een zaak);
- Koppeling met Digid en eHerkenning
- Bezoekers kunnen bestanden zoals besluit documenten downloaden


## Code

Alle code staat [op onze github repository](https://github.com/nl-portal/). Je vind hier de volgende dingen:
- [Frontend libraries](https://github.com/nl-portal/nl-portal-frontend-libraries) - De React frontend code die het hart is van de NL Portal
- [Backend libraries](https://github.com/nl-portal/nl-portal-backend-libraries) - De Kotlin code die informatie ontsluit naar de Frontend in GraphQL
- [Backend template](https://github.com/nl-portal/nl-portal-backend-template) - Template repository waarmee je de Backend kunt opstarten
- [Frontend template](https://github.com/nl-portal/nl-portal-frontend-template) - Template repository waarmee je de Frontend kunt opstarten
- [Helm charts](https://github.com/nl-portal/helm-charts) - Helm charts om de gehele applicatie in een Kubernetes cluster te draaien
- [Documentatie](https://github.com/nl-portal/documentation) - Documentatie over NL Portal
- [Docker compose](https://github.com/nl-portal/nl-portal-docker-compose) - Met dit docker compose project kun je lokaal een volledige software stack draaien zodat je lokaal features kunt ontwikkelen.


