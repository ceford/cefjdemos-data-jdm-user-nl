<!-- Filename: J4.x:Hosting_Setup / Display title: Hosting Setup -->

## Introductie

Deze pagina biedt enige begeleiding voor iedereen die helemaal nieuw is in hostingtechnologie. Je kunt een website instellen op je eigen laptop of desktopcomputer. Dit staat bekend als lokaal hosten en is een goede manier om met nieuwe functies te experimenteren en is volledig gratis. Om je website-inhoud beschikbaar te maken voor de rest van de wereld, heb je een account nodig bij een hostingdienst en daarvoor zul je moeten betalen.

## Ondersteunende Software

Joomla! is een applicatie die afhankelijk is van drie onderdelen van ondersteunende software: de PHP-scripttaal, een database (een van MySQL, MariaDB of PostgreSQL) en een webserver (een van Apache, Nginx, Microsoft IIS, of ...). De minimale versienummers worden aangegeven in de volgende tabellen:

### Vereisten voor Joomla! 5.x

| Software           | Aanbevolen      | Minimum     |
|--------------------|-----------------|-------------|
| PHP                | 8.3             | 8.1.0       |
| **Databases**      |                 |             |
| MySQL              | 8.1             | 8.0.13      |
| MariaDB            | 11.1.0          | 10.4.0      |
| PostgreSQL         | 16.0            | 12.0        |
| **Webservers**     |                 |             |
| Apache             | 2.4             | 2.4         |
| Nginx              | 1.25            | 1.21        |
| Microsoft IIS      | 10              | 10          |

### Vereisten voor Joomla! 4.x

| Software           | Aanbevolen      | Minimum     |
|--------------------|-----------------|-------------|
| PHP                | 8.2             | 7.2.5       |
| **Databases**      |                 |             |
| MySQL              | 8.0             | 5.6         |
| PostgreSQL         | 11.0            | 11.0        |
| **Webservers**     |                 |             |
| Apache             | 2.4             | 2.4         |
| Nginx              | 1.18            | 1.10        |
| Microsoft IIS      | 10              | 8           |

## Hostingdiensten

Commerciële hostingdiensten bieden alles wat je nodig hebt om een website te ondersteunen. Sommige bieden ook een installatie met één klik van populaire applicaties zoals Content Management Systemen, prikborden, wiki's enzovoort. Let op: Joomla-forumexperts raden het gebruik van de installatie met één klik van Joomla niet aan.

Elke hostingdienst biedt verschillende plannen tegen verschillende prijsniveaus. Hoe meer je betaalt, hoe meer schijfruimte en bandbreedte je krijgt, samen met meer e-mailadressen, databases enzovoort. Sommige bieden ook een gratis domeinnaam aan. Meestal moet je betalen voor een domeinnaam en een kleine jaarlijkse registratievergoeding.

## Gratis Hosting

Er is niet zoiets als gratis hosting! Er is echter een Joomla-partner hosting service die een gratis Joomla-website aanbiedt op het domein joomla.com. Dit geeft je de kans om je eigen volledig functionele Joomla-website geheel gratis uit te proberen. Het lijkt op een gedeeld hostingplan maar met beperkingen en frequente verzoeken om te upgraden naar een betaald plan. En het gratis plan moet elke 30 dagen worden verlengd, anders wordt het beëindigd. Het volgende artikel laat de stappen zien die nodig zijn om een gratis Joomla-site op te zetten.

* [Gratis Joomla Hosting](jdocmanual?article=user/hosting/free-hosting)

Als je merkt dat je Joomla leuk vindt, kun je upgraden naar een betaald plan of elders zoeken naar een hostingservice die bij je behoeften en budget past.

## Gedeelde Hosting

Je kunt een minimaal hostingplan verkrijgen voor ongeveer £/$/€50 per jaar. Dit niveau van het plan wordt vaak gedeeld hosting genoemd en is geschikt voor alles wat geen gevoelige data betreft. Bedrijven moeten gespecialiseerd advies inwinnen over geschikte hostingplannen. Het kiezen van een hostingdienst is niet zonder problemen. De goedkoopste kan onredelijk beperkende *php.ini*-instellingen hebben die niet in hun advertenties staan. Sommigen kunnen een slechte reputatie hebben wat betreft ondersteuning.

Als je kiest voor een gedeeld hostingplan, controleer dan het volgende:

