# Configuration Panel

Het Configuration Panel is de beheerapplicatie van NL Portal. Beheerders kunnen hiermee de portal configureren via een gebruikersinterface — zonder omgevingsvariabelen of configuratiebestanden handmatig aan te passen.

---

## Wat kan je ermee?

Het panel biedt toegang tot drie onderdelen:

- **Features** — Integraties met externe systemen in- of uitschakelen en de bijbehorende instellingen beheren
- **Logo** — Het logo van de portal uploaden, bekijken of verwijderen
- **Stijl** — CSS-aanpassingen instellen voor de portal

---

## Features per MijnServices-bouwsteen

De features in het panel komen overeen met de koppelingen die nodig zijn voor de MijnServices-bouwstenen. Welke features je inschakelt, bepaalt welke functionaliteit beschikbaar is voor de burger.

### MijnZaken

Zakoverzicht en documentinzage voor de burger.

| Feature | Omschrijving |
|---|---|
| Zaken API | Zaakregistratie en statussen |
| Catalogi API | Zaaktypecatalogus (omschrijvingen en statussen) |
| Documenten API | Documenten gekoppeld aan zaken |
| Besluiten API | Besluiten en beschikkingen |

→ Zie [Integraties](integraties.md) voor meer over de ZGW API-suite.

---

### MijnTaken

Openstaande acties die de burger moet uitvoeren.

| Feature | Omschrijving |
|---|---|
| Objects API | Ophalen van taken als objecten |
| Objecttypes API | Typedefinities van taken |
| Taak | Takenbeheer en formulierkoppelingen |

---

### MijnBerichten, MijnContactmomenten en MijnProfiel

Officiële berichten, contactgeschiedenis en contactgegevens — allemaal via Open Klant 2.

| Feature | Omschrijving |
|---|---|
| OpenKlant 2 | Klantinteracties API en Contactgegevens API |
| Berichten | Berichtenservice voor Wmebv-conforme correspondentie |

---

### MijnProfiel — persoonsgegevens

| Feature | Omschrijving |
|---|---|
| HaalCentraal BRP | Persoonsgegevens van burgers (BRP Personen API v2) |
| HaalCentraal HR | Bedrijfsgegevens via het Handelsregister (voor ondernemer-login) |
| HaalCentraal 2 | Gecombineerde HaalCentraal-interface |

---

### MijnProducten

Overzicht van verleende producten en diensten.

| Feature | Omschrijving |
|---|---|
| OpenProduct(en) | Productcatalogus via Open Product |

> MijnProducten vereist afstemming op het productregister van de gemeente. Zie [Functionaliteiten](../wat-kan-nl-portal/functionaliteiten.md).

---

## Overige features

De volgende features zijn niet direct gekoppeld aan één MijnServices-bouwsteen, maar ondersteunen de portal als geheel.

| Feature | Omschrijving |
|---|---|
| Ogone betaling | Betaalgateway Ogone (voor betaaltaken) |
| Directe betaling | Directe betalingsintegratie (voor betaaltaken) |
| ClamAV | Virusscan bij bestandsuploads |
| DMN | Bedrijfsregels (Decision Model & Notation) |
| Prefill | Voorinvullen van formulieren met bekende gegevens |

---

## Toegang en beveiliging

Het Configuration Panel is een aparte applicatie die naast NL Portal draait. Toegang vereist inloggen via Keycloak — dezelfde authenticatieinfrastructuur als de portal zelf.

Het panel is bereikbaar op **poort 3001**.

---

## Opstarten

Het panel wordt meegeleverd als Docker Compose-profiel:

```bash
docker compose --profile config up
```

---

## Versiecompatibiliteit

| Configuration Panel | NL Portal |
|---|---|
| 2.0.0 | 3.0.0 |
| 1.0.0 | 2.0.2 |
