<!-- Filename: J3.x:Adding_custom_fields/Sql_Field / Display title: Toevoegen extra velden/SQL veld -->

## SQL veld

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

### SQL

Biedt een drop-down lijst met items verkregen door het uitvoeren van een
query op de Joomla Database. De resultaten van de eerste kolom die door
de query worden geretourneerd, bevatten de waarden voor de drop-down
lijst.

#### Opties

Speciale opties binnen dit veld zijn:

- Meerdere
  Sta toe dat meerdere waarden geselecteerd worden - Indien geactiveerd.
- Query
  De SQL query die de gegevens voor de drop-down lijst levert. De query
  moet twee kolommen teruggeven; één genaamd 'value' welke de waarden
  van de items in de lijst bevat; de andere genaamd 'text' die de tekst
  in de drop-down lijst bevat. Als u een standaardwaarde wilt gebruiken
  dan moet u de 'value' als standaard gebruiken.

#### Verwante Informatie

Zie  SQL formulier
veldtype

#### Schermafbeeldingen

##### Het veld aanmaken

Laten we zeggen dat u een veld maakt met de opties weergegeven in de
volgende afbeelding.

<img
src="https://docs.joomla.org/images/thumb/0/06/Sql_field_create-nl.png/800px-Sql_field_create-nl.png"
decoding="async"
srcset="https://docs.joomla.org/images/0/06/Sql_field_create-nl.png 1.5x"
data-file-width="1154" data-file-height="946" width="800" height="656"
alt="Sql field create-nl.png" />

##### Het veld in het beheergedeelte gebruiken

In het beheergedeelte ziet u het veld bij het aanmaken van een artikel
of contactpersoon als in de volgende afbeeldingː

<img
src="https://docs.joomla.org/images/thumb/5/57/Sql-nl.png/800px-Sql-nl.png"
decoding="async"
srcset="https://docs.joomla.org/images/5/57/Sql-nl.png 1.5x"
data-file-width="1157" data-file-height="946" width="800" height="654"
alt="Sql-nl.png" />

##### Het veld op de website gebruiken

Op de website kunt u het veld zien zoals op de volgende afbeelding. De
optie *Automatisch tonen* is verantwoordelijk voor de positie van het
veld en uw template is verantwoordelijk voor het ontwerp van het veld.
Velden worden alleen getoond op de website als er in het artikel
gegevens in staan. Als het geen verplicht veld is kunt u dat vergetenǃ

<img
src="https://docs.joomla.org/images/thumb/3/37/Sql_field_frontend-nl.png/800px-Sql_field_frontend-nl.png"
decoding="async"
srcset="https://docs.joomla.org/images/3/37/Sql_field_frontend-nl.png 1.5x"
data-file-width="1070" data-file-height="655" width="800" height="490"
alt="Sql field frontend-nl.png" />

<a
href="https://docs.joomla.org/J3.x:Adding_custom_fields/Repeatable_Field"
id="content-button" class="button expand success">Vorig: Herhalend
veld</a>
<a href="https://docs.joomla.org/J3.x:Adding_custom_fields/Text_Field"
id="content-button" class="button expand">Volgende: Tekst veld</a>
