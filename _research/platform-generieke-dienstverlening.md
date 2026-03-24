# Onderzoek: Platform Generieke Dienstverlening (PGD)

> Bron: [dienstverleningsplatform.gitbook.io/platform-generieke-dienstverlening-public](https://dienstverleningsplatform.gitbook.io/platform-generieke-dienstverlening-public) (direct opgehaald, maart 2026)

## Wat is PGD?

Het Platform Generieke Dienstverlening (PGD) is een op Common Ground-principes gebaseerde architectuur gevuld met referentiecomponenten, ontwikkeld in samenwerking tussen gemeenten, leveranciers en Dimpact. Het is actief in ontwikkeling.

**Doel**: één gezamenlijke plek voor de werking van het platform, zodat conflicterende implementaties tussen gemeenten worden voorkomen.

**Doelgroep**: architecten, ontwikkelaars, beleidsmedewerkers en leveranciers.

**Kerngroep**: tweewekelijkse sessies — dinsdagmiddag (architecten/ontwikkelaars) en vrijdagochtend (programmamanagers, leveranciers, projectbeheer).

Roadmap: https://www.notion.so/platformvoordienstverlening/Roadmap-e1ebdc0c60904c1a9c34b45388bc4ccd

## Patronen

Patronen zijn technische interactieblauwdrukken die beschrijven hoe componenten met elkaar communiceren.

### Externe Klanttaak (status: Review)
*Auteur: Jan Brekelmans*

Taken stellen burgers in staat om zelf zaken met gemeenten af te handelen. Taaksubtypes:

| Type | Beschrijving |
|---|---|
| **URL-taak** | Link naar externe bron |
| **Formuliertaak** | FormIO-formulier dat binnen het portaal wordt ingevuld |
| **Betaaltaak (Ogone PSP)** | Geïntegreerd betalingsverzoek |

**Workflow**: ZAC maakt taak aan → automatische notificatie → burger logt in → voert taak uit → portaal werkt status bij → ZAC wordt genotificeerd → taak verdwijnt uit wachtrij.

Taken zijn archiefobjecten met permanente bewaarplicht. Portalen mogen taken tonen maar niet verwijderen.

### Berichten (status: TODO)
*Auteur: Jan Brekelmans*

Berichten zijn officiële aankondigingen (doorgaans besluiten). Berichten moeten gekoppeld zijn aan documenten en optioneel aan zaken. Vooralsnog beperkt tot DigiD/BSN-gebruikers.

Drie kanalen: digitale notificatie, MijnOverheid BerichtenBox, fysieke post.

Per Logius-standaarden mag berichttekst alleen URLs en regeleindes bevatten (geen opmaak).

### Verzoeken
Omvat: standaardverzoeken, betalingsverzoeken, zaakverzoeken, productverzoeken. Meeste nog in voorbereiding (placeholder/TODO).

### Overige patronen
- **Domeinregistratie** — Common Ground registraties, referentielijsten
- **Vertegenwoordiging en Machtiging** — authenticatiecontextdatadefinities

## Standaarden

### Zaakgericht Werken (status: IN GEBRUIK)
*Auteur: Joeri Bekker*

VNG API-standaard gebaseerd op RGBZ 2.1, RSB 3.0 en ImZTC 2.1. VNG heeft de doorontwikkeling in 2023 gestaakt; de community drijft nu experimentele uitbreidingen geïntegreerd in Open Zaak.

Bijdragende organisaties:
- Gemeenten: Amsterdam, Den Haag, Dimpact, Rotterdam, Utrecht
- Leveranciers: Maykin, **Ritense**, Atos

### Objecten (status: IN GEBRUIK)
*Auteur: Joeri Bekker (Maykin, Product Owner)*

Flexibele API uit de ZGW-moderniseringsinspanning. Aangewezen als "community standard" door VNG. Gebruikt voor: zelfstandige objectdataopslag, testen van nieuwe registraties (Taken, Productverzoeken en Klanten begonnen hier), archivering van aanvullende zaakinformatie, documentvervanging.

Bijdragende organisaties:
- Gemeenten: Den Haag, Dimpact, Rotterdam, Utrecht
- Leveranciers: ICATT, Maykin, **Ritense**

### Klantinteracties (status: BEPROEVING/PILOT)
*Auteur: Joeri Bekker*

Zie ook: VNG Realisatie klantinteracties specificatie (https://vng-realisatie.github.io/klantinteracties/).

### Conceptstandaarden (in ontwikkeling)
- **Producten** (CONCEPT) — Producttypecatalogus
- **Referentielijsten** (CONCEPT)
- **ZGW-uitbreidingen** (CONCEPT) — o.a. substatussen

## Best practices

| Best practice | Auteur | Status |
|---|---|---|
| Uniforme registratie van zaken | Joeri Diederen | In voorbereiding |
| Uniforme registratie van klanten | Jan Verbeek | In voorbereiding |
| Formulier (Verzoek) prefill | — | — |
| Eén eigenaar van één Zaak | — | — |

### Detail: Uniforme registratie van zaken
Technische specificatie voor de zaaklevenscyclus conform ZRC-API 1.5. Omvat: aanmaken zaak, statusupdates, rolkoppeling (altijd INITIATOR en BEHANDELAAR), documentkoppeling, objectkoppeling en besluitregistratie. Inclusief sequentiediagrammen voor ZTC/ZAC/ZRC/KLI-interacties. Integratie met Open Klant en Haalcentraal/KvK-API gedekt.

## Onderzoeken

Lopende onderzoeken binnen PGD:

1. Beslisregels / DMN
2. Eén of meer zaakregisters — **Conclusie: één gecentraliseerd zaakregister per organisatie heeft de voorkeur** (Scenario 1)
3. PDC/PTC/VTC etc. — "de kapstok voor alles"
4. Archiveren
5. Open Archiefbeheer
6. In sync houden TAP-straat
7. Omnichannel registratie
8. NLX en FSC — inter-component API-routing
9. VTB-component
10. Meertaligheid
11. Gebruik en migratie van URLs naar URNs

## Relatie met NL Portal

Ritense is **expliciet genoemde bijdragende leverancier** aan twee PGD-standaarden:
- Zaakgericht Werken standaard
- Objecten standaard

Het Externe Klanttaak-patroon is geïmplementeerd in NL Portal's Taak V2-module. De Berichten-patronen zijn de basis voor NL Portal's MijnBerichten-functionaliteit.

## Relatie met MijnServices

PGD en MijnServices zijn complementair:
- **MijnServices** (VNG) definieert de *bouwstenen* vanuit burgerperspectief
- **PGD** definieert de *technische patronen en conceptstandaarden* waarop die bouwstenen draaien
- MijnServices verwijst gemeenten naar PGD voor de technische uitwerking

## Bronnen

- [Platform Generieke Dienstverlening — GitBook](https://dienstverleningsplatform.gitbook.io/platform-generieke-dienstverlening-public)
- [PGD Roadmap — Notion](https://www.notion.so/platformvoordienstverlening/Roadmap-e1ebdc0c60904c1a9c34b45388bc4ccd)
- [ZGW API standaard overzicht](https://vng-realisatie.github.io/gemma-zaken/standaard/)
- [Klantinteracties API specificatie](https://vng-realisatie.github.io/klantinteracties/)
