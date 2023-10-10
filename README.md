# NL Portal

NL Portal is applicatie waarmee organisaties kunnen communiceren met burgers en dere partijen. Het is een Mijn Omgeving. NL Portaal is gebouwd volgens de principes van [Common Ground](https://vng.nl/artikelen/common-ground). NL Portal is gebruikt de API's van [VNG Zaakgericht werken](https://vng-realisatie.github.io/gemma-zaken/standaard/). De portal is open source en kan door elke (overheids-) organisatie gebruikt en verbeterd worden zonder enige restricties.

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
- [Helm charts](https://github.com/nl-portal/helm-charts) - Helm charts om de gehele applicatie in een Kubernets cluster te draaien
- [Documentatie](https://github.com/nl-portal/documentation) - Documentatie over NL Portal
- [Docker compose](https://github.com/nl-portal/nl-portal-docker-compose) - Met dit docker compose project kun je lokaal een volledige software stack draaien zodat je lokaal features kunt ontwikkelen.

## Designs

UI Designs are made in Figma and can be found here:
**Generieke Services Mijn Omgeving**
The designs of generic services notifications, messages, tasks and contactmoments and a overview of the content for these services.
Link to the project: https://figmashort.link/8emsT3
Link to the prototype: https://figmashort.link/JGDMzi
Relevant pages: 
-	🖲 Concept
-	🖥️ Prototype desktop v3
-	📱 Prototype mobiel v3

**MVP Mijn Omgeving**
The MVP for the year 2023 as defined by DenHaag PO.
Link: https://figmashort.link/WmDz3T
Relevant pages:
-	🧱 Keuzes
-	🖥️ Prototype desktop
-	📱 Prototype mobiel

**Figma Quick start**
1 - Browsing pages
Click on the Figma logo in the upper left corner to see the pages.
![image](https://github.com/nl-portal/documentation/assets/56682291/0d402c96-02f9-40f5-831b-fc8a9188ee7f)

2 - Add comment
Click on the comment button or press 'C' to leave a comment.
![image](https://github.com/nl-portal/documentation/assets/56682291/25182ff1-62fa-4bc1-a456-ee98c4ff0e24)


