# Release notes

## Nieuwe Functionaliteit

De volgende functionaliteiten zijn nieuw toegevoegd:

* **Externe-klanttaak support** Deze wijziging heeft geresulteerd in deprecated classes.\
  Zie Deprecations voor meer informatie
* **Vestigingsnummer bepaald lijst van zaken** Voor organisaties waarbij medewerkers van\
  een vestiging geen zaken van andere vestigingen mogen zien
* **Zaak informatieobject filtering**
* **Betalingen ondersteuning** Het is nu mogelijk om aanslagen te betalen en automatische\
  incasso's in te stellen
* **Notificaties worden nu weergegeven**
* **Berichten** Bied de mogelijkheid om informatieve berichten of meldingen in te zien

## Bugfixes

De volgende bugs zijn opgelost:

* **Zaken worden gepagineerd weergegeven**

## Breaking changes

Er zijn geen breaking changes

## Deprecations

De volgende classes zijn deprecated:

* Taak - Gebruik in plaats daarvan TaakV2
* TaakFormulier - Gebruik in plaats daarvan TaakFormulierV2
* TaakObject - Gebruik in plaats daarvan TaakObjectV2
* TaakMutation - Gebruik in plaats daarvan TaakMutationV2
* TaakPage - Gebruik in plaats daarvan TaakPageV2
* TaakQuery - Gebruik in plaats daarvan TaakQueryV2

## Bekende problemen

De volgende problemen zijn bekend:

* **Vestigingsnummer bepaald lijst van zaken** This feature does not work as intended yet.\
  A hotfix (version 1.5.1) will be released when it is confirmed to work properly
