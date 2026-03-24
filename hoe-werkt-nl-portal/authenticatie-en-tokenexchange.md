# Authenticatie en token exchange

## Overzicht

NL Portal gebruikt **OpenID Connect (OIDC)** als authenticatieprotocol. De burger logt in via DigiD of eHerkenning — de identity provider stuurt een OIDC-token terug naar NL Portal. Dit token bevat echter nog géén BSN of KVK-nummer: die gevoelige identifiers worden pas later toegevoegd via een **token exchange**.

---

## Waarom token exchange?

De backoffice-systemen (ZGW APIs, Klantinteracties API) moeten weten namens welke burger een aanvraag wordt gedaan. Ze verwachten het BSN of KVK-nummer in het authenticatietoken.

Het BSN mag niet in het initiële inlogtoken staan — dat token wordt ook door de frontend gebruikt en mag geen gevoelige persoonsgegevens bevatten. De oplossing is een **token exchange**:

```
1. Burger logt in via DigiD/eHerkenning → OIDC-token (zonder BSN)
2. Frontend stuurt API-aanvraag naar NL Portal backend
3. Backend onderschept het token en doet een token exchange call
4. Identity broker (Keycloak) geeft een nieuw token terug met BSN/KVK
5. Backend gebruikt dit verrijkte token voor calls naar ZGW-services
```

Het BSN/KVK-nummer verlaat de backend nooit naar de frontend. De burger ziet zijn eigen gegevens, maar de identifier is nooit zichtbaar in de browser.

---

## Betrokken componenten

| Component | Rol |
|---|---|
| **DigiD / eHerkenning** | Identity provider; voert de daadwerkelijke authenticatie uit |
| **Keycloak** (of vergelijkbare broker) | OIDC-broker; voert de token exchange uit en voegt BSN/KVK toe |
| **NL Portal backend** | OIDC-client; onderschept tokens en gebruikt verrijkt token voor backoffice-calls |
| **ZGW-services** | Ontvangt verrijkt token en autoriseer op BSN/KVK |

---

## Relatie met eHerkenning (ondernemers)

Voor ondernemers verloopt het proces identiek, maar met KVK-nummer in plaats van BSN. eHerkenning is het authenticatiemiddel; de Keycloak-broker voegt het KVK-nummer toe tijdens de token exchange.

---

> **Technische configuratie**: De concrete configuratie van Keycloak (clients, mappers, policies) valt buiten de scope van deze documentatie. Raadpleeg de [Helm Chart](https://github.com/nl-portal/helm-charts) voor deployment-specifieke configuratie.
