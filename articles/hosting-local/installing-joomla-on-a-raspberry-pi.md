<!-- Filename: Installing_Joomla_on_a_Raspberry_Pi / Display title: Raspberry Pi-installatie -->

## Voorwoord

**Opmerking: Dit document is nog niet volledig en uitgebreid getest.**

De <a href="https://www.raspberrypi.org/" rel="nofollow noreferrer noopener">Raspberry Pi</a> is een kleine single-board computer die oorspronkelijk is ontwikkeld om de basisprincipes van informatica te onderwijzen op scholen en in ontwikkelingslanden. Vanwege zijn veelzijdigheid is het erg populair geworden en wordt het gebruikt als mediaplayer, kleine zelfstandige server, enz. Je kunt het gebruiken als webserver en Joomla! erop installeren. Deze pagina laat je zien hoe je jouw Joomla!-website kunt laten draaien op de Raspberry Pi.

## Hardware

- **Raspberry Pi versie 3 Model B** - Er zijn verschillende modellen van
  Raspberry Pi. Je kunt de meeste modellen gebruiken die een Ethernet-poort hebben (de
  Model B types). Voor de prestaties gebruiken we echter de nieuwste versie
  met het meeste RAM-geheugen.
- **microSD-kaart** - Voor het besturingssysteem + webserver + Joomla.
  (RPi versie 3 Model B gebruikt een microSD-kaart, andere versies kunnen normale
  SD-kaarten gebruiken)
- **5 Volt adapter (1 Ampère)** - Om de Raspberry Pi van stroom te voorzien moet je
  de netspanning (230V of 110V) omzetten naar 5 Volt. De Raspberry Pi
  heeft ongeveer 1 Ampère nodig, en misschien meer als je USB-apparaten erop aansluit.
- standaard **Ethernet-kabel** - om de RPi aan te sluiten op je Local Area
  Network / router / het internet.

## Installeren van Besturingssysteem

Het besturingssysteem Raspbian is een versie van Debian Linux speciaal gecompileerd voor de Raspberry Pi. Er zijn twee versies van <a href="https://www.raspberrypi.com/software/" rel="nofollow noreferrer noopener">Raspbian</a> beschikbaar: **Raspbian Jessie met Pixel Lite** (versie met PIXEL desktop gebaseerd op Debian Jessie) en **Raspbian Jessie Lite** (minimale versie gebaseerd op Debian Jessie). Omdat we de Raspberry Pi als webserver voor Joomla gebruiken, hebben we de GUI niet nodig.

**Download** <a href="https://www.raspberrypi.org/downloads/raspbian/" rel="nofollow noreferrer noopener">Raspbian Jessie Lite</a> en pak het gedownloade bestand uit, bijvoorbeeld **2016-09-23-raspbian-jessie-lite.zip** (306 MB) naar **2016-09-23-raspbian-jessie-lite.img** (1,4 GB).

Nu moeten we het .img-bestand naar de (micro) SD-kaart kopiëren. Je kunt een tool met grafische interface gebruiken zoals <a href="https://unetbootin.github.io/" rel="nofollow noreferrer noopener">UNetbootin</a> (voor Windows, Mac OS X en Linux) of dit via de command line doen.

**Wees voorzichtig** bij het schrijven van de *.img*-schijf afbeelding naar een andere schijf. Als je de verkeerde doelbestandschijf opgeeft, overschrijf je die schijf met de *.img*, waardoor deze schijf onbruikbaar wordt en dataverlies veroorzaakt.

### Windows

Controleer in een terminal (CMD) welk apparaat met de SD-kaart overeenkomt en voer iets uit zoals:

```
    dd bs=1M if=c:\temp\2016-09-23-raspbian-jessie-lite.img of=[het apparaat van je SD-kaart]
```

Zie ook <a href="https://www.raspberrypi.org/documentation/installation/installing-images/windows.md" rel="nofollow noreferrer noopener">Besturingssysteemafbeeldingen installeren met Windows</a>

### Apple OSX

Controleer welk apparaat voor je SD-kaart wordt gebruikt. In ons geval is het *disk1s1* en we voeren in Terminal:

