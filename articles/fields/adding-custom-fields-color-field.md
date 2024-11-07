<!-- Filename: J3.x:Adding_custom_fields/Color_Field / Display title: Kleurveld -->

## Doel

Het kleurveld biedt een kiezer voor de visuele selectie van een kleur. Het veld toont de resulterende hex-waarde.

## Veldcreatie

Speciale opties voor dit veld:

- **Veldklasse** Instellen op *w-auto* om het veld precies breed genoeg te maken voor de staal en waarde.

## Gegevensinvoer

Je kunt een hexadecimale kleurwaarde typen als je weet dat hexadecimale getallen van 0 tot 9 lopen en daarna van a tot f. De paren van getallen staan voor rood, groen en blauw. Dus #00ff00 is geen rood, maximaal groen en geen blauw. Of je kunt een cursor gebruiken om een kleur visueel te selecteren.

![Kleurkiezer](../../../en/images/fields/fields-colour-entry.png "Kleurkiezer")

## Gegevensweergave

De volgende screenshot van de site toont het veld dat in een artikel wordt weergegeven. De optie *Automatische weergave* is verantwoordelijk voor de positie van het veld en je sjabloon is verantwoordelijk voor het ontwerp van het veld.

De standaard gegevensweergave is de hexadecimale kleurwaarde, wat niet erg nuttig is. De eenvoudige oplossing is om een sjabloonoverride voor de velden/kleurplug-in te maken. Vervang gewoon deze regel:
```
echo htmlentities($value);
```
met deze regels:
```
$value = htmlentities($value);
echo '<span style="background-color: ' . $value . ';"> ' . $value . '</span>';
```
En de hexwaarde zal worden voorafgegaan door een kleurstaal met de achtergrondkleur van de waarde.

Zoek naar het **Bloemkleur**-item.

![Weergave van alle velden](../../../en/images/fields/fields-display.png "Veldenweergave")

