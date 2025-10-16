# NL-Portal 2.0.0

## Features

- Updated several dependencies
- Implemented new `haalcentraal2` module. This provides functionality for interacting with HaalCentraal BRP 2.0 and
  Bewoningen APIs
- Added full support for NL Portal Configuration Panel 1.0
- Added feature toggle environment variable in the frontend to toggle between using OpenKlant 1 and OpenKlant 2. env
  var: `OPEN_KLANT_VERSION`
- Expanded OpenKlant2 functionality with support:
    - Searching for a specific `DigitaleAdres`
    - Search for all `KlantContactmomenten` of a Partij
    - The ability to add a note to a `DigitaleAdres`
    - A `Partij` is now created when one does not yet exist when attempting to create a `DigitaleAdres`
- Expanded OpenZaak functionality:
    - It is now possible to exclude Zaken from being shown by a ZaakType. New `zaakTypesIdsExcluded` configuration
      property: list of UUIDs to be included from getZaken query.
- Added an idle timer and logout warning popup to the frontend.
- UI Improvements:
    - User information page has been redesigned to support showing information from OpenKlant 2.0, HaalCentraal BRP 2.0
      and HaalCentraal Bewoningen.
    - Various components have improved styling and usability. 

## Bugfixes

Er zijn geen bugfixes

## Breaking changes

- Configuration Properties for NL Portal have changed. Configuration is now grouped by feature and contains a toggle.
  See [#393](https://github.com/nl-portal/nl-portal-backend-libraries/pull/393/files) for example.
- Moved away from the Keycloak js adapter for authentication in favor
  of react-oidc-context [#276](https://github.com/nl-portal/nl-portal-frontend-libraries/pull/276). It is now possible
  to use NL Portal with any OIDC compliant identity provider.

## Deprecations

Er zijn geen deprecations

## Bekende problemen

Er zijn geen bekende problemen
