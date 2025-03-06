# Architectuur

### Scope

NL Portal is een Nederlands, open source "Mijn Omgeving"-platform, primair bedoeld voor 
gebruik door overheden. Het faciliteert de interactie met klanten en ketenpartners. Klanten 
in deze context zijn personen of organisaties die een verzoek indienen. Ketenpartners zijn 
organisaties die bijdragen aan de afhandeling van het verzoek.

NL Portal verzorgt zelf geen zaakafhandeling, is geen formulierencomponent en fungeert niet
als website of content management systeem. Het werkt echter wel samen met deze componenten
voor interactie.

### Common Ground & Platform Generieke Dienstverlening <a href="#platform-generieke-dienstverlening" id="platform-generieke-dienstverlening"></a>

NL Portal is ontwikkeld op basis van de  [Common Ground](https://commonground.nl/) -principes, een initiatief 
van de Nederlandse gemeentes. De informatiearchitectuurprincipes zijn als volgt:

* **Component-gebaseerd**: NL Portal is een onafhankelijk functionerend component. 
Het fungeert als "Mijn Omgeving" voor burgers en ondernemers, en communiceert met andere 
componenten via gestandaardiseerde interfaces.
* **Open**: NL Portal is open source en wordt in een open ontwikkeld.
* **Vertrouwd**: Informatiebeveiliging staat centraal in de ontwikkeling.
* **Eenmalige vastlegging**: Data-opslag in NL Portal is geminimaliseerd; data wordt 
opgehaald bij de bron, primair de Common Ground-datalaag en secundair andere gegevensbronnen.
* **Regie op gegevens**: Burgers kunnen gegevens inzien, waar mogelijk aanpassen, verzoeken 
indienen, taken uitvoeren en berichten ontvangen. Dit is de essentie van NL Portal: 
inzicht in gegevens en eenvoudige communicatie met de overheid.
* **Standaarden**: Er wordt primair gebruik gemaakt van open standaarden.

### Platform Generieke Dienstverlening&#x20;

NL Portal wordt ingezet als onderdeel van het Platform Generieke Dienstverlening, een Common Ground-initiatief dat invulling geeft aan de gedachte van Common Ground. Dit platform bestaat uit een referentiearchitectuur en referentiecomponenten, die samen een dienstverleningsplatform vormen. Het omvat onder andere componenten voor het bouwen van formulieren, zaakafhandeling, logging, archivering en een portaal.

Twee belangrijke uitgangspunten binnen deze architectuur zijn:

* **Componenten in plaats van monolieten**: Hierdoor kunnen in de toekomst componenten 
worden vervangen zonder het gehele platform te vervangen.
* **Data gescheiden van business logica**: Dit betekent dat data niet in componenten zit, 
maar in een gestandaardiseerd formaat op een gescheiden locatie wordt opgeslagen, wat het eenvoudiger maakt om componenten te vervangen.

Deze architectuur is niet specifiek voor de Nederlandse gemeentes, maar is gebaseerd op 
universele architectuurprincipes, waarbij de microservices-architectuur een basis vormt.



