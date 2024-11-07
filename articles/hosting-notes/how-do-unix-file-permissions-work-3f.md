<!-- Filename: How_do_UNIX_file_permissions_work%3F / Display title: UNIX-bestandsrechten -->

Unix/Linux-bestandsrechten kunnen verwarrend zijn. De basis UNIX-rechten komen in drie varianten;

    Eigenaarstoestemmingen: Beheer je eigen toegang tot bestanden.
    Groepstoestemmingen: Beheer toegang voor jezelf en iedereen in je groep.
    Andere toestemmingen: Beheer toegang voor alle anderen.

In Unix, wanneer toegangsrechten zijn geconfigureerd, stelt de server je in staat om verschillende rechten te definiëren voor elk van deze drie categorieën gebruikers. In een webserveromgeving worden toestemmingen gebruikt om te bepalen welke website-eigenaren toegang hebben tot welke directories en bestanden.
## Hoe zien Unix-permissies eruit?

Wanneer je je bestanden via de commandoregel bekijkt met behulp van het Unix-commando `ls -l`, zul je regels zien zoals de volgende, één voor elk bestand en elke directory:
```
drwxr-xr-x@  7 gebruikersnaam  gebruikersgroep    224 13 Feb 10:48 includes
-rw-r--r--@  1 gebruikersnaam  gebruikersgroep   1060 13 Apr 21:00 index.php
```
Uitleg:
* Het eerste teken in de regel is een d voor directory of een - voor bestand, of ...
* De volgende 9 tekens zijn 3 groepen van 3 die staan voor lezen (r), schrijven (w) en uitvoeren (x) of een minteken (-) dat geen toegang betekent voor respectievelijk Eigenaar, Groep en Anderen.
* Het @-symbool is een van de mogelijke Uitgebreide attributen,
* Het getal vóór de gebruikersnaam is de directorydiepte.
* De twee namen zijn de eigenaar gebruikersnaam en gebruikersgroep,
* Het volgende getal is de bestandsgrootte in bytes.
* De volgende datum heeft tijd voor recente items of jaar voor oudere items.
* Als laatste komt de bestands- of directorynaam.

In een FTP-programma kan de volgorde anders zijn en kan er meer of minder informatie zijn.

### Eigenaar (Gebruiker) verwijst naar gebruikersnaam

De Eigenaar (Gebruiker) ben normaal gesproken jij, deze rechten worden toegepast op je hostingaccountnaam.

### Groep verwijst naar gebruikersgroep

De Groepsrechten worden toegepast op andere mensen die in dezelfde groep zitten als jij. Binnen een hostingomgeving zijn er zeer zelden andere mensen in dezelfde groep als jij. Dit beschermt je bestanden en directories tegen toegankelijkheid door anderen die mogelijk ook een hostingaccount op dezelfde server hebben.

### Anderen verwijst naar iedereen

De rechten van Anderen worden toegepast op iedereen op de server die niet jij bent of niet in jouw groep zit. Dus in een webhostingomgeving, ervan uitgaande dat niemand anders normaal gesproken in jouw groep zit, betekent dit dat iedereen behalve jij toegang heeft tot de server. Elk van de drie sets rechten wordt als volgt gedefinieerd;

    r = Leesrechten
    w = Schrijfrechten
    x = Uitvoeringsrechten

    Eigenaar Groep Anderen
    r w x r w x r w x

Zoals velen van jullie al weten, worden rechten normaal gesproken uitgedrukt als een numerieke waarde, iets als 755 of 644. Dus, hoe verhoudt dit zich tot wat we hierboven hebben besproken? Elk teken van de rechten krijgt een numerieke waarde toegewezen, dit gebeurt per set van drie, zodat we slechts drie waarden hoeven te gebruiken en ze voor elke set kunnen hergebruiken.

    Eigenaar Groep Anderen
    r w x r w x r w x
    4 2 1 4 2 1 4 2 1

