<!-- Filename: J3.x:Adding_custom_fields/Calendar_Field / Display title: Kalenderveld -->

## Doel

Het kalenderveld biedt een tekstvak voor het invoeren van een datum. Een pictogram naast het tekstvak opent een pop-up kalenderkiezer, waarmee een datum uit een grafische kalender kan worden geselecteerd.

## Veldcreatie

Algemene veldparameters worden in een apart artikel beschreven.

* **Titel** U kunt meerdere datumvelden in een artikel hebben, dus zorgvuldigheid is geboden bij het instellen van de titel om dubbelzinnigheid in de uitvoer te voorkomen.
* **Label** Dit is wat in de uitvoer wordt weergegeven. Als het leeg wordt gelaten, wordt het ingesteld op basis van de inhoud van het Titelveld, maar het kan worden aangepast.
* **Tijd weergeven** Als dit is ingesteld op *Ja*, wordt de tijd toegevoegd aan het datumveld, de datumkiezer en de uitvoerdatum. **Let op**: Zelfs als u de tijd niet opgeeft in de standaarddatum, wordt de tijd weergegeven wanneer de optie *Tijd weergeven* actief is.
* **Plaatshouder** Dit bevindt zich op het tabblad Opties. Het kan worden ingesteld op een datumformaat zoals *JJJJ-MM-DD* om gebruikers eraan te herinneren welk formaat vereist is en/of als geheugensteun waar de datum voor dient, zoals *Aankomstdatum*.

![kalender veldcreatie](../../../en/images/fields/fields-calendar-edit.png)

**Opmerking:** In dit voorbeeld is de opname van het veldtype in de Titel alleen voor demonstratiedoeleinden. Laat het weg in uw eigen veldtitels.

## Gegevensinvoer

In gebruik is het Kalenderveld eenvoudig. Je kunt de datum in het vereiste formaat typen of een datum selecteren met de datumkiezer. Zorgvuldigheid is geboden bij het typen van datums. Een fout in de datum wordt bij het opslaan gecorrigeerd naar een nieuwe datum. Bijvoorbeeld, een datum van 2024-14-02 wordt gecorrigeerd naar 2025-02-02.

De volgende schermafbeelding toont een Aankoopdatum:

![kalenderveld gegevensinvoer](../../../en/images/fields/fields-calendar-data-entry.png)

Velden verschijnen alleen in een artikel als ze zijn ingevuld in het gegevensinvoervormulier van het artikel.


## Gegevensweergave

De volgende screenshot van de site toont het veld dat in een artikel wordt weergegeven. De optie *Automatische weergave* is verantwoordelijk voor de positie van het veld en je sjabloon is verantwoordelijk voor het ontwerp van het veld.

![kalenderveld siteweergave](../../../en/images/fields/fields-calendar-site.png)

De datumnotaties worden gelokaliseerd met behulp van taalstrings.

