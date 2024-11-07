<!-- Filename: jdocmanual?manual=user&heading=help&filename=administrator-help.md / Display title: Beheerdershulp   -->

## Introductie

Bijna alle Joomla-beheerderpagina's hebben een werkbalk met een **Help**-knop
bijna rechtsboven op de pagina. Alleen dashboards hebben geen werkbalk en
dus ook geen Help-knop.

Veel pagina's hebben ook een knop met het label **Inline Help Aan/Uitzetten**.
Dit toont of verbergt simpelweg een veldbeschrijving als er een beschikbaar
is. Het doel hiervan is om rommel te verminderen, maar wel een mechanisme
voor herinnering te bieden waar dit nuttig zou kunnen zijn. Het wordt hier verder
niet behandeld.

De **Help**-knop activeert het openen van een nieuw venster met behulp van een
URL die in de knop is ingebed. Een voorbeeld:
```
data-url="https://help.joomla.org/proxy/index.php?keyref=Help51:Articles&lang=en"
```
In dit geval komt de inhoud van de Helppagina van een externe bron.

## De Helpbron - een MediaWiki-site

MediaWiki is de software die door WikiPedia wordt gebruikt. Het is een Free Open Source Software (FOSS) pakket dat PHP en MySQL gebruikt, net als Joomla. Je kunt het zelf downloaden en installeren. In theorie zou je je eigen Helpserver kunnen maken en die gebruiken in plaats van de gemeenschappelijke Joomla Help Server. In de praktijk moet je weten dat MediaWiki-pagina's enige verwerking nodig hebben om ze geschikt te maken voor weergave als Helppagina's.

Daar komt de **proxy** om de hoek kijken. Deze haalt de benodigde pagina op van de MediaWiki-installatie en bereidt deze voor om als Helppagina te worden weergegeven. Je kunt een originele MediaWiki-pagina zien in dit voorbeeld op https://docs.joomla.org/Help5.x:Articles en je kunt het bewerken als je iets verkeerds ziet.  

## De Wereldwijde Help-URL

Het **configuration.php**-bestand in de root van een Joomla-installatie bevat een
`$helpurl` variabele:

```
$helpurl = 'https://help.joomla.org/proxy/index.php?keyref=Help{major}{minor}:{keyref}&lang={langcode}';
```

Wanneer op een Help-knop wordt geklikt, wordt elk van de items tussen accolades vervangen.
De {major} en {minor} waarden zijn de versienummers van je installatie.
De {langcode} is de code van je momenteel geselecteerde beheerders taal en kan bijvoorbeeld 'en', 'de' of 'fr' zijn.

De {keyref} variabele is de bestandsnaam van een pagina op de Help-server, zonder de namespace. Dus voor de Artikelen-pagina is de relevante bestandsnaam toevallig
*Articles*.

**Opmerking:** `https://docs.joomla.org/` is de site voor het bewerken van Helppagina's. Maar `https://help.joomla.org/proxy` is de site voor het oproepen van Helppagina's.

Er is geen voorziening voor het wijzigen van de standaard-Help-server-URL vanuit de Beheerder Globale Configuratie-formulieren, maar je kunt het wijzigen met een teksteditor.

De complete lijst van beschikbare vervangcodes is:

| Code          | Zal worden vervangen door                                                      |
|---------------|--------------------------------------------------------------------------------|
| {app}         | Naam van de applicatie (bijv. "Administrator" in het Joomla CMS back-end)      |
| {component}   | Naam van het component (bijv. "com_content" in de Artikelenmanager)            |
| {keyref}      | Verwijzing naar de helpschermsleutel (na doorgang door het vertaalproces)      |
| {major}       | Joomla hoofdversienummer (bijv. "5" in Joomla 5.6).                            |
| {minor}       | Joomla kleine versienummer (bijv. "1" in Joomla 5.1)                           |
| {maintenance} | Joomla onderhoudsversienummer (bijv. "3" in Joomla 5.1.1).                     |
| {language}    | Volledige taalcode (bijv. "en-GB")                                             |
| {langcode}    | Taalcodegedeelte van de volledige taalcode (bijv. "en" als de volledige code "en-GB" is) |
| {langregion}  | Regio codegedeelte van de volledige taalcode (bijv. "GB" als de volledige code "en-GB" is) |

## Wereldwijde Hulp in de Toekomst

Het gebruik van een MediaWiki-site voor het leveren van Helppagina's is een zekere belasting voor degenen die de documentatie onderhouden en de procedure kan in de toekomst veranderen. Als er een wijziging plaatsvindt, is het waarschijnlijk dat de bron zal bestaan uit voorgebouwde HTML-bestanden die worden benaderd met een eenvoudige aanpassing van het $helpurl bron-domein.

## Lokale Help voor Aangepaste Componenten

Als je een aangepaste component hebt en vertrouwd bent met het bewerken van PHP-broncode en het maken van content, kun je je eigen individuele helppagina's creëren. Neem de Jdocmanual-component als voorbeeld. Als een aangepaste component zijn er geen helppagina's op de MediaWiki-site docs.joomla.org. Derde partij componenten mogen daarvandaan geen helppagina's leveren.

Bekijk deze codefragment uit administrator/components/com_jdocmanual/src/View/Manual/ViewHtml.php:
```
        $tmpl = $app->input->getCmd('tmpl');
        if ($tmpl !== 'component') {
            ToolbarHelper::help('jdocmanual', true);
        }
```
De specificatie van de ToolbarHelper::help aanroep is als volgt:
```
@param $ref: De naam van het doelformulier (exclusief de bestandsextensie).
@param $useComponent: Gebruik het helpbestand in de component map.
@param $url: Gebruik deze URL in plaats van een andere.
@param $component: Naam van de component om hulp te krijgen (null voor de huidige component)
function Toolbar::help(
    string $ref,
    bool $useComponent = false,
    string $url = null,
    string $component = null
): HelpButton
Schrijft een helpknop voor een bepaalde optie (opent een pop-up venster).
```
In dit voorbeeld is **$ref** een bestandsnaam die wordt gebruikt, in dit geval `'jdocmanual'` (het moet overeenkomen met de naamgeving van het doelformulier) en is **$useComponent** `true`, wat betekent dat de te gebruiken helppagina zich binnen de component bestanden zal bevinden op:
administrator/component/com_jdocmanual/help/en-GB/jdocmanual.html

Het gebruik van een helpbestand binnen de component zou moeten betekenen dat Help nooit ontbreekt en misschien altijd up-to-date is.

## Aangepaste Component Remote Help

Bij het maken van de Help-knop kun je $useComponent = false instellen en de URL instellen zodat deze naar een specifieke locatie op je eigen site of een externe site verwijst.

```
    ToolbarHelper::help('jdocmanual', false, 'http://example.com/help/en-GB/jdocmanual.html');
```

Dus alles wat nodig is, is een HTML-pagina met de juiste naam op de juiste plek.

*Vertaald door openai.com*

