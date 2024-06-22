<!-- Filename: Copying_a_Joomla_website / Display title: Het kopiëren van een Joomla website -->

<span id="main-portal-heading">Handleiding  
Een Joomla! website kopiëren</span>

  
Het kopiëren van een Joomla! website bestaat uit twee delen: u moet de
bestanden kopiëren en u moet de database kopiëren (waar de content
opgeslagen is). Het kopiëren van de bestanden en van de database zijn
twee verschillende acties, welke als eerste uitgevoerd wordt maakt niet
zoveel uit. Als uw website regelmatig wordt geupdate en u moet de
website offline zetten terwijl u de website kopieert dan wilt u
waarschijnlijk de database kopie als laatste uitvoeren aangezien dit de
downtime minimaliseert.

## Kopiëren van een website (algemene wijze)

#### Akeeba

- Akeeba Backup produceert een `.jpa`-bestand
- Het `.jpa`-bestand bevat alle mappen/bestanden en de
  database-bestanden.
- het `.jpa`-bestand bevat ook ook een installatiebestand.
- `kickstart.php` (van Akeeba) pakt het `.jpa`-bestand uit
- U moet dan het installatieprogramma uitvoeren en installeer uw Joomla!
  website als een gewone Joomla! installatie
- Het installatieprogramma wijzigt de configuratie om het herstellen op
  een nieuwe locatie en vraagt om de nieuwe databasegegevens.

Nadat de database gecreëerd is voor je Joomla! installatie kan je Akeeba
installeren, het kan van <a
href="https://extensions.joomla.org/extensions/extension/access-a-security/site-security/akeeba-backup/"
class="external text" target="_blank" rel="noreferrer noopener">de
Joomla extension directory</a> gedownload worden. Er is een link met de
volledige instructies beschikbaar.

### Het kopiëren van de bestanden via FTP

Eén methode van het kopiëren van bestanden van een Joomla! installatie
naar een andere kan door het gebruiken via een FTP programma. U download
eerst de bestanden van de originele webserver en upload deze naar de
locatie van de nieuwe webserver. Afhankelijk waar de kopie geplaatst
wordt, de nieuwe locatie kan een andere map zijn op zelfde server, of
het kan een nieuwe locatie zijn op een totaal nieuwe server. Er wordt,
bij het kopiëren van een Joomla installatie op dezelfde server
(bijvoorbeeld voor testdoeleinden), geadviseerd een subdomein te
gebruiken in plaats van een submap. Dit voorkomt fouten en mogelijke
problemen bij het samen draaien van installaties.

Het is belangrijk om de zelfde mappenstructuur aan te houden voor alle
mappen en bestanden als deze van de eerste locatie naar de volgende
worden gebracht. Gelukkig kunnen de FTP programma's dit automatisch
afhandelen terwijl u een serie bestanden en mappen down- en upload. (Uw
FTP-programma bevat hulpdocumentatie over FTP en hoe u dit programma kan
gebruiken). Let op: wanneer u bestanden van de eerste locatie naar de
tweede hebt verplaatst moet u mogelijk het configuratiebestand nog
aanpassen om Joomla! op de nieuwe locatie werkend te krijgen.

In zeldzame gevallen kan er een bestand corrupt raken wanneer slechts
een deel van het bestand succesvol via FTP verzonden is. Wanneer u
vreemde of onverwachte fouten tegenkomt met de nieuwe Joomla!, na het
kopiëren, kunt u proberen om de bestanden opnieuw te uploaden om dit te
verhelpen.

#### Download bestanden van de server naar uw computer

1.  Gebruik een FTP programma (zoals b.v. FileZilla) om verbinding met
    de server te maken
2.  Selecteer de map die u wilt downloaden (meestal `/public_html/` of
    `/htdocs/`).
3.  Klik rechts + selecteer de bestanden/mappen om te downloaden + of
    sleep de folder van de externe server en laat deze los op de lokale
    site.
4.  Het downloaden van de externe bestanden zal starten
5.  Nadat u de bestanden hebt gedownload, controleer dan de "Mislukte
    overdracht" om te kijken of er fouten zijn opgetreden.

#### Upload bestanden van uw computer naar een server