- Ondersteuning voor PHP-toepassingen zoals Joomla, WordPress en Mediawiki.
- Schijfruimte: 500Mb is een absoluut minimum. 1Gb of meer zou beter zijn als je van plan bent veel afbeeldingen te gebruiken.
- Aantal databases: Joomla gebruikt er één, maar je zult al snel merken dat je er 5 of 10 of meer nodig hebt. Sommige plannen bieden een onbeperkt aantal binnen de totale schijfruimte.
- Databasegrootte: met Smart Search kan de database heel snel groeien. Als gedeelde hosting een beperking heeft op de grootte van de database, is het belangrijk om te weten wat dit is. Het kan ertoe leiden dat een site niet werkt.
- Aantal e-mailadressen: veel!
- Aantal HTTP- en DB-verbindingen met de server, die sommige gedeelde hosts beperken.
- Back-ups: hoe worden deze gedaan, en is er een dienstverleningsdocument (TOS) waarin staat wie verantwoordelijk is voor back-ups.

Controleer ook het aangeboden configuratiescherm en platform. Afgaande op forumberichten gebruiken de meesten cPanel op Linux. De hostingdienst moet alle basissoftware voor websiteondersteuning bieden:

- Apache webserver 2.4+ - *directory indexes* moeten uitgeschakeld zijn. Ook ondersteund:
  - Nginx 1.18+ (minder gebruikers dus minder forumondersteuning)
  - Microsoft IIS\[6\] (minder gebruikers dus minder forumondersteuning)
- MySQLi database 8.1+ of MariaDB-klone met InnoDB-ondersteuning. Ook ondersteund:
  - PostgreSQL 11.0+ (minder gebruikers dus minder forumondersteuning).
- PHP 8+ wordt aanbevolen.
- phpMyAdmin databasebeheer-tool.

Controleer vóór aankoop de volgende minimale PHP-vereisten voor Joomla:

- *memory_limit* - Minimum: 256M
- *upload_max_filesize* - Minimum: 64M
- *post_max_size* - Minimum: 64M
- *max_execution_time* - Aanbevolen: 30
- *allow_url_fopen* - waar

Veel van deze parameters kunnen door de gebruiker in cPanel worden ingesteld. Vraag of dat mogelijk is.

Als je een domeinnaam hebt gekocht, zal je hostingdienst deze voor je configureren. Ze zouden je ook een IP-adres moeten geven om te gebruiken totdat je domeinregistratie doorvoert naar Domain Name Servers (DNS), meestal enkele uren.

Het volgende artikel laat zien wat je kunt verwachten als je een hostingplan aanschaft dat een cPanel-gebruikersinterface omvat.

* [cPanel Hosting](jdocmanual?article=user/hosting/cpanel-hosting)

## VPS Hosting

Een Virtual Private Server (VPS) hosting plan biedt volledige toegang tot een server die hardware deelt. Het gedraagt zich als een toegewijde computer. Je kunt de server stoppen en starten, opnieuw opstarten en je eigen software installeren net zoals je op een desktopcomputer zou doen. Je kunt accounts maken voor individuele gebruikers, net als bij gedeelde hosting. Doorgaans kun je enkele functies inschakelen die normaal niet zijn toegestaan in gedeelde hostingaccounts.

Dedicated en Cloud hosting plannen zijn vergelijkbaar in principe maar bieden ofwel toegewijde bronnen of bronnen op maat van jouw behoeften.

Deze geavanceerde plannen worden hier niet behandeld.

## Lokale Hosting

De meeste individuen die websites ontwikkelen, houden lokale kopieën op een laptop of desktopcomputer om updates of nieuwe extensies te testen of om nieuwe ontwerpen uit te proberen. Het opzetten van een lokale ontwikkelingssite vereist enige technische kennis, maar het is vrij eenvoudig om eenvoudige instructies te volgen.

De volgende artikelen beschrijven hoe je lokale hosting op verschillende types desktop- of laptopcomputers kunt opzetten:

* [Lokale Hosting op Windows](jdocmanual?article=user/hosting/local-hosting-on-windows) alleen voor Windows
* [Lokale Hosting met XAMPP](jdocmanual?article=user/hosting/local-hosting-with-xampp) voor Linux, Mac en Windows.
* [Lokale Hosting op Linux](jdocmanual?article=user/hosting/local-hosting-on-linux) 

