<!-- Filename: J4.x:Favicons / Display title: Favicons  -->

## De Joomla! Favicons

Favicons zijn de kleine pictogrammen die in het browsertabblad naast de naam van uw site verschijnen. Bovenaan de template index.php staan drie instructies om favicons in de pagina te laden:
```php
    // Browsers ondersteunen SVG-favicons
    $this->addHeadLink(HTMLHelper::_('image', 'joomla-favicon.svg', '', [], true, 1), 'icon', 'rel', ['type' => 'image/svg+xml']);
    $this->addHeadLink(HTMLHelper::_('image', 'favicon.ico', '', [], true, 1), 'alternate icon', 'rel', ['type' => 'image/vnd.microsoft.icon']);
    $this->addHeadLink(HTMLHelper::_('image', 'joomla-favicon-pinned.svg', '', [], true, 1), 'mask-icon', 'rel', ['color' => '#000']);
```
Voor de Cassiopeia-sjabloon zal Joomla de favicons op de volgende locaties zoeken:

1.  **media/templates/site/cassiopeia/images** - als ze daar niet zijn, zal Joomla op de volgende locatie zoeken.
2.  **media/system/images** - daar zijn ze, dus Joomla zal ze daar vandaan gebruiken.

Als u uw eigen favicons wilt gebruiken in plaats van de Joomla-favicons, uploadt u ze naar de eerste locatie: **media/templates/site/cassiopeia/images**. U kunt dit doen met behulp van het sjabloon "Aanpassen" formulier. Ze zullen niet worden beïnvloed door enige update van de Cassiopeia-sjabloon.

Favicons worden soms gebruikt in grotere formaten en op andere plaatsen dan het browsertabblad. Bijvoorbeeld, dit is een screenshot van een deel van een Firefox-startpagina die enkele van de favoriete locaties van de gebruiker toont:

![faviconvoorbeelden van Firefox startpagina](../../../en/images/templates/favicons-firefox-start-collection.png)

Alle moderne browsers ondersteunen SVG-pictogrammen, dus u zou de creatie van een SVG-pictogram als prioriteit moeten stellen.

## Over SVG

SVG is een acroniem voor Scalable Vector Graphics. Een SVG-bestand bevat tekst in een formaat dat de locaties en vormen van lijnen definieert met lijnkleuren, vulkleuren enzovoort. De volgende schermafbeelding toont het bestand *joomla-favicon.svg* geopend in een teksteditor. De regelnummers worden door de teksteditor gegenereerd en zijn niet aanwezig in het bestand. De lange regels vertegenwoordigen curves en zijn hier afgebroken voor weergavedoeleinden.

![joomla favicon tekstinhoud](../../../en/images/templates/favicons-joomla-favicon-svg-text.png)

Om een SVG-bestand te maken, moet je een geschikte applicatie gebruiken, zoals Inkscape. Rastergrafische applicaties zoals Photoshop of The GIMP voldoen niet. Als je liever een pictogram ontwerpt in een rastergrafische applicatie, of je hebt een bestaand rastergrafisch logo dat kan worden aangepast voor een pictogram, kun je het resulterende PNG-bestand in Inkscape importeren en daar traceren om een SVG-bestand te produceren. De getraceerde afbeelding moet na het traceren worden verwijderd!

Het daadwerkelijk maken van een SVG-favicon valt buiten het bestek van dit artikel. Het maken van een standaard *favicon.ico* bestand vanuit een *joomla-favicon.svg* bestand is heel eenvoudig – veel sites bieden dit gratis online aan.  

## Hoe Favicons aan te Maken

