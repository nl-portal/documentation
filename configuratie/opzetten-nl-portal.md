# Opzetten NL Portal

### Wat heb je nodig

Om de NL Portal lokaal op te zetten is enige basiskennis van de CLI (command-line interface) vereist. Daarnaast heb je de volgende software nodig:

* [Docker Desktop](https://www.docker.com/products/docker-desktop/) — de enige harde vereiste om de NL Portal demo te draaien.
* Voor het maken van een eigen portaal: [Git](https://git-scm.com/) en een [GitHub](https://github.com/) account. Het bouwen van de applicatie gebeurt via Docker, een lokale JDK- of Node-installatie is niet nodig.

#### Waar kan ik de code vinden

Alle code en informatie is opensource en kan gevonden worden op [github.com](https://github.com/nl-portal). De NL Portal is opgesplitst in meerdere repositories. Hieronder een korte beschrijving van elk.

| Repository                                                                       | Beschrijving                                                                                                                                            |
| -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Documentatie](https://github.com/nl-portal/documentation)                       | Documentatie over de NL Portal                                                                                                                          |
| [NL Portal App](https://github.com/nl-portal/nl-portal-app)                      | Referentie-implementatie van de NL Portal backend en frontend apps, inclusief een docker-compose demo-omgeving. Het startpunt voor een eigen portaal.   |
| [Frontend Libraries](https://github.com/nl-portal/nl-portal-frontend-libraries)  | Libraries voor de frontend die gebruikt worden in de NL Portal App                                                                                      |
| [Backend Libraries](https://github.com/nl-portal/nl-portal-backend-libraries)    | Libraries voor de backend die gebruikt worden in de NL Portal App                                                                                       |
| [Docker Compose](https://github.com/nl-portal/nl-portal-docker-compose)          | Een docker compose setup om het ZGW landschap op te zetten                                                                                              |
| [Helm Charts](https://github.com/nl-portal/helm-charts)                          | Kubernetes Helm charts voor het deployen van een NL Portal omgeving                                                                                     |

**Let op:** de eerdere frontend en backend template repositories zijn vervangen door de [NL Portal App](https://github.com/nl-portal/nl-portal-app) repository. Gebruik deze als startpunt voor een eigen portaal.

### Route 1: De prebuilt images draaien

De snelste manier om de NL Portal te bekijken is via de kant-en-klare demo-omgeving in de [NL Portal App](https://github.com/nl-portal/nl-portal-app) repository. De docker-compose file in deze repository bevat alles wat nodig is:

* De prebuilt NL Portal backend en frontend images (`ghcr.io/nl-portal/nl-portal-app-backend` en `ghcr.io/nl-portal/nl-portal-app-frontend`).
* De benodigde ZGW componenten (Open Zaak, Objecten API, OpenKlant, OpenProduct) en Haal Centraal mocks, opgedeeld in docker-compose profielen zodat je zelf kiest welke onderdelen je start.
* Een voorgeconfigureerde Keycloak met token exchange v1 (zie ook de [Keycloak configuratie](keycloak.md) pagina).

Clone de repository en start de demo-omgeving met:

```shell
docker compose --profile remote --profile zgw --profile haalcentraal up -d
```

De NL Portal is daarna bereikbaar op `http://localhost:3000`. Je kunt inloggen met de volgende testgebruikers:

| Gebruikersnaam | Wachtwoord | Identificatie (BSN/KVK) |
| -------------- | ---------- | ----------------------- |
| burger         | burger     | 999993847               |
| bedrijf        | bedrijf    | 14127293                |

**Let op:** het opstarten van alle ZGW componenten kan enkele minuten duren. De profielen `remote` en `local` kunnen niet tegelijk draaien omdat ze dezelfde poorten gebruiken.

De volledige tabel met services, poorten en profielen vind je in de README.md van de NL Portal App repository.

### Route 2: Configureren via het Configuration Panel

De aanbevolen manier om de NL Portal aan te passen is via het [Configuration Panel](configuration-panel.md). Hiermee kun je zonder code aan te passen:

* Alle backend modules configureren (ZGW APIs, HaalCentraal, OpenKlant, etc.)
* Een eigen logo uploaden
* De huisstijl aanpassen via design tokens

Start het Configuration Panel mee in de demo-omgeving:

```shell
docker compose --profile remote --profile zgw --profile haalcentraal --profile config up -d
```

Het Configuration Panel is bereikbaar op `http://localhost:3001` met gebruikersnaam **admin** en wachtwoord **admin**.

Zie de [Configuration Panel](configuration-panel.md) pagina voor uitgebreide documentatie over het aansluiten van een bestaande NL Portal instantie.

### Route 3: Fork de repository (geavanceerd)

Wil je de NL Portal uitbreiden met eigen componenten of functionaliteit die niet via configuratie mogelijk is? Fork dan de [NL Portal App](https://github.com/nl-portal/nl-portal-app) repository en bouw je eigen images:

1. Fork de repository op GitHub en clone je fork lokaal.
2. Pas de frontend en/of backend aan naar wens.
3. Bouw en start je eigen images met:

```shell
docker compose --profile local --profile zgw --profile haalcentraal up -d --build
```

Ook nu is de NL Portal bereikbaar op `http://localhost:3000` met dezelfde testgebruikers als hierboven.

**Wanneer forken?** Alleen nodig voor:
* Eigen frontend componenten of pagina's
* Eigen backend plugins of modules
* Aanpassingen aan de authenticatiemethoden (zie [Keycloak configuratie](keycloak.md))

Voor configuratie van API-koppelingen en huisstijl is forken niet nodig — gebruik hiervoor het [Configuration Panel](configuration-panel.md).

### Configuratie via environment variabelen

De NL Portal app images kunnen ook volledig geconfigureerd worden via environment variabelen. De volledige referentie met inline documentatie vind je in de NL Portal App repository, in de bestanden `imports/backend.env` en `imports/frontend.env`. Zie de [Deployment guide](deployment-guide.md) voor de naamconventie, de module-configuratie en het deployen met Helm.

### Vervolgstappen

Nu je eerste NL Portal draait kun je verder met:

* [Configuration Panel](configuration-panel.md) — configureer API-koppelingen en theming via een UI.
* [Eigen vormgeving](eigen-vormgeving.md) — meer informatie over design tokens en huisstijl.
* [Deployment guide](deployment-guide.md) — deploy de NL Portal naar je eigen omgeving (Azure, AWS of Kubernetes).
* [Keycloak configuratie](keycloak.md) — sluit de NL Portal aan op je eigen Keycloak.
