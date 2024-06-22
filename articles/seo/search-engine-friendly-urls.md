<!-- Filename: Search_Engine_Friendly_URLs / Display title: Zoekmachine vriendelijke URL's -->

"'Zoekmachine vriendelijk (SEF)"', "'voor mensen leesbaar"' of
<a href="https://en.wikipedia.org/wiki/Clean_URL" class="extiw"
title="wikipedia:Clean URL">schone URL's</a> zijn URL's die zinvol zijn
voor zowel mensen als zoekmachines, omdat ze het pad naar de specifieke
pagina waar ze naar verwijzen beschrijven. Sinds versie 1.5, is Joomla!
in staat URL's in alle formaten te creëren, inclusief SEF URL's. Dit is
onafhankelijk van de URL-rewriting uitgevoerd door de web-server, zodat
het zelfs werkt als Joomla! draait op een andere server dan met de
Apache mod_rewrite module. De SEF URL's volgen een bepaald patroon, maar
de gebruiker kan een  korte beschrijvende tekst
(alias)
definiëren voor elk deel van de URL.

Intern heet het lokale gedeelte van een SEF URL (het gedeelte achter de
domeinnaam) de "route"'. Het maken en verwerken van SEF URL's wordt
daarom aangeduid als "'routeren', en de relevante code wordt ook wel een
'router' genoemd.

Een goed voorbeeld van het routeren is de URL naar het "Welkom bij
Joomla!" artikel in de voorbeelddata.

- Zonder SEF URL's ingeschakeld, wordt de URL
  `http://www.example.com/index.php?option=com_content&view=article&id=1:welkom-bij-joomla&catid=1:laatste-nieuws&Itemid=50`
- Met SEF URL's aan en mod_rewrite uit, is het
  `http://www.example.com/index.php/het-nieuws/1-laatste-nieuws/1-welkom-bij-joomla`
- Met beide SEF URL's én mod_rewrite aan, is het
  `http://www.example.com/het-nieuws/1-laatste-nieuws/1-welkom-bij-joomla`

Zoekmachine vriendelijke URL's kunnen worden geactiveerd door het
inschakelen van de "'Zoekmachine vriendelijke URL's" optie bij de
"Algemene instellingen". Deze optie is standaard sinds Joomla! 1.6. Zievoor meer informatie.

## Veel gestelde vragen (Faq)

### Wat betekenen de getallen in de URL?

Door het vergelijken van de oude en de nieuwe URL zien we getallen in de
oude URL,

    http://www.example.com/index.php?option=com_content&view=article&id=1:welkom-bij-joomla&catid=1:latest-news&Itemid=50

maar ook in de nieuwe URL:

    http://www.example.com/the-­news/1­-laatste-­nieuws/1-­welkom-­bij-joomla

Deze getallen zijn de parameters die nodig zijn voor Joomla! om de
interne URL te bepalen en de pagina te tonen die u wilt zien. (In dit
geval is het eerste cijfer de ID van de categorie, het tweede cijfer is
de ID van het artikel.)

### Er is geen `index.php` in de URL meer. Kan ik het bestand nu verwijderen?

Nee! De URL bevat de `index.php` niet meer, maar intern zal de
mod_rewrite doorverwijzen naar het originele pad, zonder dat je het
ziet.

### S:MyLanguage/Alias waarde? En hoe wordt het gemaakt?

Alias wordt getoond onder het Titel veld in Artikelen, Categorieën en
Menu-items. Joomla! kan automatisch de alias aanmaken. Een automatische
aangemaakt alias begint met de titel. Alle hoofdletters worden omgezet
naar kleine letters. Spaties en speciale tekens, die niet zijn
toegestaan in een URL; worden gewijzigd in streepjes.

### Ik wil mijn eigen waarde opgeven als Alias.

Als u de alias die door Joomla! gegenereerd wordt niet mooi vindt, kan
een eigen waarde worden opgeven voor het veld. Velen geloven dat het
gebruik van goede zoekwoorden in de URL helpt bij de zoekmachine
optimalisatie. U kunt dit doen door deze zoekwoorden in de titel op te
nemen en Joomla! de alias te laten maken, of door de alias zelf te
maken.

### Hoe wordt de Alias gebruikt in een URL?

Voor een menu-item, gebruikt Joomla! de alias als URL deel. Stel dat u
de eerste twee SEF URL opties gebruikt en u een menu-item genaamd
Producten maakt, dan wordt de URL: voorbeeld.com/producten.

