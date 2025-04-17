<!-- Filename: Debugging_a_translation / Display title: Het Debuggen van een Vertaling  -->

## Joomla Taalbestanden

Telkens wanneer tekst naar het scherm moet worden uitgevoerd, voegen Joomla-programmeurs een taalconstant in, zoals JYES of JNO. Tijdens het weergevingsproces worden taalbestanden geladen met vertalingen in de juiste taal. De taalbestanden eindigen allemaal op `.ini`. U kunt kijken in languages/en-GB/joomla.ini voor enkele basisvoorbeelden. Regels die beginnen met een puntkomma worden genegeerd. Ze kunnen worden gebruikt voor opmerkingen. De overige regels bestaan uit sleutel="waarde"-paren. Elke taal heeft dezelfde set sleutels, maar de waarden zijn de juiste vertalingen.

Elke Joomla-extensie heeft zijn eigen taalbestanden, dus er zijn er in totaal honderden. Soms zijn er problemen, zoals missende taalconstanten, verkeerd gespelde taalconstanten of syntaxisfouten in de vertaalstrings die een heel taalbestand ongeldig kunnen maken.

## Debug Taal

Joomla biedt enkele nuttige debugging mechanismen die het gemakkelijker kunnen maken om niet-vertaalde strings te lokaliseren en problemen met taalvertalingen in geïnstalleerde extensies te diagnosticeren. Om het uit te proberen:

Vanuit het Home Dashboard:

* Selecteer de **Algemene configuratie** knop in het *Systeem* paneel.
* Selecteer het *Systeem* paneel en stel **Debug Taal** in op **Ja**.
* **Taalweergave** is normaal ingesteld op **Waarde**. Als het is ingesteld op **Constante**,
wordt de lay-out verstoord door lange constanten die niet worden afgebroken.

Met Debug Taal actief worden alle vertaalbare waarden getoond, omringd met speciale tekens die hun status aangeven:

* `**Joomla CMS**` Tekst omringd door twee sterren geeft aan dat er een match is gevonden in een taalbestand en dat de constante is vertaald.
* `??Joomla CMS??` Tekst omringd door paren vraagtekens geeft aan dat de constante vertaalbaar is, maar dat er geen match is gevonden in een taalbestand.
* `Joomla CMS` Tekst zonder omringende tekens geeft aan dat de waarde niet vertaalbaar is.

## Systeem Debuggen

Aanvullende taal debugging informatie kan verkregen worden door
systeemdebugging te activeren.

Vanaf het Home Dashboard:

* Selecteer **Plugins** en zoek en activeer vervolgens de **System - Debug** plugin.
* Selecteer opnieuw het Home Dashboard en dan...
* Kies de **Globale Configuratie** knop.
* Selecteer het *Systeem* paneel en zet **Debug Systeem** op **Ja**.

Met **Systeem Debug** actief, hebben alle schermen extra debugginginformatie
onderaan elke pagina. Deze kan worden uitgebreid vanaf een Joomla-icoon en de bovenrand kan verticaal worden versleept om meer regels te tonen.

De debugginginformatie wordt weergegeven onder verschillende kopjes:

* **J! Info** Basisinstallatiegegevens.
* **Request** Serververzoekvelden.
* **Session** Sessiegegegevens.
* **Profile** De hoeveelheid tijd die nodig is geweest om code uit te voeren tot diverse markeerpunten in de code.
* **Queries** De SQL-query's die zijn uitgevoerd tijdens het bouwen van de pagina.
* **Loaded** Een lijst van alle taalbestanden die geladen zijn in het proces van het opbouwen van de pagina, inclusief volledige padinformatie. Dit kan nuttig zijn om te controleren of de verwachte bestanden geladen zijn.
* **Untranslated** Een lijst van alle niet-vertaalde constanten die gevonden zijn en de waarschijnlijke bestandslocatie gezien waar de vertaalopdracht is gemaakt.
* **Errors**

## Systeem - Debug Plugin

Deze systeemplugin bepaalt wat er wordt weergegeven wanneer debugging is geactiveerd in de **Globale Configuratie**. Er zijn drie instellingen die interessant zijn voor vertalers.

In het **Taal** tabblad:

![plugin systeem debug](../../../en/images/languages/languages-debug-plugin.png)

* **Fouten bij het parseren van taalbestanden** Toon een foutmelding als een taalbestand niet kan worden geladen.

- **Taalbestanden**. Als ingesteld op *Tonen* dan ...
- **Taalstring** Als ingesteld op *Tonen* dan ...
- **Eerste woord verwijderen**.
- **Verwijderen vanaf begin**
_ **Verwijderen vanaf einde**

**De volgende uitleg moet worden herzien!**

Merk op dat niet-vertalen van strings alleen de waarde tonen die is doorgegeven aan de desbetreffende **Text**-methode. Bijvoorbeeld, met de volgende code:

    echo Text::_('Reports Import Configuration');

Als niet-vertalen weergeven als:

    # /administrator/components/com_reports/views/reports/tmpl/default.php
    REPORTS IMPORT CONFIGURATION=Reports Import Configuration

Als de Strip Key Prefix is ingesteld op "Reports", dan zou de weergave iets veranderen naar:

    # /administrator/components/com_reports/views/reports/tmpl/default.php
    REPORTS IMPORT CONFIGURATION=Import Configuration

Merk op dat het weergegeven pad slechts een zo goed mogelijke schatting is op basis van een oproep naar de PHP *debug_backtrace* functie. Soms is het nauwkeurig, soms niet en er zijn ook gevallen waarin er geen bestand kon worden bepaald. In die gevallen moet u uw beste oordeel gebruiken.

*Vertaald door openai.com*