Nu we een waarde hebben die elke permissie vertegenwoordigt, kunnen we ze in numerieke termen uitdrukken. De waarden worden simpelweg opgeteld in de respectieve sets van 3, wat ons op zijn beurt drie cijfers geeft die ons vertellen welke rechten worden ingesteld. Als ons wordt verteld dat een bestand de rechten 777 heeft, zou dit betekenen dat het volgende waar is.

    Eigenaar Groep Anderen
    r w x r w x r w x
    4 2 1 4 2 1 4 2 1

Dus...

      4+2+1 4+2+1 4+2+1
    =   7     7     7

De Eigenaar van het bestand zou volledige Lees-, Schrijf- en Uitvoeringsrechten hebben, de groep zou ook volledige Lees-, Schrijf- en Uitvoeringsrechten hebben, en de rest van de wereld kan het bestand ook Lezen, Schrijven en Uitvoeren. De standaard- en standaardrechten die door de server aan bestanden en directories worden toegewezen, zijn normaal gesproken;

    Bestanden = 644
    Directories = 755

Deze rechten zouden voor bestanden toestaan;

    644 = rw- r-- r--
    Eigenaar heeft Lees- en Schrijfrechten
    Groep heeft alleen Leesrechten
    Anderen hebben alleen Leesrechten

en voor directories;

    755 = rwx r-x r-x
    Eigenaar heeft Lees-, Schrijf- en Uitvoeringsrechten
    Groep heeft alleen Lees- en Uitvoeringsrechten
    Anderen hebben alleen Lees- en Uitvoeringsrechten

Nu kan het wat ingewikkeld worden wanneer we het hebben over gedeelde webservers. De webserversoftware draait met zijn eigen gebruikersnaam en groepsnaam. De meeste servers zijn zo geconfigureerd dat ze "apache" en "apache" of "nobody" en "nobody" als gebruikersnaam en groepsnaam gebruiken. Hier is het probleem. Je webserver draait als zijn eigen gebruiker, en deze gebruiker ben jij niet en zit ook niet in jouw groep, dus de eerste twee sets rechten zijn hier niet van toepassing. Alleen de rechten van de wereld (anderen) zijn van toepassing. Daarom, als je een rechtenconfiguratie zoals 640 instelt op je websitebestanden, kan je webserver je websitebestanden niet uitvoeren.

    640 = rw- r-- ---
    Eigenaar heeft Lees- en Schrijfrechten
    Groep heeft alleen Leesrechten
    Anderen hebben geen rechten

De webserver krijgt totaal geen rechten toegewezen en kan niet Uitvoeren, Schrijven of, nog belangrijker, zelfs niet Lezen om de inhoud naar een bezoekersbrowser te bezorgen. Als een directory de rechten 750 toegewezen krijgt, zou dit hetzelfde effect hebben, omdat de webserver zelfs geen rechten heeft om bestanden in de directory te lezen, zelfs als de bestanden in die directory gunstige rechten hadden.

    750 = rw- r-x ---
    Eigenaar heeft Lees- en Schrijfrechten
    Groep heeft Lees- en Uitvoeringsrechten
    Anderen hebben geen rechten

Directories hebben een extra eigenaardigheid: als een directory de Uitvoeringsrechten niet heeft ingesteld in de Wereldset, dan, zelfs als de Lees- en Schrijfrechten zijn ingesteld, als het programma niet wordt uitgevoerd als de gebruiker of groep, zal het nog steeds geen toegang hebben tot de bestanden binnen de directory. De Uitvoeringsinstelling staat het programma toe om opdrachten in de directory te "Uitvoeren", dus zonder die mogelijk te maken, kan het programma (in ons geval een webserver) de "Lees"-opdracht niet uitvoeren en dus je bestand niet naar de webbrowser van de gebruikers bezorgen.

## Hoe verhoudt dit zich tot Joomla?

Goede vraag. In de eerste instantie zou dit belangrijk zijn tijdens het Web-Installer proces. Als je je nog kunt herinneren toen je de Joomla! Web-Installer draaide, waren we op zoek naar specifieke mappen die als beschrijfbaar moesten worden aangemerkt. We zien nogal wat berichten die ofwel aangeven dat er problemen waren tijdens de installatie met permissies of vragen welke permissies worden aanbevolen. Sommigen vinden zelfs de melding, waarin om "Schrijfbare" permissies wordt gevraagd, te vaag.

