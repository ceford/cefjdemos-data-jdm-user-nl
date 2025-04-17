<!-- Filename: No_original_yet / Display title: Lokale Hosting op Linux -->

## Inleiding

Dit artikel gaat over het hosten van Joomla op een persoonlijke Linux-gebaseerde computer voor test- en ontwikkelingsdoeleinden. De besproken Linux-versies komen uit de Debian-Ubuntu familie, en specifiek Linux Mint. Andere distributies zijn vergelijkbaar maar hebben verschillende commando-syntaxis en bestandslocaties.

Je moet een reeks softwarepakketten installeren die vaak worden aangeduid als de LAMP-stack. De letters staan voor Linux, Apache, MySQL en PHP. Je kunt software installeren met behulp van de Grafische Gebruikersinterface (GUI) of de opdrachtregel in een terminalvenster. Dit zijn verschillende manieren om de Synaptic Package Manager te gebruiken.

## Installeer Apache met de GUI

Vanuit het systeemmenu, gemarkeerd met het LM-logo, selecteer je Beheer / Synaptic Pakketbeheerder. Je wordt gevraagd om je wachtwoord. Voer je loginwachtwoord in om de GUI te openen. Rechtsboven is er een `Zoeken` knop. Selecteer deze en voer **apache** in en selecteer `Zoeken`. Vink het `apache2` selectievakje aan en selecteer in het pop-uplabel `Markeren voor installatie`. Er verschijnt nog een pop-upvenster met een lijst van aanvullende pakketten die nodig zijn om apache te ondersteunen. Selecteer `Markeren`:

![synaptic package manager](../../../en/images/hosting/synaptic-package-manager-gui.png)

Selecteer de `Toepassen` knop in de bovenste werkbalk en de `Toepassen` knop in het Samenvattingsdialoogvenster. Apache zal worden geïnstalleerd en geconfigureerd, het proces eindigt met een **Aangesproken wijzigingen dialoogvenster**. Selecteer `Sluiten`.

Je kunt bevestigen dat Apache is geïnstalleerd en werkt door je browser te openen, standaard Firefox in een nieuwe Linux Mint install, en **localhost** in te voeren in de URL-balk. Je zou de Ubuntu Apache2 Standaardpagina moeten zien:

![apache standaardpagina](../../../en/images/hosting/apache-default-page.png)

De pagina bevat enkele nuttige informatie over bestandslocaties die later misschien niet zo gemakkelijk beschikbaar zijn, dus je wilt deze pagina misschien afdrukken op papier of naar een pdf-bestand.


## Installeer PHP met de CLI

Het is waarschijnlijk het beste om PHP via de opdrachtregel te installeren. Een reden hiervoor is dat, op het moment van schrijven, de Synaptic Package Manager alleen PHP8.1 aanbiedt, hoewel PHP8.2 al enige tijd beschikbaar is en vanuit een externe repository kan worden geïnstalleerd. Er is een goede beschrijving van de procedure in deze tutorial met Quickstart en Gedetailleerde secties.

Sluit eerst je Synaptic Package Manager GUI en open vervolgens een Terminal-venster en voer de volgende opdrachten één voor één in:

```bash
sudo add-apt-repository ppa:ondrej/php
sudo apt update
sudo apt install php8.2 php8.2-cli php8.2-{bz2,curl,mbstring,intl}
sudo apt install php8.2-fpm
sudo a2enconf php8.2-fpm
sudo systemctl reload apache2
```
Controleer in je browser dat de standaardpagina van localhost nog steeds werkt.

## Installeer MySQL of MariaDB

Je kunt op internet zoeken naar informatie over elk van deze databankpakketten. MySQL is de traditionele keuze, maar werd overgenomen door Oracle en is nu minder populair. MariaDB is een Open Source vervanging met extra functies. Beide werken met Joomla! 5, maar het is niet eenvoudig om van de ene naar de andere over te schakelen. Tabellen moeten geëxporteerd en geïmporteerd worden. Joomla! 5 vereist specifieke minimumversies die Linux Mint aanbiedt via de Synaptic Package Manager.

Open de Synaptic Package Manager GUI en zoek naar mysql-server of mariadb-server. Vink het selectievakje aan voor het item dat eindigt op -server. Selecteer `Markeren voor installatie` en daarna `Toepassen` in de bovenste werkbalk. Je kunt het detailpaneel openen om te zien wat er tijdens de installatie gebeurt. Selecteer `Sluiten` als je klaar bent.

