<!-- Filename: J4.x:Setup_a_Multilingual_Site / Display title: Een Meertalige Site Instellen  -->

## Voorbeeldgegevens

Joomla wordt geleverd met twee sets voorbeeldgegevens: Blog en Meertalig. Er is een derde testset, maar die is alleen voor gebruikers die met de Joomla-ontwikkelversie werken. Als je een bestaande site hebt met artikelen, menu's en modules, zal deze in principe vergelijkbaar zijn met een site waarop blogvoorbeeldgegevens zijn geïnstalleerd.

In het Home Dashboard zegt de Meertalige Voorbeeldgegevens **Voordat u begint, zorg ervoor dat u ten minste 2 talen heeft geïnstalleerd met hun inhoudstalen en dat er geen voorbeeldgegevens zijn geïnstalleerd**. Dat zal je waarschijnlijk ertoe brengen om handmatig de vereiste stappen één voor één uit te voeren om een meertalige site te maken. Dat is een foutgevoelige procedure waarbij je waarschijnlijk een fout zult maken, vooral als je meerdere talen gebruikt. Fouten kunnen worden hersteld, maar het hele proces is een beetje vervelend en kan verwarrend zijn.

Je kunt dat advies negeren en de Meertalige Voorbeeldgegevens gebruiken om een meertalige site op te zetten als je begrijpt hoe je later enkele correcties kunt aanbrengen in de oorspronkelijke menu's en modules.

## Initiële Site

Een nieuw geïnstalleerde Joomla-site heeft een **Hoofdmenu** in de rechterzijbalk. Het bevat een enkel menu-item genaamd **Home** van het type Uitgelichte Artikelen. Er is ook een **Inlogformulier** in de rechterzijbalk.

Aanvankelijk zijn er geen uitgelichte artikelen, dus het hoofdgedeelte van de pagina is leeg.  

## Blog Voorbeeldgegevens

Als je je eigen site-inhoud hebt gemaakt, moet je de Blog Voorbeeldgegevens **niet** installeren. Lees echter dit gedeelte door om te zien hoe het zich verhoudt. Anders:

- Selecteer **Installeren** in de sectie Meertalige Voorbeeldgegevens op het Startdashboard. De installatiefasen verschijnen kort en verdwijnen daarna.
- Je zult merken dat er verschillende nieuwe menu's zijn geïnstalleerd (laad de beheerderspagina opnieuw en vouw het Menu's-menu uit):
  - Hoofdmenu Blog.
  - Onderste Menu, met Login/Logout menu-items.
  - Speciaal Menu, zichtbaar na inloggen.
- Selecteer het **Frontend openen**-icoon in de bovenste Statusbalk of herlaad de site als deze al in een aparte tabblad is geopend.

Je kunt verwachten een lay-out vol met Informatie over Aanbevolen Artikelen te zien:

- Bovenaan bevindt zich het nieuwe **Hoofdmenu Blog** met verschillende blog lay-outs en artikelen.
- In de rechterzijbalk staan modules voor een Loginformulier, een Hoofdmenu en een Mijn Blog RSS-feed.
- Na inloggen heeft de rechterzijbalk een Speciaal Menu voor Alleen-Administratie-acties.
- Het **Home**-item van het Hoofdmenu leidt naar de lay-out van Aanbevolen Artikelen.
- Het bovenste **Blog**-menu-item leidt naar een Categorie Blog lay-out die enigszins verschilt van de lay-out van Aanbevolen Artikelen.

Neem een paar minuten de tijd om de menu-items en de soorten informatie waarnaar ze leiden te verkennen.

## Installeer en Publiceer Inhoudstalen

Installeer eerst alle talen die u wilt gebruiken. Als u later een extra taal wilt installeren, moet u de configuratiestappen voor die taal handmatig één voor één voltooien. Dat wordt elders behandeld. Voor deze tutorial zijn Frans, Duits en Welsh toegevoegd aan de standaard Engelse taal van de site tijdens de Joomla-installatie. Om talen toe te voegen na de installatie:

- Selecteer **Systeem** → **Talen installeren** in het beheerdersmenu.
- Selecteer de **Installeren** knop voor elke taal die u wilt gebruiken.

Geïnstalleerde talen moeten **Gepubliceerd** worden om ze beschikbaar te maken. Vanuit het beheerdersmenu:

- Selecteer **Systeem / Beheer paneel / Inhoudstalen**
- Publiceer in de Status-kolom elke taal die u wilt gebruiken.

## Meertalige Voorbeeldgegevens

Het installeren van de Meertalige Voorbeeldgegevens heeft gevolgen waarmee je later rekening moet houden:

