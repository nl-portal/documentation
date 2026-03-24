# Authenticatie en toegang

NL Portal biedt ondersteuning voor de twee standaard authenticatiemiddelen van de Nederlandse overheid: **DigiD** voor burgers en **eHerkenning** voor ondernemers.

---

## DigiD

DigiD is het digitale identiteitsmiddel waarmee Nederlandse burgers zich identificeren bij overheidsinstanties. NL Portal gebruikt DigiD voor de authenticatie van burgers.

Na een succesvolle DigiD-login ontvangt NL Portal het BSN (Burgerservicenummer) van de burger. Dit BSN wordt gebruikt om:
- Persoonsgegevens op te halen bij de BRP (Basisregistratie Personen, via Haalcentraal)
- Zaken, taken, berichten en contactmomenten op te halen die aan de burger gekoppeld zijn

**Wmebv-relatie**: DigiD is het authenticatiemiddel dat Wmebv vereist voor formele berichtgeving aan burgers. MijnBerichten in NL Portal is uitsluitend beschikbaar voor ingelogde DigiD-gebruikers.

---

## eHerkenning

eHerkenning is het authenticatiemiddel voor ondernemers en rechtspersonen. NL Portal biedt ondersteuning voor eHerkenning zodat ondernemers namens een bedrijf kunnen inloggen en zakelijke zaken kunnen inzien.

Na een succesvolle eHerkenning-login ontvangt NL Portal het KVK-nummer. Dit wordt gebruikt om:
- Bedrijfsgegevens op te halen bij het Handelsregister (via Haalcentraal HR)
- Zaken en taken op te halen die aan het bedrijf gekoppeld zijn

---

## Technische uitwerking

De authenticatie verloopt via **OpenID Connect (OIDC)**. NL Portal fungeert als OIDC-client; DigiD en eHerkenning zijn de identity providers, doorgaans via een intermediaire identity broker (zoals Keycloak).

Het BSN of KVK-nummer belandt via een **token exchange** in het authenticatietoken waarmee NL Portal de backoffice-APIs benadert. Dit mechanisme zorgt dat de gebruikersidentiteit veilig meegegeven wordt aan de ZGW-services, zonder dat het portaal zelf gevoelige gegevens hoeft op te slaan.

→ Zie [Authenticatie en token exchange](../hoe-werkt-nl-portal/authenticatie-en-tokenexchange.md) voor de conceptuele werking.
