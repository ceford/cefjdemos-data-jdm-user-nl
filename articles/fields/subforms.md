<!-- Filename: jdocmanual?manual=user&heading=fields&filename=subform.md / Display title: Subformulier Veld   -->

## Doel

Het Subform Field maakt het mogelijk om een selectie van velden samen te groeperen in een herhaalbare lijst.

## Veldcreatie

Maak eerst de benodigde velden in het subformulier aan. In het hier beschreven voorbeeld is er een Kalenderveld (Verwervingsdatum), een Tekstveld (Prijs) en een Kleurveld (Bloemkleur) die worden gebruikt voor een lijst van verschillende exemplaren.

**Bug:** Er zit een bug in de code van het Kalenderveld die leidt tot een fatale fout bij het voor de tweede keer opslaan van een artikel. Om dit probleem te voorkomen, stel de *Tijd Weergeven* waarde van het Kalenderveld in op *Ja*.

Speciale opties voor dit veld:

- **Titel** en **Label** In dit voorbeeld zijn deze ingesteld op *Exemplaren*.
- **Velden** Voeg de benodigde velden één voor één toe in het subformulier. Elke rij heeft een dropdownlijst van beschikbare velden en een Weergeef Waarden Ja/Nee-schakelaar. De volgorde van de items kan worden gewijzigd met het sleepicoon.

![Subformulier creatie](../../../en/images/fields/fields-subform.png "Subformulier creatie")

## Gegevensinvoer

In het gegevensinvoerformulier moet je rijen toevoegen voor elk specimen. Elke rij bevat een Kalender-veld, een Tekstveld en een Kleurveld.

![Subformulier gegevensinvoer](../../../en/images/fields/fields-subform-entry.png "Subformulier gegevensinvoer")

## Gegevensweergave

In het artikel heeft het subformulier met de titel Exemplaren één rij voor elk exemplaar.
Zoek naar het **Exemplaren** item in deze schermafbeelding:

![Weergave van alle velden](../../../en/images/fields/fields-display.png "Velden weergave")

*Vertaald door openai.com*

