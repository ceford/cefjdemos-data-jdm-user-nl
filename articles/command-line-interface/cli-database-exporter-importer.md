<!-- Filename: J4.x:CLI_Database_Exporter_Importer / Display title: CLI Databank Exporteren Importeren  -->

## Introductie

Voordat je Joomla! bijwerkt of een extensie van derden installeert, is het sterk aanbevolen om een backup van je site te maken. De Joomla! Commandoregelinterface (CLI) biedt commando's voor het exporteren (backuppen) en importeren (herstellen) van je Joomla! database. Let op: het maakt geen backup van je bestandssysteem; dit moet apart worden gedaan.

## Vereisten

Om deze commando's te gebruiken, heb je toegang tot een terminal nodig op de host waarop de site is geïnstalleerd. Dit kan een probleem zijn bij gedeelde hosting! Je hebt ook basiskennis nodig van Linux shell-commando's zoals ls en cd. Als dit allemaal onbekend is, kun je waarschijnlijk het beste Akeeba Backup gebruiken, de meest populaire back-up- en herstel-extensie, gratis voor basisgebruik.

## Backup Tijdelijke Opslaglocatie

Wees voorzichtig bij het kiezen van een opslaglocatie voor een back-up. Deze zou binnen je persoonlijke bestandsruimte moeten zijn, maar buiten je webstructuur. Het doel is om een back-upbestand te maken dat je kunt downloaden naar je lokale computer of een andere veilige locatie, waarna je het back-upbestand kunt verwijderen om ruimte te besparen. Zorg er ook voor dat je niet de systeem-/tmp-map gebruikt, die door elke gebruiker leesbaar kan zijn. De beste locatie is je persoonlijke tmp-map. De structuur van de mappen is als volgt:
```
|-/home/gebruikersnaam/tmp - jouw persoonlijke tmp-map
|-/home/gebruikersnaam/public_html - jouw Joomla root map
```

## Instructies

Log in op je host en ga naar de root map van je site.
```
cd /home/gebruikersnaam/public_html
```

- Lijst alle beschikbare CLI-opdrachten op:
```sh
  php cli/joomla.php list
```
- Exporteer de database naar de tijdelijke map van het account:
```sh
  php cli/joomla.php database:export --folder /home/gebruikersnaam/tmp/mijndbnaam
```
- Importeer de database vanuit de map:
```sh
php cli/joomla.php database:import --folder /home/gebruikersnaam/tmp/mijndbnaam
```

Je kunt ook:

- De database als een .zip-bestand exporteren:
```sh
php cli/joomla.php database:export --zip --folder /home/gebruikersnaam/tmp/mijndbnaam
```
- Een tabel exporteren:
```sh
php cli/joomla.php database:export --table xxxxx_action_log_config --folder /home/gebruikersnaam/tmp/mijndbnaam
```
- Een tabel als een .zip-bestand exporteren:
```sh
php cli/joomla.php database:export --table xxxxx_action_log_config --zip --folder /home/gebruikersnaam/tmp/mijndbnaam
```
- Een tabel importeren:
```sh
php cli/joomla.php database:import --table xxxxx_action_log_config --folder /home/gebruikersnaam/tmp/mijndbnaam
```
- Als je hulp nodig hebt:
```sh
php cli/joomla.php database:export --help
php cli/joomla.php database:import --help
```

## Backup

Om een volledige back-up van mappen, bestanden en de database te maken, voer deze commando's uit:

1. Archiveer je Joomla-rootdirectory:
```sh
tar --exclude='/home/gebruikersnaam/public_html/tmp' -zcvf /home/gebruikersnaam/tmp/joomla_bak.tgz /home/gebruikersnaam/public_html > /home/gebruikersnaam/tmp/joomla_bak.log
```
2. Exporteer de volledige Joomla-database vanuit de Joomla-rootmap:
```sh
php cli/joomla.php database:export --folder /home/gebruikersnaam/tmp/db_bak
```

## Herstellen

Om het te herstellen, zorg er eerst voor dat de database en de databasegebruiker bestaan. Voer vervolgens deze commando's uit:

1. Pak het archief uit:
```sh
tar -xvf /home/username/tmp/joomla_bak.tgz --directory /home/username/public_html
```
2. Zorg ervoor dat je je in de hoofdmap van je site bevindt:
```sh
cd /home/username/public_html
```
2. Importeer de Joomla-database:
```sh
php cli/joomla.php database:import --folder /home/username/tmp/db_bak
```

## Notities

In de tar-commando-opties -zcvf en -xvf staat de v voor verbose - een lijst van verwerkte bestanden scrolt snel langs het terminalscherm. Laat de v weg om de lijst niet te zien.

*Vertaald door openai.com*  