Als je je eigen favicons wilt maken, is de beste manier om een SVG-favicon te maken en vervolgens een online tool te gebruiken om alle andere formaten met dat als invoer te genereren. In dit voorbeeld is er een pictogram nodig dat past bij een kindtemplate genaamd Cassiopeia Green. Een pictogram moet vierkant zijn en niet te ingewikkeld, aangezien de minimale weergavegrootte 16x16 pixels is. Sommige apparaten hebben hogere resoluties nodig, zoals 32x32 of 180x180, en Google beveelt veelvouden van 48x48 pixels aan. Als je begint met een SVG hoef je je daar geen zorgen over te maken - maak gewoon een bijna vierkant beeld met een geschikt ontwerp. In dit voorbeeld zal de favicon de letters *J4* in donkergroen zijn.

### Inkscape

Inkscape is een gratis, Open Source, cross-platform vector graphics applicatie die wordt gebruikt om met SVG-bestanden te werken. Het werkt op Linux, Mac en Windows. Ga naar de Inkscape (inkscape.org) site om een exemplaar voor jouw platform te downloaden. De volgende illustraties tonen het Inkscape-scherm halverwege de volgende instructies.

![inkscape met favicon in voorbereiding](../../../en/images/templates/favicons-inkscape-favicon.png)

### Creëer een SVG

1.  Start Inkscape en maak het venster een comfortabele grootte: selecteer Weergave / Zoom / Zoom Pagina
2.  Selecteer de Teksttool, gemarkeerd met letter A in de linker Werkbalk
3.  Selecteer Arial, Normaal, 48 en px
4.  Sleep om een vak ergens op de pagina te definiëren
5.  Typ in Tekst: J4
6.  Selecteer Weergave / Zoom Selectie
7.  Selecteer Pad / Object naar Pad - geen zichtbare verandering, maar de woorden zijn geen tekst meer
8.  Selecteer Bestand / Documenteigenschappen
9.  Selecteer Aanpassen aan Inhoud
10. Zoom uit voor een beter zicht - maar zorg ervoor dat alle letters nog steeds geselecteerd zijn
11. Stel het hoogteveld in op dezelfde waarde als het breedteveld. Typ het!
12. Sluit de Documenteigenschappen-dialoog
13. Bekijk / Zoom Pagina opnieuw - de tekens moeten gecentreerd worden
14. Bewerken / Alles selecteren
15. Objecten / Uitlijnen en Verdelen
16. Beweeg selectie als groep / Relatief tot Pagina / Centrum op horizontale as - je zou J4 naar het verticale middelpunt moeten zien bewegen
17. Selecteer de Vul- en Lijn rechts - de rechterpaneel heeft een dropdownlijst gemarkeerd met een chevron naar beneden
18. In het Vul- en Lijnpaneel, selecteer Vul en het eerste gevulde vierkant
19. Voer in het RGB-paneel 006400ff in het RGBA-veld rechtsonder in - de code voor CSS-stijl *darkgreen*
20. Bestand / Opslaan
21. Voer in de Opslag-dialoog een geschikte bestandsnaam in, bijvoorbeeld green-favicon-j4.svg
22. Selecteer een geschikte locatie, bijvoorbeeld *~/Documents/joomla-dev/svgs*
23. Selecteer Geoptimaliseerde SVG (*.svg*) in de keuzelijst onderaan het formulier.
24. Selecteer *Opslaan*
25. Selecteer *OK* voor al de Standaarden in het Geoptimaliseerde SVG Uitvoerformulier
26. Sluit de SVG waar je aan werkt - er is een mogelijkheid om de afbeelding in Inkscape-formaat op te slaan, maar dat is niet echt nodig.

### Bewerk de SVG met een Teksteditor

Start je favoriete teksteditor om enkele wijzigingen aan te brengen die in Inkscape niet mogelijk waren.

