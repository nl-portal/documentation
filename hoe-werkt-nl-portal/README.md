# Hoe werkt NL Portal?

NL Portal is een component in het **Common Ground vijflagenmodel** — specifiek laag 5, de interactielaag. Het portaal beheert zelf geen data, maar aggregeert informatie uit bestaande bronregistraties en presenteert die aan de burger via een uniforme interface.

---

## Componenten

NL Portal bestaat uit drie lagen:

| Laag | Technologie | Doel |
|---|---|---|
| **Frontend** | React 19, TypeScript, NL Design System | Burgerfacing interface; thematiseerbaar per gemeente |
| **Backend** | Kotlin, Spring Boot | GraphQL-aggregatielaag; vertaalt burgervragen naar ZGW REST API-calls |
| **GraphQL API** | GraphQL | Enkelvoudig API-oppervlak tussen frontend en backend |

De backend fungeert als **vertaallaag**: de frontend stelt één GraphQL-query in, de backend vertaalt dat naar meerdere REST API-aanroepen op de backoffice-systemen (zaaksysteem, klantregistratie, BRP, etc.) en combineert de resultaten.

---

## Positie in het Common Ground vijflagenmodel

```
Laag 5 — Interactie     ← NL Portal (burgerpersoonlijke omgeving)
Laag 4 — Proces         ← Zaakafhandelingscomponent (bijv. GZAC, ZAC)
Laag 3 — Integratie     ← API-gateway, authenticatieservices
Laag 2 — Services       ← Open Zaak, Open Klant, Haalcentraal
Laag 1 — Data           ← Bronregistraties (ZRC, DRC, BRC, KIC, BRP)
```

NL Portal bevindt zich bovenaan de stack. Het bevraagt de services in laag 2 via gestandaardiseerde APIs en slaat zelf geen zaak- of persoonsgegevens op. Dit is het "data bij de bron"-principe van Common Ground.

---

## Scope van NL Portal

**In scope:**
- Communicatie met de burger (MijnZaken, MijnTaken, MijnBerichten, MijnProfiel, MijnContactmomenten)
- Aggregatie van gegevens uit meerdere bronregistraties
- Huisstijlinpassing via NL Design System tokens

**Buiten scope:**
- Zaakafhandeling (dat is het domein van ZAC/GZAC)
- Formulieren (dat is het domein van een formuliercomponent)
- Content management (dat is het domein van een CMS)
- Notificaties via e-mail/sms (dat is het domein van NL Notify of vergelijkbaar)
- Authenticatie (dat is het domein van DigiD-aansluiting + Keycloak)

---

## In deze sectie

- [Integraties](integraties.md) — Welke API-standaarden en referentie-implementaties
- [Patronen](patronen.md) — Externe Klanttaak, Berichten en Verzoeken
- [Authenticatie en token exchange](authenticatie-en-tokenexchange.md) — Hoe BSN/KVK veilig meegegeven wordt aan backoffice-APIs