Helaas, omdat de Web-Installer niet weet hoe jouw server is geconfigureerd, kan hij niet specifieker zijn. Zodra je echter de permissie-instellingen begrijpt en je weet een beetje over Web Serving omgevingen, zul je eigenlijk ontdekken dat de term *schrijfbaar* zeer specifiek is en meer dan een adequate beschrijving van wat Joomla! nodig heeft. Terugdenkend aan de bovenstaande informatie, herinner je je misschien dat er drie plaatsen zijn waar *schrijf* permissies kunnen worden ingesteld;

    Eigenaar Schrijfbaar
    Groep Schrijfbaar
    Andere Schrijfbaar

Ook moet je je realiseren dat de Web Server over het algemeen niet als je eigen gebruiker of in dezelfde groep draait. Wanneer je de Web Installer vanuit een browser draait, is het de Web Server die probeert toegang te krijgen tot de bestanden, dus zijn het de "Andere" permissies die daarop van toepassing zijn. Als de "Andere" permissies de Web Server niet toestaan om Lees-, Schrijf- of Uitvoeropdrachten uit te voeren in de Joomla! mappen, zal je de melding ontvangen dat de mappen niet *schrijfbaar* zijn.

In dit geval moet je de Andere permissies configureren naar "7" voor de mappen die vermeld staan in de Web Installer. Dus je totale permissies zouden iets kunnen zijn zoals 757, in het slechtste geval zou je 777 moeten instellen. Deze zeer open permissies kunnen na het draaien van de installer weer worden teruggezet naar 755 om de beveiliging van je mappen en bestanden te ondersteunen.

    757 = rwx r-x rwx
    Eigenaar heeft Lees-, Schrijf- en Uitvoerrechten
    Groep heeft Lees- en Uitvoerrechten
    Andere heeft Lees-, Schrijf- en Uitvoerrechten

Om het nog verwarrender te maken, maken veel hostingbedrijven gebruik van software genaamd phpsuExec of suExec. Deze tools veranderen de manier waarop de Web Server draait, waarbij de Web Server normaal niet als je gebruikersnaam zou draaien, in dit geval wel. Het gebruik van de *andere* permissies kan mogelijk niet vereist zijn, nu hoef je misschien alleen de mappen configureerbaar te maken als *schrijfbaar* voor je eigen gebruikersnaam en groepsnaam, dit maakt het mogelijk om map-permissies in te stellen als 755 of 775 in plaats van 757 of 777.

    755 = rwx r-x r-x
    Eigenaar heeft Lees-, Schrijf- en Uitvoerrechten
    Groep heeft Lees- en Uitvoerrechten
    Andere heeft Lees- en Uitvoerrechten

    775 = rwx rwx r-x
    Eigenaar heeft Lees-, Schrijf- en Uitvoerrechten
    Groep heeft Lees-, Schrijf- en Uitvoerrechten
    Andere heeft Lees- en Uitvoerrechten

De Web Server zal nog steeds de Uitvoerrechten nodig hebben voor de gebruikersnaam en Lees, Uitvoergebruikersnaam vergoedingen om de Leesopdracht uit te voeren op bestanden binnen de map. Wederom kunnen deze permissies na het voltooien van de Web Installer worden teruggezet naar 755. Dat is de basis voor mappen behandeld, wat betreft bestanden? Dit is waar dingen een beetje eenvoudiger worden. De meeste bestanden die Joomla! gebruikt zullen behoorlijk tevreden zijn met de standaard permissies van 644.

    644 = rw- r-- r--
    Eigenaar heeft Lees- en Schrijfrechten
    Groep heeft Leesrechten
    Andere heeft Leesrechten

