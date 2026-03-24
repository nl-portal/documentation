# NL Design System en huisstijl

**NL Design System (NLDS)** is het gedeelde design system voor Nederlandse overheidsdigitale diensten, beheerd door **ICTU** namens het **Ministerie van Binnenlandse Zaken en Koninkrijksrelaties (BZK)**.

NL Portal is gebouwd op NLDS-componenten. Dit betekent dat elke gemeente de eigen huisstijl kan toepassen **zonder ontwikkelwerk** — puur via een CSS-tokenbestand.

---

## In deze sectie

- [Hoe NLDS werkt](README.md) — Het drielaags tokenmodel en het Estafettemodel (deze pagina)
- [Huisstijl toepassen](huisstijl.md) — Stap-voor-stap: eigen huisstijl configureren

---

## Wat is NLDS?

NLDS is **geen monolithisch design system** maar een architectuur en een community: een set van standaarden, processen en gedeelde bouwstenen die elke overheidsorganisatie kan adopteren en thematiëren naar de eigen huisstijl.

Licentie: EUPL 1.2 — gelijk aan NL Portal en Common Ground.

---

## Het drielaags design token-model

NLDS werkt met een hiërarchie van **design tokens** — CSS-variabelen die ontwerpbeslissingen vastleggen zoals kleuren, lettertypes en afstanden. Er zijn drie lagen:

### Laag 1 — Brand tokens
De ruwe visuele waarden van de organisatie: specifieke kleuren, lettertypes, border radii. Organisaties hebben hier volledige vrijheid in naamgeving. Deze tokens representeren het merkpalet zonder semantische betekenis.

```css
--gemeente-den-haag-color-cyan: #00A6D6;
```

### Laag 2 — Common tokens
Semantische tokens die relevant zijn voor veel componenten: feedbackkleuren (fout, waarschuwing, succes), focusstates, spacingschalen. Zorgen voor consistente UX-patronen ongeacht het merk.

```css
--nl-color-primary: var(--gemeente-den-haag-color-cyan);
```

### Laag 3 — Component tokens
Tokens voor een specifiek component, die waarden overnemen van Common tokens. Elk NLDS-component gebruikt standaard component tokens om herbruikbaar te zijn.

```css
--button-background-color: var(--nl-color-primary);
```

**Naamgevingsconventie**: `{organisatie}.{component}.{element}.{modifier}.{css-eigenschap}`

Door organisatiespecifieke Brand tokens aan Common tokens te koppelen, past de volledige interface automatisch aan de huisstijl — van knoppen tot formulieren tot navigatie.

---

## Het Estafettemodel

NLDS hanteert het **Estafettemodel** om de rijpheid van componenten bij te houden:

| Status | Beschrijving |
|---|---|
| **Help Wanted** | Component geïdentificeerd als nodig; community wordt uitgenodigd te starten |
| **Community** | Organisaties bouwen en delen implementaties; meerdere varianten mogelijk |
| **Candidate** | Component is gegeneraliseerd, breed ingezet en open voor eindreview |
| **Hall of Fame** | Definitieve stabiele versie; gegarandeerd toegankelijk en herbruikbaar; in productie bij minimaal 2 organisaties met verschillende huisstijlen |

NL Portal-componenten streven naar **Candidate** of **Hall of Fame** status.

---

## Welke organisaties gebruiken NLDS?

| Groep | Omvang |
|---|---|
| **OpenWebconcept** — community van gemeenten | ~40 gemeenten |
| **Dimpact** — associatie van gemeenten | ~40 gemeenten |
| **G4** — Amsterdam, Rotterdam, Den Haag, Utrecht | 4 steden |

**Individuele gemeenten met eigen NLDS-gebaseerd design system:**
- Den Haag (`nl-design-system/denhaag`) — referentie-implementatie voor NL Portal
- Utrecht (`nl-design-system/utrecht`) — meest complete referentie
- Rotterdam (`nl-design-system/rotterdam`)

**Rijksoverheid:**
- Logius / DigiD / MijnOverheid — via "Lux: Logius Design System"
- RVO — ROOS (RVO Open Ontwerp Systeem)

---

## NLDS en Common Ground

NLDS en Common Ground zijn complementaire initiatieven:
- Beide zijn open source onder EUPL 1.2
- Beide zijn VNG-gelieerd en richten zich op dezelfde doelgroep
- Common Ground adresseert de **data/API-architectuurlaag**; NLDS adresseert de **interactie/presentatielaag**
- NL Portal is waar ze direct samenkomen

→ [Doorontwikkeling NL Design System — Digitale Overheid](https://www.digitaleoverheid.nl/innovatieproject/doorontwikkeling-nl-design-system/)
→ [nldesignsystem.nl](https://nldesignsystem.nl/)
