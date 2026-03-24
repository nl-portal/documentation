# Platform Generieke Dienstverlening

## Wat is PGD?

Het **Platform Generieke Dienstverlening (PGD)** is de technische architectuurlaag onder **VNG MijnServices**. Waar MijnServices de burgerfacing bouwstenen beschrijft (wat de burger ziet), beschrijft PGD hoe die bouwstenen technisch werken: welke patronen, welke standaarden, welke referentiecomponenten.

PGD is een Common Ground-initiatief, ontwikkeld in samenwerking tussen gemeenten, leveranciers en Dimpact. Het biedt één gezamenlijke plek voor architectuurafspraken, zodat conflicterende implementaties tussen gemeenten worden voorkomen.

**Authoritative bron**: [Platform Generieke Dienstverlening — GitBook](https://dienstverleningsplatform.gitbook.io/platform-generieke-dienstverlening-public)

---

## Relatie met MijnServices

PGD en MijnServices zijn complementair:

| | MijnServices (VNG) | PGD |
|---|---|---|
| **Perspectief** | Burger en gemeente | Architect en ontwikkelaar |
| **Inhoud** | Bouwstenen en gebruikerswensen | Patronen, standaarden, referentiecomponenten |
| **Rijpheid** | Politiek mandaat (NDS, Wmebv) | Technische uitwerking |
| **Referentie** | [vng.nl/MijnServices](https://vng.nl/MijnServices) | [PGD GitBook](https://dienstverleningsplatform.gitbook.io/platform-generieke-dienstverlening-public) |

MijnServices verwijst gemeenten naar PGD voor de technische uitwerking van de bouwstenen.

---

## Patronen in PGD

PGD definieert technische interactiepatronen die beschrijven hoe componenten met elkaar communiceren. NL Portal implementeert drie van deze patronen:

### Externe Klanttaak
Het patroon voor taken die burgers moeten uitvoeren. NL Portal implementeert dit als **Taak V2**: taken worden aangemaakt door het zaakafhandelingscomponent, opgeslagen in de Objecten API, en opgehaald en gepresenteerd door NL Portal.

→ Zie [Patronen — Externe Klanttaak](hoe-werkt-nl-portal/patronen.md#externe-klanttaak-taak-v2)

### Berichten
Het patroon voor officiële berichtgeving aan burgers. Berichten zijn altijd gekoppeld aan documenten en optioneel aan zaken. Drie kanalen: digitaal portaal, MijnOverheid BerichtenBox, fysieke post.

→ Zie [Patronen — Berichten](hoe-werkt-nl-portal/patronen.md#berichten)

### Verzoeken
Het patroon voor aanvragen die burgers indienen. Asynchroon: het verzoek wordt als object opgeslagen, waarna het zaakafhandelingscomponent via notificaties op de hoogte wordt gebracht.

→ Zie [Patronen — Verzoeken](hoe-werkt-nl-portal/patronen.md#verzoeken)

---

## Standaarden in PGD

PGD werkt met drie categorieën standaarden:

| Standaard | Status | NL Portal |
|---|---|---|
| **Zaakgericht Werken** (ZGW API-suite) | In gebruik | Volledig geïmplementeerd |
| **Objecten API** | In gebruik | Gebruikt voor taken en producten |
| **Klantinteracties API** | Beproeving / pilot | Gebruikt voor berichten, contactmomenten en profiel |
| **Producten** (Producttypecatalogus) | Concept | Basis aanwezig; vereist configuratie |

De **ZGW API-suite** is de meest volwassen standaard in het ecosysteem — formeel vastgesteld door VNG (versie 1.5). De Klantinteracties API is gepubliceerd "as is, where is" bij VNG Realisatie; actieve doorontwikkeling is momenteel gepauzeerd.

---

## Ritense als bijdragende partij

Ritense is **expliciet genoemde bijdragende leverancier** aan twee PGD-standaarden:

- **Zaakgericht Werken** — bijdrage aan de ZGW API-standaard
- **Objecten** — bijdrage aan de Objecten API-standaard

Andere bijdragende gemeenten en leveranciers: Amsterdam, Den Haag, Dimpact, Rotterdam, Utrecht, Maykin, Atos.

---

## Governance en roadmap

PGD heeft een tweewekelijkse overlegcyclus:
- Dinsdagmiddag — architecten en ontwikkelaars
- Vrijdagochtend — programmamanagers, leveranciers en projectbeheer

Roadmap: [PGD Roadmap — Notion](https://www.notion.so/platformvoordienstverlening/Roadmap-e1ebdc0c60904c1a9c34b45388bc4ccd)

Authoritative technische documentatie: [PGD GitBook](https://dienstverleningsplatform.gitbook.io/platform-generieke-dienstverlening-public)