1.  Zorg ervoor dat de configuration.php de juiste instellingen bevat
    voor de server (in bijzonder: "localhost", "database", "database
    user", "database wachtwoord", "log_path", "tmp_path").
2.  Gebruik een FTP programma (zoals FileZilla) om een verbinding met de
    server te maken.
3.  Selecteer de map waarin u wilt uploaden (meestal naar `/public_html`
    of `htdocs`)
4.  Klik rechts + selecteer de bestanden/mappen die geupload moeten
    worden, of sleep de map van de "local site" naar de externe server
    en laat deze daar los.
5.  Het uploaden van de lokale bestanden naar de externe server zal gaan
    starten.
6.  Nadat u de bestanden hebt geupload, controleer dan de "Mislukte
    overdracht" om te kijken of er fouten zijn opgetreden.

### Het kopiëren van de database met phpMyAdmin

De phpMyAdmin tool kan worden gebruikt voor het exporteren en importeren
van een database, een eenvoudige manier om een kopie van een database
met een andere naam te maken op een server.

#### Het exporteren van een kopie van een database naar uw computer

1.  Meldt u zich aan in de database die u wilt dupliceren met behulp van
    phpMyAdmin.
2.  Klik, aan linkerzijde van de pagina, op de naam van de database
3.  Selecteer de Exporteer tabblad.
4.  Selecteer de " Opslaan als bestand" optie.
5.  Klik op "Gaan"

Vervolgens zal u worden gevraagd waar het databasebestand op uw computer
opgeslagen moet worden.

#### Het importeren van de kopie in een nieuwe database

U dient eerst een nieuwe, lege database op uw server aan te maken met
behulp van het controlepaneel. Het moet als UTF8 (utf8_general_ci)
ingedeeld zijn. Nadat de nieuwe database is aangemaakt:

1.  Log in op de nieuwe database met behulp van phpMyAdmin
2.  Klik, op linkerzijde van de pagina, op de naam van de database.
3.  Selecteer de "Importeer" tabblad.
4.  Klik op de "Bladeren" knop onder "Bestand importeren" en selecteer
    het databasebestand op uw computer.
5.  Klik "Gaan" om de database te importeren.

"'Tip:"' Als je een "Geen database geselecteerd' foutmelding krijgt komt
dit waarschijnlijk omdat je vergeten bent om op de databasenaam te
klikken in de kolom aan de linkerkant.

### Wijzigen van configuration.php

Om Joomla op de nieuwe server aan het werk te krijgen moet er een aantal
noodzakelijke aanpassingen gemaakt worden in het configuration.php
bestand naar de parameters van de nieuwe serveromgeving. U moet de
volgende parameters controleren/wijzigen:

       var $host = 'localhost'; // usually "localhost". If it's different for your server then your hosting provider should be able to tell you that.
        var $user = 'the_db_username';
        var $db = 'the_databasename';
        var $password = 'the_db_password';
            var $live_site = ''; // is usually empty.
            var $cookie_domain = ''; // Should be empty.

Joomla zal werken, zelfs als `$log_path` en `$tmp_path` niet correct
zijn, hoewel er dan geen nieuwe extensies geïnstalleerd kunnen worden.
Login in de backend van uw Joomla website.

Ga naar: Systeem **→** Systeeminformatie **→** Maprechten  
Kijk naar de onderste 4 rijen:

    cache (Cache Directory) Writable
    administrator/cache (Cache Directory)  Writable
    /var/www/some/other/folder/example.com/logs/ (Log directory) Unwritable
    /var/www/some/other/folder/example.com/tmp (Temp directory)  Unwritable

Als de `$log_path` en `$tmp_path` op "Niet schrijfbaar" staan moet u
deze waarden in de `configuration.php` wijzigen.

Gebruik de waarden van de "Cache map" zonder het "/cache/" deel en
wijzig `$log_path` en `$tmp_path` naar:

       var $log_path = '/var/www/example.com/logs';
       var $tmp_path = '/var/www/example.com/tmp';

Als de Maprechten laat zien dat `$log_path` en `$tmp_path` Schrijfbaar"
zijn dan moet u extensies kunnen installeren.

## Het kopiëren van een website met behulp van SSH command line (methode voor geavanceerde gebruikers)

### Het kopiëren van bestanden met behulp van een gecomprimeerd bestand

Het kopiëren van een groot aantal afzonderlijke bestanden via FTP kan
soms onbetrouwbaar zijn. Als u command-line toegang heeft tot de bron-
en bestemminglocaties dan kunt u een gecomprimeerd bestand met daarin
alle bestanden van de bronlocatie aanmaken, dan kunt u dat ene bestand
naar de bestemminglocatie verplaatsen, waar het kan worden
gedecomprimeerd.

#### Het aanmaken van een archiefbestand

Op Unix-systemen (bijv. Linux) kunt u gebruik maken van het "gzip"'
programma om .zip bestanden te maken, of het "tar"' programma voor
.tar.gz of .tar.bz2 bestanden. Voor gedetailleerde instructies type
**man gzip' *of*** *man tar* op de command line. Bijvoorbeeld,

    tar cvfz joomlabackup.tar.gz /path-to-joomla

maakt een gzip gecomprimeerd bestand aan, met de naam
"joomlabackup.tar.gz", die alle bestanden van uw Joomla! installatie
bevat.

"'Belangrijke opmerking!"' U moet ervoor zorgen dat u NIET in de map
staat waarvan u probeert een backup te maken wanneer u het tar commando
gebruikt anders maakt u een eindeloze lus.

#### Het uitpakken van een archiefbestand

Nadat het archiefbestand is gekopieerd naar het nieuwe systeem kan deze
worden uitgepakt. Gebruik hiervoor het equivalente commando die gebruikt
is om het archiefpakket samen te stellen. Bijvoorbeeld, om het
archiefbestand uit te pakken zoals gemaakt in het bovenstaande voorbeeld
voer dan in

    cd /path-to-joomla
    tar xvfz joomlabackup.tar.gz

Als de gebruiker of de groep ID's niet identiek zijn tussen de bron- en
bestemming-systemen moet de eigenaar van de bestanden gewijzigd worden
die zojuist zijn uitgepakt. Bijvoorbeeld, onder Apache moet het volgende
commando worden uitgevoerd:

    cd /path-to-joomla
    chown -R www-user:www-group *

zodat Apache de eigenaar is van de Joomla! bestanden.

"Vraag aan uw hosting voor de juiste groep- en gebruikersnamen,
`www-group` en `www-user` op uw systeem."

### Het kopiëren met MySQL database command line methode

Meestal voert u `mysqldump` uit om een kopie van de database te maken:

    $ mysqldump -u user -p db-name > db-name.out

Kopieer het `db-name.out` bestand met behulp van sftp/ssh naar de
mySQL-server:

    $ scp db-name.out user@remote.box.com:/backup

Herstel de database de externe server (login via ssh):

    $ mysql -u user -p db-name < db-name.out
