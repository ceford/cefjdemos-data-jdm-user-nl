<!-- Filename: J3.x:Adding_custom_fields/Url_Field / Display title: Toevoegen extra velden/URL veld -->

## URL veld

**Artikelen in deze reeks**

1.  Inleiding
2.   Parameters voor alle extra
    velden
3.   Kalender
    veld
4.   Selectievakjes
    veld
5.   Kleur
    veld
6.   Tekstverwerker
    veld
7.   Integer
    veld
8.   Lijst
    veld
9.   Lijst met afbeeldingen
    veld
10.  Media
    veld
11.  Keuzerondje
    veld
12.  Herhalend
    veld
13.  SQL
    veld
14.  Tekst
    veld
15.  Tekstvak
    veld
16.  URL
    veld
17.  Gebruiker
    veld
18.  Gebruikersgroep
    veld
19.  Hoe kunt u extra velden
    groeperen
20.  Welke componenten ondersteunen extra
    velden
21.  Implementatie in uw
    component
22.  Extra velden gebruiken in uw
    overrides

### URL

Biedt een URL-invoerveld.

#### Opties

Speciale opties bij dit veld zijn:

- Schema's
  De toegestane schema's zijn HTTP, HTTPS, FTP, FTPS, MAILTO, URL en
  FILE. Dit extra veld is in wezen een tekst veld met het type URL in
  het beheergedeelte bij het aanmaken van een artikel, contactpersoon of
  component van derden die extra velden ondersteunt. Het is alleen
  mogelijk een volledige URL in te voeren - dat is er een met schema en
  domeinnaam zoals `http://voorbeeld.com`. De URL wordt vertaald naar
  <a href="https://en.wikipedia.org/wiki/Punycode" class="external text"
  target="_blank" rel="nofollow noreferrer noopener">punycode</a> voor
  het opslaan. Dit zorgt ervoor dat de URL werkt zoals bedoelt, ongeacht
  de omgeving.
- Relatief
  Gebruik deze optie om te bepalen of al dan niet relatieve URL's
  toegestaan zijn.

#### Verwante Informatie

Zie  URL formulier
veldtype

#### Schermafbeeldingen

##### Het veld aanmaken

Laten we zeggen dat u een veld maakt met de opties weergegeven in de
volgende afbeelding.

<img
src="https://docs.joomla.org/images/thumb/c/cd/Url_field_create-nl.png/800px-Url_field_create-nl.png"
decoding="async"
srcset="https://docs.joomla.org/images/c/cd/Url_field_create-nl.png 1.5x"
data-file-width="1161" data-file-height="947" width="800" height="653"
alt="Url field create-nl.png" />

##### Het veld in het beheergedeelte gebruiken

In het beheergedeelte ziet u het veld bij het aanmaken van een artikel
of contactpersoon als in de volgende afbeeldingː

<img
src="https://docs.joomla.org/images/thumb/e/ed/URL-nl.png/800px-URL-nl.png"
decoding="async"
srcset="https://docs.joomla.org/images/e/ed/URL-nl.png 1.5x"
data-file-width="1157" data-file-height="943" width="800" height="652"
alt="URL-nl.png" />

##### Het veld op de website gebruiken

Op de website kunt u het veld zien zoals op de volgende afbeelding. De
optie *Automatisch tonen* is verantwoordelijk voor de positie van het
veld en uw template is verantwoordelijk voor het ontwerp van het veld.
Velden worden alleen getoond op de website als er in het artikel
gegevens in staan. Als het geen verplicht veld is kunt u dat vergetenǃ

<img
src="https://docs.joomla.org/images/thumb/f/fe/Url_field_frontend-nl.png/800px-Url_field_frontend-nl.png"
decoding="async"
srcset="https://docs.joomla.org/images/f/fe/Url_field_frontend-nl.png 1.5x"
data-file-width="1066" data-file-height="648" width="800" height="486"
alt="Url field frontend-nl.png" />

<a
href="https://docs.joomla.org/J3.x:Adding_custom_fields/Textarea_Field"
id="content-button" class="button expand success">Vorig: Tekstvak
veld</a>
<a href="https://docs.joomla.org/J3.x:Adding_custom_fields/User_Field"
id="content-button" class="button expand">Volgende: Gebruiker veld</a>
