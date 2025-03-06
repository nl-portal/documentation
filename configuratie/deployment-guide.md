---
description: >-
  Met deze stappen is moet het mogelijk worden om je NL Portal app te deployen
  naar je gewenste omgeving, mocht dat Azure, AWS of een Kubernetes cluster
  zijn.
---

# Deployment guide

### Frontend environment properties

Hieronder zijn environment properties de gewijzigd kunnen worden in de frontend.

|                                           |                            |
| ----------------------------------------- | -------------------------- |
| KEYCLOAK\_URL                             | Keycloak URL               |
| KEYCLOAK\_REALM                           | Keycloak Realm             |
| KEYCLOAK\_CLIENT\_ID                      | Keycloak Portal ClientId   |
| KEYCLOAK\_REDIRECT\_URI                   | Keycloak Redirect URL      |
| GRAPHQL\_URI                              | GraphQL URI van de backend |
| REST\_URI                                 | REST URI van de backend    |
| SHOW\_INHABITANT\_AMOUNT                  |                            |
| SHOW\_ADDRESS\_AMOUNT                     |                            |
| ADDRESS\_RESEARCH\_URL                    |                            |
| ACCOUNT\_SHOW\_NOTIFICATION\_SUBSECTION   |                            |
| OVERVIEW\_SHOW\_INTRO                     |                            |
| OVERVIEW\_SHOW\_MAINTENANCE\_ALERT        |                            |
| OVERVIEW\_SHOW\_CURRENT\_CASES\_PREVIEW   |                            |
| OVERVIEW\_CURRENT\_CASES\_PREVIEW\_LENGTH |                            |
| THEME\_CLASS                              |                            |

### Backend environment properties

Hieronder zijn backend environment properties die gewijzigd kunnen worden.

|                                                                            |                                                   |
| -------------------------------------------------------------------------- | ------------------------------------------------- |
| SPRING\_DATASOURCE\_URL                                                    | Postgresql database URL                           |
| SPRING\_DATASOURCE\_USERNAME                                               | Username datasource                               |
| SPRING\_DATASOURCE\_PASSWORD                                               | Password datasource                               |
| SPRING\_SECURITY\_OAUTH2\_RESOURCESERVER\_JWT\_ISSUER-URI                  | URL JWT Issuer URI van Keycloak                   |
| KEYCLOAK\_RESOURCE                                                         | De clientId van de M2M client                     |
| KEYCLOAK\_AUDIENCE                                                         | De clientId van de token exchange client          |
| KEYCLOAK\_CREDENTIALS\_SECRET                                              | Het secret van de M2M client                      |
| NL-PORTAL\_ZGW\_CATALOGIAPI\_URL                                           | Openzaak Base URL                                 |
| NL-PORTAL\_ZGW\_CATALOGIAPI\_CLIENTID                                      | Openzaak ClientID voor NL Portal                  |
| NL-PORTAL\_ZGW\_CATALOGIAPI\_SECRET                                        | Openzaak Secret voor NL Portal                    |
| NL-PORTAL\_ZGW\_ZAKENAPI\_URL                                              | Openzaak Base URL                                 |
| NL-PORTAL\_ZGW\_ZAKENAPI\_CLIENTID                                         | Openzaak ClientID voor NL Portal                  |
| NL-PORTAL\_ZGW\_ZAKENAPI\_SECRET                                           | Openzaak Secret voor NL Portal                    |
| NL-PORTAL\_ZGW\_TAAK\_TAAKOBJECT\_TYPEURL                                  | Objecttypes URL voor het taakobject               |
| NL-PORTAL\_ZGW\_DOCUMENTENAPIS\_DEFAULT-DOCUMENT-API                       | Naam van de standaard documenten API configuratie |
| NL-PORTAL\_ZGW\_DOCUMENTENAPIS\_CONFIGURATIONS\_\<CONFIG>\_URL             | Documenten API URL                                |
| NL-PORTAL\_ZGW\_DOCUMENTENAPIS\_CONFIGURATIONS\_\<CONFIG>\_CLIENTID        | Documenten API ClientID                           |
| NL-PORTAL\_ZGW\_DOCUMENTENAPIS\_CONFIGURATIONS\_\<CONFIG>\_SECRET          | Documenten API Secret                             |
| NL-PORTAL\_ZGW\_DOCUMENTENAPIS\_CONFIGURATIONS\_\<CONFIG>\_RSIN            | Documenten API RSIN                               |
| NL-PORTAL\_ZGW\_DOCUMENTENAPIS\_CONFIGURATIONS\_\<CONFIG>\_DOCUMENTTYPEURL | Openzaak Catalogi URL voor document               |
| NL-PORTAL\_ZGW\_OPENKLANT\_URL                                             | Openklant URL                                     |
| NL-PORTAL\_ZGW\_OPENKLANT\_CLIENTID                                        | Openklant ClientId                                |
| NL-PORTAL\_ZGW\_OPENKLANT\_SECRET                                          | Openklant Secret                                  |
| NL-PORTAL\_ZGW\_OPENKLANT\_RSIN                                            | Openklant RSIN                                    |
| NL-PORTAL\_ZGW\_OPENFORMULIEREN\_URL                                       | Openformulieren URL                               |
| NL-PORTAL\_ZGW\_OPENFORMULIEREN\_TOKEN                                     | Openformulieren Token                             |
| NL-PORTAL\_ZGW\_OBJECTSAPI\_URL                                            | Objectsapi URL                                    |
| NL-PORTAL\_ZGW\_OBJECTSAPI\_TOKEN                                          | Objectsapi Token                                  |
