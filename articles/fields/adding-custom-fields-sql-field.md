<!-- Filename: J3.x:Adding_custom_fields/Sql_Field / Display title: SQL Veld -->

## Doel

Het SQL-veld biedt een uitklaplijst van items verkregen uit een databasequery. Om dit veld te gebruiken, moet je weten hoe je een query opstelt en je moet deze testen in phpMyAdmin.


## Veldcreatie

Speciale opties binnen dit veld zijn:

- **Meerdere** Sta toe dat meerdere waarden worden geselecteerd. Als dit op *Ja* is ingesteld, worden er 4 items in de lijst weergegeven. Anders wordt er 1 item weergegeven. In beide gevallen is er een lange lijst om doorheen te scrollen om selecties te maken - indien geactiveerd.
- **Query** De SQL-query die de gegevens voor de vervolgkeuzelijst zal leveren. De query moet twee kolommen retourneren; één genaamd 'value' die de waarden van de lijstitems zal bevatten; de andere genaamd 'text' die de tekst in de vervolgkeuzelijst bevat.

In dit voorbeeld wordt een tabel gebruikt met een lijst van landnamen. Dit is de query:
```
SELECT `id` AS value, `title` AS text
FROM `#__countrybase_countries`
WHERE `state` = 1
ORDER BY `title` ASC
```
![SQL Veld](../../../en/images/fields/fields-sql.png "SQL Veld")

## Gegevensinvoer

Simpel - selecteer uit de lijst.


## Gegevensweergave

De volgende schermafbeelding van de site toont het veld dat in een artikel wordt weergegeven. De optie *Automatische weergave* is verantwoordelijk voor de positie van het veld en je sjabloon is verantwoordelijk voor het ontwerp van het veld.

Zoek naar het item **Land van herkomst**.

![Weergave van alle velden](../../../en/images/fields/fields-display.png "Velden weergave")

De output is een enkel item of een door komma's gescheiden lijst van items (landnamen) volgend op het veldlabel (Land van herkomst).

*Vertaald door openai.com*

