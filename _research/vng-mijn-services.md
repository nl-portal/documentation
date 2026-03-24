# Onderzoek: VNG MijnServices

> Bronnen: [vng.nl/MijnServices](https://vng.nl/MijnServices) (direct opgehaald, maart 2026), aanvullend: VNG startgids maart 2024, VNG stappenplan dec 2024, VNG creatie- en vastleggingsoverzicht februari 2026

## Wat is MijnServices?

MijnServices is een VNG-programma dat herbruikbare open-source bouwstenen oplevert voor een persoonlijke digitale omgeving voor burgers ("MijnOmgeving") en een parallelle medewerkersportal. Het valt onder VNG's bredere "Omnichannel"-kanaalstrategie en is de opvolger van het originele "MijnZaken"-project (gestart 2022).

MijnServices is **geen enkelvoudige API-standaard** maar een verzameling van bouwstenen, elk ondersteund door één of meer bestaande (of in ontwikkeling zijnde) VNG API-standaarden.

De bouwstenen zijn:
- Gebruikersgetest
- Verwerkt in software van diverse leveranciers
- Compliant met wetgeving
- Afgestemd op de Common Ground-visie

## De elf bouwstenen

| Bouwsteen | Beschrijving | Rijpheid (feb 2026) |
|---|---|---|
| **MijnZaken** | Track-and-trace voor de status van aangevraagde producten/diensten; vermindert onnodig contact | Standaard (StUF); meest volwassen |
| **MijnTaken** | Acties die de burger moet uitvoeren, doorgaans via overheidsportalen | Candidate |
| **MijnProfiel** | Beheert persoonlijke voorkeuren voor organisatiecontact (kanaal-/communicatievoorkeuren) | Candidate |
| **Notificatieservice** | Alerts bij binnenkomende berichten/taken of statuswijzigingen; integreert Wmebv-vereisten | Candidate |
| **MijnBerichten** | Informatieve berichten/notificaties aan burgers over taken of besluiten (vergelijkbaar met MijnOverheid berichtenbox) | Candidate; in standaardisatieproces; Rijksoverheid actief betrokken |
| **MijnContactmomenten** | Overzicht van contactmomenten tussen gemeente en burger over een zaak | Candidate |
| **MijnProducten** | Overzicht van aangevraagde/verleende producten/diensten (bijv. goedgekeurde vergunningen) | Community |
| **MijnActies** | Proactieve acties die de burger kan ondernemen (bijv. verlening parkeervergunning) | Community |
| **MijnPlan** | Persoonlijk plan van de burger met de gemeente (nieuw) | Community |
| **MijnGesprek** | Overzicht van geplande of gevoerde gesprekken met de gemeente (nieuw) | Community |
| **MijnAgenda** | Persoonlijke agenda-integratie voor afspraken en deadlines (nieuw) | Community |

> De rijpheidsstatus volgt het MijnServices-vastleggingsproces (Help Wanted → Community → Candidate → Standaard), analoog aan het NLDS Estafettemodel. MijnPlan, MijnGesprek en MijnAgenda zijn recent toegevoegd aan de roadmap en staan nog niet op vng.nl/MijnServices (peildatum maart 2026).

## Achterliggende standaarden per bouwsteen

| Bouwsteen | Standaard(en) |
|---|---|
| MijnZaken | Zaken API, Catalogi API (ZGW-suite) |
| MijnTaken | Taken API (conceptstandaard in PGD) |
| MijnProfiel | Contactgegevens API |
| Notificatieservice | Notificaties API (ZGW-suite) |
| MijnBerichten | Klantinteracties API, Contactgegevens API |
| MijnContactmomenten | Klantinteracties API |
| MijnProducten | Producttypecatalogus / Objecten API (concept) |
| MijnActies | Nog geen formele standaard; gedreven door notificatiesysteem |
| MijnPlan | Nog geen formele standaard (nieuw) |
| MijnGesprek | Nog geen formele standaard (nieuw) |
| MijnAgenda | Nog geen formele standaard (nieuw) |

> **Terminologie**: De standaarden zijn de *Klantinteracties API* en *Contactgegevens API* (VNG Realisatie). Open Klant is de *referentie-implementatie* hiervan; versie 2 van Open Klant implementeert deze standaarden.

### ZGW API-suite (formeel vastgestelde VNG-standaard, versie 1.5)

Specificaties: https://vng-realisatie.github.io/gemma-zaken/standaard/

- **Zaken API** — zaakregistratie en -opvraging
- **Catalogi API** — zaaktypecatalogus (ZTC)
- **Documenten API** — documenten gekoppeld aan zaken
- **Besluiten API** — besluiten gekoppeld aan zaken
- **Notificaties API** — event-routing tussen componenten
- **Autorisaties API** — autorisatiebeheer voor ZGW API-consumers

### Klantinteracties API + Contactgegevens API

Vervangt de verouderde Klanten API en Contactmomenten API.

- Specificatie: https://vng-realisatie.github.io/klantinteracties/
- **Status**: Ontwikkeling bij VNG Realisatie gepauzeerd (vanaf juli 2024); gepubliceerd "as is, where is" onder EUPL. Geen component heeft versie 1.0 bereikt.
- **Referentie-implementatie**: Open Klant (Maykin Media), ontwikkeld samen met VNG Realisatie en gemeenten Amsterdam, Den Haag en Utrecht.

## Wettelijke context: Wmebv

De **Wet modernisering elektronisch bestuurlijk verkeer (Wmebv)** treedt volledig in werking op **1 januari 2026**. Gemeenten zijn dan verplicht digitale kanalen aan te bieden voor formele correspondentie. De Notificatieservice en MijnBerichten zijn het door VNG aanbevolen implementatiepad. Dit is een harde deadline.

Bronnen: [Wmebv | VNG](https://vng.nl/wmebv), [MijnServices en Wmebv | VNG](https://vng.nl/nieuws/mijnservices-met-omnichannel-en-inwerkingtreden-wmebv)

## Huidige gebruikers (~40 gemeenten)

Rotterdam, 's-Hertogenbosch, Zutphen, Venray, Noordwijk, Horst aan de Maas, Gooise Meren, Buren, Ridderkerk, Tilburg, Groningen, Leeuwarden, Weststellingwerf, Den Haag, Fryske Marren, Opsterland, Hoeksche Waard, Deventer, Assen, Súdwest-Fryslân, Oost-Gelre, Ooststellingwerf, Albrandswaard, Nijmegen, Hollands Kroon, Arnhem, Borger-Odoorn, Zwolle, Raalte, Roermond, Enschede, Oldambt, Maashorst, Barendrecht, Waterschap Aa en Maas, Gouda.

Sommige gemeenten werken samen via Dimpact en OpenWebconcept.

## Erkende leveranciers

OpenZaak, Shift2, Decos, ICATT, 2AT, Eviden, Visma-Roxit, Yard, EnableU, XXLLNC, Salesforce, Innovadis, Maykin, Brightfox, WoWeb, Pinkroccade, Acato, **Ritense**, Worth, Genetics, WeAreFrank, Conduction, Visma Circle.

**Ritense is officieel erkend als MijnServices-leverancier bij VNG.** NL Portal is daarmee een formeel erkende MijnServices-implementatie.

## Wat VNG aanbiedt aan gemeenten

- Gratis stappenplan en promotiekits
- Maandelijkse online introductiesessies met drie verdiepingssporen:
  - Implementatieadvies
  - Service Blueprints en Klantreizen
  - Architectuur en techniek
- Subsidiemogelijkheden
- Referentiearchitectuur (bedrijfs- en informatieperspectief)
- Omnichannel toolkit
- NL Design System ontwikkelrichtlijnen en Storybook-ontwerpen

## Adoptieproces voor gemeenten

Implementatie-inspanning: 300–850 uur voor een team van 4–21 medewerkers (VNG-schatting).

Aanbevolen volgorde:
1. Start met **MijnZaken** — implementeer ZGW APIs in het backofficesysteem
2. Voeg **MijnTaken, MijnBerichten, MijnContactmomenten** toe — vereist Klantinteracties API + Contactgegevens API
3. Implementeer een **Notificatieservice** voor proactieve updates
4. Stel een **burgerfacing portal** in dat de APIs ontsluit via een aggregatielaag

Stappenplan: [MijnServices stappenplan dec 2024 (PDF)](https://vng.nl/sites/default/files/2024-12/mijnservices-stappenplan.pdf)

## Relatie met Platform Generieke Dienstverlening (PGD)

PGD is de technische architectuurlaag onder MijnServices — zie apart onderzoeksdocument `platform-generieke-dienstverlening.md`.

## Voortgang architectuurwerk (februari 2026)

Op basis van het VNG creatie- en vastleggingsoverzicht:

- **Uitwisselingsgegevensmodel (UGM)** staat voor de meeste bouwstenen op **NTB** (Nader Te Bepalen) — architectuurwerk is grotendeels nog niet afgerond
- **API-specificaties** zijn alleen voor MijnZaken volledig klaar
- **Publicatie op DON** (Developer Overheid Nederland) is voor MijnZaken en MijnTaken in progress, de rest nog niet gestart
- **Figma-prototypes** (NL Design System) zijn voor vrijwel alle bouwstenen gereed
- **Rijksoverheid** is actief betrokken bij MijnBerichten: zowel "beproeven" als "helpt creëren" — MijnBerichten is het verst in het formele standaardisatieproces

## Bronnen

- [MijnServices | VNG](https://vng.nl/MijnServices)
- [Veelgestelde vragen MijnServices | VNG](https://vng.nl/artikelen/veelgestelde-vragen-mijnservices)
- [Startgids MijnServices maart 2024 (PDF)](https://vng.nl/sites/default/files/2024-03/vng-startgids-mijnservices.pdf)
- [MijnServices stappenplan dec 2024 (PDF)](https://vng.nl/sites/default/files/2024-12/mijnservices-stappenplan.pdf)
- [Omnichannel MijnServices — GEMMA Online](https://www.gemmaonline.nl/wiki/Omnichannel_MijnServices)
- [ZGW API standaard overzicht](https://vng-realisatie.github.io/gemma-zaken/standaard/)
- [Klantinteracties API specificatie](https://vng-realisatie.github.io/klantinteracties/)
