# Koppelingen

NL Portal sluit aan op backoffice-systemen via gestandaardiseerde VNG API-standaarden. Op deze pagina staat beschreven welke systemen gekoppeld kunnen worden, wat er aan beide kanten nodig is, en hoe autorisatie werkt.

---

## Welke systemen kan NL Portal koppelen?

| Systeem | Doel | Vereiste API |
|---|---|---|
| **Zaaksysteem** (bijv. Open Zaak) | Zaken, documenten en besluiten tonen | ZGW Zaken API, Catalogi API, Documenten API |
| **Klantregistratie** (bijv. Open Klant v2) | Berichten, contactmomenten en profiel | Klantinteracties API, Contactgegevens API |
| **Objectenregister** (bijv. Open Zaak Objecten) | Taken ophalen | Objecten API, Objecttypen API |
| **BRP-aansluiting** | Persoonsgegevens opvragen | Haalcentraal BRP Personen API v2 |
| **Handelsregister-aansluiting** | Bedrijfsgegevens opvragen | Haalcentraal HR API |
| **Productencatalogus** (bijv. Open Product) | Producten en diensten tonen | Producttypecatalogus / Objecten API |
| **Notificatieservice** (bijv. Open Notificaties) | Events ontvangen bij wijzigingen | Notificaties API (ZGW-suite) |

---

## Wat is er aan beide kanten nodig?

### Aan de kant van het externe systeem

Voor elk aan te sluiten systeem moet een **API-account** worden aangemaakt voor NL Portal:

1. Maak in het backoffice-systeem een nieuwe applicatie (of client) aan
2. Ken de applicatie een **client ID** en een **secret** toe
3. Stel autorisaties in: welke zaaktypen, informatieobjecttypen of resources NL Portal mag opvragen

### Aan de kant van NL Portal

NL Portal moet geconfigureerd worden met:
- De **URL** van het externe systeem
- Het **client ID** en **secret** van de aangemaakt applicatie

> **Technische configuratie** (environment variables, Helm values) valt buiten de scope van deze documentatie. Raadpleeg de [NL Portal Helm Chart](https://github.com/nl-portal/helm-charts) voor deployment-specifieke configuratie.

---

## Autorisatie via de ZGW Autorisaties API

Verbinding met een ZGW-systeem is niet voldoende — NL Portal heeft ook **autorisatie** nodig om zaakgegevens te mogen opvragen. Dit wordt geregeld via de **ZGW Autorisaties API**.

In de Open Zaak-beheeromgeving stelt u in:
- Welke **zaaktypen** NL Portal mag inzien
- Welke **informatieobjecttypen** (documenttypen) zichtbaar zijn voor burgers
- Welke **besluittypen** worden getoond

**Aanbevolen instelling**: maak een autorisatieprofiel dat précies die zaaktypen toestaat die burgers mogen inzien. Het vinkje "heeft alle autorisaties" is uitsluitend bedoeld voor ontwikkelomgevingen.

---

## Sleutelbeheer

De client ID en secret van elke koppeling zijn gevoelige gegevens. Gebruik voor opslag en beheer een secrets-management oplossing zoals:
- [Azure Key Vault](https://azure.microsoft.com/en-us/products/key-vault)
- [AWS Key Management Service](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html)
- HashiCorp Vault
- Kubernetes Secrets (met versleuteling at rest)

Sla secrets nooit op in versiebeheer.

---

## Meerdere omgevingen

NL Portal ondersteunt aparte koppelingen per omgeving (development, acceptatie, productie). Elke omgeving krijgt eigen credentials. Raadpleeg de Helm Chart-documentatie voor de exacte configuratieopties.

→ [NL Portal Helm Charts](https://github.com/nl-portal/helm-charts)
