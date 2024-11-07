<!-- Filename: https://magazine.joomla.org/all-issues/may-2022/joomla-new-http-headers-plugin-for-j4 / Display title: HTTP-headers  -->

## Tijdschriftartikel

Dit artikel is gebaseerd op een Joomla! Community Magazine artikel door Brendan Hedges in de editie van mei 2022.

Hoewel geschreven voor Joomla 4, is de inhoud evenzeer van toepassing op Joomla 5.

## Joomla’s Nieuwe HTTP Headers Plugin Voor J4

Aansluitend op het artikel van vorige maand over beveiliging, wachtwoorden en Joomla's WebAuthn-plugin, kijken we deze maand naar een andere Joomla-beveiligingsfunctie die is geïntroduceerd met J4. Dat is de HTTP Headers-plugin, die nu deel uitmaakt van de kernfuncties van Joomla.

Het internet ontwikkelt zich voortdurend en Joomla blijft nooit ver achter. Daarom kies ik het als mijn favoriete webontwikkelingsplatform. Of je website nu een kleine lokale website is of een volledig uitgeruste E-commerce platform met miljoenen aan omzet, het Joomla-framework heeft voor iedereen iets te bieden en blijft nieuwe technologieën implementeren. Sommige zijn zelfs baanbrekend.

> De introductie van de HTTP Headers-plugin in de kern van Joomla 4 is een grote stap voorwaarts in het helpen beveiligen van je website tegen aanvallen en kwaadaardige activiteiten.

Deze systeembeveiligingsplugin helpt site-eigenaren eenvoudig de HTTP-beveiligingsheaders te configureren vanuit het vertrouwde Joomla-backend, in plaats van te moeten rommelen in het htaccess-bestand of andere configuratiebestanden. Of, nog erger, je webhosting Cpanel.

Kijk eens hoe ingewikkeld het is om dit in Cpanel in te stellen en vertel me dat je geen fout zult maken! En dat alles terwijl je ervan uitgaat dat je, zodra het framework in Apache is geïnstalleerd en de mappen zijn aangemaakt, weet wat het correcte formaat is om de HTTP headers toe te voegen die je wilt integreren.

Hoe vaak heb je geprobeerd een htaccess-opdracht te implementeren om je website te herladen en vervolgens een http500-fout te krijgen?

Het grootste probleem is dat als je het format van je HTTP-header niet perfect krijgt, je je site kapot maakt.

Zelfs dan kan hetgeen dat voor de ene website werkt niet werken voor een andere. Een goed voorbeeld hiervan is mijn htaccess-bestand en de manier waarop ik de browser instel om een niet-www https-versie van mijn website te laden:
```  
##www naar niet-www en mixen van http naar https
RewriteCond %{HTTPS} off [OF]
RewriteCond %{HTTP_HOST} ^www\. [NC]
RewriteRule ^ https://mijnwebsite.nl%{REQUEST_URI} [R=301,L,NE]
##Einde www naar niet-www en mixen van http naar https
```

Dit werkte prima voor mijn vorige hostingbedrijf. Maar toen ik naar een andere host overstapte, werkte het niet meer. Ga d'r maar aan staan!

De htaccess-code die ik nu moet gebruiken om hetzelfde resultaat te behalen ziet er als volgt uit:
```  
##www naar niet-www en mixen van http naar https
RewriteCond %{HTTP_HOST} ^www\.(.*)$ [NC]
RewriteRule ^(.*)$ https://%1/$1 [R=301,L]
RewriteCond %{ENV:HTTPS} !on
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [R=301,L]
##Einde www naar niet-www en mixen van http naar https
```

Verwarrend, toch? En als je maar één foutje maakt in het formatteren, BAM! Je hebt je website kapot gemaakt! Nou ja, in ieder geval totdat je je code hebt gefixt.

Daarom betekent het simpel houden, als onderdeel van de Joomla-kern, minder frustratie, minder tijd verspild aan het googelen van je fouten, en meer tijd voor feestvieren terwijl je achterover leunt in je stoel en je nieuwe website bewondert.

Laten we dus eens kijken wat HTTP-headers eigenlijk zijn, hoe je de plugin kunt vinden en wat je ermee kunt doen. Het is hier echter de moeite waard om te vermelden dat deze Joomla-functie een geavanceerde functie van Joomla is, die meer geschikt is voor data-gevoelige websites, in plaats van de nieuwe website die je liefdevol hebt gemaakt over je schattige kittens. Echter, zelfs eenvoudige websites moeten zo veilig mogelijk zijn om te voorkomen dat kwaadaardige code wordt uitgevoerd nadat ze je website hebben gehackt.


## Wat zijn HTTP Headers?

HTTP headers moeten niet verward worden met de &lt;head&gt; sectie van je HTML-document. Ze zijn totaal verschillend. HTTP headers vormen de preambule tussen je webserver en de browser. Een set instructies die de browser vertellen wat, of belangrijker nog, wat niet aan de bezoeker getoond moet worden.

Je kunt de HTTP headers bekijken en zien hoe ze betrekking hebben op individuele HTML-objecten in de ontwikkelaarshulpmiddelen (DEV Tools) van je browser. In Google Chrome open je de ontwikkelaarshulpmiddelen en vervolgens het tabblad Netwerk. Vernieuw nu de webpagina en klik op een HTML-element in het linker paneel. Het toont de HTTP-header voor dat item in het rechter paneel.

In de afbeelding hieronder kun je zien dat de gemarkeerde afbeelding een HTTP-status van 200 retourneert, wat betekent dat de browser deze heeft gevonden. Er is ook een reeks andere informatie gekoppeld aan dat item, zoals bestandsgrootte en bewerkingsdata.

![Joomla http headers 1](../../../en/images/security/http-headers-dev-tools-headers.png)

Als een van je HTML-items niet wordt weergegeven, kun je ook een aanwijzing over de reden ervan vinden in de HTTP headers. In dit voorbeeld is de tweede afbeelding niet weergegeven en je kunt uit de informatie in de rechter paneel opmaken dat er geen HTTP-headerinformatie beschikbaar is.

Behalve het cryptische bericht:

**Referrer Policy:** 'strict-origin-when-cross-origin'

'Strict-origin-when-cross-origin' betekent simpelweg dat wanneer een HTML-item (in dit geval een afbeelding) van een andere bron komt (niet je server), de op dat moment ingestelde HTTP-headerpolicy moet worden gevolgd. In dit voorbeeld zullen de HTTP headers, zoals ingesteld in de Joomla-plugin, alle afbeeldingen afwijzen die niet afkomstig zijn van deze of een andere specifiek in de HTTP-headerparameters van de Joomla-plugin 'opgenomen' website.

Dus, wanneer de afbeelding vanuit het HTML-document wordt aangeroepen, wordt deze door de browser geweigerd en niet geladen.

![Joomla http headers 2](../../../en/images/security/http-headers-dev-tools-headers-reject.png)

Dit verschilt van niet gevonden worden en een 404 niet gevonden HTTP-foutmelding retourneren. In deze situatie wordt nog steeds naar de afbeelding gezocht op de server waar deze gehost wordt, maar de browser heeft deze niet gevonden.

![Joomla http headers 3](../../../en/images/security/http-headers-dev-tools-headers-not-found.png)

## Wat de Joomla HTTP Headers Plugin doet

Naast het de browser vertellen wat te tonen en het retourneren van algemene informatie over het HTML-document, helpen HTTP Headers bij het beperken van aanvallen en beveiligingsrisico's die u mogelijk op uw Joomla-website heeft. Daar komt de Joomla HTTP Headers plugin tot zijn recht. Dit bereikt het door HTML-content expliciet weer te geven op basis van uw instellingen in de Joomla HTTP Headers plugin zelf.

Door extra op beveiliging gebaseerde HTTP-headers toe te voegen aan uw Joomla-website met de HTTP Header plugin, biedt u nog een extra beveiligingslaag voor uw Joomla-website.

Dit is belangrijk, omdat een HTML-webpagina standaard al zijn inhoud aan uw bezoeker zal tonen, goed of slecht. Tenzij er expliciet wordt aangegeven dit niet te doen in de HTTP-headers van de webpagina. De plugin doet dit door u de mogelijkheid te bieden om de geavanceerde beveiligingsopties die beschikbaar zijn in de Content-Security-Policy voor uw website te configureren. De plugin kan anders worden geconfigureerd voor elke website, afhankelijk van uw eisen, waardoor het een werkelijk flexibel wapen is in uw arsenaal tegen hackers.

## Waarom heb ik deze plugin nodig?

In een ideale wereld zou je dat niet nodig hebben. Echter, in de wereld waarin we leven, zijn er veel te veel gewetenloze mensen die manieren proberen te vinden om geld te verdienen aan de onschuldige en argeloze mensen. In onze wereld noemen we deze mensen hackers. Hackers doen hun best om kwetsbaarheden in software uit te buiten voor geldelijk gewin, vaak ten nadele van de eigenaar van de website.

