# Zaak

Mijn lopende zaken worden worden getoond voor klanten. De informatie wordt uit de bron OpenZaak gehaald. Voor natuurlijk personen gebeurt dit op basis van het BSN, voor organisaties op basis van het KVK-nummer.&#x20;

Het architectuur gaat uit van het gebruik van 1 installatie van OpenZaak binnen de organisatie. Alle interne zaak- en taakapplicaties registreren de zaak-meta gegevens in OpenZaak, waarmee deze inzichtelijk worden voor de klant.&#x20;

Van een Zaak wordt de meta-informatie getoond, zoals aanvraagdatum, zaakstatus en behandelaar. Verder gekoppelde informatie, waaronder documenten.&#x20;



<figure><img src="../../../.gitbook/assets/Screenshot 2024-06-05 at 15.13.03.png" alt=""><figcaption></figcaption></figure>

#### Track & Trace

Een onderdeel van het zakenoverzicht is de Track & Trace functionaliteit. Organisaties worden veel gebeld en gemaild met verzoeken voor informatie met betrekking tot lopende zaken. Met track en trace willen we dit inzichtelijk maken zodat mensen weten wat de huidige status is, en idealiter ook nog hoe lang het nog duurt tot de zaak is afgerond. In NL Portal kunnen we gedetailleerde zaakstatussen en substatussen tonen en daarbij ook een tijdslijn van de verwachte doorloop.
