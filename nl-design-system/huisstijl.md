# Huisstijl toepassen

NL Portal is volledig thematiseerbaar via **NL Design System design tokens**. Eigen huisstijl toepassen is een configuratietaak — geen ontwikkelwerk.

---

## Hoe het werkt

NL Portal-componenten zijn opgebouwd met NLDS-componenttokens. Door de Brand- en Common tokens van uw gemeente te definiëren, past de volledige interface automatisch aan:

```
Brand tokens (uw kleuren, lettertypes)
    ↓ koppelen aan
Common tokens (primaire kleur, achtergrond, tekst)
    ↓ worden overgenomen door
Component tokens (knopkleur, koptekstkleur, linkkleur)
    ↓ sturen
Alle NL Portal-componenten
```

---

## Stap-voor-stap

### Stap 1 — Maak een tokenbestand aan

In de frontend-template repository staat het bestand:
`/src/styles/nl-portal-design-tokens.css`

Dit bestand bevat de design tokens die de standaardwaarden overschrijven. Begin met de Brand tokens van uw gemeente:

```css
/* Brand tokens — uw gemeentekleuren */
--gemeente-naam-color-primary: #1234AB;
--gemeente-naam-color-secondary: #ABCDEF;
--gemeente-naam-font-family: 'Uw Gemeentelettertype', sans-serif;
```

### Stap 2 — Koppel Brand tokens aan Common tokens

Wijs uw Brand tokens toe aan de NLDS-semantische laag:

```css
/* Common tokens — semantische betekenis */
--nl-color-primary: var(--gemeente-naam-color-primary);
--nl-color-secondary: var(--gemeente-naam-color-secondary);
```

### Stap 3 — Controleer het resultaat

Gebruik de browser-developer tools om te zien welk token een specifiek component aanstuurt. Selecteer een element → inspecteer de CSS-variabele in het rechterpaneel. De naam van het token is direct zichtbaar.

Voorbeeld: een knop toont `--button-background-color: var(--nl-color-primary)`. Door `--nl-color-primary` te overschrijven met uw Brand token past de knopkleur automatisch aan.

### Stap 4 — Refereer aan de Den Haag-implementatie

Gemeente Den Haag heeft een volledige NLDS-gebaseerde NL Portal-implementatie:

- Repository: [Gemeente-DenHaag/nl-portal-libraries](https://github.com/Gemeente-DenHaag/nl-portal-libraries)
- Tokenbestand als referentie: [nl-portal-design-tokens.css](https://github.com/nl-portal/nl-portal-frontend-template/blob/master/src/styles/nl-portal-design-tokens.css)

---

## Welke tokens NL Portal gebruikt

NL Portal-componenten gebruiken de volgende NLDS-tokenlagen:

| Token-categorie | Voorbeelden |
|---|---|
| Kleuren | `--nl-color-primary`, `--nl-color-background`, `--nl-color-text` |
| Typografie | `--nl-font-family`, `--nl-font-size-body` |
| Spacing | `--nl-spacing-small`, `--nl-spacing-medium` |
| Componenten | `--button-background-color`, `--header-bar-background-color` |

Het meest volledige overzicht staat in het tokenbestand van de frontend-template:
→ [nl-portal-design-tokens.css op GitHub](https://github.com/nl-portal/nl-portal-frontend-template/blob/master/src/styles/nl-portal-design-tokens.css)

---

## Toegankelijkheid

NLDS-componenten zijn ontworpen om te voldoen aan **WCAG 2.1 niveau AA** — de minimale toegankelijkheidseis voor overheidswebsites (Besluit digitale toegankelijkheid overheid). Door huisstijltokens toe te passen op NLDS-componenten, behoudt u deze toegankelijkheidsgarantie zolang u voldoende kleurcontrast handhaaft.

> Controleer altijd het kleurcontrast van uw Brand tokens met een tool zoals de [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/).

---

## Figma

NLDS publiceert een Figma Community Library voor ontwerpers:
→ [NL Design System Bibliotheek — Figma](https://www.figma.com/community/file/1508831915902670059/nl-design-system-bibliotheek)

Ontwerpers kunnen hiermee op basis van de NLDS-componenten een gemeentespecifiek prototype bouwen dat 1-op-1 overeenkomt met de implementatie in NL Portal.