Je kunt testen of je database werkt door `mysql` in te voeren in de opdrachtregel. Dit is hetzelfde voor zowel MySQL als MariaDB. Je zou een foutmelding `Toegang geweigerd` moeten zien, wat goed is omdat het aangeeft dat je database-installatie daadwerkelijk werkt.

## Installeer phpMyAdmin

phpMyAdmin is een GUI-databasebeheertool die je nodig zult hebben om je databases te maken en te beheren. Zoek in de Synaptic Package Manager GUI naar **phpmyadmin**. Vink het selectievakje aan en kies `Markeren voor installatie`. Na het downloaden verschijnt er een prompt om de `Webserver automatisch te herconfigureren` te selecteren. Vink het selectievakje voor `apache2` aan en druk op de `Volgende` knop. Laat op het volgende configuratiescherm het selectievakje `Configureer database...` aangevinkt en selecteer `Volgende`.

Kies een applicatiewachtwoord voor de gebruiker phpmyadmin. Test: voer in je browser localhost/phpmyadmin in de URL-balk in. Je zou het phpMyAdmin-inlogscherm moeten zien. Met de gebruikersnaam phpmyadmin en het wachtwoord dat je tijdens de installatie hebt ingevoerd, kun je inloggen. Maar je zult geen databases kunnen maken! Om het probleem op te lossen, moet je het configuratiebestand als root in het Terminal-venster bewerken:

```bash
sudo nano /etc/phpmyadmin/config.inc.php
```
Vind de twee regels met // $cfg['Servers'][$i]['AllowNoPassword'] = TRUE; en verwijder de voorloop-schakels om ze van commentaar te ontdoen. Beide!

Log dan in op mysql vanaf de opdrachtregel en maak een nieuwe gebruiker aan en geef die gebruiker alle rechten:
```bash
sudo mysql
CREATE USER 'admin'@'localhost' IDENTIFIED BY '';
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'localhost' WITH GRANT OPTION;
exit
```
Ga dan terug naar phpMyAdmin en probeer in te loggen met gebruikersnaam **admin** en geen wachtwoord. Je zou alle databases moeten zien en nieuwe databases moeten kunnen maken.


## Index Bestand Prioriteit

De standaardlocatie voor webpagina's op Ubuntu/Linux Mint is /var/www/html. Als je de inhoud van die directory bekijkt, zul je zien dat deze index.html bevat met de inhoud van de Ubuntu Apache2 Standaardpagina. Maak een bestand met de naam index.php in die directory met de volgende inhoud:

```php
<?php echo phpinfo();
```
Herlaad localhost. Er is geen verandering! Voer **localhost/index.php** in de URL-balk in en je zult een pagina zien met PHP-versie-informatie. Dit gedrag wordt bepaald door de standaard Apache-configuratie, die kan worden gewijzigd door de Apache `dir`-module in te schakelen en de configuratie ervan aan te passen:

```bash
sudo a2enmod dir
sudo nano /etc/apache2/mods-enabled/dir.conf
```

Verplaats index.php naar de voorkant van de lijst. Herstart daarna Apache:

```bash
sudo systemctl restart apache2
```

Deze keer, als je alleen **localhost** in de URL-balk gebruikt, zou je de inhoud van het index.php-bestand moeten zien, een PHP Informatiepagin.

## Virtuele Hosts

In een standaard Linux-installatie bevinden de systeembestanden zich in de rootmap (/) en gebruikersbestanden in de homemap (/home/mijngebruikersnaam). Dit kan een probleem zijn omdat de standaard Apache-gebruiker, www-data, mogelijk niet de juiste machtigingen heeft om bestanden in de gebruikersbestandenruimte te maken. De beste oplossing is om Virtuele Hosts aan te maken.

Eerst is er een module nodig die Apache in staat stelt om zijn gebruiker en groep te wijzigen om aan elke gebruiker tegemoet te komen:

```bash
sudo apt-get install libapache2-mpm-itk
sudo a2enmod mpm_itk
```

Maak vervolgens een kopie van het standaard siteconfiguratiebestand en bewerk het:

```bash
cd /etc/apache2/sites-available
sudo cp 000-default.conf gebruikersnaam.localhost.conf
sudo nano gebruikersnaam.localhost.conf
```

Het standaard siteconfiguratiebestand bevat commentaar om de inhoud uit te leggen. In de onderstaande illustratie worden die weggelaten. Commentaar op de ServerName-regel is opgeheven en vervang alle gevallen van `gebruikersnaam` door je eigen gebruikersnaam.

