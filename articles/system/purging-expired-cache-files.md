<!-- Filename: Purging_expired_cache_files / Display title: Verwijder Verlopen Cache  -->

## Cachebestanden

Cachebestanden zijn tijdelijke bestanden die worden aangemaakt om de prestaties van je site te verbeteren. Je moet ervoor zorgen dat cachebestanden die verlopen zijn, en dus niet langer nodig zijn, uit het systeem worden verwijderd. Anders loop je uiteindelijk het risico dat de schijfruimte opraakt.

Verlopen cachebestanden kunnen worden verwijderd via de Beheerinterface of de Command Line Interface (CLI).

## Purge - Beheerdersmethode

Vanuit het *Startdashboard*
* Selecteer de optie **Cache** in het *Systeem* paneel.
* Op de pagina *Onderhoud: Cache wissen* selecteer de knop **Verlopen cache wissen** in de werkbalk.

## Purge - Opdrachtregel Methode

Open een terminalvenster en navigeer naar de cli-directory in de root van je site.
Als je niet weet welke CLI-opdrachten beschikbaar zijn, voer dan de volgende opdracht uit:
```bash
php joomla.php
```
Je zult een lijst met beschikbare opdrachten zien. De `cache` opdracht is:
```bash
php joomla.php cache:clean
```
Er zou een groene bevestigingsboodschap of misschien een kastanjebruine foutmelding moeten zijn.

## Automatisch Verlopen Cachebestanden Opruimen

Je kunt automatisch verlopen cachebestanden opruimen met behulp van een cron-job. Hostingdiensten maken dit eenvoudig door een formulier aan te bieden waarmee je kunt selecteren hoe vaak een taak wordt uitgevoerd en welk commando je wilt gebruiken. Zo kun je ervoor kiezen om de cron elke dag om 05:00 uur uit te voeren met het volgende commando:
```
 /usr/local/bin/ea-php82 /home/gebruikersnaam/public_html/cli/joomla.php cache:clean
 ```
De meeste *cron*-jobmanagers staan je toe om een e-mailadres in te voeren waarnaar de uitvoer van de cron wordt verzonden. Als je geen bericht wilt ontvangen, voeg dan ` > /dev/null 2>&1` toe aan het commando.

De PHP-versie die op de commandoregel wordt gebruikt, is vaak anders dan die voor de levering van een website. Het kan incompatibel zijn met Joomla. Gebruik daarom het volledige pad naar de PHP-versie die je wilt gebruiken in plaats van alleen `php`.

*Vertaald door openai.com*

