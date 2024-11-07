<!-- Filename: J4.x:Home_Page_in_Different_Style / Display title: Startpagina in verschillende stijlen  -->

## Startpagina van de Site

Een startpagina van de site kan worden geselecteerd uit elk type menu-item door een grijs pictogram in de Startpagina-kolom van een lijst met menu-items te selecteren. Probeer een verandering te maken! Bekijk de verandering op je site in een apart browser-tabblad of -venster. Je kunt eenvoudig weer terug veranderen. Als je een opvallende startpagina wilt, kun je een menu-itemtype voor een Enkel Artikel, een Categorieblog menu-itemtype, een Aanbevolen Artikelen menu-itemtype of iets anders kiezen.

Stel dat je je startpagina een opvallend uiterlijk wilt geven dat enigszins verschilt van alle andere pagina's op je site. Er zijn veel verschillende methoden beschikbaar om het uiterlijk van een startpagina aan te passen:

- Via modules die alleen aan de startpagina zijn toegewezen.
- Via aangepaste stijlen.
- Via een Template Override of Layout.
- Via een aparte template of een kindtemplate die alleen voor het startpaginamenu-item wordt gebruikt.
- Meer...?

## Voorbeeld: Cassiopeia Voorbeeldgegevens

De Cassiopeia voorbeeldgegevens creëren een Startpagina met een **Uitgelichte Artikelen** menu-itemtype. Het is ingedeeld zoals te zien is in de onderstaande schermafbeelding (enkele kleine wijzigingen zijn aangebracht aan individuele artikelen om hier een betere schermafbeelding te maken).

![startpagina met cassiopeia en voorbeeldgegevens](../../../en/images/templates/templates-home-page-style-cassiopeia-sample-data.png)

Zo wordt de indeling bereikt:

### Afbeeldingsmodule

De grote afbeelding onder de menubalk bevindt zich in een aangepaste module genaamd Afbeelding die is toegewezen aan de banner-positie in de Cassiopeia-sjabloon.

![aangepaste module gebruikt in voorbeeldgegevensstijl](../../../en/images/templates/templates-home-page-style-custom-module-image.png)

In het tabblad Menu-toewijzing is de module uitsluitend toegewezen aan Startpagina:

![tabblad menu-toewijzing van aangepaste module](../../../en/images/templates/templates-home-page-style-custom-module-menu-assignment.png)

De achtergrondafbeelding wordt geselecteerd in het tabblad Opties van de Modules: Aangepaste bewerkingsformulier.

In het tabblad Geavanceerd / Indeling veld, is het `banner` item geselecteerd. De banner-indeling is een sjabloonindeling:

### Sjabloonindeling

De standaard module-indeling in `siteroot/modules/mod_custom/tmpl/default.php` toont de module niet zoals gewenst. Er is een alternatieve indeling in `siteroot/templates/cassiopeia/html/mod_custom/banner.php`. Omdat `banner.php` niet aanwezig is in de aangepaste modulecode, werkt het als een indeling die je kunt selecteren in plaats van een override die altijd wordt gebruikt. In de Afbeeldingsmodule kun je de standaardindeling selecteren, Opslaan en de site opnieuw laden om het verschil te zien. Wissel terug naar de banner-indeling en sla opnieuw op om het normale gedrag te herstellen.

Er zijn afzonderlijke artikelen over Overrides en Indelingen.

### Nieuwsflitsmodule

Onder de grote Afbeelding zijn drie kleine vakjes, elk met een afbeelding en tekst eronder. Ze zijn gemaakt met behulp van een Artikelen - Nieuwsflits module in de sjabloon top-a positie. De module is ingesteld om 3 items weer te geven. Zijn Menu-toewijzing is uitsluitend Startpagina. Het tabblad Geavanceerd heeft Indeling ingesteld op horizontaal en Modulestijl ingesteld op noCard.

![nieuwsflitsmodule](../../../en/images/templates/templates-home-page-style-newsflash-module-image.png)

Dat sluit de uitleg af van hoe de Cassiopeia voorbeeldgegevens Startpagina is gemaakt.

## Meer Opties

Misschien wil je verder gaan en meer doen, zoals een ander kleurenschema voor de startpagina, een watermerk of een aangepaste lay-out. Hier zijn enkele ideeën:

### Paginaweergave

In de menu's: in het formulier Item Bewerken voor het Home-menu selecteer je het tabblad Paginaweergave. Het veld Pagina Klasse is meestal leeg. Alles wat hier wordt ingevoerd, wordt een extra klasse in het

element van de pagina. Bijvoorbeeld, door `fancyhome` in te voeren ontstaat het volgende in de uitvoer van de startpagina voor die ene pagina:
```html
<body class="site com_content wrapper-static view-featured no-layout no-task itemid-101 fancyhome has-sidebar-right">
```
Je kunt dan een user.css-bestand aanmaken via **Systeem **→** Sjabloon voor websites **→** Cassiopeia Details en Bestanden**. Selecteer de knop `Nieuw bestand` en maak user.css aan in de css-map. Voer vervolgens stijlen in het bewerkformulier van user.css in. Voorbeeld:
```css
    .fancyhome {
      background-color: #f8fff8;
    }
```
Dit geeft de startpagina een lichtgroene achtergrond. Gebruik \#f8f8ff; voor een lichtblauwe achtergrond of \#ffffee voor lichtgeel. Je kunt allerlei andere dingen doen met je fancyhome-stijl, maar je hebt wel een goede kennis van css nodig.

### Alternatieve Sjablonen voor de Startpagina

Je kunt alternatieve sjablonen voor de site installeren die zijn verkregen van externe sjabloonleveranciers. En je kunt kind-sjablonen maken die zich op soortgelijke wijze gedragen. In beide gevallen kun je kiezen welk sjabloon de standaard voor alle pagina's moet zijn en welk sjabloon alleen voor de startpagina moet worden gebruikt.

- Selecteer **Systeem → Stijl Sjablonen Website** in het beheerdersmenu.
- Selecteer het sjabloon dat je wilt gebruiken voor de startpagina. Het moet een sjabloon zijn dat niet als standaard sjabloon is geselecteerd.
- Selecteer in het tabblad Menu-toewijzing alleen het Home-menu-item. Alles wat hier niet geselecteerd is, zal nog steeds je standaard sjabloon gebruiken.
- Je zou enkele opties kunnen selecteren in het tabblad Geavanceerd, maar die variëren per sjabloon en worden hier niet behandeld.

Er zijn andere artikelen over Cassiopeia-aanpassingen.

*Vertaald door openai.com*

