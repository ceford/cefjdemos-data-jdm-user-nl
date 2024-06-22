<!-- Filename: J3.x:Adding_custom_fields/Calendar_Field / Display title: Toevoegen extra velden/Kalender veld -->

## Kalender veld

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

## Het kalender veld

Biedt een tekstvak voor het invoeren van een datum. Een pictogram naast
het tekstvak bevat een link naar een pop-up kalender, die ook kan worden
gebruikt om de datum in te voeren.

#### Opties

Als u de standaard tijd gebruikt: De waarde kan een ISO 8601 formaat
(YYYY-MM-DD HH:MM:SS) zijn of NOW, wat de actuele datum toont. **Let
op**: Zelfs als u de de tijd niet definieert in de standaard datum, dan
nog wordt de tijd getoond als de optie *Toon tijd* actief is.
Speciale opties binnen dit veld zijn:

- Toon tijd
  Indien ingeschakeld verwacht het kalender veld een datum en tijd en
  zal ook de tijd tonen. De formaten zijn gelokaliseerd met behulp van
  de reguliere taal-strings.

#### Verwante Informatie

Zie:

-  Kalender formulier
  veldtype
- <a href="http://php.net/manual/en/datetime.formats.date.php"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">Datum formaten</a>

#### Schermafbeeldingen

##### Het veld aanmaken

Laten we zeggen dat u een veld maakt met de opties weergegeven in de
volgende afbeelding.

<img
src="https://docs.joomla.org/images/thumb/8/80/Calendar_field_create-nl.png/670px-Calendar_field_create-nl.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/8/80/Calendar_field_create-nl.png/1005px-Calendar_field_create-nl.png 1.5x, https://docs.joomla.org/images/8/80/Calendar_field_create-nl.png 2x"
data-file-width="1159" data-file-height="944" width="670" height="546"
alt="Calendar field create-nl.png" />

##### Het veld in het beheergedeelte gebruiken

In het beheergedeelte ziet u het veld bij het aanmaken van een artikel
of contactpersoon als in de volgende afbeeldingː

<img
src="https://docs.joomla.org/images/thumb/a/a2/Calendar-nl.png/670px-Calendar-nl.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/a/a2/Calendar-nl.png/1005px-Calendar-nl.png 1.5x, https://docs.joomla.org/images/a/a2/Calendar-nl.png 2x"
data-file-width="1157" data-file-height="947" width="670" height="548"
alt="Calendar-nl.png" />

##### Het veld op de website gebruiken

Op de website kunt u het veld zien zoals op de volgende afbeelding. De
optie *Automatisch tonen* is verantwoordelijk voor de positie van het
veld en uw template is verantwoordelijk voor het ontwerp van het veld.
Velden worden alleen getoond op de website als er in het artikel
gegevens in staan. Als het geen verplicht veld is kunt u dat vergetenǃ

<img
src="https://docs.joomla.org/images/thumb/0/07/Calendar_field_frontend-nl.png/670px-Calendar_field_frontend-nl.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/0/07/Calendar_field_frontend-nl.png/1005px-Calendar_field_frontend-nl.png 1.5x, https://docs.joomla.org/images/0/07/Calendar_field_frontend-nl.png 2x"
data-file-width="1024" data-file-height="639" width="670" height="418"
alt="Calendar field frontend-nl.png" />

<a
href="https://docs.joomla.org/J3.x:Adding_custom_fields/Parameters_for_all_Custom_Fields"
id="content-button" class="button expand success">Vorig: Parameters voor
alle extra velden</a> <a
href="https://docs.joomla.org/J3.x:Adding_custom_fields/Checkboxes_Field"
id="content-button" class="button expand">Volgende: Selectievakjes
veld</a>