1.  Open je nieuw aangemaakte SVG-bestand - merk op dat de eerste regel een XML-specificatie is
2.  Je kunt de tweede regel verwijderen - een opmerking met Created met Inkscape
3.  Indien aanwezig, kun je de regel met verwijderen, aangezien er geen tekst is
4.  Open het originele joomla-favicon.svg-bestand - het bevindt zich in *joomla_root/media/system/images*
5.  Kopieer het stijlblok en plak het in je SVG op de regel na de SVG-verklaring
6.  Sluit het originele *joomla-favicon-svg*-bestand om te voorkomen dat er per ongeluk wijzigingen in worden aangebracht
7.  Verander in het stijlblok van je eigen SVG-bestand path {fill: \#000;} naar path {fill: \#006400;}, de waarde in de regel
8.  Verwijder *fill="#006400"* uit de regel
9.  Opslaan
10. Open de afbeelding in je browser. Voor Firefox is dat Bestand / Bestand open...

Je zou de afbeelding in je browser moeten zien. Het voorbeeld toont J4 in een vierkant van 47 pixels. De volgende stap is om de andere soorten pictogrammen te maken die je nodig hebt met je nieuw aangemaakte SVG als basis.

### Online Verwerken

Ga naar de site van de Real Favicon Generator. Andere sites zijn beschikbaar, maar deze lijkt bijzonder uitgebreid.

1.  Selecteer de knop met de tekst *Selecteer je Favicon afbeelding*
2.  De site toont je je Master Afbeelding. Het zegt ook *Jouw afbeelding is niet vierkant (688x512). We kunnen dit oplossen door transparante marges toe te voegen*
3.  Selecteer de knop *Doorgaan met deze afbeelding* onder de Master Afbeelding.
4.  Er zijn subformulieren met lichtblauwe achtergronden voor verschillende soorten pictogrammen - vul elk formulier in en controleer of de voorvertoning bij je past.
5.  Het is het beste om je aan de standaardopties van Favicon Generator te houden, tenzij je het beter weet. Behalve:
6.  Pad, selecteer de Ik kan niet ... optie en voer in: *media/templates/site/cassiopeia-green/images*
7.  Selecteer de knop *Genereer je Favicons en HTML-code*
8.  Na een korte vertraging verschijnt er een nieuw formulier, selecteer de knop Download jouw pakket: *Favicon* pakket
9.  Laat de download opslaan ...
10. Selecteer en kopieer het blok met links om ergens op te slaan.
11. Sluit de online verwerkingssite

De download is een *zip*-bestand met 10 items: *favicon.ico*, *safari-pinned-tab.svg*, zes PNG-bestanden, *browserconfig.xml* en *site.webmanifest*.

### Implementatie

Om gebruik te maken van de standaardset Joomla-favicons moet je de pictogrammen hernoemen en verplaatsen naar *joomla_root/media/templates/je-template/afbeeldingen*:

- Je master SVG-afbeelding, *green-favicon-j4.svg*, moet worden hernoemd naar *joomla-favicon.svg*
- Het gedownloade bestand *safari-pinned-tab.svg* moet worden hernoemd naar *joomla-favicon-pinned.svg*
- Het gedownloade bestand *favicon.ico* hoeft alleen maar te worden verplaatst

### Het Koppelblok

Het eerder gekopieerde koppelblok bevat:

```html
<link rel="apple-touch-icon" sizes="180x180" href="media/templates/site/cassiopeia-green/images/apple-touch-icon.png">
<link rel="icon" type="image/png" sizes="32x32" href="media/templates/site/cassiopeia-green/images/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="media/templates/site/cassiopeia-green/images/favicon-16x16.png">
<link rel="manifest" href="media/templates/site/cassiopeia-green/images/site.webmanifest">
<link rel="mask-icon" href="media/templates/site/cassiopeia-green/images/safari-pinned-tab.svg" color="#5bbad5">
<link rel="shortcut icon" href="media/templates/site/cassiopeia-green/images/favicon.ico">
<meta name="msapplication-TileColor" content="#ffc40d">
<meta name="msapplication-config" content="media/templates/site/cassiopeia-green/images/browserconfig.xml">
<meta name="theme-color" content="#ffffff">
```

Je hoeft er waarschijnlijk geen gebruik van te maken!

*Vertaald door openai.com*

