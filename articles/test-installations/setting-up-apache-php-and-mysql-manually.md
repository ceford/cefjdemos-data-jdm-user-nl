<!-- Filename: Setting_up_Apache,_PHP_and_MySQL_manually / Display title: Handmatig Apache, PHP en MySQL instellen  -->

## Overzicht

Hier is een kort overzicht van de stappen om Apache, PHP en MySQL in te stellen in een Windows-omgeving. We verwijzen ook naar verschillende gerelateerde tools om de meeste taken met betrekking tot Joomla! te onderhouden en ermee te werken.

Om de instructie duidelijk en beknopt te houden, gaan we ervan uit dat, waar we geen expliciete instructies geven, je de standaard installatiepaden toepast zonder aanpassingen.

### Waarschuwing

Als je al een van de vooraf verpakte AMP-stacks op je computer hebt geïnstalleerd:

- Teruggaan naar je AMP-stack zal moeilijk zijn. De verschillende installaties die we hieronder uitvoeren, zullen registerwaarden overschrijven en algemene omgevingswijzigingen aanbrengen. (Dit geldt ten minste voor de PC/Windows-omgeving.)
- Als je enige configuratie (Apache, MySQL of PHP) of gegevens (je bestaande websites en gerelateerde databases) moet behouden, maak dan voor pogingen om deze instructie te volgen, goede back-ups.

(nodig uit te breiden met specifiek advies over hoe het bovenstaande te bereiken...)

## MySQL Installatie

1.  Download de geschikte <a href="https://dev.mysql.com/downloads/mysql/" rel="nofollow noreferrer noopener">MySQL-installateur</a> voor jouw platform.
2.  Start de installatie en kies een Aangepast installatiepad.
3.  Klik door het volledige installatieproces en klik op Voltooien.
4.  Je wordt nu gepresenteerd met de *MySQL Server Instance Configuration Wizard*.
    1.  Zorg ervoor dat de *Standaardconfiguratie* is geselecteerd en ga verder naar Volgende.
    2.  Als je MySQL al geïnstalleerd hebt, kun je de melding krijgen *Een Windows-service met de naam MySQL bestaat al. Verwijder deze service correct of kies een andere naam voor de nieuwe service.* Kies in dat geval een alternatieve servicenaam.
    3.  Controleer in het volgende venster of *Bin Directory opnemen in Windows PATH* is aangevinkt. Hierdoor kun je de verschillende MySQL-hulpprogramma's via de opdrachtregel benaderen.
    4.  In het volgende venster kun je een wachtwoord aanmaken voor je root MySQL-gebruiker, de gebruiker met het hoogste toegangslevel op je server.
    5.  In het laatste venster worden alle wijzigingen die je tot nu toe hebt geconfigureerd opgeslagen wanneer je op de knop *Uitvoeren* drukt, en wordt de Windows-service voor dit exemplaar gestart.

### Notities

1.  Om de instructie zo toegankelijk mogelijk te maken, hebben we een aantal configuratiescenario's van je MySQL-exemplaar overgeslagen, zoals de mogelijkheid om je databasebestanden te verplaatsen.
2.  MySQL installeert standaard met een STRICT-modus, wat kan leiden tot enkele fouten bij het gebruik van extensies of applicaties die hiermee geen rekening hebben gehouden.

### MySQL Bronnen

- <a href="https://www.heidisql.com/" class="external text" rel="nofollow noreferrer noopener">HeidiSQL</a> Een eenvoudig te gebruiken en uitbreidbare volledige client-vervanging van phpMyAdmin in constante ontwikkeling.
- <a href="https://dev.mysql.com/downloads/workbench/" class="external text" rel="nofollow noreferrer noopener">MySQL Workbench</a> Diverse tools waarvan je de Administrator zult waarderen, die je helpt bij het configureren van je MySQL-exemplaar. Vereist het <a href="https://dotnet.microsoft.com/nl-nl/" class="external text" rel="nofollow noreferrer noopener">.Net-framework</a>.
- <a href="https://www.phpmyadmin.net/" class="external text" rel="nofollow noreferrer noopener">phpMyAdmin</a> Een krachtige webgebaseerde MySQL-client voor het beheren van alles wat met MySQL te maken heeft.
- <a href="https://dev.mysql.com/doc/" class="external text" rel="nofollow noreferrer noopener">MySQL documentatie</a>

## Apache Installatie

