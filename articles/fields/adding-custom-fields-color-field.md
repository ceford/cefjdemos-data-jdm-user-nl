<!-- Filename: J3.x:Adding_custom_fields/Color_Field / Display title: Kleurveld -->

## Doel

Het kleurveld biedt een selectiehulpmiddel voor het visueel selecteren van een kleur. Het veld toont de resulterende hex-waarde.


## Veldaanmaak

Speciale opties voor dit veld:

- **Veldklasse** Instellen op *w-auto* om het veld net breed genoeg te maken voor de kleurstaal en waarde.

![Kleur veld aanmaken](../../../en/images/fields/fields-colour-edit.png)

**Opmerking:** In dit voorbeeld is het opnemen van het veldtype in de titel enkel voor demonstratiedoeleinden. Laat het weg in je eigen veldtitels.

## Gegevensinvoer

Je kunt een hex kleurwaarde typen als je weet dat hex getallen van 0 tot 9 lopen en daarna van a tot f, en de paren van getallen staan voor rood, groen en blauw. Dus #00ff00 is geen rood, maximaal groen en geen blauw. Of je kunt een cursor gebruiken om een kleur visueel te selecteren.

![Kleurveld gegevensinvoer](../../../en/images/fields/fields-colour-data-entry.png)


## Gegevensweergave

De volgende schermafbeelding van de site toont het veld dat in een artikel wordt weergegeven. De optie *Automatische weergave* is verantwoordelijk voor de positie van het veld en je template is verantwoordelijk voor het ontwerp van het veld.

De standaard gegevensweergave is de hex kleurwaarde, wat niet erg nuttig is. De eenvoudige oplossing is om een template-override te maken voor de velden / kleur-plugin. Vervang gewoon deze regel:
```
echo htmlentities($value);
```
met deze regels:
```
$value = htmlentities($value);
echo '<span style="background-color: ' . $value . ';"> ' . $value . '</span>';
```
En de hex-waarde wordt voorafgegaan door een kleurvoorbeeld met de achtergrondkleur van de waarde.

Zoek naar het **Bloem Kleur** item.

![kleurveld siteweergave](../../../en/images/fields/fields-colour-site.png)

