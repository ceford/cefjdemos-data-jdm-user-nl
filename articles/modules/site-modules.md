<!-- Filename: J4.x:Site_Modules / Display title: Sitemodules  -->

## Introductie

Modules zijn lichte en flexibele extensies die worden gebruikt om stukjes informatie weer te geven in **vakjes** die rond een component op een pagina zijn gerangschikt. Een bekend voorbeeld is de inlogmodule. Modules worden per menu-item toegewezen, zodat je kunt beslissen om een module te tonen of te verbergen, afhankelijk van welke pagina de gebruiker momenteel bekijkt.

Sommige modules zijn gekoppeld aan componenten. Bijvoorbeeld, de module **Laatste Nieuws** is gekoppeld aan de inhoud-component om links naar de nieuwste artikelen weer te geven. Modules hoeven echter niet gekoppeld te zijn aan componenten. Ze hoeven zelfs nergens aan gekoppeld te zijn en kunnen gewoon statische HTML of tekst zijn.

Er kunnen meerdere instanties van dezelfde module zijn. Bijvoorbeeld, je kunt één instantie van de module Willekeurige Afbeelding gebruiken voor sommige pagina's en een andere instantie voor andere pagina's, waarbij elke instantie gebruikmaakt van een andere afbeeldingsmap om afbeeldingen uit te selecteren.

## Moduleposities

Modules worden toegewezen aan een positie op een pagina die wordt gedefinieerd door de gebruikte template. De volgende illustratie toont een schematische lay-out van de Cassiopeia-template:

![Cassiopeia template positiediagram](../../../en/images/modules/cassiopeia-template-positions.png)

En de volgende lijst toont de beschikbare moduleposities per naam:

```xml
    <positions>
        <position>topbar</position>
        <position>onder-top</position>
        <position>menu</position>
        <position>zoeken</position>
        <position>banner</position>
        <position>top-a</position>
        <position>top-b</position>
        <position>main-top</position>
        <position>main-bottom</position>
        <position>broodkruimels</position>
        <position>sidebar-links</position>
        <position>sidebar-rechts</position>
        <position>bottom-a</position>
        <position>bottom-b</position>
        <position>footer</position>
        <position>debug</position>
    </positions>
```

## Een Kernmodule Toevoegen

Kernmodules zijn modules die worden geleverd met een nieuwe Joomla-installatie. Er zijn duizenden aanvullende modules beschikbaar van derde partijen. Stel dat je een willekeurige afbeelding wilt tonen om je site interessanter te maken voor bezoekers. Selecteer vanuit het Administrator-menu **Content → Site Modules** om de lijst van reeds in gebruik zijnde site-modules te zien:

![Lijst van Site Modules](../../../en/images/modules/cassiopeia-modules-list.png)

Selecteer de knop Nieuw om een lijst van beschikbare site-modules te zien die je kunt installeren:

![Beschikbare Site Modules](../../../en/images/modules/cassiopeia-modules-available.png)

Scroll naar beneden en selecteer de module Willekeurige Afbeelding. Hiermee wordt het **Modules: Willekeurige Afbeelding** bewerkingsformulier geopend, klaar voor verdere invulling.

![Willekeurige afbeelding-module](../../../en/images/modules/cassiopeia-module-random-image.png)

- **Titel** Dit is een verplicht veld.
- **Afbeeldingstype** Standaard is jpg.
- **Afbeeldingsmap** Voer een pad in naar een map die daadwerkelijk afbeeldingen bevat van het type dat je hebt geselecteerd.
- **Link** Een URL om naar te worden doorgestuurd als de afbeelding is geselecteerd.
- **Breedte** Dwingt alle afbeeldingen om met deze breedte in pixels te worden weergegeven.
- **Hoogte** Laat leeg om de beeldverhouding te behouden.
- **Positie** Selecteer een modulepositie zodat de module daadwerkelijk op een pagina verschijnt. In de illustratie is 'sidebar-right' geselecteerd.
- **Opslaan & Sluiten** Of gebruik de Help-knop in de werkbalk om te ontdekken wat de andere velden doen.

## Module Volgorde

Na het opslaan, moet je mogelijk de volgorde van de modules wijzigen op de gekozen positie. Ga als volgt te werk:

