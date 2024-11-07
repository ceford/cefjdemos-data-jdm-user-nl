<!-- Filename: J4.x:Template_Basics / Display title: Sjabloon Basisprincipes -->

## Inleiding

In Joomla! is een sjabloon een verzameling bestanden die samen het uiterlijk van de website bepalen. Joomla 4 biedt twee sjablonen: Atum is het Beheerderssjabloon dat wordt gebruikt voor sitebeheer; en Cassiopeia is het Sitesjabloon dat wordt gebruikt voor sitebezoekers. Veel meer sitesjablonen zijn beschikbaar van onafhankelijke leveranciers, hetzij gratis of tegen een bescheiden vergoeding. Er is zelfs een hele industrie gebaseerd op de levering van specialistische sitesjablonen.

Een typisch sitesjabloon bevat PHP-bestanden om de inhoud te ordenen en CSS-bestanden om de inhoud te stijlen. Er zijn vaak extra bestanden zoals afbeeldingen die in de opmaak worden gebruikt en JavaScript-bestanden die worden gebruikt om te communiceren met sitefuncties zoals links en knoppen. De volgende schermafbeelding toont de Cassiopeia-sjabloonmappen en -bestanden in een nieuwe Joomla 4-installatie:

![templates customize cassiopeia pagina](../../../en/images/templates/templates-customise-cassiopeia.png)

Let op dat de php-bestanden in de map /templates van de site staan en de mediabestanden in de map /media van de site.

## Sjabloonposities

Het sjabloon van de site definieert de posities van de hoofdinhoud, bijvoorbeeld een individueel artikel of een blogindeling van aanbevolen artikelen, en eventuele modules die boven, onder, links of rechts van de hoofdinhoud moeten worden weergegeven. De volgende illustratie toont de beschikbare posities in Cassiopeia:

![sjabloonposities diagram](../../../en/images/templates/cassiopeia-template-positions.png)

Ook kunt u de sjabloonposities in elk sjabloon bekijken door Voorvertoning Moduleposities in te schakelen in het Sjabloon: Opties-formulier en vervolgens ?tp=1 aan de url toe te voegen. Als er al een querystring aan de url is toegevoegd, voeg dan in plaats daarvan &tp=1 toe.

## Gebruikersstyling

Cassiopeia heeft enkele opties die je kunt wijzigen om het uiterlijk van de site aan te passen
(er is een apart artikel over Cassiopeia-aanpassing). Dat kan misschien niet
voldoende zijn voor jouw doeleinden. Je kunt je eigen wijzigingen aan het uiterlijk maken
met een user.css-stylesheet. Je moet deze zelf maken in het
Formulier:Sjablonen aanpassen. Selecteer gewoon Nieuw bestand en voer Bestandsnaam in:
user, selecteer Bestandstype: .css, en selecteer css uit de lijst met mappen.
Selecteer vervolgens het nieuw aangemaakte user.css-bestand in het Bewerken-formulier en voer
enkele stijlen in, bijvoorbeeld om koppen donkergroen te maken:
```css
    h1, h2, h3, h4, h5, h6 {
      color: darkgreen;
    }
```

## Sjabloonoverschrijvingen

Naast de algemene lay-out die door het sitesjabloon wordt bepaald, heeft elk component of elke module een sjabloon om het uiterlijk binnen de algemene lay-out te definiëren. Dergelijke sjablonen bevinden zich in een tmpl-map binnen het component of de module. Sommige plugins hebben ook sjablonen. En er zijn lay-outs die vanuit elk type extensie kunnen worden aangeroepen.

Soms is een van deze *extensie*-sjablonen niet helemaal naar wens. In dat geval kunt u een sjabloonoverschrijving maken. Dit is een kopie van de code die wordt gebruikt om de extensielay-out te genereren, zodat u deze naar eigen inzicht kunt wijzigen. De volgende schermafbeelding toont het sjabloon: Aangepaste Overschrijvingen maken formulier:

![sjabloon overschrijvingen](../../../en/images/templates/cassiopeia-customisation-create-overrides.png)

Cassiopeia heeft al enkele overschrijvingen geïnstalleerd. Dat lijkt misschien een probleem te zijn. Als u een van de standaard Cassiopeia-bestanden wijzigt, worden uw wijzigingen bij de volgende Joomla-update overschreven (en dus verloren). De oplossing is kind-sjablonen.

## Alternatieve Layouts

Een sjabloon, of een sjabloonoverschrijving, definieert de uitstraling van een extensie in een specifiek bestand, zoals default.php. In sommige gevallen wil je misschien kiezen tussen de standaardlayout en een alternatieve layout. Bijvoorbeeld, een menu in een bovenpositie heeft meestal een andere layout nodig dan hetzelfde menu in een zijpositie. In een menumodule is er een Layout-parameter in het tabblad Geavanceerd van het modulebewerkingsformulier, waarmee je kunt kiezen uit beschikbare alternatieve layouts. Er is een apart tutorial over Alternatieve Layouts voor Sjablonen.

## Kindsjablonen

Een kindsjabloon gebruikt de bestanden in zijn oudersjabloon, behalve voor bestanden die in het kindsjabloon aanwezig zijn. Je zou bijvoorbeeld verschillende user.css-bestanden in de ouder en het kind kunnen hebben, zodat verschillende pagina's verschillende kleurenschema's kunnen hebben. Of je zou het index.php-bestand van de ouder naar het kind kunnen kopiëren en het kind aanpassen om een andere lay-out te creëren dan de ouder. Er is een aparte handleiding over kindsjablonen.

*Vertaald door openai.com*

