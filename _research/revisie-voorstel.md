# Voorstel: Revisie NL Portal documentatie

> Opgesteld: maart 2026
> Status: ter review

## Aanleiding

De huidige documentatie is primair geschreven vanuit een technisch ontwikkelaarsperspectief. De beoogde nieuwe doelgroepen zijn:

- **Informatieadviseurs** — beoordelen of NL Portal past binnen de gemeentelijke informatievoorziening en beleidsdoelstellingen
- **Architecten** — ontwerpen de integratieoplossing en toetsen aan standaarden
- **Functioneel beheerders** — richten NL Portal in, beheren koppelingen en huisstijl

De revisie sluit aan op drie externe kaders waarop gemeenten worden aangesproken:
1. **Nationale Digitaliseringsstrategie (NDS)** — politiek mandaat voor digitale dienstverlening (prioriteit 4 en 5)
2. **VNG MijnServices** — operationele invulling van dat mandaat; NL Portal is erkende leverancier
3. **NL Design System (NLDS)** — standaard voor toegankelijke, herkenbare overheidsinterfaces

---

## Voorgestelde structuur

### 0. Welkom

Korte landingspagina. Geen technische details. Antwoord op de vraag: *"Wat kan ik hier vinden?"* met drie paden voor de drie doelgroepen.

Bestaand: `README.md` — volledig herschrijven.

---

### 1. Waarom NL Portal?
*Primaire doelgroep: informatieadviseur*

#### 1.1 Digitale dienstverlening als opgave
- NDS prioriteit 4: burgers en ondernemers centraal
- NDS prioriteit 5: leveranciersonafhankelijkheid via open source
- Wmebv: wettelijke verplichting per 1 januari 2026 (MijnBerichten)
- Common Ground: data bij de bron, vijflagenmodel

#### 1.2 NL Portal als MijnServices-implementatie
- Wat is VNG MijnServices?
- De elf bouwstenen en hun rijpheidsstatus
- NL Portal als erkende VNG MijnServices-leverancier
- Welke bouwstenen NL Portal implementeert (en welke nog niet)

#### 1.3 Open source en governance
- Licentie: EUPL 1.2
- Community-gedreven ontwikkeling
- Relatie met Ritense als maintainer
- Bestaand: `fundamentals/open-source.md` — hergebruiken en uitbreiden

---

### 2. Wat kan NL Portal?
*Primaire doelgroep: informatieadviseur + functioneel beheerder*

#### 2.1 Functionaliteiten per MijnServices-bouwsteen

Per geïmplementeerde bouwsteen een korte beschrijving:
- Wat ziet de burger?
- Welke backoffice-koppeling is vereist?
- Wat is de rijpheidsstatus van de standaard?

**Out-of-the-box (zonder maatwerk):**
- MijnZaken
- MijnTaken (via Externe Klanttaak V2-patroon)
- MijnBerichten
- MijnProfiel
- MijnContactmomenten

**Met maatwerk:**
- MijnProducten
- MijnActies

**Niet geïmplementeerd:**
- MijnPlan, MijnGesprek, MijnAgenda (nieuw in roadmap VNG)

#### 2.2 Authenticatie en toegang
- DigiD voor burgers
- eHerkenning voor ondernemers
- Relatie met Wmebv-vereisten

Bestaand: `fundamentals/architectuur/authentication-en-authorization.md` — hergebruiken.

---

### 3. Hoe werkt NL Portal?
*Primaire doelgroep: architect*

#### 3.1 Architectuuroverzicht
- Positie in het Common Ground vijflagenmodel (laag 5)
- Componenten: React frontend, Spring Boot backend, GraphQL aggregatielaag
- Principe: portaalbackend als vertaallaag tussen GraphQL en ZGW REST-APIs

Bestaand: `fundamentals/architectuur/README.md` en `5-lagenmodel.md` — hergebruiken en actualiseren.

#### 3.2 Integraties

Per integratie: wat, waarvoor, welke standaard, welke referentie-implementatie.

| Integratie | Standaard | Referentie-implementatie |
|---|---|---|
| Zaken, documenten, besluiten | ZGW-suite (Zaken API, Catalogi API, Documenten API, Besluiten API) | Open Zaak |
| Klantinteracties en berichten | Klantinteracties API + Contactgegevens API | Open Klant (v2) |
| Persoonsgegevens (BRP) | Haalcentraal BRP v2 | — |
| Bedrijfsgegevens (KVK) | Haalcentraal HR | — |
| Producten en diensten | Producttypecatalogus / Objecten API | Open Product |
| Notificaties | Notificaties API (ZGW-suite) | Open Notificaties |

Bestaand: `fundamentals/architectuur/integraties/` — herstructureren per bovenstaand schema.

#### 3.3 Patronen
- Externe Klanttaak (PGD-patroon, geïmplementeerd als Taak V2)
- Verzoek
- Berichten

Bestaand: `fundamentals/architectuur/patronen/` — actualiseren met verwijzing naar PGD-documentatie.