```
    sudo dd bs=1M if=~/Downloads/2016-09-23-raspbian-jessie-lite.img of=/dev/disk1s1
```

Zie ook: <a href="https://www.raspberrypi.org/documentation/installation/installing-images/mac.md" rel="nofollow noreferrer noopener">Besturingssysteemafbeeldingen installeren op MacOS</a>

### Linux

We verbinden een SD-kaartlezer met de (micro) SD-kaart met een computer. Met *dmesg* kunnen we de apparaatnaam van de SD-kaart vinden. In ons geval toont dmesg iets zoals `[xxxxxx.xxxxxxx]  sdd: sdd1 sdd2`, wat betekent dat we een SD-kaart met 2 partities hebben. Schrijf de Raspbian afbeelding niet naar een partitie maar naar de hele schijf **sdd**.

We zullen *dd* ("Disk Dump") gebruiken om een invoerbestand (*if*) naar een uitvoerbestand (*of*) te schrijven met een gespecificeerde blokgrootte (*bs*).

**Wees voorzichtig**: *dd* schrijft naar een apparaat zonder enige waarschuwing. Controleer dubbel of je naar het juiste apparaat schrijft! Als je naar de verkeerde schijf schrijft, zul je het *dd* commando altijd herinneren als "Disk Destroyer".

```bash
    sudo dd if=~/Downloads/2016-09-23-raspbian-jessie-lite.img of=/dev/sdd bs=4M
```

Zie ook <a href="https://www.raspberrypi.org/documentation/installation/installing-images/linux.md" rel="nofollow noreferrer noopener">Besturingssysteemafbeeldingen installeren op Linux</a>

**WAARSCHUWING voor Raspbian Stretch versie**: om een SSH-server vanaf de boot werkend te krijgen, moet je een leeg bestand *ssh* creëren op de root partitie.

## Raspberry Pi Verbinden met LAN

Wanneer we het Raspbian-besturingssysteem op de SD-kaart hebben geïnstalleerd, zullen we:

- De micro SD-kaart in de SD-kaartsleuf van de Raspberry Pi plaatsen.
- Een Ethernet-kabel aansluiten op de Raspberry Pi en op het lokale netwerk (aansluiten op onze router).
- De 5V-voeding aansluiten op de Raspberry Pi.

Het opstarten van de Raspberry Pi duurt ongeveer 30 seconden. We moeten het IP-adres vinden om verbinding te maken via SSH. We kunnen daar verschillende benaderingen voor gebruiken:

- Log in op de webinterface van je router en zoek naar de verbonden apparaten;
- Gebruik een mobiele telefoon die is verbonden met de wifi-router met een netwerkscan-app genaamd **Fing Overlook**;
- Gebruik een opdracht zoals **nmap**. Aangezien onze pc het IP-adres **192.168.0**.25 heeft, kunnen we alle andere apparaten in hetzelfde netwerkbereik vinden door het volgende te doen:
```
    sudo nmap -sP 192.168.0/24
```
Dit kan de volgende details tonen:

    Starting Nmap 6.47 ( http://nmap.org ) at 2016-10-22 17:42 CEST
    Nmap scan report for 192.168.0.35
    Host is up (0.00042s latency).
    MAC Address: 42:42:42:42:42:42 (Raspberry Pi Foundation)

Om in te loggen op onze Raspberry Pi gebruiken we de opdracht **ssh**.

```
    ssh pi@192.168.0.35
```

De eerste keer dat je verbinding maakt, zal het iets als het volgende tonen:

    The authenticity of host '192.168.0.35 (192.168.0.35)' can't be established.
    ECDSA key fingerprint is 42:42:42:42:42:42:42:42:42:42:42:42:42:42:42:42.
    Are you sure you want to continue connecting (yes/no)?

We zullen kiezen voor **Yes**

    Warning: Permanently added 192.168.0.35 (ECDSA) to the list of known hosts.
    pi@192.168.0.35's password:

En gebruik het *standaard wachtwoord*: *raspberry*, wat bij succesvolle login het volgende zal tonen:

    The programs included with the Debian GNU/Linux system are free software;
    the exact distribution terms for each program are described in the
    individual files in /usr/share/doc/*/copyright.

    Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
    permitted by applicable law.
    pi@raspberrypi:~ $

We kunnen de Raspberry Pi configureren via een tekstinterface met:

    sudo raspi-config

### Raspberry Pi Software Configuration Tool (raspi-config)

Met deze configuratietool zullen we alleen de volgende instellingen wijzigen.

#### 1 Uitbreiden Bestandssysteem

Standaard is de schijfruimte op de SD-kaart even groot als het 1.4GB .img-bestand dat je hebt gebruikt om de SD-kaart te maken voor je Raspberry Pi. Je kunt deze optie gebruiken om de rest van de schijfruimte te benutten.

#### 2 Wijzig Gebruikerswachtwoord

Om veiligheidsredenen is het het beste om **het standaardwachtwoord** "raspberry" zo snel mogelijk te **wijzigen**.

#### 3 Opstartopties

We willen dat de Raspberry Pi opstart naar de Tekstconsole.

##### B2 Console Autologin Tekstconsole, automatisch ingelogd als 'pi' gebruiker

#### 9 Geavanceerde Opties

##### A3 Geheugen Splits

Omdat we de Raspberry Pi zullen gebruiken als een headless server zonder deze aan een monitor te verbinden, kunnen we het geheugen dat wordt gebruikt voor de GPU verminderen van 64 naar **16**.

#### 5 Internationalisatie-opties

##### I2 Wijzig Tijdzone

We zullen de Tijdzone wijzigen naar onze eigen tijdzone (bijvoorbeeld Europa/Amsterdam).

Na alle wijzigingen zullen we de Raspberry Pi herstarten en opnieuw inloggen met ons nieuwe wachtwoord.

    ssh pi@192.168.0.35

Nu is het tijd om de rest te installeren.

## Software bijwerken

Voordat we iets anders installeren, zullen we:

- de lijst met softwareversies van alle externe
  repositories **bijwerken**
    `sudo apt-get update`

- alle geïnstalleerde software **upgraden**
    `sudo apt-get upgrade`

**Het bijwerken van de versielijst en het upgraden van alle software is iets dat
regelmatig gedaan moet worden.**

## Nginx Webserver

Een snel en lichtgewicht alternatief voor de Apache-webserver is de steeds populairder wordende **Nginx** webserver.

### Installatie van Nginx

We zullen nginx en alle benodigde afhankelijkheden (lees: software die nginx nodig heeft om te functioneren) installeren met

    sudo apt-get install nginx

We krijgen een bericht zoals:

    Pakketlijsten worden ingelezen... Klaar
    Boom van vereisten wordt opgebouwd
    Statusinformatie wordt gelezen... Klaar
    De volgende extra pakketten zullen geïnstalleerd worden:
     fontconfig-config fonts-dejavu-core libfontconfig1 libgd3 libjbig0 libtiff5 libvpx1 libxpm4 libxslt1.1 nginx-common nginx-full
    Voorgestelde pakketten:
     libgd-tools fcgiwrap nginx-doc ssl-cert
    De volgende NIEUWE pakketten zullen geïnstalleerd worden:
     fontconfig-config fonts-dejavu-core libfontconfig1 libgd3 libjbig0 libtiff5 libvpx1 libxpm4 libxslt1.1 nginx nginx-common nginx-full
    0 opgewaardeerd, 12 nieuw geïnstalleerd, 0 te verwijderen en 0 niet opgewaardeerd.
    Er moeten 3.550 kB aan archieven opgehaald worden.
    Na deze operatie zal er 8.666 kB aan additionele schijfruimte gebruikt worden.
    Wilt u doorgaan? [J/n] j

Door "j" te kiezen, zullen nginx en alle benodigde pakketten worden geïnstalleerd.

Je kunt de installatie controleren met een browser. Ga naar het IP-adres van je Raspberry Pi, in ons geval
<a href="http://192.168.0.35/"
rel="nofollow noreferrer noopener">http://192.168.0.35/</a> We zouden een bericht moeten zien zoals:

    Welkom bij nginx op Debian!
    Als je deze pagina ziet, is de nginx-webserver succesvol geïnstalleerd en werkt op Debian. Verdere configuratie is vereist.
    Voor online documentatie en support verwijzen wij naar nginx.org
    Gebruik alstublieft het reportbug-hulpmiddel om bugs in het nginx-pakket met Debian te rapporteren.
    Controleer echter bestaande bugrapporten voordat u een nieuwe bug rapporteert.
    Bedankt voor het gebruik van Debian en nginx.

#### Starten en stoppen van Nginx

Na installatie zal Nginx automatisch worden gestart. Je kunt:

- Nginx stoppen: sudo service nginx stop
- Nginx starten: sudo service nginx start
- Nginx herstarten: sudo service nginx restart

### Configureren van Nginx

#### Globale Nginx-configuratie

In de globale configuratie van Nginx kunnen we standaard caching configureren enzovoort. De Raspberry Pi 3 gebruikt een 1.2 GHz 64-bit **quad-core** ARM Cortex-A53 processor. Als je een eerdere versie hebt met minder CPU-kernen, dan moet je

    sudo nano /etc/nginx/nginx.conf

gebruiken om de "worker_processes" aan te passen aan het aantal CPU's van je apparaat. Standaard is het geconfigureerd als

    worker_processes 4;

dus voor Raspberry Pi 3 hoef je het niet te veranderen.

Na het aanpassen van de Nginx-configuratie of virtuele domeinconfiguratie, moet je een

    sudo nginx reload

doen om de wijzigingen door te voeren.

#### Virtuele Domeinen

Het is mogelijk om meerdere Joomla-websites op dezelfde server te draaien met behulp van virtuele domeinen.

Plaats elke website in een aparte map in de standaard webroot /var/www/ bijvoorbeeld:

- /var/www/example.com/
- /var/www/voorbeeld.nl/
    sudo mkdir /var/www/example.com
    sudo mkdir /var/www/voorbeeld.nl

Voor elke site maken we een virtueel domein aan, wat in feite een tekstbestand is met domeinspecifieke informatie:

- /etc/nginx/sites-available/example.com
    server {
    listen 80;
    server_name example.com www.example.com;
    root /var/www/example.com;

    access_log /var/log/nginx/example.com.access_log;
    error_log /var/log/nginx/example.com.error_log info;

    location / {
      index index.php index.html index.htm;
      }
    }

- /etc/nginx/sites-available/voorbeeld.nl
    server {
    listen 80;
    server_name voorbeeld.nl www.voorbeeld.nl;
    root /var/www/voorbeeld.nl;

    access_log /var/log/nginx/voorbeeld.nl.access_log;
    error_log /var/log/nginx/voorbeeld.nl.error_log info;

    location / {
      index index.php index.html index.htm;
      }
    }

We moeten elke site inschakelen door een link te maken van /etc/nginx/sites-enabled/ naar het virtuele domein in "sites-available". We maken een symbolische link voor elk virtueel domein:

    sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/example.com
    sudo ln -s /etc/nginx/sites-available/voorbeeld.nl /etc/nginx/sites-enabled/voorbeeld.nl

Om deze configuratie van virtuele domeinen effectief te maken, doen we

    sudo nginx reload

en als alles correct is geconfigureerd zal het reageren:

    Reloading nginx configuration: nginx.

## Database

We kunnen MariaDB of MySQL installeren; Joomla werkt met beide. Laten we
MariaDB installeren met:

    sudo apt-get install mariadb-server

Tijdens de installatie moet je een wachtwoord toevoegen voor de **root**-gebruiker.
Laten we een **databasewachtwoord** aanmaken, bijvoorbeeld
**correcthorsebatterystaple**.

Laten we ten slotte de beveiliging van onze MariaDB-installatie verbeteren door rootaccounts te verwijderen die toegankelijk zijn vanaf buiten de lokale host, anonieme gebruikersaccounts en de testdatabase. We kunnen dat doen met

    mysql_secure_installation

## PHP

Voor PHP gaan we **php-fpm** (FastCGI Process Manager) installeren, die als een daemon draait en Fast/CGI-verzoeken ontvangt. Verder zullen we **php5-mysql** installeren, wat een module is voor MySQL-databaseverbindingen direct vanuit PHP-scripts.

De meer recente php7 moet worden geïnstalleerd met

```bash
sudo apt-get install php-fpm php-mysql
```

Nu moeten we Nginx laten weten dat het php-fpm moet gebruiken voor .php-bestanden. We voegen een paar regels toe aan onze virtuele domeinen:

```bash
sudo nano /etc/nginx/sites-available/example.com
```

voeg toe:

```nginx
location ~ \.php$ {
    fastcgi_pass unix:/var/run/php/php7.0-fpm.sock;
    fastcgi_index index.php;
    include fastcgi_params;
}
```

Test dit door het volgende PHP-bestand te maken:

```bash
sudo nano /var/www/example.com/test.php
```

We gebruiken een browser om te testen of we de PHP-configuratiepagina zien op [http://192.168.0.35/example.com/test.php](http://192.168.0.35/example.com/test.php)

## Joomla!

- te doen
```
    sudo wget https://github.com/joomla/joomla-cms/releases/download/3.6.3/Joomla_3.6.3-Stable-Full_Package.zip
    sudo unzip -x Joomla_3.6.3-Stable-Full_Package.zip
```

## Raspberry Pi verbinden met internet

We willen dat mensen op het internet onze Joomla-website op onze Raspberry Pi kunnen bezoeken. Om dat te doen, moeten we **onze internetrouter configureren** om alle **inkomende verkeer** op poort 80 **naar onze Raspberry Pi** door te sturen.

Gebruik je webbrowser om verbinding te maken met de webinterface van je router. Een router bevindt zich meestal op het eerste nummer van je IP-bereik, in ons geval op 192.168.0.1. In onze router configureren we **Port Forwarding**:

- Extern IP-adres: 0.0.0.0
- Externe Startpoort: 80
- Externe Eindpoort: 80
- Intern IP-adres: 192.168.0.35 ( = onze Raspberry Pi)
- Interne Startpoort: 80
- Interne Eindpoort: 80
- Protocol: TCP

Zorg ervoor dat het ingeschakeld is.

Als alles correct werkt, zou je je eigen Joomla-website op de Raspberry Pi moeten zien door je externe IP-adres te bezoeken (Vind je externe IP-adres met een tool zoals <a href="http://www.whatsmyip.org/" rel="nofollow noreferrer noopener">whatsmyip.org</a>).

### Een domeinnaam gebruiken

Laten we aannemen dat ons externe IP-adres 42.42.42.42 is. Laten we ook aannemen dat we een domeinnaam hebben geregistreerd genaamd example.com. We willen onze Joomla-site op onze Raspberry Pi aanbieden aan bezoekers die example.com bezoeken. Als je domeinnaamregistrar ons de mogelijkheid geeft om de **Domain Name System (DNS)**-server te configureren, moeten we een **MX-record** in de DNS aanmaken dat onze **domeinnaam aanwijst naar** ons **IP-adres** 42.42.42.42. Let op dat het tot 24 uur kan duren voordat alle internetproviders het verkeer van hun klanten naar het geconfigureerde MX-record omleiden.

### Statisch IP-adres

De meeste routers zullen hetzelfde interne IP-adres blijven toewijzen aan je Raspberry Pi. Soms is het beter om je Raspberry Pi te configureren om een statisch IP-adres te gebruiken:

    sudo nano /etc/network/interfaces

verander

    iface eth0 inet static

naar

    iface eth0 inet static
    address 192.168.0.35
    netmask 255.255.255.0
    gateway 192.168.0.1

De gateway is het IP-adres van je router. Je kunt het ook vinden met

    route

# Externe links

- <a href="https://raspberrypi.org" rel="nofollow noreferrer noopener">Raspberry Pi Foundation</a> (RPF) - officiële website en forums
- <a href="http://elinux.org/RaspberryPiBoard" rel="nofollow noreferrer noopener">Raspberry Pi Wiki</a>, ondersteund door de RPF
- Video van presentatie <a href="https://youtu.be/u2MFQCoexD0" rel="nofollow noreferrer noopener">Joomla op Raspberry Pi (met Nginx)</a> op Joomladay Duitsland 2013 in Neurenberg, Duitsland

*Vertaald door openai.com*

