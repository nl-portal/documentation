# Configuration Panel

Het Configuration Panel is een beheerapplicatie waarmee je de NL Portal backend en theming kunt configureren via een gebruiksvriendelijke interface — zonder code aan te passen of eigen images te bouwen.

Zie de [nl-portal-configuration-panel repository](https://github.com/nl-portal/nl-portal-configuration-panel) voor installatie-instructies, environment variabelen en versiecompatibiliteit.

## Wat kun je configureren

### Backend modules

Via het Configuration Panel kun je alle backend modules in- en uitschakelen en configureren:

| Module | Beschrijving |
|--------|--------------|
| Zaken API | Koppeling met Open Zaak voor zaken |
| Catalogi API | Zaaktypen en informatieobjecttypen |
| Documenten APIs | Documentopslag (meerdere configuraties mogelijk) |
| Besluiten API | Besluiten bij zaken |
| Objecten API | Objectregistratie voor taken en berichten |
| OpenKlant 2 | Klantgegevens en contactmomenten |
| HaalCentraal BRP v2 | Persoonsgegevens uit de BRP |
| HaalCentraal HR | Bedrijfsgegevens uit het Handelsregister |
| Taak | Externe taken via Objecten API |
| Berichten | Berichtenfunctionaliteit |
| Product | Productweergave |
| OpenProduct | Koppeling met OpenProduct API |
| DMN | Decision Model and Notation |
| Prefill | Voorinvullen van formulieren |
| Payment (Ogone/Direct) | Betalingsintegraties |
| ClamAV | Virusscanning van uploads |

### Theming

Het Configuration Panel biedt ook theming-opties:

* **Logo** — upload een eigen logo voor de header
* **Design tokens** — pas kleuren, typografie en andere stijlen aan via een CSS-editor

Zie [Eigen vormgeving](eigen-vormgeving.md) voor meer informatie over design tokens.

## Uitproberen via de demo-omgeving

De eenvoudigste manier om het Configuration Panel te gebruiken is via de [NL Portal App](https://github.com/nl-portal/nl-portal-app) demo-omgeving. Start het `config` profiel mee:

```shell
docker compose --profile remote --profile zgw --profile haalcentraal --profile config up -d
```

Het Configuration Panel is daarna bereikbaar op `http://localhost:3001` met gebruikersnaam **admin** en wachtwoord **admin**.

## NL Portal aansluiten op het Configuration Panel

De NL Portal backend libraries hebben ingebouwde ondersteuning voor het Configuration Panel.

**Beveiliging:** het Configuration Panel bevat gevoelige configuratie zoals API-tokens en secrets. Maak het Configuration Panel nooit publiek toegankelijk. Zowel de webapp als de config server endpoints mogen alleen bereikbaar zijn via interne netwerken (bijv. Kubernetes cluster-netwerk, localhost) of via een beveiligde gateway met authenticatie.

Configureer de volgende environment variabelen op de **NL Portal backend**:

| Variabele | Beschrijving |
|-----------|--------------|
| `CONFIGURATION_PANEL_ENABLED` | Zet op `true` om de integratie te activeren (default: `false`) |
| `CONFIGURATION_PANEL_URI` | URL van het Configuration Panel, bijv. `http://config-panel:8090/configuration` |
| `CONFIGURATION_PANEL_TOKEN` | Token voor authenticatie (moet overeenkomen met `CONFIG_SERVER_TOKEN` op het Configuration Panel) |
| `CONFIGURATION_PANEL_APPLICATION_NAME` | Naam van de applicatie, bijv. `nl-portal-app` |

Voorbeeld:

```shell
CONFIGURATION_PANEL_ENABLED=true
CONFIGURATION_PANEL_URI=http://host.docker.internal:8090/configuration
CONFIGURATION_PANEL_TOKEN=VerySecretToken
CONFIGURATION_PANEL_APPLICATION_NAME=nl-portal-app
```

De NL Portal backend haalt bij opstarten de configuratie op uit het Configuration Panel. Waarden uit het Configuration Panel hebben voorrang op environment variabelen. Als notify is ingeschakeld op het Configuration Panel, kan de backend automatisch herstarten bij wijzigingen via Spring Actuator endpoints.

## Helm charts

Voor Kubernetes-omgevingen zijn er Helm charts beschikbaar (`nl-portal-configpanel-backend` en `nl-portal-configpanel-frontend`). Zie de [helm-charts repository](https://github.com/nl-portal/helm-charts) voor installatie-instructies.
