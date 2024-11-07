<!-- Filename: J4.x:Using_the_CLI / Display title: De CLI gebruiken -->

## De Command Line Interface (CLI)

Als je terminaltoegang hebt tot de server waarop je website draait, kun je
de Joomla CLI gebruiken om routinetaken uit te voeren zonder dat je
Joomla-gebruikersinloggegevens nodig hebt. Zelfs zonder terminaltoegang, zoals op
sommige gedeelde hostingaccounts, kun je CLI-opdrachten uitvoeren met cron-jobs.
CLI-opdrachten zijn vaak sneller of handiger dan de equivalenten
uitgevoerd via de Joomla (of cPanel) Beheerdersinterface.
Het maken van een back-up van de site en het instellen van de site naar offline/online zijn voorbeelden waarbij je
de voorkeur zou kunnen geven aan het gebruik van de CLI.

De Joomla-kern heeft ongeveer 30 nuttige opdrachten en je kunt er meer toevoegen met
aanvullende extensies. Je zou bijvoorbeeld externe gegevens kunnen ophalen zoals
geolocatie- of wisselkoersgegevens voor een aangepast component.  

## Gebruik maken van de CLI

De CLI wordt gebruikt door het aanroepen van de command line php uitvoerbare. Deze is vaak anders dan die welke door een webserver zoals Apache wordt gebruikt. Als je een cron job gebruikt, moet je mogelijk het volledige pad naar de php uitvoerbare opgeven, zoals dit:

    /usr/local/bin/php /home/gebruikersnaam/public_html/[optionele submap]/cli/joomla.php

Anders, wanneer je de terminal command line gebruikt, verander je naar de Joomla cli-directory en begin je met het uitvoeren van het commando zonder parameters:

    cd /home/gebruikersnaam/public_html/[optionele submap]/cli
    php joomla.php