- Menu's in de rechter zijbalk zullen niet worden gepubliceerd. Dat betekent dat de Hoofdmenu-module niet gepubliceerd zal zijn en er geen link zal zijn naar de Indeling van Uitgelichte Artikelen. Als je andere links in het Hoofdmenu had, zullen deze ook niet beschikbaar zijn.
- Het Speciale Menu zal niet worden gepubliceerd. Dat bevatte een link om een nieuw bericht te maken.

De Meertalige Voorbeeldgegevens bieden de volgende extra functies:

- Een artikelcategorie voor elke taal.
- Een artikel dat voor elke taal is geconfigureerd, hoewel in Lorem ipsum pseudo-tekst.
- Een apart menu voor elke taal. Je ziet dit in de lijst **Administrator**→**Menu's**.
- Een **Hoofdmenu xx-YY** menumodule in de rechter zijbalk van de site, waarbij xx-YY een taalcode is zoals en-GB.
- Het **Hoofd** menu-item leidt nu naar een Categorieblog-indeling voor artikelen in de geselecteerde taal. Het bevat slechts één artikel.
- Er is een **Taalwisselaar**-module in de rechter zijbalk. Het is ongetiteld om de noodzaak voor een aparte module voor elke taal met vertaalde titels te vermijden. Selectie gebeurt via een taalvlaggetje. Probeer het uit.

Let op: woorden die door Joomla worden geleverd, zullen worden vertaald, bijvoorbeeld in de Broodkruimels en het Inlogformulier. Woorden die door gebruikers worden getypt, moeten handmatig vertaald worden, bijvoorbeeld Inlogformulier en Hoofdmenu. Meer hierover later.

## Oplossen van Initiële Problemen

### Taalvolgorde

Je zult misschien merken dat de talen in de taalwisselaar in omgekeerde alfabetische volgorde staan. Om de volgorde te wijzigen:

- Selecteer **Systeem → Inhoudstalen** in het beheerdersmenu.
- Gebruik verticale ellipsis-iconen om de talen in de gewenste volgorde te slepen.
- Herlaad de site en zie dat de taalwisselaar nu de talen in je gewenste volgorde heeft.

### Volgorde Module Rechter Zijbalk

De volgorde van modules in de rechter zijbalk is een kwestie van persoonlijke voorkeur. Om de volgorde te wijzigen:

- Selecteer **Inhoud → Sitemodules** in het beheerdersmenu.
- Filter op **Positie → zijbalk-rechts**.
- Selecteer het icoon in de volgordekolom om de ordening sleepgrepen te onthullen (verticale ellipsis-iconen). Het kolomhoofdicoon moet een chevron zijn die naar boven wijst.
- Sleep items in de juiste volgorde:
  - Taalwisselaar
  - Hoofdmenu (alle varianten - volgorde maakt niet uit).
  - Speciale Menu
  - Inlogformulier
  - Gearchiveerde Artikelen
  - Syndicatie

### Uitgelichte Artikelen

Het oorspronkelijke hoofdmenu is niet gepubliceerd, maar het homemenuelement dat het bevat kan elders worden gereproduceerd. De meest handige plaats is het bovenste menu.

- Selecteer **Menu's **→** Hoofdmenu Blog** in het beheerdersmenu.
- Selecteer de **Nieuw** knop in de werkbalk.
- Voer een **Titel** in in het formulier **Menu's: Nieuw Item**, bijvoorbeeld **Uitgelicht**.
- Gebruik de **Selecteer** knop in het veld **Menuelementtype**.
- Selecteer **Artikelen **→** Uitgelichte Artikelen** uit de lijst **Menuelementtype**.
- Selecteer **Opslaan** in de werkbalk.
- Selecteer **- Eerste -** in het veld **Ordening**.
- Stel op het tabblad **Bloglayout** **Intro-artikelen** in op 3.
- Selecteer **Opslaan & Sluiten** in de werkbalk.

### Toewijzing van Sitemodules

De oorspronkelijke voorpagina Uitgelichte Artikelen layout werd geproduceerd door geselecteerde modules toe te wijzen om alleen op die ene pagina te verschijnen. De nieuwe Uitgelichte pagina moet worden toegevoegd voor elk van die modules.

- Selecteer **inhoud **→** Sitemodules** in het beheerdersmenu.
- Vind en selecteer het item **Afbeelding**.
- Zoek in het tabblad **Menu Toewijzing** en selecteer het item **Uitgelicht** in de sectie **Hoofdmenu Blog**.
- Selecteer **Opslaan & Sluiten** in de werkbalk.
- Vind en selecteer het item **Laatste Berichten**.
- Zoek in het tabblad **Menu Toewijzing** en selecteer het item **Uitgelicht** in de sectie **Hoofdmenu Blog**.
- Selecteer **Opslaan & Sluiten** in de werkbalk.

## Herlaad Site