- In de Modulelijst selecteer je het Kolom Sorteervolgorde-icoon in de moduletabelkop; dit is een gecombineerd op/neer-driehoekje. Hiermee sorteer je de tabel en worden er sleeptekens getoond, een verticale ellipsis. Selecteer opnieuw om de sorteervolgorde om te keren! Het kolomsorteerpictogram verandert: op-driehoekje om de normale sorteervolgorde aan te geven, neer-driehoekje om omgekeerde sorteervolgorde aan te geven.
- Pak en sleep de ellipsis van de Willekeurige Afbeelding om deze omhoog of omlaag te verplaatsen. Laat los wanneer deze op de door jou gewenste positie staat.

## Bekijk de Site

![Random image module site view](../../../en/images/modules/cassiopeia-module-random-image-site.png)

Controleer het uiterlijk van de site. In dit geval kan het een goed idee zijn om de afbeelding te centreren. Dat kan als volgt worden gedaan:

- Ga terug naar het bewerkingsformulier en selecteer het tabblad Geavanceerd.
- Voer in het veld Module klasse de tekst `text-center` in en sla op.
- Bekijk het resultaat door de sitepagina te herladen.

Alles klaar?

## Lijst van Kernmodules

- **Artikelen - Gearchiveerd** Deze module toont een lijst van de kalendermaanden met Gearchiveerde Artikelen. Nadat je de status van een Artikel naar Gearchiveerd hebt veranderd, wordt deze lijst automatisch gegenereerd.
- **Artikelen - Categorieën** Deze module toont een lijst van categorieën van één bovenliggende categorie.
- **Artikelen - Categorie** Deze module toont een lijst van artikelen uit één of meer categorieën.
- **Artikelen - Laatste** Deze module toont een lijst van de meest recent gepubliceerde en huidige Artikelen.
- **Artikelen - Meest Gelezen** Deze module toont een lijst van de gepubliceerde Artikelen met het hoogste aantal paginaweergaven.
- **Artikelen - Nieuwsflits** De Nieuwsflits Module toont een vast aantal artikelen uit een specifieke categorie.
- **Artikelen - Gerelateerd** Deze module toont andere Artikelen die gerelateerd zijn aan het artikel dat wordt bekeken. Deze relaties worden vastgesteld door de Trefwoorden. Alle trefwoorden van het huidige Artikel worden vergeleken met alle...
- **Banners** De Bannermodule toont de actieve Banners van de Component.
- **Kruimelpad** Deze module toont het Kruimelpad.
- **Aangepast** Deze module stelt je in staat om je eigen Module te maken met behulp van een WYSIWYG-editor.
- **Feedweergave** Deze module stelt je in staat om een gesyndiceerde feed weer te geven.
- **Footer** Deze module toont de Joomla! copyright-informatie.
- **Taalwisselaar** Deze module toont een taalwisselaar op je website van beschikbare content talen.
- **Laatste Gebruikers** Deze module toont de laatst geregistreerde gebruikers.
- **Inloggen** Deze module toont een gebruikersnaam- en wachtwoordinlogformulier. Het toont ook een link om een vergeten wachtwoord terug te halen. Als gebruikersregistratie ingeschakeld is (in Gebruikers → Beheren → Opties),...
- **Menu** Deze module toont een menu op de Frontend.
- **Willekeurige Afbeelding** Deze module toont een willekeurige afbeelding uit je gekozen map.
- **Slim Zoeken** Dit is een zoekmodule voor het Slim Zoeken systeem.
- **Statistieken** De Statistiekenmodule toont informatie over je serverinstallatie samen met statistieken over de websitegebruikers en het aantal Artikelen in je database.
- **Syndicatie-Feeds** Slimme Syndicatiemodule die een Gesyndiceerde Feed maakt voor de pagina waar de Module wordt weergegeven.
- **Tags - Populair** Deze module toont tags die op de site worden gebruikt in een lijst- of wolkopmaak. Tags kunnen worden gesorteerd op titel of op het aantal getagde items en beperkt tot een specifieke tijdsperiode.
- **Tags - Vergelijkbaar** De Vergelijkbare Tags Module toont links naar andere items met vergelijkbare tags. De nauwkeurigheid van de match kan worden gespecificeerd.
- **Wie is Online** De Wie is Online Module toont het aantal Anonieme Gebruikers (Gasten) en Geregistreerde Gebruikers (ingelogde gebruikers) die momenteel toegang hebben tot de website.
- **Wrapper** Deze module toont een iframe-venster naar een gespecificeerde locatie.

*Vertaald door openai.com*
