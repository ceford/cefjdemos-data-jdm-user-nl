<!-- Filename: J4.x:Template_Overrides / Display title: Sjabloonoverschrijvingen -->

## Invoering

Joomla-extensies definiëren hun outputweergave met sjabloonbestanden, die HTML en door PHP gegenereerde HTML-opmaak bevatten, en CSS-bestanden die de lay-out, het kleurenpalet, lettertypen, enzovoort definiëren. Dat kan perfect aan uw behoeften voldoen, vooral omdat u het uiterlijk met uw eigen CSS-stijlen kunt aanpassen. Soms wilt u echter extra informatie tonen of juist minder informatie weergeven. Daarvoor moet u een sjabloonoverride maken.

Veel van de Joomla-extensies hebben vrij complexe outputsjablonen die moeilijk te lezen zijn. Voor sommige daarvan hebt u een goed begrip van HTML, PHP en CSS nodig om ze aan te pakken. Dit artikel illustreert het proces door een override te maken voor het uitlogformulier, dat zich eigenlijk in de inlogmodule, mod_login, bevindt. De eigenaar van de site wil graag dat het uitlogformulier de tijd toont waarop automatisch uitloggen zal plaatsvinden na een periode van inactiviteit.

## Voorbeeld: Sjabloonoverschrijving voor mod_login

Begin door **Systeem → Sjablonen → Websitesjablonen** in het beheermenu te selecteren en selecteer vervolgens het item Cassiopeia Details en Bestanden. Dat opent het formulier Sjablonen: Aanpassen (Cassiopeia):

![sjabloon aanpassen cassiopeia site tab](../../../en/images/templates/templates-customise-cassiopeia.png)

**Belangrijk:** bewerk geen van de bestanden die als onderdeel van de Cassiopeia-sjabloon worden geleverd. Bij de volgende Joomla-update kunnen die bestanden worden overschreven en gaan uw wijzigingen verloren.

De html-map is waar overschrijvingen zich bevinden. Als u de html-map uitklapt, ziet u dat er al overschrijvingen zijn voor lay-outs, mod_custom, mod_menu en tinymce. Klap ze allemaal uit om te zien wat erin zit. Er is op dit moment geen mod_login.

## Aanmaken van Overrides

Selecteer het tabblad Aanmaken van Overrides om de lijst met Modules, Componenten, Plugins en Lay-outs te zien waarvoor je overrides kunt maken:

![templates aanpassen cassiopeia overrides tab](../../../en/images/templates/cassiopeia-customisation-create-overrides.png)

Selecteer het mod_login-item. De mod_login template php-bestanden worden naar de html-map gekopieerd en je keert terug naar het Editor-tabblad. Vouw de html- en mod_login-mappen uit. Je zult default.php en default_logout.php zien.

Je wilt het default.php bestand niet, omdat dat een override is voor het inlogformulier. Selecteer het en vervolgens de **Bestand Verwijderen** knop in de werkbalk. Bevestig in het waarschuwingsdialoogvenster dat je het bestand wilt verwijderen.

Let op hoe eenvoudig het is om bestanden te verwijderen als je van gedachten verandert. En met de Mapbeheer-knop kun je ook hele mappen verwijderen. Wees voorzichtig dat je niets verwijdert dat je niet zelf hebt aangemaakt.

## Bewerk default_logout.php

Selecteer in het tabblad Editor het bestand default_logout.php. Let op de knoppen rechtsboven: Toon Originele Bestand en Toon Verschillen. Voor de volgende schermafbeelding is de laatste optie op Ja gezet om een aantal toevoegingen aan code aan de bovenkant van het bestand te laten zien. Deze regels code berekenen wanneer de gebruikerssessie zal verlopen na het laden van de pagina met het uitlogformulier.

![templates aanpassen cassiopeia overrides tabblad](../../../en/images/templates/cassiopeia-customisation-edit-logout-override.png)

Het verschilgebied toont toegevoegde regels met een groene achtergrond en verwijderde regels met een rode achtergrond. In dit geval zijn er geen regels verwijderd. De code wordt hier getoond mocht je deze willen kopiëren om het zelf te proberen.

```php
    use Joomla\CMS\Factory;

    date_default_timezone_set('Europe/London');
    $config = Factory::getContainer()->get('config');
    $lifetime = $config->get('lifetime', 0);
    $time = time() + $lifetime * 60;
    $endTime = date('H:i:s', $time); // time() retourneert al een tijd in seconden
```

Verder naar beneden in het override-bestand, regel 36, zijn enkele regels toegevoegd om de gewenste mededeling te tonen:

```html
<p class="text-center">
Je sessie verloopt om <br><?php echo $endTime; ?>
</p>
```

Sla op en herlaad de sitepagina met het uitlogformulier.

![templates aanpassen cassiopeia overrides tabblad](../../../en/images/templates/cassiopeia-customisation-logout-override-result.png)

Je zou het uitlogformulier elke keer moeten zien veranderen wanneer de pagina opnieuw wordt geladen. Maar wat als je van gedachten verandert? Of verschillende opties hebt voor verschillende gebruikersgroepen? Welkom bij Layouts, het onderwerp van een apart artikel.

## Andere Overrides

Het tabblad Create Overrides van het sjabloon: Aanpassen (Cassiopeia)-formulier
wordt gebruikt om elk van de elementen van de Joomla-uitvoer te maken waarvoor het
mogelijk is om overrides te maken. De namen van de override-mappen beginnen meestal
met com\_, mod\_ of plg\_. Merk op dat het tweede deel van een plugin
override-map de plugingroep aangeeft. Hier is een voorbeeldselectie
van override-mappen:

![sjablonen aanpassen cassiopeia overrides tab](../../../en/images/templates/templates-customise-example-override-folder.png)

## Layout-Overschrijvingen

Kleine lay-outbestanden worden vaak gebruikt voor individuele elementen van Joomla!-pagina's. De Lees Meer-knop van artikelen, de Intro-afbeelding en de Volledige afbeelding zijn allemaal voorbeelden van elementen die worden gegenereerd door hun eigen lay-outbestanden. Deze micro-lay-outs zijn te vinden in de /layouts map. In de weergave Category Blog bevat bijvoorbeeld het bestand blog_item.php de code om de artikelkop, een intro-afbeelding, de introtekst, evenals verschillende andere relevante delen van de pagina te plaatsen. Dit doet het door gebruik te maken van een LayoutHelper-aanroep waarbij de te gebruiken lay-out als parameter wordt doorgegeven. Dit is een voorbeeld, de aanroep om de Titel van het Artikel in de bloglay-out in te voegen:

```php
<?php echo LayoutHelper::render('joomla.content.blog_style_default_item_title', $this->item); ?>
```

De locatie van het bestand voor dit specifieke element wordt gevonden door de punttekens te vervangen door schuine strepen, voorafgegaan door /layouts/ en gevolgd door .php:

```php
    JOOMLAROOT/layouts/joomla/content/blog_style_default_item_title.php
```

Wanneer een override-bestand wordt aangemaakt, staat het in:

```php
    JOOMLAROOT/templates/cassiopeia/html/layouts/joomla/content/blog_style_default_item_title.php
```

## Verdere Informatie

- Sjabloon Basisprincipes
- Cassiopeia Sjabloonmappen en -bestanden
- Cassiopeia Sjabloonaanpassing
- Sjabloonoverrides
- Sjabloonindelingen
- Cassiopeia Sjabloon Vereenvoudigd - Een Gevalstudie - een eenvoudig sjabloon gebaseerd 
  op Cassiopeia

*Vertaald door openai.com*

