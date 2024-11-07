<!-- Filename: J4.x:Cassiopeia_Template_Customisation / Display title: Cassiopeia Aanpassing  -->

## Inleiding

Cassiopeia is het sjabloon dat wordt geleverd met Joomla 4. Het is een uitstekend algemeen **toegankelijk** en **responsive** sjabloon. Het kan worden aangepast via de sjabloonopties en het *user.css*-bestand door gebruikers met enige kennis van HTML en CSS.

De onderstaande illustratie toont het uiterlijk van een Joomla 4-site met één artikel en een paar aangemaakte menupunten.

![Cassiopeia weergave van een enkel artikel](../../../en/images/templates/cassiopeia-customisation-article-view.png)

## Sjablonen: Stijl Bewerken

Je kunt experimenteren met de uitstraling van de site door het formulier Stijl Bewerken te openen. Ga naar **Systeem → Sjablonen → Site Sjabloon Stijlen** en selecteer de sjabloontitel in de kolom Stijl, Cassiopeia - Standaard. Het tabblad Geavanceerd bevat instellingen die je kunt aanpassen:

![Cassiopeia stijl bewerken geavanceerd tabblad](../../../en/images/templates/cassiopeia-customisation-edit-style.png)

Om de opties te proberen, open je één browsertabblad of venster met de Beheerder interface en een tweede tabblad of venster met de Site interface, en wissel je heen en weer na elke opgeslagen wijziging.

### Merk

- **Ja** de standaard. De Cassiopeia logo balk met een Logo of Merknaam wordt weergegeven met een donkere achtergrond, standaard in blauw.
- **Nee** De logo balk wordt niet weergegeven. De opties om een Logo, Titel en Slagzin te selecteren verdwijnen.

Het standaard merkbeeld is het woord Cassiopeia als een afbeelding in een SVG-bestand. Dat is wat wordt weergegeven in de eerste illustratie hierboven.

Je kunt het Merk op Nee zetten als je branding wilt bieden in een aangepast HTML-module.

### Logo

- **Geen** Het standaard Cassiopeia afbeeldingslogo zal worden gebruikt tenzij een Titel is gedefinieerd.
- **Logo Afbeelding** Het geselecteerde Logo zal verschijnen in plaats van het Cassiopeia logo, zelfs als een Titel is gedefinieerd.

### Titel (alternatief voor logo)

- **Mijn Merknaam** Indien aanwezig en je hebt geen Logo afbeelding geselecteerd, verschijnt de tekst in het Titelveld, maar onderstreept in de blauwe bovenbalk.

### Slagzin

- **Altijd tot uw dienst** Indien aanwezig verschijnen de woorden in het slagzinveld in een klein lettertype onder het logo of de merknaam.

![Cassiopeia merk met slagzin](../../../en/images/templates/cassiopeia-customisation-brand-with-tagline.png)

### Lettertype Schema

- **Geen** de standaard. De lettergrootte gespecificeerd in de sjabloonstijl wordt gebruikt, wat meestal betekent dat de site de lettertypen gebruikt die op je eigen computer beschikbaar zijn.
- **Anders** Een lettertypefamilie in de sjabloonmaphiërarchie of gedownload van het web wordt gebruikt. Je kunt de veranderde uitstraling van de tekst op een pagina zien wanneer je de site opnieuw laadt na het wijzigen van deze optie.

### Kleuren Thema

- **Standaard** Een donkerblauwe achtergrondkleur voor de Merk balk en andere elementen zoals de Inlogknop.
- **Alternatief** Een kastanjebruine achtergrondkleur in plaats van donkerblauw.

![Cassiopeia alternatief kleurenschema](../../../en/images/templates/cassiopeia-customisation-alt-color-scheme.png)

### Lay-out

- **Statisch** de standaard. De maximale breedte is ingesteld op 1320px. Op bredere schermen worden de marges breder.
- **Vloeibaar** Er is geen maximale breedte.

Het beeld op een smal scherm (mobiel apparaat):

![Cassiopeia mobiele weergave](../../../en/images/templates/cassiopeia-customisation-mobile-view.png)

### Plakkerige Kop

- **Nee** de standaard. Hoofdelementen en inhoud scrollen naar boven uit het zicht.
- **Ja** Behalve op smalle schermen blijven hoofdelementen vast aan de bovenkant van het zicht terwijl de inhoud omhoog scrollt. Dat is alleen zichtbaar waar paginainhoud hoger is dan het zicht.

### Terug-naar-boven Link

- **Nee** de standaard. Er is geen Terug-naar-boven link.
- **Ja** Waar de inhoud hoger is dan het zicht, staat rechtsonder op de pagina een knop gemarkeerd met een Omhoog-chevron. Selecteer het om terug naar de bovenkant van de pagina te scrollen.