Joomla! maakt ook gebruik van de primaire sleutel van de gegevens binnen
de URL om de router te helpen naar de juiste pagina te navigeren. Verder
gaand met het vorige voorbeeld: Als uw producten menu-item naar een
artikel/categorie blog was, dan zou de link naar de titel van het
artikel en/of de 'lees meer' link uit drie delen bestaan:

- De menu-item-URL - voorbeeld.com/producten;
- Plus, de primaire sleutel voor de categorie en de categorie alias -
  32-fruit;
- Plus, de primaire sleutel voor het artikel en het artikel alias -
  1-appel;

De volledige URL is: `http://voorbeeld.com/producten/32-fruit/1-appel`

### Hoe kan ik de getallen in de SEF URL's kwijtraken?

    De nummers in de SEF URL zijn nodig voor Joomla!'s-router om het directe verkeer op de site te sturen. Zodra de router logica stabiliseert, kunnen eenvoudige plugins van anderen ontwikkeld worden voor het verbeteren van de routeer-mogelijkheden door meer keuze toe te laten. Op dat moment, zullen cijfers waarschijnlijk uit de URL verwijderd worden.

## Route formaten en het routerings-mechanisme

"Deze sectie beschrijft Joomla!'s core (ingebouwd)
routerings-mechanisme. Routerings-extensies kunnen de manier waarop
routeringen worden gemaakt binnen uw systeem veranderen."

### Route formaten

Om het routerings-mechanisme van Joomla! in meer detail te beschrijven,
moeten we eerst vaststellen wat we een "route" noemen. Stel dat Joomla!
is geïnstalleerd in `http://voorbeeld.com/sites/eerst/`. Het pad voor de
installatie wordt in het algemeen aangeduid als "basis-URL"'. Een
mogelijke voorbeeld URL is
`http://voorbeeld.com/sites/eerst/producten/32-fruit/1-appel`. Het
eerste deel van deze URL is de eerder genoemde basis-URL, en noch
Joomla!, noch enige andere router kunnen URL's met een ander eerste deel
maken. Het tweede deel, `producten/32-fruit/1-appel`, is een "route",
bestaande uit drie "onderdelen".

Het eerste onderdeel van een route is, voor normale URL's, de alias van
een menu-item. De SEF URL wordt zogenaamd "'doorgeleid naar"' dat
menu-item. De andere onderdelen worden volledig bepaald door de router
van de component bij het 'type' van het menu-item. Het "Categorie -
Blog" menu-item-type, bijvoorbeeld, wordt verzorgd door de
<a href="https://docs.joomla.org/Special:/MyLanguage/Inhoud" class="new"
title="Special:/MyLanguage/Inhoud (page does not exist)">S:/MyLanguage/Inhoud</a>
component, en dat onderdeel van de router is dus verantwoordelijk voor
de opbouw en ontleding van de overige onderdelen.

Het is ook mogelijk (voor extensies) het systeem te vragen om een route
te creëren zonder een menu-item. In dat geval zal het systeem meestal
besluiten een speciale route te maken die het woord `component` als
eerste onderdeel heeft. Deze routes worden gemaakt met een vaste
indeling: de naam van de component (zonder het voorafgaande `com_`) is
gekozen als tweede onderdeel en eventuele parameters als de andere
onderdelen.

### Beperkingen

Het is belangrijk te weten dat het creëren van een menu-item de "enige"
manier voor een Joomla! gebruiker is om een route te definiëren die
leidt naar een specifiek onderdeel. Het is echter mogelijk om een route
te creëren, zonder dat het op de site (in het menu) zichtbaar is. Een
vaak toegepaste methode is het aanmaken van een menu-item in een menu
dat nergens weergegeven wordt. Zo' n menu wordt meestal een <a
href="https://docs.joomla.org/index.php?title=S/MyLanguage/Menu&amp;action=edit&amp;redlink=1"
class="new" title="S/MyLanguage/Menu (page does not exist)">verborgen
menu</a> genoemd.

De voorgaande paragraaf geeft aan dat het niet mogelijk is om één
component verantwoordelijk te maken voor de verwerking van alle routes.
Het is bijvoorbeeld niet mogelijk om aan te geven dat de URL
`http://voorbeeld.com/dealias` de Inhoud van het item met de alias
`dealias` moet weergeven, waarbij `dealias` ieder willekeurig woord kan
zijn. Als dit gedaan moet worden voor een klein aantal artikelen, dan
kunnen handmatig menu-items worden aangemaakt. Anders is een
routerings-extensie noodzakelijk.

