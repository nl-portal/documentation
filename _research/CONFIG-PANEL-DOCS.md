# NL Portal Configuration Panel — Functionele Documentatie

## Wat is het Configuration Panel?

Het Configuration Panel is een beheerinterface waarmee beheerders de NL Portal applicatie kunnen configureren. Het biedt een centrale plek om:

- **Features** in- of uitschakelen (API-koppelingen, betalingen, berichtenservices, etc.)
- **API-instellingen** beheren per feature (endpoints, credentials, opties)
- **Thema-elementen** aanpassen (logo's, stijlen)

Het is een alternatief voor het handmatig beheren van configuratie via Spring Cloud Config Server of omgevingsvariabelen.

---

## Architectuur

Het panel bestaat uit twee lagen:

```
nl-portal-configuration-panel/
├── frontend/    # React 19 + TypeScript + Vite  (poort 3001)
├── backend/     # Kotlin + Spring Boot 3.5       (poort 8080)
├── imports/     # Omgevingsvariabelen voor Docker
└── docker-compose.yaml
```

**Versiecompatibiliteit:**

| Config Panel | NL Portal |
|---|---|
| 2.0.0 | 3.0.0 |
| 1.0.0 | 2.0.2 |

---

## Configuratieopslag

Alle instellingen worden opgeslagen als **flat key-value paren** in PostgreSQL:

```
Tabel:     nlp_configuration
Sleutelformaat: {prefix}.{feature}.properties.{veld}
Voorbeeld: nl-portal.config.zakenapi.properties.url
```

De frontend werkt intern met geneste objecten en vertaalt deze naar/van de flat representatie via de `useConfigurationPropertyMapperHook`.

**Thema-opslag:**
- Logo's: tabel `nlp_theme_logos` (binaire data + MIME-type)
- Stijlen: tabel `nlp_theme_styles`

---

## Schermen en functionaliteit

### 1. Dashboard (Configuratielijst)

Het startscherm toont twee secties:
- **Thema's** — toegang tot logo- en stijlinstellingen
- **Features** — overzicht van alle configureerbare features met link naar detailpagina

### 2. Feature-configuratiepagina (`/features/{featureId}`)

Elke feature heeft een eigen configuratiepagina met:
- **Toggle** om de feature in/uit te schakelen
- **Formuliervelden** voor API-URL, client-ID, credentials, en feature-specifieke opties
- **Opslaan/Annuleren** knoppen (opslaan alleen actief bij geldige en gewijzigde waarden)
- **Notificatie** bij succes of fout

Het opslaan verloopt in twee stappen:
1. Bestaande properties voor de feature worden verwijderd (`DELETE`)
2. De nieuwe waarden worden in bulk opgeslagen (`POST`)

### 3. Themagpagina (`/theme/{themeId}`)

**Logo (`/theme/logo`):**
- Huidig logo bekijken (bestandsnaam, grootte, uploaddatum)
- Nieuw logobestand uploaden
- Logo verwijderen

**Stijl (`/theme/style`):**
- CSS-aanpassingen instellen voor de portal

---

## Configureerbare features (16 stuks)

| Feature | Omschrijving |
|---|---|
| Zaken API | Zaakbeheer |
| Catalogi API | Servicekatalogusen |
| Documenten API | Documentopslag (meerdere instanties mogelijk) |
| Besluiten API | Besluiten/beschikkingen |
| Objects API | Generieke objectopslag |
| Objecttypes API | Objecttype-definities |
| OpenKlant 2 | Klantinteractiebeheer |
| HaalCentraal BRP | Persoonsgegevens burgers |
| HaalCentraal HR | Handelsregister |
| HaalCentraal 2 | Gecombineerde HaalCentraal interface |
| OpenProduct(en) | Productcatalogus |
| Taak | Takenbeheer |
| Berichten | Berichtenservice |
| Ogone betaling | Betaalgateway Ogone |
| Directe betaling | Directe betalingsintegratie |
| ClamAV | Virusscan bij bestandsuploads |
| DMN | Decision Model & Notation (bedrijfsregels) |
| Prefill | Voorinvullen van formulieren |

---

## Gegevensflow

```
Beheerder vult formulier in
  ↓
React Hook Form valideert invoer
  ↓
useConfiguration hook (React Query)
  ↓
DELETE /api/v1/configurations/{app}/features/{featureKey}
  ↓
POST  /api/v1/configurations (bulk opslaan)
  ↓
ConfigurationPropertiesService
  ↓
JPA → PostgreSQL (nlp_configuration)
  ↓
ApplicationEvent gepubliceerd
  ↓
NotifyEventListener stuurt HTTP POST naar gekoppelde NL Portal instanties
```

---

## REST API (backend)

Base URL: `/api/v1/configurations`

| Methode | Pad | Omschrijving |
|---|---|---|
| `GET` | `/{application}` | Alle configs voor een applicatie |
| `GET` | `/{application}/features/{featureKey}` | Configs voor één feature |
| `GET` | `/{application}/features/{featureKey}/enabled` | Feature-toggle status |
| `POST` | `/{application}/features/{featureKey}` | Feature aan/uitzetten |
| `DELETE` | `/{application}/features/{featureKey}` | Feature-config verwijderen |
| `POST` | `/` | Bulk opslaan van properties |

Thema-endpoints zijn beschikbaar voor logo- en stijlbeheer.

---

## Authenticatie en beveiliging

- **Frontend:** OIDC via `react-oidc-context` met redirect naar Keycloak
- **Backend:** JWT-validatie via Spring Security (`TokenAuthenticationProvider`)
- Elke API-aanroep vereist een Bearer-token in de `Authorization`-header
- CORS configureerbaar via omgevingsvariabelen

---

## Omgevingsvariabelen

### Frontend (runtime, via `window.*`)

| Variabele | Omschrijving |
|---|---|
| `OIDC_URL` | Keycloak realm URL |
| `OIDC_CLIENT_ID` | OIDC client ID |
| `OIDC_REDIRECT_URL` | Redirect URL na login |
| `OIDC_POST_LOGOUT_REDIRECT_URL` | Redirect URL na logout |
| `CLIENT_APPLICATION_NAME` | Naam van de NL Portal applicatie |
| `CONFIG_PANEL_REST_API_URL` | (Optioneel) REST API URL van de backend |

### Backend

| Variabele | Omschrijving |
|---|---|
| `DATABASE_URL` | PostgreSQL connectiestring |
| `JWKS_URI` | URL voor JWT-sleutelvalidatie |
| `CONFIG_CACHE_TTL` | Cache-duur in milliseconden |
| `CONFIG_SERVER_TOKEN` | Auth-token voor config server |
| `CONFIG_NOTIFY_ENABLED` | Notificaties naar andere instanties aan/uit |
| `CONFIG_NOTIFY_LIST` | Kommagescheiden lijst van NL Portal URLs |
| `CORS_ALLOWED_*` | CORS-instellingen |

---

## Caching

De backend gebruikt EHCache op property-lookups (`@Cacheable("configCache")`). De TTL is instelbaar via `CONFIG_CACHE_TTL`. Dit is relevant voor omgevingen waar meerdere NL Portal instanties draaien en configuratiewijzigingen snel doorgevoerd moeten worden.

---

## Notificaties naar NL Portal instanties

Wanneer `CONFIG_NOTIFY_ENABLED=true` en `CONFIG_NOTIFY_LIST` geconfigureerd is, stuurt de backend na elke configuratiewijziging een HTTP POST naar de opgegeven NL Portal instanties. Dit zorgt ervoor dat instanties hun cache kunnen invalideren en de nieuwe configuratie ophalen.

---

## Technologiestack

**Frontend:**
- React 19, TypeScript, Vite
- React Router 7, TanStack React Query 5
- React Hook Form, react-intl
- Gemeente Den Haag / Utrecht Design System
- pnpm, Node 22

**Backend:**
- Kotlin, Spring Boot 3.5, JDK 21
- Spring Security (OAuth2/JWT)
- Spring Data JPA, PostgreSQL 15
- Apache Tika (MIME-detectie)
- EHCache, Spring Events
- Gradle, ktlint

---

## Docker Compose

```bash
# Config panel starten als onderdeel van de NL Portal stack:
docker compose --profile config up
```

Het config-profiel start de frontend (poort 3001), backend (poort 8080) en PostgreSQL.
