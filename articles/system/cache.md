<!-- Filename: Cache / Display title: Cache  -->

## Voor Beheerders

Als beheerder biedt Joomla je de mogelijkheid om delen van je site te cachen. Je kunt ervoor kiezen om hele webpagina's of alleen delen van die pagina's te cachen. Deze handleiding legt uit hoe.

Op een webpagina van een Joomla-site zijn er 3 dingen die gecachet kunnen worden:

1. De hele pagina zelf – de Pagina-cache
2. De output van de Joomla-component voor die webpagina – bekend als de Weergave-cache
3. De output van de modules die op die pagina worden weergegeven – bekend als de Module-cache

Je hebt een aantal cache-instellingen waarmee je kunt bepalen wat er gecachet wordt:

1. De systeemplugin "Systeem – Pagina-cache"
2. De Globale Configuratie, Systeemtabblad, Cache-instellingen. Hier kan de Systeem Cache-optie worden ingesteld op
   - UIT – Caching uitgeschakeld
   - AAN – Conservatieve caching
   - AAN – Progressieve caching
3. Veel modules hebben binnen hun opties een Geavanceerd tabblad waarin de Caching kan worden ingesteld op *Gebruik globaal* of *Geen caching*

Zoals hieronder beschreven, zijn er ook regels voor caching die binnen de Joomla-code zijn geïmplementeerd en waarover je geen controle hebt.

Je kunt de cache wissen via het menu Beheerder → Systeem → Cache wissen. Over het algemeen kun je denken aan Joomla als een systeem met 3 niveaus van cache, oplopend in intensiteit:

1. Conservatieve caching
2. Progressieve caching
3. Pagina-caching

Daarnaast kunnen Joomla-ontwikkelaars gebruik maken van cachingfaciliteiten om het resultaat van databasequery's op te slaan, bijvoorbeeld om de responsiviteit van de site te verhogen, maar dit valt buiten het bereik van de mogelijkheden van de Beheerder.

## Paginacaching

Om dit in te schakelen, ga naar Beheerder → Extensies → Plugins. Zoek vervolgens de plugin Systeem – Pagina Cache en schakel deze in. Dit betekent dat sitepagina's nu worden gecached en dat, wanneer ze opnieuw worden opgevraagd, de gecachte pagina wordt geserveerd in plaats van dat deze door Joomla uit de database-informatie wordt gegenereerd. De gecachte pagina blijft geserveerd worden totdat deze vervalt – zoals gedefinieerd door de parameter *Cachetijd* in de Beheerder → Globale Configuratie → Systeem tab → Cache-instellingen.

Als je deze pagina als tutorial leest en de paginacaching wilt testen, kun je de cache-instellingen van de Globale Configuratie het beste instellen op:

- Cachehandler – Bestand
- Pad naar Cachemap – laat leeg
- Cachetijd – 15 (de standaard van 15 minuten)
- Platformspecificieke Caching - Nee
- Systeemcache – UIT – Caching uitgeschakeld

Om te controleren of paginacaching werkt, ga je naar een websitepagina die een artikel weergeeft. Nadat je die pagina hebt weergegeven, zou je in het bestandssysteem een `cache/page`-directory moeten vinden met een bestand erin dat een bestandsnaam heeft zoals `xxx-cache-page-yyy.php`, waarbij xxx en yyy lange hash-strings zijn. Joomla moet afzonderlijke cachepagina's opslaan voor afzonderlijke URL's, dus is de tweede reeks hexadecimale cijfers een hash van de URL van de sitepagina, om de bestandsnaam uniek te maken voor die pagina.

Gebruik vervolgens de Beheerderfunctionaliteit om de tekst van dat artikel te wijzigen en de sitepagina opnieuw weer te geven. Je zou de gecachte versie moeten vinden, niet je gewijzigde tekst.

