# NL Portal als MijnServices-implementatie

## Wat is VNG MijnServices?

**VNG MijnServices** is een programma van de VNG dat herbruikbare open source bouwstenen oplevert voor een persoonlijke digitale omgeving van burgers. Het is de operationele invulling van NDS Prioriteit 4 en het door VNG aanbevolen pad voor Wmebv-compliance.

MijnServices is **geen enkelvoudige API-standaard**, maar een verzameling van bouwstenen — elk ondersteund door één of meer bestaande of in ontwikkeling zijnde VNG API-standaarden. De bouwstenen zijn gebruikersgetest, verwerkt in software van erkende leveranciers, compliant met wetgeving en afgestemd op Common Ground.

---

## De elf bouwstenen

MijnServices bestaat uit elf bouwstenen. Elke bouwsteen heeft een rijpheidsstatus die het proces van standaardisatie weergeeft: **Help Wanted → Community → Candidate → Standaard**.

| Bouwsteen | Omschrijving | Rijpheidsstatus |
|---|---|---|
| **MijnZaken** | Track-and-trace voor status van aangevraagde producten en diensten | Standaard (meest volwassen) |
| **MijnTaken** | Acties die de burger moet uitvoeren via het portaal | Candidate |
| **MijnProfiel** | Persoonlijke voorkeuren voor organisatiecontact | Candidate |
| **Notificatieservice** | Alerts bij binnenkomende berichten, taken of statuswijzigingen | Candidate |
| **MijnBerichten** | Digitale berichten en notificaties van de gemeente (Wmebv) | Candidate — in standaardisatieproces |
| **MijnContactmomenten** | Overzicht van contactmomenten tussen gemeente en burger | Candidate |
| **MijnProducten** | Overzicht van aangevraagde of verleende producten en diensten | Community |
| **MijnActies** | Proactieve acties die de burger kan ondernemen | Community |
| **MijnPlan** | Persoonlijk plan van de burger met de gemeente | Community (nieuw) |
| **MijnGesprek** | Overzicht van geplande of gevoerde gesprekken met de gemeente | Community (nieuw) |
| **MijnAgenda** | Persoonlijke agenda-integratie voor afspraken en deadlines | Community (nieuw) |

> MijnPlan, MijnGesprek en MijnAgenda zijn recent toegevoegd aan de MijnServices-roadmap. De technische standaarden hiervoor zijn nog in ontwikkeling.

---

## Welke bouwstenen NL Portal implementeert

### Out-of-the-box (zonder maatwerk)

| Bouwsteen | Toelichting |
|---|---|
| **MijnZaken** | Volledig ondersteund via ZGW Zaken API en Catalogi API |
| **MijnTaken** | Via het Externe Klanttaak V2-patroon (PGD) |
| **MijnBerichten** | Via Klantinteracties API; ondersteunt Wmebv-verplichting |
| **MijnProfiel** | Persoonlijk profiel en contactvoorkeuren via Contactgegevens API |
| **MijnContactmomenten** | Overzicht van contactmomenten via Klantinteracties API |

### Met maatwerk

| Bouwsteen | Toelichting |
|---|---|
| **MijnProducten** | Mogelijk via Producttypecatalogus / Objecten API; vereist configuratie |
| **MijnActies** | Mogelijk via notificatiesysteem; vereist maatwerk |

### Nog niet geïmplementeerd

MijnPlan, MijnGesprek en MijnAgenda zijn nieuw in de VNG-roadmap. De onderliggende standaarden zijn nog niet vastgesteld. NL Portal volgt de ontwikkeling en implementeert zodra standaarden beschikbaar zijn.

---

## Ritense als erkende MijnServices-leverancier

VNG houdt een officieel register bij van leveranciers wier software voldoet aan MijnServices. **Ritense — en daarmee NL Portal — staat op deze erkende leverancierslijst.**

Andere erkende leveranciers zijn onder meer: OpenZaak, Shift2, Decos, ICATT, 2AT, Eviden, Visma-Roxit, Yard, EnableU, XXLLNC, Salesforce, Innovadis, Maykin, Brightfox, WoWeb, Pinkroccade, Acato, Worth, Genetics, WeAreFrank, Conduction en Visma Circle.

---

## Wat VNG aanbiedt aan gemeenten

VNG ondersteunt gemeenten bij de adoptie van MijnServices met:

- Een gratis **stappenplan** (PDF, december 2024)
- Maandelijkse online introductiesessies met drie verdiepingssporen: implementatieadvies, service blueprints en architectuur
- **Subsidiemogelijkheden**
- Referentiearchitectuur (bedrijfs- en informatieperspectief)
- NL Design System-richtlijnen en Storybook-ontwerpen

Implementatie-inspanning: **300–850 uur** voor een team van 4–21 medewerkers (VNG-schatting).

Aanbevolen volgorde:
1. Start met **MijnZaken** — implementeer ZGW APIs in het backofficesysteem
2. Voeg **MijnTaken, MijnBerichten, MijnContactmomenten** toe — vereist Klantinteracties API
3. Implementeer een **Notificatieservice** voor proactieve updates
4. Stel een **burgerfacing portal** in (zoals NL Portal) dat de APIs ontsluit

→ [MijnServices stappenplan (PDF)](https://vng.nl/sites/default/files/2024-12/mijnservices-stappenplan.pdf)
→ [VNG MijnServices](https://vng.nl/MijnServices)

---

## Huidige gebruikers

NL Portal wordt al ingezet door tientallen gemeenten, waaronder Rotterdam, Den Haag, Nijmegen, Deventer, Tilburg, Groningen, Leeuwarden, Zwolle, Enschede, Arnhem en vele anderen. Sommige gemeenten werken samen via Dimpact of OpenWebconcept.