![Cassiopeia terug naar boven](../../../en/images/templates/cassiopeia-customisation-back-to-top.png)

## Cassiopeia Sjabloonposities

Bij het bouwen van een website met Cassiopeia is het erg handig om de locaties van de posities te kennen die je voor modules kunt gebruiken. Sommige zijn beschrijvend, zoals *menu* en *bottom-a*, maar het is niet zo duidelijk waar ze zijn totdat je ze gebruikt. Deze illustratie zou moeten helpen:

![Cassiopeia sjabloonposities](../../../en/images/templates/cassiopeia-template-positions.png)

Probeer het volgende:

### Verplaats de Menu Module naar de *menu* Positie

Een nieuw geïnstalleerde Joomla 4-site heeft een menu in de *sidebar-right* positie, te zien in de eerste illustratie hierboven. Voor deze tutorial zijn enkele menu-items toegevoegd, waarvan één een ouder is met twee onderliggende items. Om dit menu naar de menupositie te verplaatsen, ga je naar **Inhoud **→** Site Modules** in het beheerdersmenu. In de lijst staan drie modules, waaronder Hoofdmenu. Selecteer deze om het Modules: Menu bewerkformulier te openen.

Verander in het Module-tabblad het veld Positie aan de rechterkant naar Menu \[menu\]. Sla op en bekijk het resultaat in de weergave van de site. Het menu ziet er prima uit, maar de onderliggende items zijn er niet.

Selecteer in het menu bewerkformulier het tabblad Geavanceerd en scroll naar beneden naar het veld Lay-out. Het is een keuzelijst met vier opties. --Van Module-- / Standaard is standaard geselecteerd. Probeer de andere opties en bekijk het resultaat. (Vergeet niet om te *saven* in het bewerkformulier en opnieuw te laden in de site weergave.) Geen van de --Van Module-- opties toont de onderliggende menu-items, maar beide van de --Van Cassiopeia Sjabloon-- doen dat wel.

![Cassiopeia menu posities](../../../en/images/templates/cassiopeia-customisation-menu-position.png)

Dus wat voor verschil maakt **Inklapbaar**?

- Inklapbare Dropdown: Op smalle schermen van mobiele apparaten klapt het menu in tot een Hamburger-icoon totdat het is geselecteerd. Bij selectie vouwt het uit tot een verticale lijst.
- Dropdown: Het menu verschijnt altijd als een verticale lijst.

### Verplaats de Menu Module naar de *topbar* Positie

Stel in het bewerkformulier van de Module het Positie in op Topbalk \[topbar\] en bekijk het resultaat. Er is een probleem - het menu is verder naar links gepositioneerd dan toen het in de menupositie stond. Dat komt omdat de menupositie en de logolocatie een CSS-klasse van *grid-child* hebben, maar de topbar niet. Dat kan worden opgelost met een regel in het *user.css* bestand, hieronder beschreven.

## Cassiopeia Aanpassen

Wat als je de donkerblauwe achtergrondkleur van de header niet mooi vindt? Stel dat je de voorkeur geeft aan een donker groen thema. Om dat aan te passen heb je enige kennis van CSS nodig. Ga naar **Systeem** → **Site Sjablonen** → **Cassiopeia Details en Bestanden** om het Sjabloon: Aanpassen (Cassiopeia) formulier te openen.

De onderstaande illustratie toont twee mapgroepen. De eerste groep bestaat uit de sjabloonmappen en -bestanden die je niet zou moeten wijzigen, maar waaraan je mag toevoegen. In het bijzonder mag je sjabloonoverride-HTML-bestanden toevoegen aan de *html* map. De tweede groep bevat de sjabloon mediabestanden die je niet zou moeten wijzigen. Je mag echter een *user.css* bestand toevoegen aan de *css* map en/of een *user.js* bestand aan de *js* map. Dit zou je doen als je enkele eenvoudige aanpassingen aan de site wilt maken.

![Cassiopeia bestanden bewerken](../../../en/images/templates/cassiopeia-customisation-edit-files.png)

Let op dat er geen *user.css* bestand aanwezig is in de *css* map. Dat is er een die je zelf aanmaakt zodat je eerder gedefinieerde stijlen kunt overschrijven. Als het niet aanwezig is, maak het dan nu door de *css* map te selecteren en vervolgens op de *Nieuw* knop te klikken. In het Nieuwe Bestandsvenster selecteer je de *css* map, anders verschijnt het nieuwe bestand op de verkeerde plaats. Voer user (kleine letters en zonder *.css*) in het Veld Bestandsnaam in en selecteer *.css* in het Veld Bestandstype. Selecteer de knop Maken om het bestand aan te maken. Als *user.css* al aanwezig is, selecteer het dan om het bewerkingsformulier te openen.

