# Onderzoek: NL Design System (NLDS)

> Bronnen: nldesignsystem.nl, GitHub nl-design-system, AccessibleEU (online onderzoek maart 2026)

## Wat is NLDS?

NL Design System (NLDS) is een gedeeld design system voor Nederlandse overheidsdigitale diensten, beheerd door **ICTU** namens het **Ministerie van Binnenlandse Zaken en Koninkrijksrelaties (BZK)**. In 2024 is NLDS overgegaan naar een meer zelfstandige projectstructuur.

Het is **geen monolithisch design system** maar een architectuur en een community: een set van standaarden, processen en gedeelde bouwstenen die elke organisatie kan adopteren en thematiëren naar de eigen huisstijl.

Licentie: EUPL 1.2 (gelijk aan NL Portal / Common Ground)

## Hoe werkt het technisch: design tokens

NLDS is gebouwd op een **drielaags design token-architectuur**:

### Laag 1 — Brand tokens
De ruwe visuele opties van de organisatie: specifieke kleurwaarden, lettertypes, border radii, etc. Organisaties hebben hier volledige naamvrijheid. Deze representeren het merkpalet zonder semantische betekenis.

Voorbeeld: `--gemeente-amsterdam-color-blue: #004699`

### Laag 2 — Common tokens
Semantische tokens die relevant zijn voor veel componenten: feedbackkleuren (fout, waarschuwing, succes), focusstates, spacingschalen, etc. Zorgen voor consistente UX-patronen ongeacht het merk.

Voorbeeld: `--nl-color-primary: var(--gemeente-amsterdam-color-blue)`

### Laag 3 — Component tokens
Alle tokens voor een specifiek component, die waarden overnemen van Common tokens. Elk NLDS-component moet deze standaard component tokens gebruiken om herbruikbaar te blijven.

Voorbeeld: `--button-background-color: var(--nl-color-primary)`

**Naamgevingsconventie**: `{org}.{component}.{element}.{modifier}.{css-eigenschap}`
Voorbeeld: `example.text-input.placeholder.color`

Het organisatieprefix werkt als "vendor prefix" om conflicten tussen teams te voorkomen.

## Het Estafettemodel (componentrijpheid)

NLDS hanteert het **Estafettemodel** met vier statusniveaus:

| Status | Beschrijving |
|---|---|
| **Help Wanted** | Component geïdentificeerd als nodig; community wordt uitgenodigd te starten |
| **Community** | Organisaties bouwen en delen implementaties vrijelijk; meerdere varianten mogelijk |
| **Candidate** | Component is gegeneraliseerd, breed ingezet, en open voor eindreview voor standaardisatie |
| **Hall of Fame** | Definitieve stabiele versie; gegarandeerd toegankelijk, herbruikbaar, stabiel; gebruikt in productie bij minstens 2 organisaties met verschillende huisstijlen |

## Adoptieproces voor een gemeente

1. **Definieer brand tokens** — Maak een CSS-bestand (of Figma-bibliotheek) met de ruwe ontwerpwaarden van de organisatie
2. **Koppel Brand → Common → Component tokens** — Wijs merkwaarden toe aan de NLDS-semantische tokenlaag
3. **Installeer npm-pakketten** — Componenten volgen het patroon `@{org}/{component}-css` of `@utrecht/{component}`
4. **Optioneel: stel een Storybook in** — Voor documentatie en visueel testen
5. **Participeer in de community** — Tweewekelijkse online meetings, Slack, community sprints

## Welke organisaties gebruiken NLDS?

**Gemeentegroepen:**
- **OpenWebconcept** — community van ~40 gemeenten
- **Dimpact** — associatie van ~40 gemeenten
- **G4** — Amsterdam, Rotterdam, Den Haag, Utrecht

**Individuele gemeenten met eigen design system op NLDS-basis:**
- Den Haag (`nl-design-system/denhaag`)
- Utrecht (`nl-design-system/utrecht`) — meest volledige referentie-implementatie
- Rotterdam (`nl-design-system/rotterdam`) — RODS
- Tilburg, Nijmegen

**Rijksoverheid:**
- RVO — ROOS (RVO Open Ontwerp Systeem)
- Logius / DigiD / MijnOverheid — via "Lux: Logius Design System"
- Rijkshuisstijl Community (2024) — Logius, Ministerie van Justitie, RIVM

## NL Portal en NLDS

NL Portal is expliciet gebouwd om gestileerd te worden via NLDS design tokens:

- De `nl-portal-frontend-libraries` paketten produceren herbruikbare componenten die voldoen aan NLDS-specificaties
- Gemeenten wisselen de huisstijl door een ander tokenbestand te importeren
- Den Haag tokens zijn de standaard in de NL Portal frontend template
- Gemeente Den Haag heeft een eigen fork (`Gemeente-DenHaag/nl-portal-libraries`) die hun NLDS-gebaseerde tokens toepast

**Praktische implicatie voor functioneel beheerders**: eigen huisstijl toepassen is een configuratietaak (CSS tokens), geen ontwikkelwerk.

## Relatie met Common Ground

NLDS en Common Ground zijn complementaire initiatieven:
- Beide zijn open source onder EUPL 1.2
- Beide zijn VNG-gelieerd en richten zich op dezelfde doelgroep
- Common Ground adresseert de **data/API-architectuurlaag**; NLDS adresseert de **interactie/presentatielaag**
- NL Portal is waar ze het meest direct samenkomen

## Recente ontwikkelingen (2024–2025)

- **2024**: NLDS overgegaan naar zelfstandig project (los van directe ICTU/BZK-aansturing)
- **Rijkshuisstijl Community Sprints (zomer 2024)**: Eerste community sprints voor Rijkshuisstijl-teams; betrokken partijen: Logius, Ministerie van Justitie, RIVM
- **Design Systems Week 2024 en 2025**: Jaarlijks meerdaags evenement
- **Nieuwe Figma Bibliotheek**: Gepubliceerd als community file
- **Global Design System**: NLDS betrokken bij W3C internationale samenwerking overheden

## Figma-integratie

- NLDS publiceert een Figma Bibliotheek met Brand-, Common- en Component-secties
- Updates gesynchroniseerd via URL-gekoppelde JSON elke ~2 maanden
- Aankondigingen in Slack-kanaal `#nl-design-system-designers`
- Figma community file: https://www.figma.com/community/file/1508831915902670059/nl-design-system-bibliotheek

## Bronnen

- [NL Design System](https://nldesignsystem.nl/)
- [Design Token Conventie](https://nldesignsystem.nl/handboek/developer/design-token-conventie/)
- [Estafettemodel](https://nldesignsystem.nl/handboek/estafettemodel/)
- [Onboarding](https://nl-design-system.github.io/onboarding/)
- [GitHub: nl-design-system/themes](https://github.com/nl-design-system/themes)
- [GitHub: nl-design-system/utrecht](https://github.com/nl-design-system/utrecht)
- [GitHub: Gemeente-DenHaag/nl-portal-libraries](https://github.com/Gemeente-DenHaag/nl-portal-libraries)
- [VNG: NLDS voor heel BV Nederland](https://vng.nl/praktijkvoorbeelden/nlds-voor-heel-bv-nederland)
- [Doorontwikkeling NLDS — Digitale Overheid](https://www.digitaleoverheid.nl/innovatieproject/doorontwikkeling-nl-design-system/)