Door gebruik te maken van Joomla's HTTP Header plugin om te controleren welke inhoud aan uw bezoekers wordt geserveerd, verkleint u de kans dat hackers schadelijke website-inhoud aan uw bezoekers kunnen serveren via verouderde kwetsbare plugins. Dit helpt om kwaadaardige scriptinjecties op uw website te stoppen.

**Laten we even nadenken over deze hypothetische situatie.**

U heeft een mooie Joomla 3 website. Die is 5 jaar geleden gemaakt en ziet er nog steeds perfect uit en werkt perfect. Al uw componenten, plugins en modules zijn up-to-date. Perfect, toch?

Nou, niet helemaal, want toen u vijf jaar geleden uw website maakte, installeerde u de trendy Foo Bar Plugin om "FOO BAR" op uw startpagina af te drukken. Het zag er in het begin cool uit, maar na een tijdje veranderde u van gedachten en verwijderde de plugins {foo}FOO - BAR{/bar} shortcode uit uw homepage artikel.

Maar, hier is het probleem: u heeft de plugin zelf niet gedepubliceerd of verwijderd en het gebruik ervan raakte in de vergetelheid. **Hier zijn we allemaal schuldig aan, daar ben ik zeker van.**

Snelle sprong naar vandaag, 5 jaar later, die plugin staat nog steeds op uw website, gepubliceerd en actief, maar het is al 5 jaar niet bijgewerkt omdat u het lang geleden bent vergeten of de auteur is gestopt met de ondersteuning ervan. Nu heeft een duister figuur opgemerkt dat deze plugin een beveiligingslek heeft dat kan worden uitgebuit om een **Cross Site Scripting (XSS)** aanval op uw website te starten en uw nietsvermoedende bezoekers tot slachtoffers te maken.

Cross-site scripting, ook bekend als XSS, is een beveiligingslek in uw website dat een aanvaller in staat stelt om de interacties die uw gebruikers met uw nu kwetsbare website hebben te compromitteren.

De aanvaller/hacker gebruikt XSS om uw kwetsbare website uit te buiten door een schadelijk script naar uw nietsvermoedende gebruiker te sturen. Omdat het script van uw website komt, weet of vermoedt de browser van uw gebruiker niet dat het script niet vertrouwd moet worden en voert het script uit wanneer de webpagina wordt geladen en geopend.

Kwaadaardige scripts die op deze manier worden uitgevoerd, kunnen veel problemen veroorzaken voor uw gebruiker, van het stelen van inlogwachtwoorden en gebruikersnamen in cookies tot het sturen van uw gebruiker naar valse phishing-websites. Scripts kunnen zelfs het uiterlijk van de webpagina die uw website serveert veranderen en u andere advertenties laten zien.

Met behulp van **Joomla's HTTP Headers plugin** voorkomt u cross-site scripting door ervoor te zorgen dat alleen de scripts en inhoud die u aan uw bezoeker wilt serveren, daadwerkelijk worden geserveerd. Alles wat hier niet aan voldoet, wordt geblokkeerd.

Dus, in het bovenstaande voorbeeld had u de HTTP Headers plugin kunnen configureren om alleen de JavaScript (script) bestanden van uw website vanuit een opgegeven map te serveren, of misschien een CDN als u er een gebruikt, om de aanval te stoppen.

U zou ook kunnen voorkomen dat de website inline JavaScript uitvoert dat in de HTML is ingebed. Maar, wees ervan bewust dat dit, afhankelijk van hoe u uw website HTML heeft ontworpen, verderop problemen kan veroorzaken.

Dit zou helpen om te voorkomen dat kwaadaardige JavaScript-code op uw website wordt uitgevoerd. Zelfs als uw kwetsbare Foo Bar Plugin de schuld was dat een hacker in de eerste plaats kwaadaardige code in uw website kon injecteren.

**Opmerking:**

