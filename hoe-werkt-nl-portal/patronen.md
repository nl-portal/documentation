# Patronen

NL Portal implementeert technische interactiepatronen die zijn vastgelegd door het **Platform Generieke Dienstverlening (PGD)**. Deze patronen beschrijven hoe componenten met elkaar communiceren en vormen de technische blauwdruk achter de MijnServices-bouwstenen.

→ Zie [Platform Generieke Dienstverlening](../platform-generieke-dienstverlening.md) voor de bredere context van PGD.

---

## Externe Klanttaak (Taak V2)

Het **Externe Klanttaak**-patroon beschrijft hoe taken worden aangemaakt door het zaakafhandelingssysteem en beschikbaar worden gesteld aan de burger via het portaal.

NL Portal implementeert dit patroon als **Taak V2**. Taken worden opgeslagen als objecten in de Objecten API en opgehaald door het portaal.

### Workflow

```
1. Zaakafhandelingscomponent maakt taak aan in Objecten API
2. Notificatieservice brengt NL Portal op de hoogte
3. Burger logt in → ziet taak in MijnTaken
4. Burger voert taak uit (formulier, betaling, of URL-taak)
5. NL Portal werkt de taakstatus bij in de Objecten API
6. Zaakafhandelingscomponent wordt genotificeerd → taak verdwijnt uit de wachtrij
```

### Taaktypen

| Type | Beschrijving |
|---|---|
| **URL-taak** | Link naar een externe bron; burger wordt doorgestuurd |
| **Formuliertaak** | FormIO-formulier dat binnen het portaal wordt ingevuld |
| **Betaaltaak** | Geïntegreerd betalingsverzoek |

**Belangrijk**: Taken zijn archiefobjecten met een permanente bewaarplicht. NL Portal mag taken tonen maar niet verwijderen — dat is de verantwoordelijkheid van het zaakafhandelingscomponent.

---

## Berichten

Het **Berichten**-patroon beschrijft hoe officiële berichten van de gemeente aan burgers worden afgeleverd. Berichten zijn altijd gekoppeld aan een document en optioneel aan een zaak.

NL Portal ondersteunt drie kanalen:
- **Digitale notificatie** in het portaal (MijnBerichten)
- Doorstuur naar **MijnOverheid BerichtenBox** (voor DigiD-gebruikers)
- **Fysieke post** als terugvaloptie

**Wmebv-relatie**: Het Berichten-patroon is de technische invulling van de wettelijke berichtenplicht (Wmebv, 1 januari 2026).

**Technische beperking**: Per Logius-standaarden mag de berichttekst alleen platte tekst bevatten (URLs en regeleindes; geen HTML-opmaak).

---

## Verzoeken

Het **Verzoeken**-patroon beschrijft hoe burgers aanvragen indienen bij de gemeente. Dit is een asynchroon patroon:

```
1. Burger dient verzoek in via NL Portal → verzoek wordt als object opgeslagen in Objecten API
2. Objecten API notificeert het notificatiecomponent
3. Zaakafhandelingscomponent is geabonneerd op notificaties van dit type → wordt op de hoogte gesteld
4. Zaakafhandelingscomponent haalt het verzoek op uit de Objecten API en start de zaakafhandeling
```

Het verzoek bevat geen gevoelige data in de notificatie zelf (informatie-arm principe van Common Ground) — alleen een verwijzing naar het object.

---

## Synchrone en asynchrone communicatie

NL Portal gebruikt beide communicatiestijlen:

| Stijl | Gebruik | Voorbeeld |
|---|---|---|
| **Synchroon** (REST) | Direct opvragen van data voor weergave | Zaken ophalen bij Open Zaak |
| **Asynchroon** (events) | Verwerking van inkomende acties | Verzoek indienen via Objecten API |

Synchrone communicatie is eenvoudig maar maakt NL Portal afhankelijk van de beschikbaarheid en snelheid van de backoffice-service. Asynchrone communicatie via de Notificaties API maakt de koppeling losser: de services kennen elkaar niet direct.
