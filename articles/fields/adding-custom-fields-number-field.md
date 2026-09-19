<!--
{
    "source": "https://docs.joomla.org/localhost",
    "title": "Getalveld",
    "description": " ",
    "author": ""
}
-->

## Doel

Het getalveld biedt een methode om een reëel getal in te voeren, met de optie om vóór of na het getal een valuta- of ander symbool toe te voegen. Het besturingselement kan worden gebruikt als een geheel-getalveld met pijlen voor verhogen en verlagen, met een standaardbereik van 1 tot 100. Er kunnen echter ook reële waarden, positief of negatief, in het veld worden ingevoerd. Voorbeeld: `99.99` kan zo worden opgemaakt dat het voor de eindgebruiker wordt weergegeven als `£99.99`. Of `-273.15` kan voor de eindgebruiker worden weergegeven als `-273.15C`.

## Veld maken

### Tabblad Algemeen

![Aanmaken van een getalveld](../../../en/images/fields/adding-custom-fields-number-field/01-fields-number-edit.png)

- **Type** Getal, dat na selectie niet kan worden gewijzigd.
- **Name** De unieke naam van het veld.
- **Label** Een vertaalbaar label voor het veld.
- **Description** Een optionele vertaalbare veldbeschrijving.
- **Required** Stel in op *Ja* als dit veld verplicht is?
- **Only Use in Subform** *Ja of *Nee*.
- **Default Value** Een optionele standaardwaarde.
- **Minimum** De minimumwaarde die kan worden gekozen met de pijlen omhoog/omlaag; de standaardwaarde is 1. Dit kan een negatief getal zijn, dus stel dit in op een waarde lager dan het laagste verwachte getal, **anders kan het selecteren van de pijl omlaag het bestaande getal wissen**.
- **Maximum** De maximumwaarde die kan worden gekozen met de pijlen omhoog/omlaag; de standaardwaarde is 100. Stel dit in op een waarde hoger dan het hoogste verwachte getal, **anders kan het selecteren van de pijl omhoog het bestaande getal wissen**.
- **Stapgrootte** De grootte van de verhoging of verlaging die met de pijlen omhoog/omlaag aan de huidige veldwaarde wordt toegevoegd of ervan wordt afgetrokken. Dit kan een geheel getal zijn, de standaardwaarde is 1, of een decimaal getal zoals 0.01. **Stel deze in op de kleinste hoeveelheid waarmee u de waarde wilt verhogen of verlagen**.
- **Opmaken als valuta** Als deze optie is geselecteerd, zijn er aanvullende velden:
    - **Valutasymbool** Dit kan één symbool zijn, zoals `£` of `$`, of een tekenreeks, zoals `&deg;C`, die wordt weergegeven als *&deg;C*.
    - **Positie van symbool** Selecteer *Voor* of *Na* het getal.
    - **Aantal decimalen** Gewoonlijk 2 voor valuta, maar in andere contexten kan dit ook een andere waarde zijn.

### Tabblad Opties

#### Paneel Formulieropties:

- **Placeholder**  Plaatshoudertekst die in het veld wordt weergegeven als hint voor de gebruiker voor de vereiste invoer.
- **Veldklasse**  Een optionele klasse die aan het gegevensinvoerformulier wordt toegevoegd.
- **Labelklasse**  Een optionele klasse die aan het label van het gegevensinvoerformulier wordt toegevoegd.
- **Bewerkbaar in**  Toegestane bewerkingsinterfaces: *Site*, *Beheerder* of *Beide*.
- **Showon-kenmerk**  Het veld voorwaardelijk weergeven of verbergen, afhankelijk van de waarde van andere velden.

#### Paneel Weergaveopties:

- **Weergaveklasse** De klasse van de veldcontainer in de uitvoer.
- **Waardeklasse** De klasse van de veldwaarde in de uitvoer.
- **Label** *Tonen* of *Verbergen* van het label in de uitvoer. Als dit is ingesteld op Tonen:
    - **Labelklasse (uitvoer)** Een klasse voor het uitvoerlabel.
- **Automatische weergave** Of en waar het veld moet worden weergegeven:
    - **Na titel**
    - **Vóór weergegeven inhoud**
    - **Na weergegeven inhoud**
    - **Niet automatisch weergeven**
- **Voorvoegsel** Tekst die vóór de veldwaarde wordt weergegeven.
- **Achtervoegsel** Tekst die na de veldwaarde wordt weergegeven.
- **Indeling** Een lijst met beschikbare indelingen.
- **Weergeven in alleen-lezenmodus** Keuze uit *Overnemen*, *Ja* of *Nee*.

#### Paneel Slim zoeken

- **Zoekindex** Keuze of er moet worden gezocht en welke zoekmethode moet worden gebruikt.

### Tabbladen Publicatie en machtigingen

De inhoud van deze tabbladen spreekt voor zich en wordt elders behandeld.

## Gegevensinvoer

Gegevensinvoer: typ eenvoudig de gewenste waarde in. Dit voorbeeld toont het kookpunt van argon:

![Gegevensinvoer in een nummerveld](../../../en/images/fields/adding-custom-fields-number-field/02-fields-number-data-entry.png)

**Let op:** als het ingevoerde getal buiten het minimum- en maximumbereik valt dat is ingesteld in de opties voor het aanmaken van het veld, geeft een browserlabel bij aanwijzen met de muis dit aan, maar de verstrekte informatie wordt niet afgedwongen. U kunt een getal buiten het bereik invoeren en het wordt geaccepteerd.

## Gegevensweergave

De volgende afbeelding toont de weergave van een item met een negatieve waarde:

![Weergave van een nummerveld op de site](../../../en/images/fields/adding-custom-fields-number-field/03-fields-number-site.png)

*Vertaald door openai.com*