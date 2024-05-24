# Architectuur

### Platform Generieke Dienstverlening

&#x20;Het Platform Generieke Dienstverlening is een Common Ground initiatief, voortgekomen uit de behoefte om concreet invulling te geven aan de gedachte van Common Ground. Het bestaat uit een referentie architectuur en referentie componenten, die als geheel een dienstverleningsplatform vormen. Het Platform Generieke Dienstverlening omvat onder meer componenten voor het bouwen van formulieren, zaakafhandeling, logging, archivering en een portaal.

&#x20;Twee belangrijke uitgangspunten binnen deze architectuur zijn:

* Componenten in plaats van monolieten. Dat maakt dat in de toekomst componenten vervangen kunnen worden, zonder dat het gehele platform vervangen hoeft te worden.
* Data gescheiden van business logica. Met als voordeel dat data niet in componenten zit, maar op een gestandaardiseerd formaat en een gescheiden locatie wordt opgeslagen, zodat componenten eenvoudiger vervangen kunnen worden.

Deze architectuur is niet uitgevonden door de Nederlandse gemeentes noch uniek: het is gebaseerd op universele architectuurprincipes. Het is een toepassing van de micro services architectuur. Voor wie daar meer over wil weten, het BOEK.&#x20;

### Scope van NL Portal

NL Portal verzorgt de interactie met klanten en ketenpartners. Klanten zijn natuurlijk personen of organisaties, die partij die een verzoek heeft. Ketenpartners zijn organisaties die gedurende afhandeling van het verzoek een bijdrage leveren.\
\
NL Portal doet geen zaakafhandeling, is geen formulierencomponent en is geen website of content management systeem. Dit zijn wel componenten waarmee typisch interactie plaats vindt.

### Integratiepatronen

&#x20;NL Portal integreert met de datalaag én omliggende componenten. In deze paragraaf worden eerst algemene principes uitgelegd.

####