Wanneer je de site herlaadt, zal het eerste item in het bovenste menu de uitgelichte link zijn die leidt naar de lay-out van de Uitgelichte Artikelen. Het aangrenzende Blog-item is een compactere Categorie Blog lay-out. Probeer de taalwisselaar. De door Joomla geleverde tekst, in de broodkruimels en het inlogformulier, verandert dienovereenkomstig. Ook bevatten de uitgelichte artikelen nu één artikel uit de Meertalige Voorbeeldgegevens, in de geselecteerde taal. Dit kan op de laatste pagina staan.

### Hybride of Pure Meertalige Site

Op dit moment heb je een hybride site: sommige inhoud is beschikbaar in alle talen en sommige inhoud is beschikbaar in een specifieke taal. Als je een pure meertalige site wilt, moet je de Blog-module van het bovenste hoofdmenu en misschien andere modules niet publiceren. In sommige gevallen wil je misschien taal specifieke modules maken, bijvoorbeeld het inlogformulier zou versies kunnen hebben met titels als Formulaire de connexion, Login Formular en Ffurflen Mewngofnodi.

Wat je hierna doet, is aan jou!  

## Oorspronkelijk Hoofdmenu

Uw oorspronkelijke Hoofdmenu-module, die nu niet gepubliceerd is, kan extra menu-items hebben bevat. U zou het kunnen publiceren. Het probleem is dat het item 'Home' naar dezelfde locatie linkt als de taal specifieke menu 'Home' pagina's, maar dan alleen in het Engels. U kunt dit als volgt omzeilen:

- Selecteer **Menu's**→**Hoofdmenu** vanuit het beheerdersmenu.
- Selecteer het **Home** menu-item.
- Selecteer het tabblad **Linktype**.
- Stel **Weergeven in menu** in op **Nee**.
- Selecteer **Opslaan & Sluiten** in de werkbalk.
- Selecteer **Content**→**Site-modules** vanuit het beheerdersmenu.
- Zoek het **Hoofdmenu** en publiceer het door het grijze kruis te veranderen in een groen vinkje.

De zichtbare items in het oorspronkelijke Hoofdmenu zouden nu normaal moeten werken. Als het Hoofdmenu geen zichtbare items heeft, zal het niet worden weergegeven.

## Een Extra Taal Toevoegen

Na de initiële setup van een meertalige site, als je een extra taal wilt toevoegen, moet je de stappen handmatig één voor één doorlopen:

### Stap 1: Installeer de Taal

- Selecteer **Systeem** → **Installeren** → **Talen** in het Beheerdersmenu.
- Zoek de vereiste taal in de lijst **Extensies: Talen**.
- Selecteer de knop **Installeren**.
- Er zal een bericht verschijnen: **Installatie van het taalpakket was succesvol.**

In dit voorbeeld is de extra taal Spaans.

### Stap 2: Publiceren en Ordenen

- Selecteer **Systeem** → **Beheren** → **Inhoudstalen** in het Beheerdersmenu.
- Schakel de nieuw geïnstalleerde taal in: selecteer de Status-knop om het grijze kruis in een groene vink te veranderen.
- Gebruik verticale ellipsiconen om de talen in de gewenste volgorde te slepen.

### Stap 3: Maak een Menu

- Selecteer **Menu's** → **Beheren** in het Beheerdersmenu.
- Selecteer de knop **Nieuw** in de Werkbalk.
- Voer een geschikte menutitel en unieke naam in, voorbeelden: Hoofdmenu (es-ES) en hoofdmenu-es-es.
- Voer een Beschrijving in, voorbeeld: Het hoofdmenu voor de site in de taal Spaans (es-ES).

### Stap 4: Voeg een Menu Module Toe

- Selecteer **Menu's** → **Beheren** in het Beheerdersmenu.
- Selecteer de knop **Voeg een module voor dit menu toe** voor het nieuw aangemaakte menu.
- Voer een geschikte titel in, voorbeeld: Hoofdmenu es-ES
- Selecteer een Positie: Sidebar-rechts
- Selecteer een Taal: Spaans (es-ES)
- Selecteer **Opslaan**.
- Orden de module: selecteer in de Ordenlijst het item waarna dit nieuwe item moet verschijnen.
- Selecteer **Opslaan & Sluiten**.

### Stap 5: Voeg een Categorie Toe

- Selecteer **Inhoud** → **Categorieën** in het Beheerdersmenu.
- Selecteer de knop **Nieuw** in de Werkbalk.
- Voer een geschikte titel in, voorbeeld: Categoría (es-es)
- Selecteer de correcte taal: Spaans (es-ES)
- Selecteer het tabblad **Associaties**.
- Selecteer voor elke taal een Categorie. Er is telkens slechts één keuze.
- Selecteer **Opslaan & Sluiten**.

### Stap 6: Voeg een Menu-item Toe

