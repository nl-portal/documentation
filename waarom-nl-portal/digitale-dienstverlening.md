# Digitale dienstverlening als opgave

Digitale dienstverlening voor gemeenten is geen optie meer — het is een wettelijke en beleidsmatige verplichting. Drie kaders bepalen de urgentie.

---

## Nationale Digitaliseringsstrategie (NDS)

De **Nationale Digitaliseringsstrategie** is de eerste gezamenlijke digitaliseringsstrategie van alle overheidslagen in Nederland, gelanceerd op 4 juli 2025. Ze is ontwikkeld door en voor nationale ministeries, provincies, gemeenten (VNG), waterschappen en publieke dienstverleners.

Kernboodschap: *vrijblijvendheid is voorbij*. Standaarden worden bindend, en gemeenten worden aangesproken op resultaat.

### Prioriteit 4 — Burgers en ondernemers centraal

> "De overheid stelt burgers en ondernemers centraal in digitale dienstverlening."

Burgers ervaren één overheid: proactieve, toegankelijke en op maat gemaakte dienstverlening via het juiste kanaal. Dit beschrijft direct het doel van een burgerpersoonlijke omgeving: één plek waar de burger zijn zaken, taken, berichten en profiel beheert.

### Prioriteit 5 — Digitale weerbaarheid

Verminder afhankelijkheid van een klein aantal leveranciers; versterk digitale autonomie. De NDS motiveert open source en leveranciersneutrale oplossingen. NL Portal is open source onder EUPL 1.2 en niet gebonden aan één backofficesysteem.

### Van vrijwillig naar bindend

De NDS introduceert vier interventies:

1. **Versterkt gebruik van standaarden** — Forum Standaardisatie krijgt uitgebreide bevoegdheden; adoptie van open standaarden (zoals ZGW APIs) is niet meer vrijwillig
2. **Verplichte collectieve oplossingen** — Bepaalde bouwstenen worden verplicht voor alle overheidsorganisaties
3. **Collectieve inkoopstrategie** — Overheid organiseert zich als collectieve opdrachtgever voor IT
4. **Governance en accountability** — NDS-raad stuurt en bewaakt voortgang over alle overheidslagen

**Implicatie**: voldoen aan open standaarden en gebruik van gedeelde bouwstenen wordt steeds meer een wettelijke en beleidsmatige verplichting.

---

## Wmebv — Wet modernisering elektronisch bestuurlijk verkeer

De **Wet modernisering elektronisch bestuurlijk verkeer (Wmebv)** trad volledig in werking op **1 januari 2026**. Gemeenten zijn sindsdien verplicht digitale kanalen aan te bieden voor formele correspondentie met burgers en ondernemers.

Concreet houdt dit in:

- Burgers moeten berichten van de gemeente digitaal kunnen ontvangen en beantwoorden
- Gemeenten moeten een betrouwbaar digitaal berichtenkanaal aanbieden

**MijnBerichten** — de bouwsteen voor digitale berichtenuitwisseling — is het door VNG aanbevolen implementatiepad voor Wmebv-compliance. NL Portal implementeert MijnBerichten out-of-the-box.

→ Zie ook: [Wmebv | VNG](https://vng.nl/wmebv)

---

## Common Ground

**Common Ground** is het informatiearchitectuurprogramma van VNG Realisatie voor Nederlandse gemeenten. Het is volledig in lijn met de NDS en vormt de technische fundering van NL Portal.

Kernprincipes:

| Principe | Betekenis |
|---|---|
| **Data bij de bron** | Gegevens worden bevraagd bij de gezaghebbende bronregistratie; niet gekopieerd naar het portaal |
| **Vijflagenmodel** | Strikte scheiding van interactie, orkestratie, integratie, services en data |
| **API-first** | Alle gegevensuitwisseling via gestandaardiseerde REST APIs (ZGW-suite) |
| **Open source** | Software gepubliceerd onder EUPL 1.2 |
| **Samen bouwen** | Gemeenten stellen gezamenlijk standaarden op en zijn collectieve opdrachtgever |

NL Portal bevindt zich op **laag 5** (interactielaag) van het vijflagenmodel. Het bevraagt data bij de bron — Open Zaak, Open Klant, Haalcentraal BRP — en presenteert die aan de burger zonder lokale kopieën op te slaan.

De **Realisatiekoers Common Ground** (goedgekeurd door VNG ALV mei 2025) stelt digitale dienstverlening als eerste focusdomein.

---

## Wat dit betekent voor uw gemeente

| Kader | Wat het vraagt | NL Portal-invulling |
|---|---|---|
| NDS Prioriteit 4 | Één digitale omgeving voor burgers | MijnZaken, MijnTaken, MijnBerichten, MijnProfiel |
| NDS Prioriteit 5 | Open source, geen vendor lock-in | EUPL 1.2, community-gedreven, leveranciersneutraal |
| Wmebv (1 jan 2026) | Digitaal berichtenkanaal verplicht | MijnBerichten out-of-the-box |
| Common Ground | API-first, data bij de bron | GraphQL-aggregatielaag op ZGW REST APIs |
| Bindende standaarden | ZGW-suite, REST API Design Rules | Volledig geïmplementeerd |

**Kernboodschap**: NL Portal kiezen is geen productbeslissing — het is een compliancekeuze die aansluit bij NDS-prioriteiten en Common Ground-verplichtingen.
