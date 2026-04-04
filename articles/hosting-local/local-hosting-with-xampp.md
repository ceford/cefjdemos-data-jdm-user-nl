<!-- Filename: / Display title: Lokale Hosting met XAMPP  -->

## Introductie

XAMPP is een eenvoudig te installeren pakket dat de Apache webserver, PHP, XDEBUG en de MySQL-database bundelt. Hiermee kun je de omgeving creëren die je nodig hebt om Joomla! op je lokale machine te draaien. De nieuwste versie van XAMPP is beschikbaar op de [Apache Friends](https://www.apachefriends.org/index.html) website. Downloads zijn beschikbaar voor Linux, Windows en Mac OS X. Download het pakket voor jouw platform.

*Belangrijke Opmerking Betreffende XAMPP en Skype:* Apache en Skype gebruiken allebei poort 80 als een alternatief voor inkomende verbindingen. Als je Skype gebruikt, ga dan naar het paneel Extra-Opties-Geavanceerd-Verbindingen en deselecteer de optie *Gebruik poort 80 en 443 als alternatieven voor inkomende verbindingen*. Als Apache als een service start, zal het poort 80 in beslag nemen voordat Skype start en zul je geen probleem ondervinden. Maar om veilig te zijn, schakel de optie uit in Skype.

## Installatie

Installatie op elk platform is heel eenvoudig - gebruik de Installer. Er is geen echt handboek of handleiding voor XAMPP. De documentatie is in de vorm van veelgestelde vragen die gelinkt zijn vanaf de Download-pagina.

### Installatie op Windows

Voor Windows wordt aanbevolen om XAMPP te installeren in "c:\xampp" (niet in "c:\program files"). Als je dit doet, zullen je Joomla! (en andere lokale website mappen) in de map "c:\xampp\htdocs" komen. (Volgens conventie gaat alle webcontent onder de "htdocs" map.)

Als je meerdere HTTP-servers hebt (zoals IIS), kun je de luisterpoort van xampp wijzigen. In \apache\conf\httpd.conf, wijzig je de regel Listen 80 naar Listen \[poortnummer\] (bijv. "Listen 8080").

<div class="alert alert-info">
<h4>Joomla Community Magazine Tutorial</h4>
<p>Je kunt een gedetailleerde tutorial vinden over het installeren van XAMPP op Windows, samen met de Joomla 4 Beta, de Joomla Patch Tester en Git in dit <a href="https://magazine.joomla.org/all-issues/june-2020/github-installing-git" rel="noreferrer noopener">artikel van het Joomla Community Magazine</a>.</p></div>

Om XDebug te installeren: [XAMPP - XDebug Setup voor PHP 8](https://odan.github.io/2020/12/03/xampp-xdebug-setup-php8.html)

### Installatie op Linux

#### Installeer XAMPP

De Download-pagina downloadt een installer xampp-linux-x64-8.2.12-0-installer.run waarbij 8.2.12 de nieuwste versie is. Voer het installatiebestand uit om Apache2, MySQL en PHP te installeren.

Na de installatie gebruik je de volgende commando's om de services te starten en te stoppen:
```sh
    sudo /opt/lampp/lampp start
    sudo /opt/lampp/lampp stop
```

#### Test je XAMPP localhost server

Open je browser en navigeer naar

    http://localhost

De index.php zal omleiden naar

    http://localhost/xampp

Daar vind je instructies over hoe je de standaardgebruikersnamen/-wachtwoorden kunt wijzigen. Op een pc die geen bestanden bedient aan het internet of LAN is het wijzigen van de standaarden een persoonlijke beslissing.

#### Haal Joomla

* Download het nieuwste Joomla installatie-zipbestand
* Pak het uit naar je harde schijf
* Verbind met localhost met een FTP-client standaard
* Maak een map voor je Joomla op de localhost server
* FTP de uitgepakte Joomla installatiebestanden naar de nieuw aangemaakte Joomlamap.

##### Belangrijk:

- De xampp-installatie stelt de juiste Eigendom van de bestanden en machtigingen in.
- Het gebruik van de **CHOWN-commando** zal **eigendom problemen met xampp veroorzaken**.
- **Het gebruik van nautilus** om mappen/bestanden te manipuleren op localhost zal **eigendom problemen met xampp veroorzaken**.

#### Database-informatie

- Host: localhost
- Standaard databasenaam: test
- Standaard databasegebruiker: root
- Standaard wachtwoord: Er is **geen** standaard wachtwoord.
- Wachtwoord administrator: jouw keuze.

Het installeren van voorbeeldgegevens wordt aanbevolen voor de beginnende gebruiker.

Na installatie verwijder je de installatiemap en navigeer je browser naar: `http://localhost/yournewjoomlafolder` of `http://localhost/yournewjoomlafolder/administrator`.

#### Een koppeling maken in het Ubuntu-menu

##### Om een GUI voor xampp te maken die is verbonden met je Ubuntu-menu

Open de Terminal en typ

    sudo nano /usr/share/applications/xampp-control-panel.desktop

Kopieer en plak het volgende in de nano editor en sla op.

    [Desktop Entry]
    Encoding=UTF-8
    Name=XAMPP Control Panel
    Comment=Start and Stop XAMPP
    Exec=gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"
    Icon=/usr/share/icons/Tango/scalable/devices/network-wired.svg
    Terminal=false
    Type=Application
    Categories=GNOME;Application;Network;
    StartupNotify=true

Als het bedieningspaneel niet start, probeer het Exec-commando rechtstreeks in de terminal uit te voeren:

    gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"

Als je de foutmelding krijgt:

    Error importing pygtk2 and pygtk2-libglade

Installeer de ontbrekende libraries:

    sudo apt-get install python-glade2

#### XDebug PHP Debugger

Het XAMPP-pakket voor Linux bevat niet de XDebug PHP Debugger. Om XDebug te installeren op Debian of Ubuntu:

- Installeer het *build-essential* pakket:

    sudo apt-get update
    sudo apt-get install build-essential
    sudo apt-get install autoconf

- Download het [ontwikkel-pakket](http://www.apachefriends.org/en/xampp-linux.html) voor jouw versie van XAMPP en pak deze uit over je bestaande installatie:

    sudo tar xvfz xampp-linux-devel-1.7.7.tar.gz -C /opt

- Bouw XDebug:

    wget http://xdebug.org/files/xdebug-2.1.3.tgz
    tar xzf xdebug-2.1.3.tgz
    cd xdebug-2.1.3/
    /opt/lampp/bin/phpize

Na dit krijg je de volgende output op je console...

    Configuring for:
    PHP Api Version:         20090626
    Zend Module Api No:      20090626
    Zend Extension Api No:   20090626

    ./configure --with-php-config=/opt/lampp/bin/php-config
    make
    sudo make install

Daarna zal de output dit zijn.. let goed op de opgegeven directory.

    Installing shared extensions:     /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/

Maak een map in je temp map aan die het datbestand zal bewaren gegenereerd door XDebug:

    sudo mkdir /opt/lampp/tmp/xdebug
    sudo chmod a+rwx -R /opt/lampp/tmp/xdebug

Alternatieve installaties:

Installeer met behulp van de PHP extensions community library (PECL) gebundeld met xampp:

    sudo /opt/lampp/bin/pecl install xdebug

Op Ubuntu/Debian kun je installeren met:

    apt-get install php5-xdebug

(waarschuwing: dit zal ook Apache en PHP uit de apt-repositories installeren).

##### Waarschuwing voor 64-bit gebruikers

Wanneer je XDebug compileert of installeert via apt-get, ontvang je een foutmelding bij het (her)starten van xampp:

    /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/xdebug.so: wrong ELF class: ELFCLASS64

Dit komt omdat xampp als 32-bits draait maar XDebug 64-bits is. Om dit probleem te verhelpen, maak xdebug.so op een 32-bits machine of download het van:

    http://code.activestate.com/komodo/remotedebugging/

Download het bestand: "PHP Remote Debugging Client" voor "Linux (x86)". Pak de inhoud van het bestand uit op je computer, dit gecomprimeerde bestand bevat verschillende mappen met versienummers bijv. 4.4, 5.0, 5.1 ... 5.3 enzovoort, ga in de map met het hoogste versienummer of de map die voor jou werkt, en kopieer dan handmatig het bestand "xdebug.so" naar de volgende locatie, overschrijf indien nodig:

    /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/

Vergeet niet dat deze locatie anders kan zijn op je computer.

### Installatie op Mac OS X

Mac OS X bevat eigenlijk al een Apache-server, maar de meeste ontwikkelaars geven de voorkeur aan de geïntegreerde tools en configureerbaarheid geleverd door XAMPP.

Zoals met de meeste programma’s op Mac, is de installatie eenvoudig. Bezoek de [Apache Friends](https://www.apachefriends.org/) website en download de installer (xampp-osx-8.2.4-0-installer.dmg). Dubbelklik op de gedownloade installer om het installatieproces te starten.

Om de server te starten, open je "XAMPP Control.app" en druk je op de startknop naast Apache.

#### Een beetje probleemoplossen

Veel Mac-gebruikers hebben wat moeilijkheden op dit punt bij het instellen van een andere instantie van Apache op hun machine. Als je de Apache van XAMPP niet kunt starten, heb je twee opties:
**Je kunt de luisterpoort van XAMPP wijzigen.** In \Applications\XAMPP\xamppfiles\etc\httpd.conf, wijzig je de regel die zegt: "Listen 80" naar Listen \[poortNummer\]. Bijv.:

    Listen 8080

**Je kunt de luisterpoort van de vooraf geïnstalleerde Apache-server wijzigen.** In Finder ga je naar "/etc" (CMD+SHIFT+G); vanaf hier kun je door de normaal verborgen Apache-bestanden navigeren. Vind de map genaamd Apache2, en bewerk het "http.conf" bestand. Wijzig de regel die zegt: "Listen 80" naar Listen \[poortNummer\]. Bijv.:

    Listen 8080

*Opmerking: Als je ervoor kiest de poort van de vooraf geïnstalleerde Apache-server te wijzigen, moet je mogelijk je computer opnieuw opstarten om de wijzigingen van kracht te laten worden. Je zult ook moeten aanmelden als administrator om deze bestanden te kunnen wijzigen.*

### Test XAMPP Installatie

Zodra XAMPP is geïnstalleerd en je de Apache-service hebt gestart met behulp van de XAMPP Control Panel tool, kun je het testen door je browser te openen en te navigeren naar `http://localhost`. Je zou het XAMPP welkomstscherm moeten zien, vergelijkbaar met degene hieronder.

![De xampp startpagina](../../../en/images/hosting/local-hosting-xampp.png)

Selecteer de link genaamd `phpinfo()` in het bovenste menu. Dit zal een lange pagina met informatie over de PHP-configuratie weergeven, zoals hieronder weergegeven.

![De xampp php versie informatiepagina](../../../en/images/hosting/local-hosting-xampp-php.png)

Op dit punt is XAMPP succesvol geïnstalleerd. Let op het *Loaded Configuration File*. We zullen dit bestand in het volgende gedeelte bewerken om XDebug te configureren.

*Vertaald door openai.com*

