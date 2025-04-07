# NL-Portal 1.5.1

## Bugfixes

The following has been fixed:
* **Limiting returned zaken by vestigingsnummer**  
    ZakenAPI Client now correctly searches for cases based on a vestigingsnummer and kvk, when the authentication used
    is of type `BedrijfAuthentication` and the token claims contain a `vestigingsnummer`.

## Breaking changes

Er zijn geen breaking changes

## Deprecations

Er zijn geen deprecations

## Bekende problemen

Er zijn geen bekende problemen