Dit routerings-mechanisme is dus niet zo flexibel als gebruikers soms
willen. Aan de andere kant, het heeft één groot voordeel: het vermindert
de kans op een dubbele routes (routes die kunnen leiden naar twee
verschillende pagina's). Aangezien het eerste deel van een route altijd
een menu-item alias is, weet het systeem direct welke component-router
moet worden gebruikt om het te ontleden.

## Details over de implementatie

### Afhandelen routes

"Deze sectie beschrijft de routerings uitvoering. Kijk, als u een
ontwikkelaar van componenten bent, bij [het ondersteunen van SEF URL's
in uw
component](https://docs.joomla.org/Supporting_SEF_URLs_in_your_component "Special:MyLanguage/Supporting SEF URLs in your component")."

Joomla routes worden gemaakt en herleid door
<a href="https://docs.joomla.org/JRouter" class="new"
title="Special:MyLanguage/JRouter (page does not exist)">de JRouter
class</a>. Deze class kijkt in de root van de actieve component
(opgegeven in het `option` parameter van de query string) en bevat het
`router.php` bestand in de hoofdmap van de component. Het roept dan een
van de twee functies aan: één voor het aanmaken van de SEF URL en één
voor het interpreteren van de SEF URL.

De JRouter class wordt overschreven door het Joomla CMS in
`/includes/router.php`. In dit bestand wordt de opbouw en ontleed
functie overschreven om een juiste URL op te bouwen of te ontleden voor
het Joomla CMS.

Het `router.php` bestand in iedere component (bijvoorbeeld
`/components/com_content/router.php`) moet de volgende twee functies
bevatten:

- ContentBuildRoute - deze bouwt de SEF URL op
  - Parameters
    - \$query - dit is een array die de querystring variabelen bevat
  - Returns: een array met segmenten, waarbij elk segment gescheiden
    wordt door een '/' die later, als combinatie, tot de werkelijke URL
    wordt herleid (de items in de array mogen geen '/' tekens bevatten)
- ContentParseRoute - deze interpreteert een SEF URL
  - Parameters
    - \$segments - dit is een array met de segmenten van de gevraagde
      URL.
  - Returns: een name =\> value array van de querystring variabelen waar
    de link naartoe verwijst

### De SEF Plugin

De Joomla "System - SEF" plugin erft `JPlugin` en voert de
`onAfterRender()` functie uit. In deze functie wordt de body van de
reactie die wordt verzonden naar de browser opgehaald met behulp van
`JResponse::getBody()`. De body van de reactie wordt vervolgens
doorzocht naar links met de `/index.php...` en vervangen door een juiste
SEF URL door `JRoute::_("url")` aan te roepen.

JRoute bouwt SEF URL's op door het instantiëren van een `JRouter` object
en het te vragen de juiste link uit de doorgegeven URL op te bouwen.

### Afhandelen SEF URL's

Standaard worden de SEF URL's afgehandeld door het `JRouterSite` object
(uit `/includes/router.php`) en wordt aangeroepen door een call naar
`JApplication::route()` in index.php. Deze aanroep wordt gedaan in de
`$app` variabele, die eigenlijk een instantie van `JSite` is (uit
`/includes/application.php`).

`JApplication::route()` is het niet-destructieve resultaat van de
`$_GET` array. Dat betekent, dat `JApplication::route()` variabelen vult
in `$_GET` door het aanroepen van `JRequest::set()` met het overwrite
flag op false. Als dus de naam van een variabele die komt uit
`JRouter::route()` al in `$_GET` staat, dan zal die waarde niet in
`$_GET` gezet worden. Dit maakt aangepaste routering mogelijk.

### Aangepaste routering

Joomla geeft de mogelijkheid uw eigen routerings mechanisme aan te
maken. Om dit mechanisme te gebruiken moet u beschikken over een plugin
die de `JPlugin::onAfterInitialise()` functie overschrijft. Deze functie
ontleedt de URL en maakt de noodzakelijke variabelen aan in `$_GET` voor
de standaard Joomla routering wordt uitgevoerd.

"Zie  Het maken van een Systeem plugin om JRouter uit te
breiden
als voorbeeld."