```xml
<VirtualHost *:80>
        ServerName gebruikersnaam.localhost
        ServerAdmin webmaster@localhost
        DocumentRoot /home/gebruikersnaam/public_html
        <IfModule mpm_itk_module>
                AssignUserId gebruikersnaam gebruikersnaam
        </IfModule>
        <Directory /home/gebruikersnaam/public_html/ >
                Options Indexes FollowSymLinks
                AllowOverride None
                Require all granted
        </Directory>
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

Activeer de nieuwe site en herstart Apache:

```bash
sudo a2ensite gebruikersnaam.localhost
sudo systemctl reload apache
```

Maak een regel in het /etc/hosts bestand om een vermelding voor de nieuwe virtuele host toe te voegen. Anders zal je browser er op het internet naar zoeken.

```bash
sudo nano /etc/hosts
```
Wanneer het klaar is, ziet het er ongeveer zo uit:

```bash
127.0.0.1       localhost
127.0.0.1       gebruikersnaam.localhost
127.0.1.1       hostname

# De volgende regels zijn wenselijk voor IPv6-capabele hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```
**Hostnaam:** Dit is de naam die je aan je computer hebt gegeven tijdens de installatie van Linux. Je hebt het zo meteen nodig. Je kunt het wijzigen als je dat wilt - maar het is het beste om je daar eerst over in te lezen en het dan te doen.

Als alles goed is, zul je met een URL van de vorm gebruikersnaam.localhost een directorylijst van je public_html-map zien. Openbare weergave van mappenlijsten wordt gezien als een slechte gewoonte, een beveiligingsrisico, en meestal niet toegestaan door een andere Apache-configuratie-instelling. Voor een persoonlijke site op een persoonlijke computer die voor ontwikkeling en testen wordt gebruikt, is dit echter erg nuttig. Veel verschillende sites kunnen in verschillende submappen worden opgezet. Bijvoorbeeld Joomla 4- en Joomla 5-sites, Bulletin Boards, Wiki's enzovoort. Wanneer je veel testsites hebt, is het moeilijk om al de submapnamen te onthouden!

## Toegang tot Thuisnetwerk

Als je een andere computer op je thuisnetwerk hebt, wil je waarschijnlijk ook vanaf daar toegang krijgen tot je Linux-site. Om dat te laten werken, heb je een ander virtueel host nodig. Kopieer en bewerk de zojuist gemaakte:

```bash
cd /etc/apache2/sites-available
sudo cp username.localhost.conf username.conf
sudo nano username.conf
```
Verander de ServerName van username.localhost naar username.hostname en activeer vervolgens de nieuwe virtuele site en herstart Apache.

```bash
sudo a2ensite username
sudo apachectl restart
```
Ga naar je andere computer op het thuisnetwerk en bewerk het persoonlijke hosts-bestand. Bewerk bijvoorbeeld op een Mac /private/etc/hosts en voeg de volgende regel helemaal onderaan toe:

```bash
192.168.178.20 username.hostname www.username.hostname
```
Waar 192.168.178.20 het IP-adres is van je Linux-computer.

Nu zou je op je tweede computer toegang moeten hebben tot de webserver op je Linux-computer door username.hostname in de URL-balk van je browser in te voeren.


## Partitienotities

Software geïnstalleerd met behulp van de Synaptic Package Manager bevindt zich meestal in de Linux rootdirectory (/). Gebruikersdata bevindt zich in de homedirectory (/home). In een eenvoudige installatie staan deze directories op dezelfde fysieke schijfpartitie.

In een meer complexe installatie, mogelijk met de optie om verschillende besturingssystemen (Windows of Linux) of verschillende versies van hetzelfde besturingssysteem op te starten, bevinden de root en gebruikersdata zich vaak in aparte partities. Dit maakt toegang tot dezelfde gebruikersdata vanuit elk besturingssysteem mogelijk.

Er is echter een probleem: een Joomla-site in een /home/gebruikersnaam directory heeft databasegegevens nodig die meestal in de rootdirectory zijn, specifiek in /var/lib/mysql. Je kunt de MySQL/MariaDB-datadirectory verplaatsen naar een locatie die beschikbaar is voor beide besturingssystemen, hetzij in de /home partitie of in een aparte partitie. Deze tutorial beschrijft hoe je de MySQL Datadirectory kunt wijzigen in Ubuntu en Debian Linux. Dat moet voor elk besturingssysteem worden gedaan, maar wordt hier niet behandeld.

*Vertaald door openai.com*