1.  <a href="https://httpd.apache.org/download.cgi" class="external text" rel="nofollow noreferrer noopener">Download de installer</a> van uw voorkeur.
2.  Voer de installatie-wizard uit en klik door elke stap totdat u het Serverinformatie-venster bereikt. Vul de onderstaande opties respectievelijk en in de gegeven volgorde in elk van de velden in, tenzij u specifieke vereisten hebt voor de opzet van uw webserver:
    1.  localhost,
    2.  localhost en
    3.  admin@localhost
3.  Klik verder door de wizard heen, die de Apache webserver als een Windows-service zal installeren en starten.
4.  In de statusbalk van Windows ziet u nu een roze gekleurde veer met een groen gekleurd afspeelknopje dat aangeeft dat Apache actief is. Wijs uw browser naar <a href="http://localhost/" rel="nofollow noreferrer noopener">http://localhost/</a> en u zou een pagina moeten krijgen die aangeeft dat het werkt.
5.  Laten we nu naar de locatie gaan waar Apache is geïnstalleerd, wat gewoonlijk wordt gevonden op *C:\Program Files\Apache Software Foundation\Apache2.2*, en door de verschillende mappen bladeren.
    1.  *bin* - bevat de verschillende binaire bestanden, waarvan sommige hieronder zijn vermeld. Om toegang te krijgen tot deze toepassingen, waarvan de meeste op opdrachten zijn gebaseerd, moeten we het pad naar de *bin*-directory toevoegen aan onze globale PATH-variabele. Om dit te doen, klik met de rechtermuisknop op Deze computer \> Eigenschappen \> Geavanceerd \> Omgevingsvariabelen en zoek en selecteer de Variabele PATH in de lijst met Systeemvariabelen en klik op Bewerken en voeg een puntkomma toe aan het einde, indien nog niet aanwezig, gevolgd door het absolute pad naar uw bin-directory. Klik op Accepteren om uit het dialoogvenster Systeemeigenschappen te gaan.
        1.  *httpd.exe* dat de Apache webserver zelf is, die wordt gespawnd naar verschillende subprocessen terwijl het zoveel gelijktijdige inkomende clientverzoeken bedient als vereist door de MaxClients-directive;
        2.  *ab.exe* is een benchmarking-tool die met Apache wordt meegeleverd en waarmee u kunt zien hoe goed uw applicatie per tijdseenheid kan presteren
    2.  *conf* - map waar verschillende configuratiebestanden zich bevinden, waarvan de volgende in ons geval van het meeste belang zijn
        1.  *httpd.conf* - de meeste serverdirectieven bevinden zich in dit bestand en voor gemakkelijke toegang moet u het *.conf*-bestandstype associëren met een gebruiksvriendelijke editor, dat wil zeggen iets anders dan de standaard Kladblok.
        2.  *extra\httpd-vhosts.conf* - bevat directieven waarmee u uw lokale server kunt gebruiken als een virtuele host, dat wil zeggen in staat om meerdere servers op uw pc te draaien. Een gebruiksscenario is dat tijdens een ontwikkelingsfase, indien u het werkelijke domein waarvoor u werkt wilt koppelen aan uw lokale kopie, u dat kunt doen door kleine aanpassingen te maken in dit bestand. We zullen dit hieronder meer in detail bespreken.
    3.  *htdocs* - de standaard root van de webserver, hier wordt de <a href="http://localhost/" rel="nofollow noreferrer noopener">http://localhost/</a> naar verwezen, tenzij u dit niet opnieuw configureert in *httpd.conf* hierboven.
    4.  *logs* - toegang- en foutlogbestanden, nuttig bij het oplossen van problemen met uw server of zelfs uw applicatie

### Apache Hulpbronnen

- De
  <a href="https://httpd.apache.org/docs/current/" class="external text" rel="nofollow noreferrer noopener">Apache referentiedocumentatie</a>

## PHP Installatie

1.  <a href="https://windows.php.net/download/" class="external text" 
     rel="nofollow noreferrer noopener">Download PHP</a>
    en kies meestal voor VC6 x86 Thread Safe in Zip-formaat. De
    verschillende opties hebben te maken met hoe de PHP-codebase naar
    binair is gecompileerd en daar hoef je je waarschijnlijk nu geen
    zorgen over te maken.
2.  Maak een map aan onder je C:\Program Files\\ (of waar je
    programmamap zich ook bevindt) met de naam PHP.
3.  Zoek je gedownloade Zip-bestand en verplaats het naar de nieuw
    aangemaakte map en pak het direct in de map uit.
4.  Laten we nu het PHP-pad toevoegen aan onze globale PATH-variabele
    door de bovenstaande instructie te volgen.

### PHP Configureren

