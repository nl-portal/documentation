# Functionaliteiten per MijnServices-bouwsteen

Per bouwsteen een beschrijving van wat de burger ziet, welke backoffice-koppeling vereist is, en de rijpheidsstatus van de onderliggende standaard.

---

## Out-of-the-box (zonder maatwerk)

### MijnZaken

**Wat ziet de burger?**
Een overzicht van alle ingediende aanvragen, met de huidige status en voortgang. De burger kan documenten bekijken die aan een zaak gekoppeld zijn.

**Vereiste backoffice-koppeling**
- ZGW Zaken API — zaakregistratie en statussen
- ZGW Catalogi API — zaaktypecatalogus (ZTC) voor omschrijvingen
- ZGW Documenten API — zaakgerelateerde documenten

**Referentie-implementatie backoffice**: [Open Zaak](https://openzaak.org/)

**Rijpheid standaard**: Standaard (formeel vastgesteld, meest volwassen van alle MijnServices-bouwstenen)

---

### MijnTaken

**Wat ziet de burger?**
Een lijst van openstaande acties die de burger moet uitvoeren om een zaak voort te zetten — zoals het invullen van een formulier, doen van een betaling of bevestigen van een afspraak.

**Vereiste backoffice-koppeling**
- Objecten API — taken worden als objecten opgeslagen
- Objecttypen API — voor de typedefinitie van taken

NL Portal implementeert het **Externe Klanttaak V2-patroon** (Platform Generieke Dienstverlening). Taken worden aangemaakt door het zaakafhandelingssysteem (bijv. ZAC) en door NL Portal opgehaald en gepresenteerd.

**Rijpheid standaard**: Candidate

---

### MijnBerichten

**Wat ziet de burger?**
Officiële berichten van de gemeente, zoals beschikkingen, bevestigingen en beslissingen. De burger kan berichten inzien en beantwoorden.

**Vereiste backoffice-koppeling**
- Klantinteracties API — berichten en klantcontact
- Contactgegevens API — koppeling aan burgergegevens

**Referentie-implementatie**: [Open Klant](https://github.com/maykinmedia/open-klant) (implementatie van de Klantinteracties API en Contactgegevens API door Maykin Media)

**Wettelijke context**: MijnBerichten is de door VNG aanbevolen invulling van de **Wmebv**-verplichting (in werking per 1 januari 2026).

**Rijpheid standaard**: Candidate — actief in standaardisatieproces bij VNG; Rijksoverheid betrokken

---

### MijnProfiel

**Wat ziet de burger?**
Persoonlijke contactgegevens en communicatievoorkeuren: via welk kanaal de burger benaderd wil worden en welke contactgegevens de gemeente heeft.

**Vereiste backoffice-koppeling**
- Contactgegevens API — opslaan en opvragen van contactgegevens en voorkeuren

**Referentie-implementatie**: Open Klant (versie 2)

**Rijpheid standaard**: Candidate

---

### MijnContactmomenten

**Wat ziet de burger?**
Een overzicht van eerder contact tussen de burger en de gemeente — telefoongesprekken, e-mails, bezoeken aan de balie — gekoppeld aan zaken.

**Vereiste backoffice-koppeling**
- Klantinteracties API — registratie en opvragen van contactmomenten

**Referentie-implementatie**: Open Klant (versie 2)

**Rijpheid standaard**: Candidate

---

## Met maatwerk

### MijnProducten

**Wat ziet de burger?**
Een overzicht van verleende producten en diensten — zoals een goedgekeurde vergunning, toegekende subsidie of actief abonnement.

**Vereiste backoffice-koppeling**
- Producttypecatalogus / Objecten API — productregistraties

**Referentie-implementatie**: [Open Product](https://github.com/maykinmedia/open-product)

**Toelichting**: NL Portal biedt ondersteuning voor MijnProducten, maar de configuratie vereist afstemming op het specifieke productregister van de gemeente.

**Rijpheid standaard**: Community

---

### MijnActies

**Wat ziet de burger?**
Proactieve acties die de gemeente aanbiedt — bijvoorbeeld een herinnering dat een parkeervergunning verlengd kan worden.

**Toelichting**: De onderliggende standaard is nog in ontwikkeling bij VNG. NL Portal biedt basisondersteuning, maar volledige implementatie vereist maatwerk op de notificatielogica.

**Rijpheid standaard**: Community

---

## Nog niet geïmplementeerd

| Bouwsteen | Status |
|---|---|
| **MijnPlan** | Nieuw in VNG-roadmap; standaard nog niet vastgesteld |
| **MijnGesprek** | Nieuw in VNG-roadmap; standaard nog niet vastgesteld |
| **MijnAgenda** | Nieuw in VNG-roadmap; standaard nog niet vastgesteld |

NL Portal volgt de ontwikkeling van deze bouwstenen. Zodra VNG de standaarden heeft vastgesteld, wordt implementatie in de roadmap opgenomen.

→ Zie [Roadmap](../product-management/roadmap.md) voor de huidige planningen.