![Lijst van commando's](../../../en/images/command-line-interface/cli-command-list.png)

En probeer enkele help-commando's uit om vertrouwd te raken met wat je kunt verwachten:

    php joomla.php help
    php joomla.php list
    php joomla.php help cache:clean
    php joomla.php help config:get

Elk van de Help-beschrijvingen en gebruiksstrings zijn hard gecodeerd in Console-bibliotheekbestanden of in plugins van derden.

Probeer enkele eenvoudige actiecommando's:

    php joomla.php config:get debug
    php joomla.php cache:clean
    php joomla.php site:down
    php joomla.php site:up

## Opties

Als je commando's vanuit een cron aanroept, wil je misschien geen output zien:

    php joomla.php -q cache:clean

Merk op dat opties een spatie of = teken kunnen gebruiken, maar variabelen moeten een = teken gebruiken:

    php joomla.php session:gc --application administrator
    php joomla.php session:gc --application=administrator

    php joomla.php config:set debug=true

## Commando's

Een korte uitleg van elk kerncommando.

### Cache

Verwijder verlopen items uit de systeemcache:

```bash
php joomla.php cache:clean --help
php joomla.php cache:clean
```

![Uitvoer van cache clean](../../../en/images/command-line-interface/cli-cache-clean.png)

```bash
php joomla.php cache:clean expired
```

![Uitvoer van cache clean expired](../../../en/images/command-line-interface/cli-cache-clean-expired.png)

### Config

Haalt of stelt een configuratievariabele in, een van de variabelen in
configuration.php of een groep van variabelen. Geldige groepen zijn db, sessie,
mail,

```bash
php joomla.php config:get debug --help
php joomla.php config:get debug
```

![Uitvoer van config get debug](../../../en/images/command-line-interface/cli-get-debug.png)

```bash
php joomla.php config:set debug=true
```

![Uitvoer van config set debug](../../../en/images/command-line-interface/cli-set-debug.png)

```bash
php joomla.php config:get --group session
```

![Uitvoer van config get group session](../../../en/images/command-line-interface/cli-config-get-group-session.png)

### Core

Controleer op updates of update Joomla.

```bash
php joomla.php core:check-updates --help
php joomla.php core:check-updates
```

![Uitvoer van core check updates](../../../en/images/command-line-interface/cli-check-updates.png)

```bash
php joomla.php core:update --help
php joomla.php core:update
```

![Uitvoer van core update](../../../en/images/command-line-interface/cli-core-update.png)

### Database

Exporteer of importeer de database. Je kunt alle tabellen exporteren of importeren of een geselecteerde tabel. Gebruik deze functie niet om alle tabellen van een meertalige site te importeren. Er is een probleem dat ervoor kan zorgen dat Slim Zoeken volledig stopt met werken.

```bash
php joomla.php database:export --help
php joomla.php database:export --table f4rc2_banners --folder /home/gebruikersnaam/tmp/mydb (één tabel)
php joomla.php database:export --folder /home/gebruikersnaam/tmp/mydb (alle tabellen)
```

```bash
php joomla.php database:import --help
php joomla.php database:import --table /home/gebruikersnaam/tmp/mydb/f4rc2_banners (één tabel)
[ERROR] Het bestand /home/gebruikersnaam/tmp/mydb/f4rc2_banners.xml bestaat niet.
php joomla.php database:import --folder /home/gebruikersnaam/tmp/mydb (alle tabellen in deze map)
```

### Extension

Lijst, Ontdek, Installeer of Verwijder extensies.

```bash
php joomla.php extension:list --help
php joomla.php extension:list
php joomla.php extension:list --type component
php joomla.php extension:list --type file
php joomla.php extension:list --type language
php joomla.php extension:list --type library
php joomla.php extension:list --type module
php joomla.php extension:list --type package
php joomla.php extension:list --type plugin
php joomla.php extension:list --type template
```

```bash
php joomla.php extension:discover --help
php joomla.php extension:discover
php joomla.php extension:discover:list
php joomla.php extension:discover:install --eid=
```

```bash
php joomla.php extension:install --help
php joomla.php extension:install --path=
php joomla.php extension:install --url=
```

```bash
php joomla.php extension:remove --help
php joomla.php extension:remove
```

### Finder

Leegt en herbouwt de index (zoekfilters blijven behouden).

```bash
php joomla.php finder:index --help
php joomla.php finder:index
php joomla.php finder:index purge
```

![Uitvoer van finder index purge](../../../en/images/command-line-interface/cli-finder-index-purge.png)

### Scheduler

Lijst, wijzig de status of voer geplande taken uit.

```bash
php joomla.php scheduler:list --help
php joomla.php scheduler:list
```

```bash
php joomla.php scheduler:state --help
php joomla.php scheduler:state (interactieve prompt voor taak-ID)
```

```bash
php joomla.php scheduler:run --help
php joomla.php scheduler:run --id ID
php joomla.php scheduler:run --all
```

### Session

Voer sessieafvalverzameling uit.

```bash
php joomla.php session:gc --help
php joomla.php session:gc
php joomla.php session:gc --application administrator
```

```bash
php joomla.php session:metadata:gc --help
php joomla.php session:metadata:gc
```

### Site

Zet de site offline of online.

```bash
php joomla.php site:down --help
php joomla.php site:down
```

```bash
php joomla.php site:up --help
php joomla.php site:up
```

### Update

Controleert op hangende uitbreidingsupdates. Verwijdert oude bestanden die tijdens een Joomla-update verwijderd hadden moeten worden

```bash
php joomla.php update:extensions:check --help
php joomla.php update:extensions:check
```

```bash
php joomla.php update:joomla:remove-old-files --help
php joomla.php update:joomla:remove-old-files
```

![Uitvoer van update Joomla verwijder oude bestanden](../../../en/images/command-line-interface/cli-update-remove-old-files.png)

### User

Beheer en beheer gebruikers.

```bash
php joomla.php user:list --help
php joomla.php user:list
```

```bash
php joomla.php user:add --help
php joomla.php user:add --username assepoester --name Assepoester --email assepoester@localhost --usergroup Manager (prompt voor wachtwoord)
php joomla.php user:add (prompts voor gegevens)
```

![Uitvoer van user add met prompts](../../../en/images/command-line-interface/cli-add-user.png)

```bash
php joomla.php user:addtogroup --help
php joomla.php user:addtogroup (prompts voor gegevens)
php joomla.php user:addtogroup --username=assepoester --group=Manager
```

```bash
php joomla.php user:removefromgroup --help
php joomla.php user:removefromgroup (prompts voor gegevens)
php joomla.php user:removefromgroup --username=assepoester --group=Manager
```

```bash
php joomla.php user:reset-password --help
php joomla.php user:reset-password (prompts voor gegevens)
php joomla.php user:reset-password --username=assepoester (prompts voor wachtwoord)
```

```bash
php joomla.php user:delete --help
php joomla.php user:delete (prompts voor gebruikersnaam)
php joomla.php user:delete --username=assepoester (vragen om bevestiging - y om te bevestigen)
```

*Vertaald door openai.com*