#### 3.4 Authenticatie en token exchange
Conceptuele uitleg: waarom token exchange, hoe BSN/KVK in het token belandt, relatie met DigiD/eHerkenning/Keycloak.

Bestaand: `configuratie/tokenexchange.md` — alleen conceptuele kern overnemen; Keycloak-configuratiestappen vervallen (→ Helm Chart).

#### 3.5 Objectfiltering
Bestaand: `features/zaakinformatieobjecten-filtering/` — beoordelen bij uitwerking of dit architectureel relevant is voor de doelgroep.

---

### 4. NL Design System en huisstijl
*Primaire doelgroep: functioneel beheerder + architect*

#### 4.1 Hoe NLDS werkt
- Drielaags tokenmodel: Brand → Common → Component
- Wat is een theme-bestand?
- Estafettemodel: componentrijpheid

#### 4.2 NL Portal themen
- Welke tokens NL Portal gebruikt
- Stap-voor-stap: eigen huisstijl toepassen
- Voorbeelden: Den Haag als referentieimplementatie

Bestaand: `configuratie/eigen-vormgeving.md` — uitbreiden met NLDS-context.

---

### 5. Koppelingen
*Primaire doelgroep: functioneel beheerder + architect*

Conceptuele pagina: welke systemen kan NL Portal aan, wat is er aan beide kanten nodig (API-account, client ID/secret), hoe werkt autorisatie via de ZGW Autorisaties API. Geen stap-voor-stap configuratieschermen, geen env vars.

Bestaand: `configuratie/connectiviteit.md` — alleen conceptuele kern overnemen; screenshots en env var-verwijzingen vervallen.

> Technische configuratie (environment variables, Helm values) → Helm Chart documentatie.

---

### 6. Platform Generieke Dienstverlening
*Primaire doelgroep: architect*

Nieuwe pagina op basis van onderzoek. Beschrijft:
- Wat PGD is en hoe het zich verhoudt tot MijnServices
- De patronen (Externe Klanttaak, Berichten, Verzoeken) als technische blauwdruk
- Standaarden in PGD: ZGW (in gebruik), Objecten (in gebruik), Klantinteracties (pilot)
- Ritense als bijdragende partij
- Link naar PGD GitBook voor technische details

---

### 7. Community en bijdragen
*Primaire doelgroep: alle*

#### 7.1 Community en support
Bestaand: `support-en-resources/community-en-support.md` — hergebruiken.

#### 7.2 Repositories
Bestaand: `support-en-resources/repositories.md` — hergebruiken.

#### 7.3 Bijdragen aan NL Portal
Bestaand: `contributing/contributing.md` — hergebruiken.

---

### 8. Product management
Bestaand: `product-management/` — ongewijzigd.

---

### 9. Release notes
Bestaand: `release-notes/` — ongewijzigd.

---

## Wat vervalt

| Huidige pagina | Reden |
|---|---|
| `fundamentals/wat-is-nl-portal.md` | Inhoud verdeeld over secties 1 en 2 |
| `configuratie/opzetten-nl-portal.md` | Developer setup → Helm Chart |
| `configuratie/deployment-guide.md` | Deployment → Helm Chart |
| `support-en-resources/best-practices.md` | 3 ontwikkelaarspunten; inhoud opgenomen in NLDS-sectie (tokens) en community-sectie (bijdragen) |
| `support-en-resources/impressies.md` | Verouderde screenshots; vervangen door actueel beeldmateriaal in sectie 2 |

> Alle pagina's met environment variables, Keycloak-configuratieschermen of deployment-stappen vervallen. Verwijzing naar Helm Chart als technische referentie.

---

## Nieuw te schrijven pagina's

| Pagina | Sectie | Prioriteit |
|---|---|---|
| Digitale dienstverlening als opgave (NDS + Wmebv) | 1.1 | Hoog |
| NL Portal als MijnServices-implementatie | 1.2 | Hoog |
| Functionaliteiten per MijnServices-bouwsteen | 2.1 | Hoog |
| Platform Generieke Dienstverlening | 6 | Middel |
| NLDS context en tokenmodel | 4.1 | Middel |

---

## Openstaande vragen voor review

1. ~~**Welke MijnServices-bouwstenen implementeert NL Portal precies?**~~ — Beantwoord, zie sectie 2.1.
2. ~~**MijnProfiel**: wordt dit ondersteund in NL Portal?~~ — Ja, out-of-the-box.
3. ~~**Taal**~~ — Nederlands, docs blijven volledig NL.
4. ~~**Impressies-pagina**~~ — Verouderd en niet mooi; vervangen door actueel beeldmateriaal in sectie 2.
5. ~~**Best practices**~~ — Vervalt als pagina; inhoud geïntegreerd in NLDS-sectie en community-sectie.
6. ~~**Helm Chart**~~ — Publieke Helm Chart beschikbaar op https://github.com/nl-portal/helm-charts.
7. ~~**MijnContactmomenten**~~ — Geïmplementeerd, verplaatst naar out-of-the-box lijst in sectie 2.1.
8. ~~**Actueel beeldmateriaal**~~ — Wordt aangeleverd door de opdrachtgever.