### Koppen

Als eenvoudige starter, verander de kleur van koppen naar donkergroen. Koppen zijn tags in het bereik *h1, h2, h3, h4, h5* en *h6*. Voer in het *user.css* bestand de volgende stijldefinitie in:
```css
    h1, h2, h3, h4, h5, h6 {
      color: darkgreen;
    }
```
Bewaar en vernieuw de site om het resultaat te zien. De Pagina of Artikel titel zou donkergroen moeten zijn. Zo niet, controleer wat je hebt getypt. De formele taal voor Joomla-documentatie is Brits Engels, dus colour in plaats van color zoals in Amerikaans Engels. Maar in CSS moet het color zijn. Is de interpunctie correct?

Minder voor de hand liggend is dat sommige tags anders dan koppen gestyled kunnen worden om eruit te zien als koppen. Voeg daarom dit toe:
```css
    .h1, .h2, .h3, .h4, .h5, .h6 {
      color: darkgreen;
    }
```
Let hier op dat de vooraanstaande punt (.) een klasse-selector is, bijvoorbeeld Dummy H1 - dus er is een punt in het CSS-bestand maar niet in de klassenaam.

### Header Achtergrond

In het browsertabblad met de site, open je browserontwikkelaarstools, Firefox in dit voorbeeld, en selecteer de header tag.

![Cassiopeia ontwikkelaarstools](../../../en/images/templates/cassiopeia-customisation-developer-tools.png)

Dat toont de gebruikte stijlen. De stijl container-header is waar de background-color en background-image worden ingesteld. Ze moeten overschreven worden in het *user.css* bestand. Probeer dit:
```css
    .container-header {
      background-color: darkgreen;
      background-image: none;
    }
```
### *topbar* Stijl

Herinner je die opmerking over het menu dat te ver naar links in de topbar staat? Dat komt omdat het geen maximale breedte en gepaste marges heeft ingesteld. Voeg dit toe aan het *user.css* bestand om dat te verhelpen:
```css
    .container-topbar {
      max-width: 1320px;
      margin-left: auto;
      margin-right: auto;
    }
```
Dit is het werkende groene thema:

![Cassiopeia groen thema](../../../en/images/templates/cassiopeia-customisation-green-theme.png)

### Toegankelijkheid

Let op dat er voldoende contrast moet zijn tussen achtergrond- en voorgrondkleuren om te voldoen aan de webtoegankelijkheidsnormen. Je kunt het contrast controleren met de WebAIM Contrast Checker. Donkergroen is #006400.

## Overschrijvingen

Het sjablonenformulier: Aanpassen (Cassiopeia) onder het tabblad Overschrijvingen maken toont de lijst van extensies waarvoor je een overschrijving kunt maken. Let op de verschillende symbolen: selecteer een map-symbool om een lijst van de mappen en bestanden erin te tonen; selecteer een multi-bestand symbool om direct een overschrijving voor die extensie te maken; het aangemaakte item verdwijnt uit de lijst - selecteer het tabblad Editor en vind de aangemaakte overschrijving in de *html* map. Er kunnen meer dan één bestand worden aangemaakt - de aangemaakte bestanden worden gekopieerd van de originele extensie en zijn klaar om door jou bewerkt te worden. Daarvoor moet je enige HTML en PHP kennen!

Dit is het tabblad Overschrijvingen maken:

![Cassiopeia overschrijvingen maken](../../../en/images/templates/cassiopeia-customisation-create-overrides.png)

Als je slechts aan het experimenteren bent en eigenlijk geen overschrijving wilt, kun je het bewerkingsformulier *Sluiten*, de knop Beheer Mappen in de werkbalk selecteren en de knop Verwijderen onderaan het Beheer Mappen venster selecteren.

Overschrijvingen gaan echt meer over het aanpassen van extensies dan over de Cassiopeia-sjabloon en dat is een ander verhaal.

## Kindersjablonen

Als je meer substantiële veranderingen aan de uitstraling van de site wilt maken, kun je een kindersjabloon creëren. Dat kopieert slechts een kleine selectie van mappen en bestanden die je kunt wijzigen of uitbreiden, maar blijft verder de mappen en bestanden van het hoofdsjabloon gebruiken. Door kindersjablonen te gebruiken, kun je sommige pagina's één themakleur geven en andere pagina's een tweede themakleur. Kindersjablonen worden elders behandeld. Dit is een illustratie van de bestandsstructuur in een kind van Cassiopeia:

![Cassiopeia kindersjabloonbestanden](../../../en/images/templates/cassiopeia-customisation-child-template-files.png)

*Vertaald door openai.com*

