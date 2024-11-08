<!-- Filename: J3.x:Adding_custom_fields/Sql_Field / Display title: SQL Veld -->

## Doel

Het SQL-veld biedt een dropdownlijst van invoerwaarden verkregen via een databasequery. Om dit veld te gebruiken, moet je weten hoe je een query moet opstellen en kun je deze testen in phpMyAdmin.


## Veldcreatie

Speciale opties binnen dit veld zijn:

- **Meerdere** Sta toe dat meerdere waarden worden geselecteerd. Als ingesteld op *Ja* toont de lijst 4 items. Anders toont het 1 item. In beide gevallen is er een lange lijst om doorheen te scrollen voor het maken van selecties - indien geactiveerd.
- **Query** De SQL-query die de gegevens voor de vervolgkeuzelijst zal leveren. De query moet twee kolommen retourneren; één genaamd 'value' die de waarden van de lijstitems bevat; de andere genaamd 'text' met de tekst in de vervolgkeuzelijst.

In dit voorbeeld wordt een tabel gebruikt met een lijst van landnamen. Dit is de query:
```
SELECT `id` AS value, `title` AS text
FROM `#__countrybase_countries`
WHERE `state` = 1
ORDER BY `title` ASC
```
![SQL Veldcreatie](../../../en/images/fields/fields-sql-edit.png)

**Opmerking:** In dit voorbeeld is het opnemen van het veldtype in de titel alleen voor demonstratiedoeleinden. Laat het weg in je eigen veldtitels.

## Gegevensinvoer

Eenvoudig - selecteer uit de lijst.

![SQL veldgegevensinvoer](../../../en/images/fields/fields-sql-data-entry.png)

## Gegevensweergave

De volgende schermafbeelding van de site toont het veld dat in een artikel wordt weergegeven. De optie *Automatische weergave* is verantwoordelijk voor de positie van het veld en jouw template is verantwoordelijk voor het ontwerp van het veld.

![SQL veld site weergave](../../../en/images/fields/fields-sql-site.png)

De output is een enkel item of een door komma's gescheiden lijst van items (landennamen) na het veldlabel (Land van herkomst).

*Vertaald door openai.com*

