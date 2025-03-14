# Token exchange


## Wanneer en hoe gebeurt het?
Als je een api call doet naar de backend wordt de token onderschept en wordt
er een call naar keycloak gedaan en hier wordt een nieuwe token opgehaald 
waar de bsn/kvk wel in zit. Deze wordt nu gebruikt in de verdere applicatie.

### Hoe moet je keyclaok instellen:

Maak een nieuwe client aan voor de backend.

![tokenexchange1](img/tokenexchange-1.png)

![tokenexchange2](img/tokenexchange-2.png)

Op de credentials tab vind je de secret key die je in de application yaml moet zetten.

![tokenexchange3](img/tokenexchange-clientSecret.png)
![tokenexchange4](img/tokenexchange-yamlconfig.png)

LET OP: niet zomaar op regenarate klikken dan veranderd de key en kan je niet de oude meer terug zetten.

Hierna creëer je nog een client deze is voor de token exchange.
![generalsettings1](img/tokenexchange-generalsettings-1.png)
![generalsettings2](img/tokenexchange-generalsettings-2.png)


Navigeer naar de ‘Client scopes’ tab. Hier klik je op de 1e client scope.

![clientscopes](img/tokenexchange-clientscopes.png)

In ons geval met de naam ‘gzac-portal-token-exchange-dedicated’.

Hierin komen de mappers van de bsn en kvk.

![mappers](img/tokenexchange-mappers.png)

Ga terug naar client details en navigeer nu naar de tab ‘Permissions’.

Zorg dat de ‘permissions enabled’ op ‘on’ staat.

Je krijgt een permissions list te zien. Navigeer naar ‘token exchange’.

![permission-list](img/tokenexchange-permissionslist.png)

Hierin moet je een nieuwe polici maken om de backend client toegang te geven tot een token exchange.

![policy-config](img/tokenexchange-policy-config.png)

De policy.

![policy](img/tokenexchange-policy.png)

Hierna moet je nog naar de ‘oude’ al bestaande client om de mappers(kvk en bsn) weg te gooien bij
de al bestaande client die nu alleen nog gebruikt zal worden door de frontend.

In de backend moet je nu per omgeving een parameter zetten die de secret en de resource heeft om 
de token exchange succesvol te kunnen runnen.