- Selecteer **Menu's** → **Hoofdmenu (es-ES)**, het nieuw aangemaakte menu.
- Selecteer de knop **Nieuw** in de Werkbalk.
- Voer een geschikte titel in, voorbeeld: Página de inicio
- Gebruik de Selecteer-knop aan het einde van het veld **Menu-item Type** om een itemtype te selecteren.
- Selecteer in de pop-uplijst **Artikelen** → **Categorie Blog**.
- Gebruik de Selecteer-knop in het veld Kies een Categorie.
- Selecteer in de pop-up Categorie lijst de categorie Categoría (es-es).
- Stel het veld **Standaardpagina** in op **Ja**.
- Selecteer in de vervolgkeuzelijst **Taal** de optie **Spaans (es-ES)**.
- **Opslaan & Sluiten**

### Stap 7: Voeg een Artikel Toe

De gemakkelijke manier om een artikel voor de nieuwe taal toe te voegen is door een bestaand artikel te kopiëren.

- Selecteer **Inhoud** → **Artikelen** in het Beheerdersmenu.
- Selecteer het artikel om te kopiëren, in dit voorbeeld **Artikel (en-GB)**.
- Verander in het formulier **Artikelen: Bewerken** de titel naar **Artikel (es-ES)**.
- Verander de **Categorie** naar **Categoria (es-es) (es-ES)**.
- Verander de **Taal** naar Spaans (es-ES).
- Selecteer **Opslaan als Kopie** in de vervolgkeuzelijst **Opslaan & Sluiten** in de Werkbalk. **Let op!**
- Selecteer het tabblad **Associaties**.
- Selecteer voor elke taal een artikel om te associëren - het equivalente artikel in elke taal.
- Selecteer **Opslaan & Sluiten** in de Werkbalk.

## Een Meertalig Artikel Toevoegen

Stel dat je een artikel wilt maken in elk van je geselecteerde talen.

- Selecteer **Inhoud **→** Artikelen **→** +** vanuit het Administrator menu of de **Nieuw** knop van de werkbalk in de artikelenlijst.
- Voer een titel in voor het artikel, bijvoorbeeld **William Shakespeare**.
- Stel het veld **Categorie** in op **Categorie (en-gb) (en-GB)**.
- Stel het veld **Taal** in op **Engels (en-GB)**.
- Voer de **Artikeltekst** in, bijvoorbeeld van Wikipedia:

"William Shakespeare (gedoopt 26 april 1564 – 23 april 1616) was een Engelse toneelschrijver, dichter en acteur. Hij wordt algemeen beschouwd als de grootste schrijver in de Engelse taal en 's werelds grootste dramaturg. Hij wordt vaak de nationale dichter van Engeland en de "Bard of Avon" (of simpelweg "de Bard") genoemd. Zijn overgebleven werken, inclusief samenwerkingen, bestaan uit ongeveer 39 toneelstukken, 154 sonnetten, drie lange verhalende gedichten, en een paar andere verzen, waarvan sommige een onzekere auteurschap hebben. Zijn toneelstukken zijn vertaald in elke grote levende taal en worden vaker uitgevoerd dan die van enige andere toneelschrijver. Hij blijft wellicht de meest invloedrijke schrijver in de Engelse taal, en zijn werken worden nog steeds bestudeerd en her geïnterpreteerd."

- Selecteer **Opslaan** van de werkbalk.
- Selecteer het tabblad **Associaties**.
- Voor elke taal:
  - Selecteer de **Creëer** knop.
  - Voer in het popupformulier **Nieuw Artikel** een vertaalde titel in, **William Shakespeare**.
  - Stel de Categorie in voor de taal die je hebt geselecteerd.
  - Voer de vertaalde tekst in het veld **Artikeltekst** in (je kunt <a href="https://translate.google.com/" rel="nofollow noreferrer noopener">https://translate.google.com/</a> proberen).
  - Selecteer **Opslaan & Sluiten**.
- Nadat een nieuw artikel voor elke taal is aangemaakt, selecteer **Opslaan & Sluiten**.

## Hoofdmenu

Als je een link naar een artikel voor Alle Talen in het Hoofdmenu hebt en dat artikel later als basis gebruikt voor bijbehorende artikelen in andere talen, moet je de link in het Hoofdmenu wijzigen. Anders zal het wisselen van taal met dat artikel geselecteerd leiden tot een Pagina Niet Gevonden-fout in de geselecteerde taal.

- Selecteer **Menu's**→** Hoofdmenu** in het Administratiemenu.
- Selecteer het menu-item dat je moet wijzigen, bijvoorbeeld **William Shakespeare**.
- Verander het **Taal** veld naar **Engels (en-GB)**.
- Selecteer **Opslaan & Sluiten** in de Werkbalk.

Als er slechts dat ene item in het Hoofdmenu staat, zal die module verdwijnen bij het overschakelen naar andere talen.

*Vertaald door openai.com*