Het wijzigen van een artikel (of ander Joomla-item) wist de paginacache niet voor de webpagina('s) waarop dat artikel wordt weergegeven. Om de paginacache te wissen, ga je naar Beheerder → Systeem → Cache wissen. Klik op het selectievakje naast de *Cachegroep* genaamd "pagina" en druk op de Verwijderen-knop. Wanneer je je webpagina opnieuw weergeeft, zou je gewijzigde tekst nu moeten worden weergegeven.

Als je site een functie heeft zoals een winkelmandje, zal het toepassen van paginacaching problemen veroorzaken, aangezien pagina's moeten laten zien wat de klant al heeft geselecteerd in plaats van het weergeven van een gecachte pagina die voor iedereen hetzelfde is. Echter, je kunt de plugin Systeem - Pagina Cache configureren om caching uit te sluiten voor gespecificeerde Menu-items of gespecificeerde URL's en URL-bereiken (in het tabblad Geavanceerd), zodat alleen echt statische pagina's worden gecached.

## Conservatieve Caching

Met Conservatieve Caching kun je de View-uitvoer van componenten en de uitvoer van die Modules die caching toestaan, cachen. Let echter op dat dit alleen werkt op pagina's die niet worden gecached met de Pagina Cache. Voor die pagina's wordt de hele webpagina gecached, en Conservatieve Caching wordt niet eens overwogen.

Om Conservatieve Caching in te schakelen:

1. Ga naar Administrator → Systeem → Globale Configuratie → Systeem tab en stel binnen Cache-instellingen de Systeem Cache in op AAN – Conservatieve caching.
2. Ga naar Administrator → Extensies → Modules en selecteer de modules die je wilt cachen. Als die module caching toestaat, zou je onder het tabblad Geavanceerd Caching moeten kunnen instellen op:

- Gebruik Globaal – deze module wordt gecached (aangezien de Globale optie nu is ingesteld op Conservatieve caching).
- Geen caching – deze module wordt niet gecached.

(Houd er rekening mee dat de Cache Tijd in de Globale Configuratie in minuten is, maar de Cache Tijd in de Module-instellingen in seconden.)

Om te controleren of het werkt, ga je naar je site, zorg ervoor dat je uitgelogd bent, en navigeer naar een webpagina die een artikel weergeeft. Controleer je bestandssysteem en je zou een map `cache/com_content` moeten vinden die een cachebestand bevat.

Je zult ook andere mappen vinden zoals `cache/com_languages` (aangezien de pagina weergeven het laden van de huidige taal inhoudt, en deze ook zal worden gecached) en ook mappen die betrekking hebben op modulecache, bijvoorbeeld `cache/com_modules`. Deze zijn het resultaat van het gebruik van cache die ontwikkelaars hebben gecodeerd binnen de Joomla-applicatie.

Als je dat artikel bewerkt en opslaat en vervolgens de sitepagina vernieuwt, zul je ontdekken dat de site de bijgewerkte tekst dit keer weergeeft. Dit komt omdat Joomla elke keer dat de bewerking wordt opgeslagen, de cache voor dat artikel wist.

Je kunt echter aantonen dat de cache werkt door het cachebestand in de map `cache/com_content` te bewerken met een eenvoudige teksteditor. Met de editor verander je één letter in de artikeltekst in het cachebestand en sla je het bestand op. Als je dan de webpagina vernieuwt, zou je de wijziging die je in het cachebestand hebt aangebracht moeten zien.

Hoe kun je selecteren welke componentviews worden gecached, en onder welke omstandigheden? Helaas, dat kun je niet doen. Dit is bepaald door de kerncomponentontwikkelaars van Joomla en gecodeerd in de PHP-code van de component. De criteria zijn verschillend voor elke component. Je kunt echter gemakkelijk ontdekken welke criteria worden gebruikt, omdat ze voor elke sitecomponent zijn gecodeerd in de site `DisplayController.php` bestand. Bijvoorbeeld, ten tijde van deze revisie (Joomla versie 5) voor de component Contacten vinden we in `components/com_contact/src/Controller/DisplayController.php`

```php
    public function display($cachable = false, $urlparams = [])
    {
        if ($this->app->getUserState('com_contact.contact.data') === null) {
            $cachable = true;
        }
```

Dit betekent dat de views die bij contactpersonen horen cachbaar zullen zijn, tenzij er sessiegegevens zijn met com_contact.contact.data als sleutel – wat het geval zal zijn als in de gebruikerssessie de gebruiker een contactformulier heeft weergegeven (bijvoorbeeld op een pagina waarnaar wordt verwezen door een menu-item van het type Contacten → Enkel Contact).

Het equivalente bestand voor artikelen `components/com_content/src/Controller/DisplayController.php` bevat:

```php
    public function display($cachable = false, $urlparams = false)
    {
        $cachable = true;

        /**
         * Stel de standaard weergavenaam en -formaat in op basis van het verzoek.
         * Let op dat we a_id gebruiken om botsingen met de router en de terugkeerpagina te voorkomen.
         * De frontend is iets rommeliger dan de backend.
         */
        $id    = $this->input->getInt('a_id');
        $vName = $this->input->getCmd('view', 'categories');
        $this->input->set('view', $vName);

        $user = $this->app->getIdentity();

        if (
            $user->get('id')
            || ($this->input->getMethod() === 'POST'
            && (($vName === 'category' && $this->input->get('layout') !== 'blog') || $vName === 'archive'))
        ) {
            $cachable = false;
        }
```

De expressie `$user->get('id')` is waar als dit een ingelogde gebruiker is. Dit betekent dat artikelen nooit worden gecached voor ingelogde gebruikers. De daaropvolgende expressies hebben betrekking op andere omstandigheden wanneer de caching niet wordt uitgevoerd, zelfs als de gebruiker niet is ingelogd.

Op deze manier kun je ontdekken onder welke omstandigheden caching wordt uitgevoerd, maar het is niet aan te raden om deze te wijzigen. Je kunt ook aantonen dat modules worden gecached door de Joomla Breadcrumbs-module te gebruiken, ervoor te zorgen dat deze op een bepaalde modulepositie op de webpagina wordt weergegeven, de Caching-optie in te stellen en het gecachete bestand handmatig in cache/mod_breadcrumbs te bewerken.

## Progressieve Caching

Net als Conservatieve Caching, slaat Progressieve Caching ook de output van componentweergaven en modules op. Het functionele verschil tussen de twee is dat bij Progressieve Caching **alle modules altijd worden opgeslagen voor uitgelogde gebruikers**. In dit geval heeft het instellen van de *Geen Caching* optie voor een module geen effect. Als de opslagoptie voor caching is ingesteld op *Bestand*, kun je het cachebestand voor modules vinden (de output van alle modules wordt binnen hetzelfde bestand opgeslagen) in de `cache/com_modules` directory.

Om Progressieve Caching in te schakelen, ga naar Beheerder → Systeem → Globale Configuratie → Systeemtab en stel binnen *Cache-instellingen* *Systeemcache* in op *AAN – Progressieve caching*.

Wat de voorwaarden betreft voor het cachen van Joomla kerncomponentweergaven, **is er geen verschil tussen conservatieve en progressieve caching**. Ondanks wat je misschien leest op sommige websites en antwoorden op vragen op Stack Overflow, is het niet zo dat Conservatieve Caching betrekking heeft op wanneer de gebruiker niet is ingelogd en Progressieve Caching op wanneer de gebruiker is ingelogd.

## Samenvatting

Een samenvatting van de verschillende soorten caching staat hieronder.

### Caching van de hele pagina

- **Configuratie**: Ingebouwde Plugin (Administrator → Extensies →
  Pluginbeheer → Systeem - Pagina Cache)
- **Cachet**: elke gehele pagina van uw site
- **Gebaseerd op**: URL
- **Meer info**:
  - Optionele browsercaching: Cachet ook op de browser/computer van uw bezoekers
  - Cachet alleen pagina's voor gastbezoekers (niet voor ingelogde bezoekers).
    Wees voorzichtig met het gebruik van deze plugin als u een interactieve site heeft waar
    u content wilt serveren op basis van sessie-/cookie-informatie
    in plaats van alleen op de URL. Functionaliteiten zoals een winkelwagen
    zullen niet werken.

### Weergavecaching

- **Configuratie**: Algemene Configuratie -> Cache
- **Cachet**: elke weergave van een component
- **Gebaseerd op**: URL, weergave, parameters, ...
- **Meer info**: Ontwikkelaars van componenten moeten dit in hun code opnemen
  om het te laten werken. Meestal wordt dit niet gedaan. Het Joomla hoofdinhoudcomponent
  gebruikt dit, maar alleen voor gastbezoekers van uw site, hoewel dit niet verplicht is voor elk component.

### Modulecaching

- **Configuratie**: Algemene Configuratie -> Cache
- **Cachet**: elke module (individueel aangepast via de Geavanceerde Parameters van elke module)
- **Gebaseerd op**: de module-id, de gebruikersweergaveniveaus en de *Itemid*
  parameter in de HTTP-verzoek
- **Meer info**: U moet het uitschakelen op sommige modules om problemen te vermijden

### Verdere caching

Als u andere cachesystemen en mogelijkheden wilt bekijken,
wilt u misschien de extensies van derden over caching bekijken.

### Caching engines of opslagplaatsen

- **Configuratie**: Algemene Configuratie -> Cache

Hier kunt u kiezen welk systeem u voor alle caching
van uw site wilt gebruiken. Enkele opties zijn: APC, Eaccelorator, Bestand, Memcache, Redis,
XCache.

APC, bijvoorbeeld, cachet ook uw PHP opcode.

## Voor Ontwikkelaars

<div class="alert alert-warning">
Deze sectie moet worden herzien voor Joomla! 4/5.
</div>

De klasse **JCache** maakt verschillende soorten en niveaus van caching mogelijk. De volgende subklassen zijn specifiek gemaakt, maar je kunt je eigen toevoegen of de hoofdklasse op veel verschillende manieren gebruiken.

Vergeet niet dat het eerste cache-niveau dat wordt aangetroffen, elke diepere caching zal overschrijven. Ik veronderstel dat te veel niveaus ook contraproductief zijn (*te verifiëren echter*).

- **JCacheView** cachet en retourneert de output van een bepaalde view (in MVC). Een cache-id wordt automatisch gegenereerd op basis van de URI, specifieke view en de specifieke methode daarvan, of je kunt je eigen geven.

Dit kan automatisch worden gedaan via de display-functie van de basiscontroller. Bijvoorbeeld in de controller van je component:

    class DeliciousController extends JController {
        function display() {
            parent::display(true); //true vraagt om caching.
        }
    }

Er zijn ook enkele urlparams waar rekening mee moet worden gehouden. Bekijk dit
[Joomla StackExchange](http://joomla.stackexchange.com/questions/5781/how-can-i-use-joomlas-cache-with-my-components-view/7000#7000 "")

Wees er ook van bewust dat eventuele updates (zoals hits of bezoektellingen) NIET zullen worden geüpdatet (tenzij je dit buiten deze methode toevoegt en dus enige diepere MVC-deel).

- **JCachePage** cachet en retourneert de body van de pagina.
- **JCacheCallback** cachet en retourneert de output en resultaten van functies of methoden.

Als je queries wilt cachen, is dit een goede klasse daarvoor, zoals hier geïllustreerd: Caching gebruiken om je code te versnellen

- **JCacheOutput** cachet en retourneert output.

Dit is eerder bedoeld voor het cachen van een specifiek deel van PHP-code. Het functioneert als een output buffer, maar dan gecachet.

*Vertaald door openai.com*

