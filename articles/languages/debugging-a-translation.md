<!-- Filename: Debugging_a_translation / Display title: Het debuggen van een vertaling -->

<img
src="https://docs.joomla.org/images/thumb/6/69/Split-icon.png/25px-Split-icon.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/6/69/Split-icon.png/38px-Split-icon.png 1.5x, https://docs.joomla.org/images/thumb/6/69/Split-icon.png/50px-Split-icon.png 2x"
data-file-width="200" data-file-height="67" width="25" height="8"
alt="Split-icon.png" />Split Page into Specific Joomla! Versions - J2.5
and 3.x

It has been suggested that this article or section be split into
specific version
*Namespaces*.
(<a
href="https://docs.joomla.org/index.php?title=Talk:Debugging_a_translation/nl&amp;action=edit&amp;redlink=1"
class="new"
title="Talk:Debugging a translation/nl (page does not exist)">Discuss</a>).
If version split is not obvious, please allow split request to remain
for 1 week pending discussions. <span class="small">*Proposed since **2
years ago***.</span>


Joomla ondersteunt een aantal nuttige debug-mechanismen die het
makkelijker maken onvertaalde strings te vinden en problemen te
onderzoeken met vertalingen van geïnstalleerde extensies.

#### Foutopsporing taal

<img
src="https://docs.joomla.org/images/thumb/6/62/Global-config-language-debug-nl.png/250px-Global-config-language-debug-nl.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/6/62/Global-config-language-debug-nl.png/375px-Global-config-language-debug-nl.png 1.5x, https://docs.joomla.org/images/6/62/Global-config-language-debug-nl.png 2x"
data-file-width="464" data-file-height="168" width="250" height="91"
alt="Global-config-language-debug-nl.png" />

U activeert foutopsporing taal via Administratie beheer door naar de
algemene instellingen te gaan en te klikken op de Systeem tab. Zoek het
Foutopsporing taal veld, wijzig de waarde in “Ja” en sla uw wijzigingen
op.

Met deze optie actief worden alle te vertalen strings getoond met
speciale tekens omgeven, die hun status aangeven

|                    |                                                                                                                                       |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------|
| Code               | Status                                                                                                                                |
| \*\*Joomla CMS\*\* | *(tekst omgeven door sterretjes)* geeft aan dat er een overeenkomst gevonden is in het taalbestand en de string vertaald is.          |
| ??Joomla CMS??     | *(tekst omgeven door een stel vraagtekens)* geeft aan dat de string vertaalbaar is maar er geen match gevonden is in het taalbestand. |
| Joomla CMS         | "(tekst zonder omringende tekens)" geeft aan dat de string niet te vertalen is.                                                       |

#### Foutopsporing systeem

Extra foutopsporingsinformatie kan worden verkregen dor het activeren
van de systeem foutopsporing. Dit wordt gedaan door naar de Algemene
instellingen te gaan in op de systeem tab te klikken. Zoek het
Foutopsporing systeem veld op, wijzig de waarde in “Ja” en sla de
wijzigingen op.

Met deze optie actief hebben alle schermen extra informatie over
foutopsporing aan het einde van de pagina. Momenteel bevat deze

- **Profiel informatie.** Dit is de tijd om de code uit te voeren tot de
  verschillende markeerpunten in de code.
- **Geheugen gebruik.** De hoeveelheid systeem-RAM-geheugen gebruikt.
- **SQL query's uitgevoerd.** Alle SQL query's die uitgevoerd zijn
  tijdens het opbouwen van de pagina.
- **De taal-bestanden geladen.** Een lijst met alle taalbestanden die
  geladen zijn tijdens het opbouwen van de pagina, inclusief de
  volledige pad-informatie. Dit kan handig zijn om te controleren of de
  verwachte bestanden geladen zijn. Het aantal achter elk pad is het
  aantal keren dat er naar het bestand verwezen is.
- **Onvertaalde strings diagnose.** Een lijst met alle gevonden
  onvertaalde strings en de waarschijnlijke bestandslocatie waar de
  **JText** aanroep wed gedaan.
- **Onvertaalde strings ontwerp.** Een lijst met al de gevonden
  onvertaalde strings in een KEY=Waarde formaat zodat ze gekopieerd en
  geplakt kunnen worden naar een taalbestand (INI).

#### Foutopsporing plugin

<img src="https://docs.joomla.org/images/d/db/Debug-plugin-nl.png"
decoding="async" data-file-width="544" data-file-height="423"
width="544" height="423" alt="Debug-plugin-nl.png" />

deze systeem plugin regelt wat getoond wordt als de foutopsporing actief
is bij de **Algemene instellingen**. Het is standaard ingeschakeld. U
kunt de parameters van de plugin bereiken via **Extensies →
Pluginbeheer**. Zoek de “Systeem - Foutopsporing” plugin en klik erop.
Er zijn drie instellingen van belang voor vertalers.

- **Toon taalbestanden**. Indien dit op “Ja” staat bevat de
  foutopsporings-informatie een lijst met taalbestanden die opgevraagd
  werden toen de pagina opgebouwd werd.
- **Toon taalstrings** Indien gezet op “Ja” dan wordt een lijst met
  onvertaalde strings met de locatie van het bestand dat de aanroep naar
  **JText** doet opgenomen in de foutopsporingsinformatie.
- **Verwijder vanaf het begin**. Wordt alleen gebruikt als **Toon
  taalstrings** op “Ja” staat. Dit biedt de mogelijkheid een voorvoegsel
  van de string te strippen om de sleutel te vormen. Dit is handig als
  de ontwikkelaar een algemeen voorvoegsel gebruikt voor zijn extensie
  bij gebruik van de **JText** methode. Zie onderstaande voorbeeld.

Merk op dat het tonen van niet-vertaalde strings alleen de waarde die
naar de juiste **JText** methode wordt gestuurd toont. Bijvoorbeeld de
volgende code:

    echo JText::_( 'Reports Import Configuration' );

Indien niet vertaald, zal de ontwikkel modus dit tonen als:

    # /administrator/components/com_reports/views/reports/tmpl/default.php
    REPORTS IMPORT CONFIGURATION=Reports Import Configuration

Als de 'Verwijder vanaf het begin' voorvoegsel op "Reports" staat
verandert de uitvoer enigszins in:

    # /administrator/components/com_reports/views/reports/tmpl/default.php
    REPORTS IMPORT CONFIGURATION=Import Configuration

Merk op dat het getoonde pad een gok is gebaseerd op de aanroep naar de
PHP *debug_backtrace* functie. Soms is het juist, soms niet en er zijn
ook gevallen waarbij geen bestand bepaald kan worden. In dit geval moet
u een oordeel vellen.