> Veel voorkomende zwakke punten op websites die vatbaar zijn voor XSS-aanvallen zijn invoervelden voor gebruikers (gebruikersloginpagina's, nieuwsbrief aanmeldformulieren, contactformulier, enz.) zonder validatie en codering.

## Waar is de HTTP Headers-plugin?

Je kunt de HTTP Headers-plugin van Joomla vinden samen met alle andere Joomla-plugins en deze is toegankelijk op precies dezelfde manier zoals je gewend bent te doen.

![Joomla http headers 4](../../../en/images/security/http-headers-plugins.png)

## Het gebruik van de HTTP-headersplugin

Het gebruik van Joomla's HTTP Plugin is relatief eenvoudig, hoewel het een goed idee kan zijn om, voordat je wijzigingen aanbrengt in de standaardinstellingen, je te verdiepen in enkele van de speciale termen die betrekking hebben op het gebruik ervan. Hoewel, hierbij gezegd, sommige van deze termen al bekend bij je zouden moeten zijn.

**Bijvoorbeeld:**

Wanneer je met afbeeldingen werkt, zul je de term 'img-src' tegenkomen, waarbij 'img' verwijst naar afbeeldingen en 'src' naar de geldige bron van de afbeelding. Deze termen kennen we al vanuit de basis van HTML.

Aan het einde van dit artikel vind je een lijst met nuttige websites met extra informatie om je te helpen deze Joomla-plugin te gebruiken.

## HTTP Headers Plugin-instellingen - Tabblad 1

Wanneer je de plugin opent, is het eerste geopende tabblad de basisinstellingen van de plugin. Hier kun je aanpassingen doen aan X-Frame-opties, de Referrer-Policy, de Cross-Origin-Opener-Policy en ook Force HTTP Headers. Er zijn ook enkele links voor meer informatie om je te helpen begrijpen wat deze items in meer detail doen.

**Laten we elk van deze op hun beurt bekijken.**

![Joomla http headers 5](../../../en/images/security/http-headers-plugins-tab-plugin.png)

### X-Frame-opties

De eerste instelling is voor de X-Frame-opties. **Deze is standaard ingeschakeld.**

Met deze optie kun je beslissen of de inhoud van je website kan worden getoond op een andere website in een &lt;frame&gt;, &lt;iframe&gt;, &lt;embed&gt; of &lt;object&gt;. Als je deze optie uitschakelt, kan elke andere website jouw website in een iframe weergeven.

Zodra deze is ingeschakeld, wordt een 'x-frame-options: SAMEORIGIN'-tag toegevoegd aan de headers van je website. Deze tag stelt je nog steeds in staat om je eigen inhoud te tonen in een &lt;frame&gt;, &lt;iframe&gt;, &lt;embed&gt; of &lt;object&gt; op je eigen website. Maar niemand anders kan jouw inhoud in een &lt;iframe&gt; op hun eigen website tonen.

![Joomla http headers 6](../../../en/images/security/http-headers-plugins-headers.png)

De X-Frame-optie-header helpt je website en gebruikers te beschermen tegen **‘Click Jacking’**-aanvallen. Dit is wanneer een aanvaller een &lt;iframe&gt; op hun eigen website plaatst en de bron van het &lt;iframe&gt; instelt als jouw website. Vervolgens gebruikt de aanvaller meerdere transparante lagen van hun eigen website erboven.

Hierdoor wordt een gebruiker ertoe gebracht om op een knop of link op de transparante bovenste laag te klikken, omdat de gebruiker denkt dat ze klikken op een link in het iframe eronder.

Dus, de aanvaller **“kaapt”** klikken die bedoeld zijn voor de originele pagina in het frame en stuurt ze naar een andere webpagina.

Nog ernstiger is dat soortgelijke praktijken kunnen worden gebruikt om toetsaanslagen te oogsten voor wachtwoorden en gebruikersnamen van inloggegevens van e-mailaccounts, sociale media-accounts en natuurlijk jouw bankrekening.

De meeste moderne browsers ondersteunen X-Frame-opties, wat geweldig is. Dus, mijn aanbeveling zou zijn om deze instelling in de HTTP-headers-plugin in te schakelen om je gebruikers te helpen beschermen tegen ‘Click Jacking’.

**De meeste moderne browsers ondersteunen de X-Frame-opties.**

![Http headers browser support](../../../en/images/security/http-headers-plugins-xframe-browser-support.png)

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem; ">
Samenvatting

Stel dit in op inschakelen. Dit zal wereldwijd beperken wat er kan worden gedaan met &lt;frame&gt;, &lt;iframe&gt;, &lt;embed&gt; of &lt;object&gt; op je website. Om uitzonderingen toe te voegen, gebruik 'Force HTTP Headers' om gedetailleerde uitzonderingen toe te voegen.
</div>

### Referrer-Policy

Het volgende item op de lijst in het eerste tabblad is de **Referrer-Policy**. Dit, als ingeschakeld, stelt je in staat om te kiezen hoeveel van je potentiële websitegegevens worden overgedragen naar een andere website als een link, of een ander HTML-object, op je website wordt aangeklikt.

Gewoonlijk zien we dit ingesteld als een HTML-kenmerk op &lt;a&gt;-tags, waarbij je mogelijk een link zou opmaken als &lt;a href="https://someplace.com" rel="noreferrer"&gt;Klik hier&lt;/a&gt;. De noreferrer-tag houdt de details van de verzendende webpagina geheim voor de ontvangende webpagina. Dit doet het door de verwijzingsinformatie van de HTTP-header van de webpagina te verwijderen.

Zich bewust zijn van de gegevens die je website mogelijk 'lekt' naar een andere website waarnaar je linkt, is een belangrijk onderdeel van het beveiligen van je website en gebruikers.

Dit is vooral belangrijk als je gebruikersregistratie toestaat, het gevoelige gegevens bevat, of als je website met monetaire transacties omgaat. Joomla's HTTP Headers-plugin helpt dit op globaal niveau te beheersen, in plaats van op individueel linkniveau.

Standaard is het Referrer Policy van je website ingesteld op 'strict-origin-when-cross-origin'. Wat geen van de verwijzingsgegevens van de originele webpagina blokkeert, tenzij deze naar een minder veilige http-pagina worden verzonden. Maar, aangezien de meeste webpagina's tegenwoordig https gebruiken, is dit nu een groter probleem dan het ooit was.

![Joomla http headers 8](../../../en/images/security/http-headers-plugins-headers-referer-policy.png)

Er zijn natuurlijk veel onschuldige toepassingen van deze 'gelekte' gegevens als je geen Referrer Policy voor je website vaststelt. Deze kunnen gegevens bevatten die worden verzameld door de gelinkte website voor analyses, logging of geoptimaliseerde caching.

Helaas gebruikt niet elke verwijzende website daarbuiten je 'gelekte' gegevens voor zulke onschuldige operaties. Neem het volgende geval als voorbeeld.

De meeste websites die gebruikersregistratie toestaan, hebben een wachtwoord herstelkoppeling naast hun inlogformulier op een login/registreer webpagina. Het is ook waarschijnlijk dat de webpagina ook andere links naar externe websites, sociale medialinks, of misschien enkele 'Handige Links' in de voettekst bevat.

Deze leiden allemaal weg van je veilige omgeving. Nu, als er geen Referrer Policy van kracht is, is het mogelijk dat de Referrer Header die naar een van die externe websites wordt verzonden wanneer een link wordt aangeklikt vanaf die login webpagina, de wachtwoord herstelkoppeling bevat. Evenals andere informatie die je met die externe website hebt gedeeld.

Dit zou een beveiligingsrisico voor de gebruiker kunnen vormen door hun gegevens in gevaar te brengen.

Vanwege het potentiële beveiligingsrisico op dit soort gegevensgevoelige pagina, is het ook goed gebruik om alle inhoud van derden van de pagina te verwijderen. Dit zou alle links en inhoud bevatten die in &lt;iframes&gt; worden geleverd, zoals sociale mediawidgets en YouTube-video's. Aangezien op deze pagina ingevoerde gegevens kunnen worden verzonden via de Referrer Header naar die sites als je op die schattige kittenvideo klikt die net is verschenen.

Joomla's HTTP Headers-plugin pakt dit probleem aan door je in staat te stellen te kiezen uit een van de 8 Referrer Policies om een Referrer Policy voor je website vast te stellen. Elk met hun eigen beperkingen op wanneer en hoeveel gegevens te delen.

![Joomla http headers 9](../../../en/images/security/http-headers-plugins-headers-referer-policy-setting.png)

Laten we eens naar deze kijken. Er is een uitstekende beschrijving van hen op de Mozilla Headers-pagina die deze beschrijft als:

* **no-referrer**<br>
    De Referrer Header zal worden weggelaten: verzonden verzoeken bevatten geen verwijzingsinformatie.
* **no-referrer-when-downgrade**<br>
    Stuur de bron, het pad en de querystring in de Referrer Header wanneer het protocolbeveiligingsniveau hetzelfde blijft of verbetert (HTTP→HTTP, HTTP→HTTPS, HTTPS→HTTPS). Stuur de Referrer Header niet naar minder veilige bestemmingen (HTTPS→HTTP, HTTPS→bestand).
* **origin**<br>
    Stuur alleen de bron in de Referrer Header. Bijvoorbeeld, een document op https://example.com/page.html stuurt de verwijzer https://example.com/.
* **origin-when-cross-origin**<br>
    Bij dezelfde oorsprong een verzoek uitvoeren naar hetzelfde protocolliveau (HTTP→HTTP, HTTPS→HTTPS), stuur de bron, het pad en de querystring. Stuur alleen de bron voor cross-origin verzoeken en verzoeken naar minder veilige bestemmingen (HTTPS→HTTP).
* **same-origin**<br>
    Stuur de bron, het pad en de querystring voor verzoeken van dezelfde oorsprong. Stuur de Referrer-header niet voor cross-origin verzoeken.
* **strict-origin**<br>
    Stuur alleen de bron wanneer het protocolliveau hetzelfde blijft (HTTPS→HTTPS). Stuur de Referrer-header niet naar minder veilige bestemmingen (HTTPS→HTTP).
* **strict-origin-when-cross-origin (standaard)**<br>
    Stuur de bron, het pad en de querystring bij een verzoek vanuit dezelfde oorsprong. Voor cross-origin verzoeken stuur alleen de bron wanneer het protocolliveau hetzelfde blijft (HTTPS→HTTPS). Stuur de Referrer-header niet naar minder veilige bestemmingen (HTTPS→HTTP).
    **Opmerking:** Dit is het standaardbeleid als je geen beleid specificeert, of als de opgegeven waarde ongeldig is. Voorheen was de standaard no-referrer-when-downgrade.
* **unsafe-url**<br>
    Stuur de bron, het pad en de querystring bij elke aanvraag, ongeacht de beveiliging.
    **Waarschuwing:** Dit beleid zal mogelijk privé-informatie lekken van HTTPS-bron-URL's naar onveilige oorsprongen. Overweeg de impact van deze instelling zorgvuldig.

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem; ">
Samenvatting

Als een goed startpunt, tenzij er een reden is om dat niet te doen, zou ik dit instellen op ‘no-referrer’, dus een algeheel ‘deel niets’-beleid voor je website. Of, 'origin-when-cross-origin', wat je in staat zou stellen om verkeer op URL's binnen je eigen website te analyseren (dus geen gegevens ‘lekkage’), maar alleen je domein als verwijzend domein naar de externe website te sturen, omdat geen ‘extra’ gegevens van de URL aan de Referrer-header worden toegevoegd.
</div>

### Cross-Origin-Opener-Policy

De derde instelling om in het eerste tabblad in te stellen is de Cross Origin Opener Policy, wat een browsergebaseerde beveiligingsfunctie is die je in staat stelt om verschillende **‘Browser Context Groups'** van elkaar te scheiden.

![Joomla http headers 10](../../../en/images/security/http-headers-plugins-headers-cross-origin-opener-policy.png)

Een goed voorbeeld hiervan is het gebruik van pop-ups. Waar de originele browser contextgroep (alle tekst, afbeeldingen, links enz.) wordt losgekoppeld van een nieuwe browser contextgroep die wordt aangemaakt en vervolgens wordt weergegeven in de pop-up.

![Joomla http headers 10](../../../en/images/security/http-headers-plugins-headers-cross-origin-opener-popup.png)

> Deze HTTP Header optie is vrij diepgaand en ingewikkeld, hoewel er slechts 3 opties zijn. Dus ik moedig je aan om de links hieronder te bekijken om een beter begrip te krijgen van waarom deze optie moet worden ingesteld op je website. Evenals om te leren over enkele van de geavanceerde functies die beschikbaar voor je worden wanneer deze optie actief is.

De Cross Origin Opener Policy helpt om een historische zwakke plek in de manier waarop browsers gegevens delen tussen verschillende contextgroepen te dichten, vooral wanneer pop-ups op de website worden gebruikt.

Het instellen van je **COOP** zal je helpen om databeveiligingsbedreigingen te verminderen, waarvan de meest voorkomende vaak wordt aangeduid als **‘Spectre’**. Spectre maakt gegevens die in dezelfde contextgroep worden geladen als jouw code mogelijk leesbaar voor een hacker. Spectre maakt het mogelijk om de tijd te meten die bepaalde operaties in beslag nemen. Hierdoor kunnen die hackers raden wat er in de CPU-cache zit. Als ze daarin slagen, weten ze wat zich in het werkgeheugen bevindt. Ze hebben dan toegang tot je gegevens. Die gevoelig kunnen zijn.

**COOP** werkt door je originele HTML-documentgegevens te isoleren van de HTML-gegevens die in een pop-up van het originele document zouden worden getoond. Dit helpt om te voorkomen wat wordt aangeduid als **cross-origin aanvallen, of XS-Leaks**.

Dit proces is als de bekende rel="noopener" die we gebruiken op reguliere links. Maar in tegenstelling tot de rel="noopener" die alleen actief is op uitgaande links, beperken documenten die de cross-origin-opener-policy in de HTTP-headers hebben ingesteld door de Joomla-plugin, gegevens in beide richtingen. Dus, het HTML-document met een actieve COOP-policy zal er geen verwijzing naar hebben in de HTTP-header, en de window.opener HTTP-header-eigenschap van het nieuwe venster zal worden ingesteld op null.

Bij het instellen van deze optie in de Joomla HTTP Header-plugin, zijn er 3 opties beschikbaar voor je.

* **unsafe-none**<br>
    Dit is de standaardwaarde. Het stelt je document in staat om te worden toegevoegd aan de browsing contextgroep van zijn opener, tenzij de opener zelf een cross-origin-opener-policy heeft van dezelfde oorsprong of dezelfde oorsprong die pop-ups toestaat.
* **same-origin-allow-popups**<br>
    Deze optie behoudt referenties naar nieuw geopende vensters of tabbladen die ofwel geen cross-origin-opener-policy instellen, of die zichzelf uit isolatie uitsluiten door een cross-origin-opener-policy van unsafe-none in te stellen.
* **same-origin**<br>
    Isoleert de browsing contextgroep alleen naar documenten van dezelfde oorsprong. Cross-origin documenten worden niet geladen in dezelfde browsing contextgroep.

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem; ">
Samenvatting

Een goed startpunt voor je website zou zijn om deze optie in de plugin ingesteld te laten op same-origin, wat de standaardinstelling is. Dit stelt inhoud op je eigen website/domein in staat om succesvol te worden geladen in pop-ups, maar beperkt items van externe bronnen van het worden geladen in een pop-up.

Zoals aan het begin van deze sectie vermeld, zijn bepaalde geavanceerde functies afhankelijk van cross-origin-isolatie. Functies zoals SharedArrayBuffer-objecten of Performance.now() methoden die bepaalde serviceworkers nodig hebben voor ongeblokkeerde timers, zijn alleen beschikbaar wanneer je document een cross-origin-opener-policy HTTP Header met de waarde ‘same-origin’ ingesteld heeft.
</div>

### Force HTTP Headers

De laatste optie om op te focussen in het eerste tabblad is de Force HTTP Headers, wat niet moet worden verward met ‘Force HTTPS’ in de algemene instellingen van Joomla.

![Joomla http headers 11](../../../en/images/security/http-headers-plugins-force-http-headers.png)

Dit gedeelte van de Joomla HTTP Header-plugin stelt je in staat om, indien gewenst, een selectie van ‘andere’ headers toe te voegen die niet specifiek in de plugintabs worden vermeld, evenals om de opname van enkele van de inbegrepen headers te forceren.

Uit de keuzelijst heb je momenteel 10 opties. Maar het is goed om op te merken dat sommige daarvan **na verloop van tijd kunnen vervallen** omdat de headerbeleid waarnaar ze verwijzen, gaan veranderen of heroverwogen worden.

De huidige HTTP-headers die je hier direct kunt instellen zijn headers die gericht zijn op het volgende:

Je kunt meer over elke functie vinden op de Mozilla Developers website.

#### Content-Security-Policy (lijst)

De Content-Security-Policy antwoordkop stelt websites in staat om de middelen te controleren die de gebruiker voor elke webpagina mag laden. Beleid specificeert meestal serveroorsprongen en scriptendpoints. Dit helpt bij het beschermen tegen cross-site scripting aanvallen.
Mozilla: Content-Security-Policy

#### Content-Security-Policy-Report-Only

De HTTP Content-Security-Policy-Report-Only antwoordkop stelt webontwikkelaars in staat om te experimenteren met beleid door hun effecten te monitoren (maar niet af te dwingen).
Mozilla: Content-Security-Policy-Report-Only

#### Cross-Origin-Opener-Policy (COOP)

De HTTP Cross-Origin-Opener-Policy (COOP) antwoordkop stelt je in staat ervoor te zorgen dat een document op topniveau geen browsing contextgroep deelt met cross-origine documenten.
Mozilla: Cross-Origin-Opener-Policy

COOP zal je document proces-isoleren en potentiële aanvallers kunnen niet toegang krijgen tot je globale object als ze het in een pop-up zouden openen, waardoor een reeks cross-origine-aanvallen, aangeduid als **XS-Leaks**, wordt voorkomen.

#### Expect-CT (Wordt Stopgezet)

De Expect-CT header laat sites zich aanmelden voor rapportage en/of handhaving van eisen met betrekking tot Certificate Transparency, om te voorkomen dat het gebruik van verkeerd uitgegeven certificaten voor die site onopgemerkt blijft.
Mozilla: Expect-CT (Wordt Stopgezet)

#### Feature-Policy (Sindsdien Verouderd)

De HTTP Feature-Policy header biedt een mechanisme om het gebruik van browserfuncties in zijn eigen frame toe te staan of te weigeren, en in inhoud binnen alle &lt;iframe&gt;-elementen in het document.
Mozilla: Feature-Policy

#### Permissions-Policy

Dit is de vervanging voor het bovengenoemde Feature-Policy.
Mozilla: Permissions-Policy (Vervangt hierboven Feature Policy)

#### Referrer-Policy (in lijst)

De Referrer-Policy HTTP header regelt hoeveel verwijzingsinformatie (verzonden met de Referrer header) moet worden opgenomen in verzoeken.
Mozilla: Referrer-Policy

#### Report-To

Onderdeel van de Content-Security-Policy. De Content-Security-Policy Report-To HTTP antwoordkop instructeert de user agent om rapportage-eindpunten voor een oorsprong op te slaan.
Mozilla: Report-To

De report-to-richtlijn is bedoeld ter vervanging van de verouderde report-uri-richtlijn, report-to wordt nog niet in de meeste browsers ondersteund.

#### Strict-Transport-Security

De HTTP Strict-Transport-Security antwoordkop (vaak afgekort als HSTS) informeert browsers dat de site alleen toegankelijk mag zijn via HTTPS, en dat pogingen om deze via HTTP te openen automatisch moeten worden omgezet naar HTTPS.
Mozilla: Strict-Transport-Security

Dit is veiliger dan simpelweg een HTTP naar HTTPS (301) omleiding op je server te configureren, waarbij de initiële HTTP-verbinding nog steeds kwetsbaar is voor een man-in-the-middle-aanval.

#### X-Frame-Options (in lijst)

De X-Frame-Options HTTP antwoordkop geeft aan of een browser is toegestaan om een pagina in een &lt;frame&gt;, &lt;iframe&gt;, &lt;embed&gt; of &lt;object&gt; weer te geven, of niet. Sites kunnen dit gebruiken om click-jacking-aanvallen te vermijden, door ervoor te zorgen dat hun inhoud niet in andere sites wordt ingebed.
Mozilla: X-Frame-Options

De toegevoegde beveiliging wordt alleen geboden als de gebruiker die toegang heeft tot het document een browser gebruikt die X-Frame-Options ondersteunt.

De X-Frame-Options-header heeft kinditems genaamd frame-ancestors die de Frame-Options-header vervangen. Als een bron beide beleidsregels heeft, wordt het frame-ancestors beleid gehandhaafd en het X-Frame-Options beleid genegeerd.

Met behulp van het HTTP Header Value-veld kun je de waarden instellen die je wilt laten volgen en deze toewijzen aan je website, de beheersite of beide.

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem; ">
Samenvatting

Het is de moeite waard om op te merken dat de ondersteuning voor HTTP headers door browsers varieert, dus het is een goed idee om voor het implementeren van je keuze van HTTP Header zijn browserondersteuning voor je potentiële publiek te controleren.

Als je een reeks HTTP headers voor je website instelt en de browser van de gebruiker ondersteunt die headeroptie niet, zal de browser deze negeren.
</div>

## HTTP-Header Plug-in Instellingen - TAB 2

### Strict-Transport-Security (HSTS)

**Het Strict Transport Security Policy-tabblad is standaard uitgeschakeld.**

![Joomla http headers 12](../../../en/images/security/http-headers-plugins-headers-strict-transport-security.png)

Ik hou van onderzoek doen. Want soms kom je een echte OMG! Moment tegen. Dit is een van die momenten.

Wikipedia stelt:

> Netscape Communications creëerde HTTPS in 1994 voor zijn Netscape Navigator-webbrowser. Oorspronkelijk werd HTTPS gebruikt met het SSL-protocol. Naarmate SSL evolueerde naar Transport Layer Security (TLS), werd HTTPS formeel gespecificeerd door RFC 2818 in mei 2000. Google kondigde in februari 2018 aan dat zijn Chrome-browser HTTP-sites zou markeren als "Niet Beveiligd" vanaf juli 2018. Deze stap was bedoeld om website-eigenaren aan te moedigen HTTPS te implementeren, als een inspanning om het World Wide Web veiliger te maken.” ……

Wie had gedacht dat Netscape de HTTPS-protocollen zo lang geleden heeft uitgevonden? Wat nog verrassender is, is hoe lang het duurde om het te implementeren in het internet zoals we het nu kennen en waar we van kunnen genieten.

Al jaren proberen ze ons te beïnvloeden, te dwingen, en uiteindelijk te bedreigen, om HTTPS op al onze websites te implementeren. De meesten van ons gaven toe en het world wide web is nu eindelijk veilig. Of toch niet?

Er zijn echter enkele achterblijvers, fanatiekelingen of vergeten websites die nog steeds alleen http gebruiken om hun inhoud te leveren, zij het met een Google/Firefox enz. “Deze website is onveilig” waarschuwing.

Een snelle Google-zoekopdracht leverde verschillende verouderde lijsten op van die ‘HTTP-only Schuldige’ websites. Hoewel sinds de publicatie van die lijsten veel websites zijn geüpdatet naar HTTPS. Er waren echter enkele voor de hand liggende uitsluitingen van organisaties waarvan je zou denken dat ze beter zouden weten.

Bijvoorbeeld:

* NGINX (http://nginx.org/)
* GNU (http://www.gnu.org/)
* De Universiteit van Washington (http://www.washington.edu/)

Volgens w3techs.com draait ongeveer 20% van alle websites nog steeds alleen op HTTP.

**Dus, waarom is dit een probleem?**

Dit is een probleem omdat alle gegevens die naar en van de browser van een gebruiker worden verzonden het risico lopen te worden onderschept. We kennen dit als een **man-in-the-middle aanval**. Nu lijkt dit misschien geen belangrijk aandachtspunt als je website alleen gaat over foto's van schattige kittens.

![beeld van schattige kittens](../../../en/images/security/http-headers-plugins-headers-kittens.jpg)

Maar zelfs eenvoudige websites kunnen het slachtoffer worden van hackers en aanvallers die **click-jacking** en andere cross-origin-aanvallen zullen implementeren die je gebruikers schaden.

Een website die geen gebruikersgegevens of inloggegevens uitwisselt, **moet nog steeds HTTPS gebruiken**.

**Oké, laten we terug naar het onderwerp gaan.**

Zoals je al weet, is het hele punt van HTTPS om een veilige verbinding tot stand te brengen tussen de browser van de gebruiker en je server. Een verbinding waarbij elke uitwisseling van gegevens plaatsvindt in een veilige omgeving die niet kan worden onderschept en gekopieerd door een derde partij. Een man in het midden.

![man in het midden aanval](../../../en/images/security/http-headers-plugins-headers-man-in-middle.png)

Maar wist je dat, tenzij je **HTTPS SSL-certificaat** **TLS** gebruikt, je 'veilige' verbinding niet zo veilig is als je zou verwachten? Niet-TLS HTTPS-verbindingen zijn nog steeds **kwetsbaar voor man-in-the-middle aanvallen**.

Hoewel een oude blogpost, legt dit artikel mooi uit hoe een man-in-the-middle aanval werkt.

Browsers hebben TLS op grote schaal geadopteerd.

En, TLS 1.3 is niet direct compatibel met eerdere versies tenzij het wordt uitgevoerd in compatibiliteitsmodus. Wat een probleem zou kunnen vormen voor sommigen.

![tls certificaat informatie](../../../en/images/security/http-headers-plugins-headers-tls.png)

Het gebruik van de HTTP-Header Plug-in van Joomla om om te gaan met Strict-Transport-Security (HSTS) helpt man-in-the-middle aanvallen te beperken door het gebruik van TLS in de webbrowser van je bezoekers af te dwingen. TLS zorgt ervoor dat alle webcommunicatie aan de clientzijde plaatsvindt met behulp van een veilige transportlaag.

**Gebruik je een 301-omleiding om de niet-veilige HTTP-versie van je website naar de veilige HTTPS-versie te serveren?**

De meeste mensen doen dat. 301-omleidingen zijn instructies die de meeste website-eigenaren instellen in hun htaccess-bestand. Ze laten Google weten dat de versie van de website die moet worden gebruikt de HTTPS (veilige) is. Het probleem hiermee is dat **de 301 slechts een URL-omleiding is**, dus je website voert nog steeds een element van de eerste verbinding uit via HTTP.

In tegenstelling tot verbindingen tussen een gebruiker en een website-server die HSTS gebruiken, waar de server automatisch alleen via HTTPS interacteert.

HSTS heeft echter een zwakte, aangezien de eerste initiële verbinding tussen de browser van de gebruiker en de website-server nog steeds plaatsvindt via HTTP. Maar alle volgende verbindingen worden automatisch tot stand gebracht via HTTPS totdat de vervaldatum van de HTTP-header is bereikt en deze header opnieuw wordt ingesteld.

Dit is anders dan een standaard 301-omleiding waar elke paginalading een initiële http-verzoek omvat om de https-verbinding in gang te zetten.

Er is een oplossing voor deze zwakte in de HTTP-Headers HSTS-instellingen, activeer 'Preload'.

Wat de ‘Preload’-tag aan de response-header toevoegt.

In de instellingen is er ook een link preload lijst**. Dit is een lijst die hard gecodeerd is in veel moderne browsers. De lijst informeert de browser dat de verbinding met example.com alleen via HTTPS tot stand moet worden gebracht. Hierdoor vervalt de noodzaak om zelfs maar de initiële verbinding via HTTP tot stand te brengen.

![hsts preload](../../../en/images/security/http-headers-plugins-headers-enter-domain.png)

Zodra HSTS is ingesteld in de Joomla HTTP-header plug-in, worden alle noodzakelijke tags toegevoegd aan de HTTP-response-header. Dit laat elke gebruikersbrowser die probeert verbinding te maken met je server weten dat alle verbindingen **moeten worden gemaakt met HTTPS**, of dit nu in je HTML is gespecificeerd of niet.

Samengevat is het gebruik van Joomla’s HTTP-header plug-in om HSTS te integreren in plaats van te vertrouwen op 301-omleidingen om je inhoud via HTTPS te leveren een belangrijke beveiligingsverbetering. Een verbetering die helpt om **man-in-the-middle aanvallen** te stoppen en je gebruiker een veilige omgeving biedt.

HSTS dekt het hele domein, in tegenstelling tot een 301-omleiding die alleen een specifieke URI-pad dekt.

HSTS gebruikt een aparte browsercache die meestal is gescheiden, zodat deze niet gemakkelijk of per ongeluk kan worden gewist.

HSTS kan worden voorbelast in een browser. Dit zorgt ervoor dat een gebruiker alleen via HTTPS verbinding maakt met je server, ongeacht of ze de site eerder hebben bezocht.

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem; ">
Samenvatting

Inschakelen: HSTS

Stel max-leeftijd in: De standaard is 1 jaar (31536000 seconden), maar sommigen raden aan dit in te stellen op 2 jaar (63072000 seconden).

Inschakelen: Subdomeinen - Als je subdomeinen hebt, zorg ervoor dat je een geldig SSL-certificaat hebt om ze individueel of als een wildcard van je hoofd-domein te dekken.

Inschakelen: Preload

Stuur ten slotte je domein naar de HSTS-preloadlijst.
</div>

## HTTP Headers Plugin-instellingen - TAB 3

### Content Security Policy (Tab 3)

**De Content Security Policy-tab is standaard uitgeschakeld.**

Wanneer je Joomla’s Content Security Policy inschakelt via de HTTP Headers-plugin, geef je de browser van je bezoeker precies aan welke middelen vanaf de server van je website worden geladen. Dit is een uitstekende manier om ervoor te zorgen dat je alleen de content levert die je daadwerkelijk wilt leveren.

![content security policy tab](../../../en/images/security/http-headers-plugins-headers-csp.png)

Het implementeren van een effectieve Content Security Policy is een effectieve manier om **Cross-Site Scripting (XSS)** en **Clickjacking**-aanvallen vanaf je website te stoppen.

Cross-Site Scripting, ook wel een **XSS-aanval** genoemd, is een aanval op je website waarbij een kwaadaardig script wordt ‘ingespoten’ in een nietsvermoedende en anderszins vertrouwde website. Aanvallers zoeken naar een zwak punt, meestal waar een gebruiker gegevens kan invoeren.

Verouderde componenten die gebruikersinvoer toestaan, zoals ongecontroleerde opmerkingenformulieren, kunnen kwetsbaarheden bevatten die kunnen worden benut in een Cross Site Scripting-aanval. Daarom is het verstandig om je Joomla-componenten altijd up-to-date te houden en de kansen op deze aanvallen te verkleinen.

**Een voorbeeld van een geïnfecteerd opmerkingenformulier:**

Je website gebruikt een opmerkingenformulier aan het einde van een artikel om gebruikersdiscussies te verzamelen, zoals veel websites dat doen. Dit is ideaal.

Je opmerkingenextensie van dodgy-joomla-extensions.com werkt goed en je gebruikers vinden het geweldig. Maar je hebt het al 5 jaar niet bijgewerkt en de ontwikkelaars hebben het allang verlaten.

Nu, 5 jaar later, ontdekt Mr. Hacker dat hij, door een kwetsbaarheid in de code van de opmerkingencomponent, een stukje nare code in een opmerking kan verbergen die er verder onschuldig uitziet.

Wat die code uiteindelijk doet varieert, maar wat zeker is, is dat elke keer dat je onschuldige artikelpagina met de opmerkingen wordt geladen, die slechte code ook wordt geladen en uitgevoerd. Het is tenslotte onderdeel van de HTML, en de browser weet niet dat het daar niet hoort.

Dus, de slechte code draait. Misschien controleert het je cookiedata. Misschien steelt het gevoelige gegevens die door de browser worden bewaard. Of misschien laadt het advertenties van online casino’s of volwassen websites. Misschien wordt zelfs de HTML van je onschuldige pagina over schattige kittens volledig herladen vanuit een extern JavaScript-bestand om de creditcardgegevens van je gebruikers te stelen.

**In feite kan op dit punt bijna alles worden uitgevoerd door een script.**

Een goede Content Security Policy helpt om dit soort aanvallen te stoppen, zelfs als je gecompromitteerde opmerkingenextensie het doelwit wordt van Mr. Hacker.

Dit gebeurt omdat de Joomla HTTP Header-plugin de CSP als een HTTP Response Header levert, **die de browser precies vertelt wat te laden**. In de instellingen van het CSP-tabblad in de HTTP Headers-plugin kun je **28 beleidsrichtlijnen** direct instellen. De richtlijnen helpen je website te beveiligen door alleen goedgekeurde bronnen voor je bestanden en content te gebruiken.

Het aanvalsexample hierboven laadde uiteindelijk een JavaScript-bestand van een andere bron om de HTML-uitvoer op het scherm te wijzigen. Dit had voorkomen kunnen worden door de richtlijn `script-src 'self'` toe te voegen aan Joomla's CSP in de plugin.

![policy directive self](../../../en/images/security/http-headers-plugins-headers-policy-directive.png)

In dit voorbeeld zal de browser alleen JavaScript-bestanden in het HTML-document laden als ze van je domein komen. Alle andere JavaScript-bestanden, inclusief die van Mr. Hacker, worden geweigerd.

Hoewel dit je website helpt te beveiligen, kan het ook voorkomen dat andere legitieme JavaScript-bestanden worden geladen tijdens het renderen van de webpagina. Deze externe bestanden kunnen worden toegevoegd als goedgekeurde bronnen in dezelfde richtlijn. Bijvoorbeeld, als je Bootstrap gebruikt vanaf een CDN, voeg je toe:

```
script-src 'self' https://cdn.jsdelivr.net
```

Als je problemen hebt met het laden van Bootstrap vanaf de CDN, `https://cdn.jsdelivr.net`, kun je proberen de volledige URL naar het benodigde Bootstrap-bestand toe te voegen. Je zou je richtlijn als volgt formatteren: `script-src 'self' https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.min.js`.

![policy directive self](../../../en/images/security/http-headers-plugins-headers-policy-directive-self.png)

Het toevoegen van deze externe bronnen is gemakkelijker te implementeren op een nieuwe website terwijl je deze opbouwt. Maar als je je HTML met Dev Tools doorneemt, zou je alle externe bestanden die al op je bestaande website worden gebruikt, moeten kunnen vinden en in je CSP kunnen opnemen.

Bij het toevoegen van richtlijnen aan je Content Security Policy in de HTTP Headers Plugin, zijn er een **aantal kernwaarden** die je kunt gebruiken om te bepalen wat de browser expliciet moet laden. Dit zijn de basiswaarden om je eerste Content Security Policy op te zetten.

Er zijn andere opties beschikbaar voor enkele van de meer geavanceerde richtlijnen, een volledige lijst en voorbeelden van hun gebruik zijn te vinden op de Content Security Policy (CSP) Quick Reference Guide-website.

* **'none'** blokkeert het gebruik van dit type bron.
* **'self'** komt overeen met de huidige oorsprong (maar niet subdomeinen).
* **'unsafe-inline'** staat het gebruik van inline JS en CSS toe.
* **'unsafe-eval'** staat het gebruik van mechanismen zoals eval() toe.

Laten we nu eens kijken naar enkele van die richtlijnen. Hier is een lijst met enkele van de richtlijnen die beschikbaar zijn in de Joomla HTTP Headers-plugin, samen met een korte beschrijving, met dank aan Content Security Policy. Bezoek deze website voor meer informatie en voorbeelden.

<dl>
<dt>default-src</dt>
<dd>De default-src richtlijn definieert het standaardbeleid voor het ophalen van resources zoals JavaScript, afbeeldingen, CSS, lettertypen, AJAX-verzoeken, frames, HTML5-media.<br>
VOORBEELD DEFAULT-SRC BELEID<br>
default-src 'self' https://cdn.example.com
</dd>
<dt>script-src</dt>
<dd>Definieert geldige bronnen van JavaScript.<br>
VOORBEELD SCRIPT-SRC BELEID<br>
script-src 'self' https://js.example.com
</dd>
<dt>style-src</dt>
<dd>Definieert geldige bronnen voor stylesheets of CSS.<br>
VOORBEELD STYLE-SRC BELEID<br>
style-src 'self' css.example.com
</dd>
<dt>img-src</dt>
<dd>Definieert geldige bronnen van afbeeldingen.<br>
VOORBEELD IMG-SRC BELEID<br>
img-src 'self' https://img.example.com https://example.com
</dd>
<dt>connect-src</dt>
<dd>Van toepassing op XMLHttpRequest (AJAX), WebSocket, fetch(), &lt;a ping&gt; of EventSource. Indien niet toegestaan, simuleert de browser een 400 HTTP-statuscode.<br>
VOORBEELD CONNECT-SRC BELEID<br>
connect-src 'self'
</dd>
<dt>font-src</dt>
<dd>Definieert geldige bronnen voor lettertypen (geladen via @font-face).<br>
VOORBEELD FONT-SRC BELEID<br>
font-src https://font.example.com https://example.com
</dd>
<dt>object-src</dt>
<dd>Definieert geldige bronnen van plug-ins, zoals &lt;object&gt;, &lt;embed&gt; of &lt;applet&gt;.<br>
VOORBEELD OBJECT-SRC BELEID<br>
object-src 'self'
</dd>
<dt>media-src</dt>
<dd>Definieert geldige bronnen van audio en video, zoals HTML5 &lt;audio&gt;-, &lt;video&gt;-elementen.<br>
VOORBEELD MEDIA-SRC BELEID<br>
media-src https://media.example.com
</dd>
<dt>frame-src</dt>
<dd>Definieert geldige bronnen voor het laden van frames. In CSP Level 2 is frame-src verouderd ten gunste van de child-src richtlijn. In CSP Level 3 is frame-src niet langer verouderd en zal deze worden gebruikt als child-src niet aanwezig is.<br>
VOORBEELD FRAME-SRC BELEID<br>
frame-src 'self'
</dd>
<dt>sandbox</dt>
<dd>Stelt een sandbox in voor de opgevraagde resource, vergelijkbaar met het iframe-sandboxattribuut. De sandbox past eenzelfde oorsprongbeleid toe, voorkomt pop-ups, plug-ins en blokkeert de uitvoering van scripts. U kunt de sandbox-waarde leeg laten om alle beperkingen te behouden, of waarden toevoegen: allow-forms allow-same-origin allow-scripts allow-pop-ups, allow-modals, allow-orientation-lock, allow-pointer-lock, allow-presentation, allow-popups-to-escape-sandbox en allow-top-navigation.<br>
VOORBEELD SANDBOX BELEID<br>
sandbox allow-forms allow-scripts
</dd>
<dt>report-uri</dt>
<dd>Geeft de browser de opdracht om meldingen van beleidsfouten naar deze URI te sturen. U kunt ook Content-Security-Policy-Report-Only als HTTP-headernaam gebruiken om de browser alleen rapporten te laten verzenden (blokkeert niets). Deze richtlijn is in CSP Level 3 verouderd ten gunste van de report-to richtlijn.<br>
VOORBEELD REPORT-URI<br>
report-uri /some-report-uri
</dd>
<dt>child-src</dt>
<dd>Definieert geldige bronnen voor web workers en geneste bladercontexten die worden geladen via elementen zoals &lt;frame&gt; en &lt;iframe&gt;<br>
VOORBEELD CHILD-SRC BELEID<br>
child-src 'self'
</dd>
<dt>form-action</dt>
<dd>Definieert geldige bronnen die kunnen worden gebruikt als een HTML &lt;form&gt; actie.<br>
VOORBEELD FORM-ACTION BELEID<br>
form-action 'self'
</dd>
<dt>frame-ancestors</dt>
<dd>Definieert geldige bronnen voor het insluiten van de resource met &lt;frame&gt; &lt;iframe&gt; &lt;object&gt; &lt;embed&gt; &lt;applet&gt;. Als u deze richtlijn instelt op 'none', zou dit ongeveer gelijk moeten zijn aan X-Frame-Options: DENY. Wanneer deze richtlijn actief is, en indien ondersteund door de browser, zal deze de instellingen in X-frame-options overschrijven.<br>
VOORBEELD FRAME-ANCESTORS BELEID<br>
frame-ancestors 'none'
</dd>
<dt>plugin-types</dt>
<dd>Definieert geldige MIME-typen voor plug-ins die worden aangeroepen via &lt;object&gt; en &lt;embed&gt;. Om een &lt;applet&gt; te laden, moet u application/x-java-applet specificeren.<br>
VOORBEELD PLUGIN-TYPES BELEID<br>
plugin-types application/pdf
</dd>
<dt>base-uri</dt>
<dd>Definieert een set toegestane URL's die kunnen worden gebruikt in het src-attribuut van een HTML-basistag.<br>
VOORBEELD BASE-URI BELEID<br>
base-uri 'self'
</dd>
<dt>report-to</dt>
<dd>Definieert een rapportagegroepnaam die is gedefinieerd door een Report-To HTTP-responseheader. Zie de Reporting API voor meer informatie.<br>
VOORBEELD REPORT-TO RICHTLIJN<br>
report-to groupName
</dd>
<dt>worker-src</dt>
<dd>Beperkt de URL's die als Worker, Shared Worker of Service Worker kunnen worden geladen.<br>
VOORBEELD WORKER-SRC BELEID<br>
worker-src 'none'
</dd>
<dt>manifest-src</dt>
<dd>Beperkt de URL's waaruit toepassingsmanifesten kunnen worden geladen.<br>
VOORBEELD MANIFEST-SRC BELEID<br>
manifest-src 'none'
</dd>
<dt>prefetch-src</dt>
<dd>Definieert geldige bronnen voor het vooraf ophalen en prerenderen van aanvragen, bijvoorbeeld via de link-tag met rel="prefetch" of rel="prerender":<br>
VOORBEELD PREFETCH-SRC BELEID<br>
prefetch-src 'none'
</dd>
<dt>navigate-to</dt>
<dd>Beperkt de URL's waarheen het document op welke manier dan ook kan navigeren. Bijvoorbeeld wanneer op een link wordt geklikt, een formulier wordt ingediend, of window.location wordt aangeroepen. Als form-action aanwezig is, wordt deze richtlijn genegeerd voor formulierindieningen. Implementatiestatus<br>
VOORBEELD NAVIGATE-TO BELEID<br>
navigate-to https://example.com
</dd>
</dl>

Joomla’s HTTP Headers-plug-in biedt ook de mogelijkheid om **enkele globale parameters in te stellen in het tabblad Content Security Policy**.

![Joomla http headers 14](../../../en/images/security/http-headers-plugins-headers-csp-global.png)

U kunt ervoor kiezen om het CSP toe te passen op uw website, de beheeromgeving of beide met de clients-instelling.

De ‘Report-Only’-optie stelt u in staat om uw richtlijnen te testen en te controleren op fouten met Dev Tools voordat u live gaat. Het is altijd leuk om de oorzaak van CSP-fouten in de Google-console op te sporen!

Vervolgens is er de ‘Nonce’-instelling. Nonce, wat 'nummer eenmalig gebruikt' betekent, is een systeem dat een willekeurig gegenereerde tekenreeks toepast op een inline &lt;script&gt;- of &lt;style&gt;-tag die via de Joomla API aan uw HTML is toegevoegd. Deze gevallen worden meestal geïmplementeerd door ontwikkelaars van componenten/modules/plug-ins van derden voor Joomla wanneer u die extra functionaliteit op uw website installeert.

In de onderstaande afbeelding ziet u de &lt;style&gt;-tag met een nonce-rel-attribuut dat is toegevoegd aan de CSS-stijlen die door de Akeeba Backup-component aan mijn HTML-document zijn toegevoegd.

![Joomla http headers 16](../../../en/images/security/http-headers-plugins-headers-akeeba-style.png)

Opmerkelijk is dat de kern-JavaScript- en CSS-code van Joomla die aan het HTML-document wordt toegevoegd, momenteel geen ‘nonce’-tag bevat. Dit komt omdat **ze deel uitmaken van de 'kern'** en niet worden toegevoegd via de Joomla API.

Als je de optie ‘Nonce’ inschakelt in de CSP-instellingen, stel je de browser in staat om inline scripts en stijlen als ‘veilig’ weer te geven. Je moet dan ook de Joomla {nonce}-tag instellen in je script-src beleidsrichtlijn als `script-src 'self' {nonce}`. Als fallback voor oudere browsers die geen 'nonces' ondersteunen, kun je ook {script-hashes} toevoegen na de {nonce}-placeholder, zoals in `script-src 'self' {nonce} {script-hashes}` (let op de spaties). Vergeet niet om eerst **Script Hashes** in te schakelen.

![Joomla nonce-instellingen](../../../en/images/security/http-headers-plugins-headers-nonce-settings.png)

Joomla genereert willekeurig de ‘nonce’ tekststring en voegt deze toe aan de &lt;style&gt;- en &lt;script&gt;-tags. Wanneer je de ‘nonce’-optie in de plug-in instellingen inschakelt, wordt de tekststring doorgegeven aan de HTTP-header. De browser interpreteert vervolgens de HTTP-header en verwerkt de bijbehorende &lt;script&gt; of &lt;style&gt;. Tegelijkertijd verwijdert hij de Nonce-tekststring uit de weergegeven HTML in de browser.

![Joomla nonce stijl](../../../en/images/security/http-headers-plugins-headers-nonce-style.png)

Hierdoor wordt voorkomen dat een hacker de nonce-tekststring kan kapen en aan zijn eigen geïnjecteerde code kan toevoegen. Zelfs als een hacker erin slaagt om schadelijke JavaScript in jouw HTML te injecteren, zal de browser dit blokkeren.

### Script Hashes

We weten allemaal dat we geen inline JavaScript in onze HTML moeten opnemen; je moet het in een `my-javascript.js`-bestand schrijven en in de &lt;head&gt; plaatsen of net voor de &lt;/body&gt;-tag. Maar we doen het soms toch.

Het probleem is dat als je dit doet en dan de CSP-richtlijn `script-src 'self'` toevoegt, al het inline JavaScript standaard geblokkeerd zal worden. Dit is zo ontworpen om te voorkomen dat geïnjecteerd JavaScript van hackers op je website kan worden uitgevoerd.

Er is een oplossing hiervoor met de richtlijn `script-src 'unsafe-inline'`, die hackers’ inline JavaScript, evenals jouw betrouwbare code, zou toestaan. Dit is om voor de hand liggende redenen niet de beste optie.

**Script Hashes als oplossing!**

De HTTP Headers-plug-in van Joomla verzamelt automatisch alle &lt;styles&gt; en &lt;scripts&gt; **die via de Joomla API worden doorgegeven** aan de site. Vervolgens genereert hij de bijbehorende hashes en geeft deze door via de HTTP-header. De browser genereert zelf de hashes op de site en bevestigt dat deze overeenkomen. Als dat zo is, worden de scripts uitgevoerd; zo niet, dan worden ze geblokkeerd.

Om deze functie van de plug-in in te schakelen, zet je de schakelaar op **'Ingeschakeld'**. Voeg in je script-src beleidsrichtlijn de waarde `'self' {script-hashes}` toe. Als je zowel de ‘nonce’- als ‘script-hashes’-functie gebruikt, stel dan de richtlijnwaarde in zoals in het nonce-voorbeeld hierboven.

![Joomla script-hashes](../../../en/images/security/http-headers-plugins-headers-csp-script-hashes.png)

**Slim bedacht.**

Maar nog beter is dat we hetzelfde idee kunnen gebruiken om handmatig script-hashes te verwerken en ze toe te voegen aan onze `script-src 'self'`-richtlijn. Dit kost wat tijd om op te zetten en te onderhouden, maar kan handig zijn als je JavaScript aan een artikel of aangepaste module hebt toegevoegd.

Er zijn meer gedetailleerde manieren om dit te doen met een SHA256-, SHA384- of SHA512-hashgenerator. Maar omdat de meeste mensen alleen kleine stukjes JavaScript aan een artikel of aangepaste module toevoegen, laten we dit door de Dev-tools van Google doen.

Het proces is eenvoudig. Het enige verschil is hoe we de hash genereren.

Stel dat je de Joomla HTTP Headers-plug-in hebt ingeschakeld, CSP actief is en je de richtlijn `script-src 'self'` hebt ingesteld en opgeslagen.

Stap 1 - Voeg je inline JavaScript toe aan je artikel of aangepaste module en sla het op. Vergeet niet om je editor-instellingen aan te passen om te voorkomen dat de editor je code verwijdert tijdens het opslaan.

Stap 2 - Ga naar de webpagina met je script erin. Open Dev Tools en in het console-tabblad zie je een foutmelding die lijkt op:

> Refused to execute inline script because it violates the following Content Security Policy directive: "script-src 'self'". Either the 'unsafe-inline' keyword, a hash ('sha256-0Q1c1CuhLHV7WbNt+ltwJoCf3wF/O+MWqsXetkxWSm0='), or a nonce ('nonce-...') is required to enable inline execution.

![Joomla script-hashes foutmelding](../../../en/images/security/http-headers-plugins-headers-csp-script-hashes-tools-error.png)

Stap 3 - Nu hoef je alleen de hash uit de foutmelding te kopiëren en toe te voegen aan je JavaScript-richtlijn in de plug-in en deze opnieuw op te slaan:

```markdown
script-src 'self' 'sha256-0Q1c1CuhLHV7WbNt+ltwJoCf3wF/O+MWqsXetkxWSm0='
```

![Joomla script-hashes toepassen](../../../en/images/security/http-headers-plugins-headers-csp-script-src-self-hash.png)

Herlaad daarna je webpagina en controleer opnieuw in Google’s Dev Tools. De foutmelding zal nu verdwenen zijn en de browser zal je script op de webpagina laden.

**Let op:** Er blijft een foutmelding staan in mijn voorbeeld, omdat het JavaScript dat ik aan mijn artikel heb toegevoegd niet compleet is. Maar dit toont aan dat de inline-code tenminste probeert te werken.

Het toevoegen van hashes aan je inline-code is een goede manier om deze in de HTTP-header op de whitelist te zetten zodat ze toch worden uitgevoerd, terwijl inline-code die niet expliciet is gehasht en toegevoegd aan je CSP, wordt geblokkeerd. Dit voorkomt dat een hacker je website probeert te compromitteren.

![Joomla script hashes tools foutmelding](../../../en/images/security/http-headers-plugins-headers-csp-script-src-self-hash-tools-error.png)

**Opmerking:**

Als je je JavaScript wijzigt, moet je je hash opnieuw berekenen en de waarde in de CSP-richtlijn wijzigen.

Als je problemen hebt om je hashes te laten werken, zijn er 3 veelvoorkomende problemen, waarvoor je oplossingen kunt vinden op de pagina _Using a hash with CSP_.

### Strict Dynamic

Als je de optie Strict Dynamic in je CSP inschakelt, geeft dit expliciete machtiging aan een script via een Hash of Nonce en past dit toe op elk ander script dat direct eraan gekoppeld is of dat ervan wordt aangeroepen. Deze actie overschrijft ook standaardrichtlijnen zoals 'self' of 'unsafe-inline' die in je algemene CSP-richtlijnen op die child-scripts zijn toegepast. Deze worden genegeerd.

### Style Hashes

De Style Hash van de CSP werkt precies zoals de JavaScript-hashes hierboven werken, maar gebruik dit als je CSS &lt;style&gt;-blokken in je HTML-body toevoegt. Net zoals bij 'Script Hashes' **schakel** je de plug-infunctie in en stel je een `style-src` beleidsrichtlijn in om hiernaar te verwijzen met de waarde `'self' {style-hashes}`.

![Joomla style-hashes](../../../en/images/security/http-headers-plugins-headers-csp-style-hash.png)

**Opmerking:**

Als je je inline CSS wijzigt, in plaats van CSS die door de Joomla API wordt gemaakt, moet je je hash opnieuw berekenen en de waarde in de CSP-richtlijn wijzigen.

### Frame Ancestors ‘self’

Deze optie in de plug-in staat toe dat een pagina wordt weergegeven in een iframe, maar alleen van dezelfde site.

Als je expliciet wilt toestaan dat een andere website je content framed, kun je een specifieke richtlijn ‘frame-src’ instellen.

![Joomla style-hashes frame src](../../../en/images/security/http-headers-plugins-headers-csp-style-hash-frame-src.png)

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem; ">
Take Away

Een goede CSP is soms eenvoudiger te maken op een nieuwe website terwijl je bouwt aan de externe bronnen die nodig zijn.

Het is belangrijk om de volledige, correcte basis-URL voor het toegestane domein in de CSP-richtlijn te gebruiken. Bijvoorbeeld: https://www.mijnwebsite.nl, of https://www.eenanderewebsite.com

Het is ook mogelijk om subdomeinen met dezelfde CSP te targeten door gebruik te maken van wildcards. Bijvoorbeeld: https://*.voorbeeld.org.

Niet alle browsers ondersteunen alle richtlijnen.

CSP ondersteunt SHA256-, SHA384- en SHA512-hashes.
</div>

## Slotopmerking / Conclusie:

Bij het schrijven van dit artikel realiseerde ik me dat ik slechts het oppervlak van dit enorme onderwerp heb aangeraakt.

Ik hou ervan om onderwerpen te ontdekken die ik voorheen anders had genegeerd of waar ik niets van afwist. Ben jij hetzelfde?

De conclusie die ik heb getrokken bij het onderzoeken van het onderwerp HTTP Headers, en in het bijzonder het gebruik van Joomla's nieuwe J4-plugin om deze in te stellen, is dat we allemaal dit onderwerp moeten beheersen. Er zijn veel te veel mensen (hackers) die gewoon wachten op een kans om misbruik te maken van websites met zwakke beveiliging. Dus help je gebruikers niet om slachtoffers te worden.

Veel plezier met het onderzoeken van de Joomla HTTP Headers-plugin en leer hoe deze kan helpen om je website te beveiligen.

Ik raad je aan om voordat je begint nog wat meer onderzoek te doen naar dit interessante onderwerp. Er zijn links hieronder om je eigen onderzoek een vliegende start te geven. Je krijgt een veel beter begrip van hoe het internet werkt en hoe je website ermee omgaat.

### Voor Referentie

Als je de plugin opnieuw moet instellen, is de HTTP Headers-plugin geïnstalleerd met de volgende opties ingesteld:

De plugin is standaard ingeschakeld.

* De HSTS- en CSP-tabbladen zijn standaard uitgeschakeld.
* De X-Frame-Options zijn standaard ingeschakeld.
* De Referrer-Policy is aanvankelijk ingesteld op: strict-origin-when-cross-origin.
* De Cross-Origin-Opener-Policy is aanvankelijk ingesteld op same-origin.

Als je tot hier hebt gelezen en dacht "Dat is niet eerlijk, hoe zit het met J3?", "Waarom kunnen we niet dezelfde functies in Joomla 3 hebben?". Nou, het goede nieuws is dat je dat wel kunt. Hoewel je de plugin moet downloaden van de [JED.

Wanneer je je HTTP-headers hebt ingesteld met de Joomla 4-plugin, kun je je HTTP Headers testen op de Security Headers-website.

Hoe scoorde je?

Wees je ervan bewust dat activering van de HTTP Headers-plugin onverwachte acties kan hebben aan de voorkant.

Tenslotte wil ik Tobias Zulauf & Ced Keiflin bedanken voor hun bijdrage aan het tijdig afronden van dit artikel!
<!--
### Meer Lezen:

Hier zijn enkele van de webpagina's die ik heb gebruikt om dit artikel te onderzoeken, ze staan vol met nuttige informatie over dit onderwerp.

* https://docs.joomla.org/J4.x:Http_Header_Management
* https://csp.withgoogle.com/docs/index.html
* https://content-security-policy.com/
* https://scotthelme.co.uk/content-security-policy-an-introduction/
* https://scotthelme.co.uk/csp-cheat-sheet/
* https://support.cpanel.net/hc/en-us/articles/1500001533562-How-to-add-nosniif-CORS-HSTS-Clickjack-and-X-Xss-Protection-headers-on-a-per-domain-basis
* https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Referrer-Policy
* https://developer.mozilla.org/en-US/docs/Web/Security/Referer_header:_privacy_and_security_concerns
* https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cross-Origin-Opener-Policy
* https://web.dev/why-coop-coep/
* https://en.wikipedia.org/wiki/Spectre_(security_vulnerability)
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/SharedArrayBuffer
* https://developer.mozilla.org/en-US/docs/Web/API/Performance/now
* https://www.troyhunt.com/clickjack-attack-hidden-threat-right-in/
* https://scotthelme.co.uk/hsts-the-missing-link-in-tls/
* https://scotthelme.co.uk/wifi-pineapple-karma-sslstrip/
* https://help.upguard.com/en/articles/4581202-what-s-the-difference-between-using-hsts-and-doing-a-301-redirect
* https://content-security-policy.com/hash/
* https://content-security-policy.com/frame-ancestors/
* https://content-security-policy.com/nonce/

Computerpictogrammen gemaakt door Freepik - Flaticon

Serverpictogrammen gemaakt door Freepik - Flaticon

Duitse vertaling van dit artikel: https://www.jug-zueri.ch/artikel/das-http-headers-plugin-in-joomla-4

Russische vertaling van dit artikel, deel 1: https://habr.com/ru/articles/697214/

Russische vertaling van dit artikel, deel 2: https://habr.com/ru/articles/704778/
-->
*vertaald door openai.com*

