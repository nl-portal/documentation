# Connectiviteit

NL Portal koppelt met alle common ground systemen op laag 1 zoals OpenZaak en de Objecten API. Het koppelen van deze systemen verloopt altijd op ongeveer dezelfde manier:

1. In het aan te sluiten systeem moet een api account aangemaakt worden voor NL Portal
2. In NL Portal configureer je de url van het aan te sluiten systeem en de gegevens van het bij stap 1 aangemaakte account

#### Voorbeeld

Stel dat we een NL Portal instantie willen koppelen aan Open Zaak. Als eerste loggen we dan in in Open Zaak en gaan we naar Applicaties.

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

Vervolgens kun je daar een nieuwe applicatie toevoegen.

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

Vul de client id van de nieuwe applicatie in en een secret key. Het vinkje "heeft alle autorisaties" mag alleen gebruikt worden op development omgevingen.

<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

Ga vervolgens naar het scherm beheer autorisatiegegevens en selecteer daar welke machtigingen NL Portal moet krijgen.

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

Vervolgens moet NL Portal geconfigureerd worden om gebruik te maken van de aangemaakte autorisatiegevens. Dit kan met behulp van [environment variabelen](https://en.wikipedia.org/wiki/Environment_variable), of oplossing zoals de [azure key vault](https://azure.microsoft.com/en-us/products/key-vault), of de [aws key management service](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html).&#x20;
