---
description: >-
  Met deze stappen moet het mogelijk worden om de NL Portal app images te
  deployen naar je gewenste omgeving, mocht dat Azure, AWS of een Kubernetes
  cluster zijn.
---

# Deployment guide

De NL Portal app images (`ghcr.io/nl-portal/nl-portal-app-backend` en `ghcr.io/nl-portal/nl-portal-app-frontend`) worden volledig geconfigureerd via environment variabelen. De complete, versie-specifieke referentie met inline documentatie vind je in de NL Portal App repository, in de bestanden `imports/backend.env` en `imports/frontend.env`. Raadpleeg altijd het bestand dat hoort bij de release die je deployt.

De backend variabelen volgen de Spring Boot relaxed binding naamconventie: de property `nl-portal.config.zakenapi.properties.url` wordt de environment variabele `NLPORTAL_CONFIG_ZAKENAPI_PROPERTIES_URL`.

### Deployen met Helm (Kubernetes)

Voor Kubernetes-omgevingen zijn er officiële Helm charts beschikbaar in de [helm-charts repository](https://github.com/nl-portal/helm-charts). Deze repository bevat charts voor de NL Portal backend, frontend en het Configuratiepaneel (backend en frontend). De beschikbare configuratiewaarden per chart, installatie-instructies en de changelogs met migratie-instructies per versie staan in de README van die repository.

```shell
helm repo add nl-portal https://nl-portal.github.io/helm-charts
helm repo update
```

### Backend: module-configuratie

De functionele modules van de backend (onder andere Zaken API, Catalogi API, Documenten APIs, Objecten API, OpenKlant 2, HaalCentraal, Berichten, Taak, Prefill, DMN, OpenProduct, betalingen en virusscan) worden per module aangezet met een enable-vlag. Alle modules staan standaard uit.

Elke module heeft daarnaast eigen properties die met hetzelfde patroon worden gezet: `NLPORTAL_CONFIG_<MODULE>_PROPERTIES_<PROPERTY>`. Bijvoorbeeld voor de Zaken API:

```shell
NLPORTAL_CONFIG_ZAKENAPI_ENABLED=true
NLPORTAL_CONFIG_ZAKENAPI_PROPERTIES_URL=https://openzaak.example.com
NLPORTAL_CONFIG_ZAKENAPI_PROPERTIES_CLIENTID=nl-portal
NLPORTAL_CONFIG_ZAKENAPI_PROPERTIES_SECRET=<secret>
```

**Let op:** de zaken-functionaliteit vereist dat de Zaken API, Catalogi API én Objecten API modules alle drie enabled zijn.

Alle module properties, inclusief de optionele, zijn met inline documentatie te vinden in `imports/backend.env` in de NL Portal App repository.

Zie de [Keycloak configuratie](keycloak.md) pagina voor het instellen van de bijbehorende clients in Keycloak.