De configuratie komt neer op het bewerken van het *php.ini* bestand. Een voorbeeldbestand voor verschillende scenario's bevindt zich al in je PHP-map. Laten we *php.ini-development* hernoemen naar *php.ini* en openen in je favoriete teksteditor. De gebruikelijke waarden om aan te passen zijn als volgt en al deze variabelen zijn goed gedocumenteerd in het *php.ini* bestand. (Merk op dat dit een serverbrede instelling is die van toepassing is op al je projecten.):

- *max_execution_time* - wanneer je scripts hebt die te lang duren en de server verschillende onverwachte resultaten retourneert waarvan je denkt dat ze te wijten zijn aan het niet volledig kunnen uitvoeren van het proces
- *memory_limit*
- *error_reporting*
- *display_errors*
- *log_errors* - een variabele waarmee je rekening moet houden in productiescenario's
- *upload_tmp_dir*
- *upload_max_filesize*
- *extension_dir* - om complicaties te vermijden, zullen we wijzen op de map waar de volgende extensies zijn gelokaliseerd door deze variabele te decommentariëren en het absolute pad van de map toe te wijzen. De complete regel zou er als volgt uit moeten zien:
    extension_dir = "C:\Program Files\PHP\ext"

- De sectie Dynamische extensies bevat verschillende aanvullende modules die je wilt laden, en de uitgecommentarieerde zijn degene die voorverpakt zijn met PHP en kunnen worden gevonden in de *ext* directory in je PHP-map. Als je een wil activeren, verwijder je gewoon de commentaar, zoals je zou moeten doen met de volgende extensies:
  - php_curl.dll
  - php_gd2.dll
  - php_mbstring.dll
  - php_mysql.dll
  - php_mysqli.dll
  - php_pdo.dll
  - php_pdo_mysql.dll
  - php_xsl.dll
- session.save_path

### Apache Configureren om met PHP te Werken

Nu we PHP hebben geconfigureerd om te werken zoals we willen, laten we naar Apache gaan en hetzelfde doen.

- Open *httpd.conf* en voeg in de sectie "Dynamic Shared Object (DSO) Support" de volgende richtlijnen toe. (Als je je PHP-map anders hebt gelokaliseerd, dien je overeenkomstige wijzigingen aan te brengen voor php5apache2_2.dll hieronder.):
    LoadModule php5_module "C:/Program Files/PHP/php5apache2_2.dll"
    AddType application/x-httpd-php .php

- Voeg in de DirectoryIndex *index.php* en *index.htm* toe als mogelijke bestanden om te serveren wanneer de directory als volgt wordt opgevraagd:
    DirectoryIndex index.html index.htm index.php

- Voeg aan het einde van het bestand de volgende regel toe die aangeeft waar het *php.ini* bestand zich bevindt:
    PHPIniDir "C:/Program Files/PHP"

### PHP Herstarten en Testen

Zodra je een wijziging aanbrengt in *php.ini*, *httpd.conf* of andere configuratiebestanden, moet je Apache herstarten om het effect van de wijzigingen te zien. Laten we nu Apache herstarten door de Apache Monitor-tool te gebruiken die je kunt vinden in je Windows-statusbalk. Hopelijk wordt je niet geprompt met enkele dialogen en blijft de Apache Monitor groen.

We zullen nu testen of PHP werkt. Ga naar de documentroot van je webserver (in het standaardgeval *C:\Program Files\Apache Software Foundation\Apache2.2\htdocs*) en voeg een bestand toe met de naam *phpinfo.php* met de volgende inhoud:

Dit zal een pagina renderen met informatie over je PHP-installatie en over de verschillende modules/extensies die momenteel geladen zijn. Richt je browser naar <a href="http://localhost/phpinfo.php" rel="nofollow noreferrer noopener">http://localhost/phpinfo.php</a>.

### *xdebug* Installeren en Configureren

1.  Richt je browser op <a href="https://xdebug.org/wizard" class="external text" 
     rel="nofollow noreferrer noopener">Xdebug Installation Wizard</a>. Deze pagina helpt je om een geschikte versie van Xdebug te vinden.
2.  Kopieer de volledige pagina van de *phpinfo* pagina die we hierboven hebben uitgevoerd en plak het in het tekstgebied en volg de gegeven instructies om te installeren.

### XDebug Bronnen

- De <a href="https://www.php.net/docs.php" class="external text" 
   rel="nofollow noreferrer noopener">PHP Handleiding</a>
  Uitstekende en up-to-date documentatie met waardevolle extra opmerkingen van gebruikers. Downloadbare versies zijn beschikbaar.
- De <a href="https://xdebug.org/docs/" class="external text" 
  rel="nofollow noreferrer noopener">Xdebug 3 Documentatie</a>

*Vertaald door openai.com*