Dit is geldig als je geen noodzaak hebt om naar de bestanden te Schrijven vanaf de Web Server. Dezelfde regels gelden als voor mappen als je deze noodzaak wel hebt. Een bestand dat je misschien "Schrijfbaar" zou willen maken voor de Web Server is je configuration.php-bestand. Dit is het configuratiebestand voor Joomla!, als je van plan bent om configuraties te wijzigen via de Web Admin interface, dan moet dit bestand Schrijfbaar zijn voor de Web Server.

Als je server mappermissies nodig had om als "Andere" Schrijfbaar te worden ingesteld voor de installatie, dan zal dit bestand waarschijnlijk ook 757 of 777 moeten zijn. Het laten staan van dit bestand als 757 of 777 is echter gevaarlijk, aangezien je iedereen "Schrijfrechten" geeft; veel beveiligingsinbreuken op websites maken hier gebruik van, dus in het algemeen wordt niet aanbevolen om dit bestand met deze permissies te laten.

Als je Web Server een van de SU-tools heeft geïnstalleerd en je alleen 755 op mappen nodig had te configureren voor de installatie, dan zul je waarschijnlijk ook alleen 755 of 775 voor dit bestand moeten instellen om bewerkingen via de Admin interface mogelijk te maken, en deze permissies worden over het algemeen geaccepteerd als veiliger dan 757 of 777.

Kortom, welke permissies moeten worden ingesteld voor de Joomla! installatie? Nou, zoals je kunt zien, hangt het ervan af!

Ik weet dat dit niet zo behulpzaam is als je zou willen en het is zeker geen definitief antwoord, maar over het algemeen, na de installatie, kunnen eventuele onveilige "7" instellingen worden teruggezet naar iets veiliger. Bijvoorbeeld:

    Bestanden = 644
    Mappen = 755

Deze permissies zouden toestaan, voor bestanden;

    644 = rw- r-- r--
    Eigenaar heeft Lees- en Schrijfrechten
    Groep heeft alleen Leesrechten
    Andere heeft alleen Leesrechten

en voor mappen,

    755 = rwx r-x r-x
    Eigenaar heeft Lees-, Schrijf- en Uitvoerrechten
    Groep heeft alleen Lees- en Uitvoerrechten
    Andere heeft alleen Lees- en Uitvoerrechten

Als je toegang hebt tot een SSH-shell, kunnen de volgende opdrachten vanaf de opdrachtregel worden uitgevoerd om alle bestanden en mappen terug te zetten naar de serverdefaults van 755 en 644. Wijzig de mappen naar de bovenste map ("/") van je Joomla! installatie, en voer vervolgens uit:

    find . -type f -exec chmod 644 {} \;
    find . -type d -exec chmod 755 {} \;

Als je alleen FTP-toegang hebt, kan dit een zeer tijdrovende klus zijn, maar tenzij je meer mappen hebt veranderd tijdens de installatie dan werd gevraagd, zou je alleen ongeveer 10 mappen en het *configuration.php* bestand opnieuw moeten instellen.

Houd er rekening mee dat je om na de daadwerkelijke Joomla! installatie uitbreidingen of sjablonen te installeren, mogelijk de standaard permissies opnieuw op de juiste mappen voor de installatieperiode moet verhogen. Vervolgens kun je ze opnieuw verlagen nadat de toevoeging is geïnstalleerd.

Als je besluit om *caching* te gebruiken, moet de cachemap door de Web Server-gebruiker *beschrijfbaar* zijn om de tijdelijke bestanden te kunnen schrijven.

## Recurseerbaar permissies herstellen

In een terminalvenster, beginnend vanaf de Joomla-site-root, gebruik de volgende
commando's om bestand- en maprechten in te stellen naar de Joomla-standaardinstellingen.

find . -type f -exec chmod 644 {} \;
find . -type d -exec chmod 755 {} \;

Opmerking: Het find-commando gaat ervan uit dat het moet beginnen vanaf de huidige directory. Om veilig te zijn, ga naar je public_html-directory en specificeer een pad als het eerste
argument. Sommige shells, zoals bash op Apple OS X, moeten een pad hebben gespecificeerd
in het find-commando.

Test alle derde partij extensies na het wijzigen van de permissies.

*Vertaald door openai.com*

