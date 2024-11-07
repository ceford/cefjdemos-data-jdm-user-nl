<!-- Filename: J6.x:_Article_Metadata / Display title: Artikel: Bewerken - Metadata  -->

## Inleiding

Metadata is informatie over een webpagina die zich in het eerste deel van de pagina bevindt tussen de `<head>...</head>` tags. Het merendeel van deze informatie is niet zichtbaar voor sitebezoekers, maar wordt door zoekmachines gebruikt om relevante resultaten voor zoekopdrachten te leveren. Het is daarom in je belang om informatieve metadata te gebruiken.

Sommige metadata-items worden verstrekt door de gebruikte sjabloon en hoef je niet zelf in te stellen. Veelvoorkomende voorbeelden:

```html
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="generator" content="Joomla! - Open Source Content Management">
```
Er zijn andere vormen van metadata, zoals Open Graph Data die door Facebook wordt gebruikt, en schema's die worden gebruikt om specifieke typen pagina's te beschrijven, zoals Persoon, Plaats of Product. Deze worden hier niet behandeld.

De metadata-items die vaak over het hoofd worden gezien, zijn de paginatitel (**Title**), die voorkomt binnen `<title>...</title>` tags in de pagina `<head>`, en de paginabeschrijving (**Description**), die voorkomt binnen `<meta>` tags maar mogelijk ontbreekt. Deze worden hier behandeld.

## De paginatitel

Een artikeltitel is vereist voor elke nieuwe pagina. Enkele richtlijnen en tips voor het samenstellen van goede titels van het Mozilla Developer Network:

>* Vermijd titels van één of twee woorden. Gebruik een beschrijvende zin of een term-definitiecombinatie voor woordenboek- of referentiestijlpagina's.
>* Zoekmachines tonen meestal de eerste 55–60 tekens van een paginatitel. Tekst daarbuiten kan verloren gaan, dus probeer titels niet langer te maken dan dat. Als u een langere titel moet gebruiken, zorg er dan voor dat de belangrijke onderdelen eerder komen en dat er niets cruciaals in het deel van de titel staat dat waarschijnlijk wordt weggelaten.
>* Gebruik geen "sleutelwoordblokken". Als uw titel slechts een lijst met woorden is, verlagen algoritmen vaak de positie van uw pagina in de zoekresultaten.
>* Zorg ervoor dat uw titels zo uniek mogelijk zijn binnen uw eigen site. Duplicaat- of bijna-duplicaat-titels kunnen bijdragen aan onnauwkeurige zoekresultaten.

Aanvullende aanbevelingen van Google:

>- Specificeer een unieke titel voor elke pagina
>- Maak uw titel beschrijvend voor de pagina-inhoud en bondig
>- Vermijd keyword stuffing (herhaaldelijk gebruik van vergelijkbare woorden zoals "Foobar, foo bar, foobars, foo bars")
>- Vermijd het gebruik van generieke titels - elke pagina zou een unieke titel moeten hebben, idealiter dynamisch bijgewerkt in relatie tot de weergegeven inhoud
>- Merk uw titels, maar doe het op een beknopte manier en in relatie tot de aangeboden inhoud

Er zijn verschillende webmasters-tools die kunnen worden gebruikt om te identificeren of er problemen zijn met uw vermeldingen in een specifieke zoekmachine - het is altijd de moeite waard om op te letten en eventuele problemen te corrigeren. Een voorbeeld:

[Google ondersteuningsartikel over het gebruik van titels voor uw webpagina's](http://support.google.com/webmasters/bin/answer.py?hl=nl&amp;answer=35624)

In Joomla wordt voor een enkele pagina de artikelkop de paginatitel die in de head wordt gebruikt en in het browsertabblad wordt weergegeven. Voor een samengestelde pagina, zoals *Uitgelichte artikelen* of een *Categorieblog*, wordt de menukoptitel de paginatitel. Dus je moet goed nadenken over het samenstellen van goede beschrijvende titels voor zowel artikelen als menu-items.

## De pagina Beschrijving

Het artikel *Meta Beschrijving* is een veld in het tabblad *Publiceren* van het artikeldata-invoerformulier:

![Het artikelbewerking formulier publicatie tabblad](../../../en/images/articles/articles-edit-publishing-tab.png)

Als er geen artikelmetadata beschrijving is, wordt een metadata beschrijving van een enkel artikelmenu-item gebruikt als deze is ingesteld. Als er geen metadata beschrijving van een menu-item is, wordt de globale site meta beschrijving gebruikt als deze is ingesteld. Anders wordt het metadata beschrijving veld weggelaten.

Google raadt het volgende aan om ervoor te zorgen dat u het meeste haalt uit uw zoekmachine-indexering:

>- Zorg ervoor dat elke pagina een unieke, relevante meta beschrijving heeft
>- Zorg ervoor dat u metadata toepast voor overzichtspagina's (bijv. blog- en lijstlayouts) naast individuele artikelen - dit wordt vaak over het hoofd gezien op Joomla! websites
>- Voeg feitelijke informatie toe indien relevant (bijv. blogartikelen kunnen de auteur bevatten, producten kunnen de prijs of fabrikant bevatten)
>- Overweeg automatisch gegenereerde metadata te gebruiken - maar zorg ervoor dat deze relevant, leesbaar en accuraat zijn.
>- Maak uw beschrijvingen beschrijvend!

Een andere referentie:

[Google support artikel over het gebruik van metadata](http://support.google.com/webmasters/bin/answer.py?hl=en&amp;answer=35624)

## Trefwoorden

Er was eens een tijd waarin zoekmachines trefwoorden gebruikten om inhoud te classificeren. Dus vulden auteurs hun trefwoorden-metadata met een groot aantal trefwoorden in de hoop hun SEO-ranking te verbeteren. Als reactie hierop stopte Google met het gebruik van trefwoorden voor rangschikkingsdoeleinden. Als je op internet zoekt naar advies, zul je bronnen vinden die zeggen dat het niet de moeite waard is, terwijl anderen zeggen dat ze nog steeds waarde hebben.

Trefwoorden worden niet gebruikt door de Joomla-kern. Bij twijfel, doe geen moeite.

## Robots

De standaardwaarde van *Use Global* plaatst geen metatag in de HTML-kop van de pagina. Andere waarden doen dat wel. Er is een `robots.txt`-bestand in de root van de Joomla-site. Als je robots wilt beheren, moet je dit bestand lezen. Het bevat een uitleg over hoe je het kunt gebruiken.

## Auteur

Je kunt de formele naam van de auteur invoeren om als metadata te verschijnen.

## Rechten

U kunt een copyrightverklaring invoeren die als metadata verschijnt.

## Voorbeeldmetadata

Zo ziet de metadata eruit in de bronweergave van het artikel:
Hier is een voorbeeld van de inhoud van de `<head>` na invulling van alle 
metadata-velden:

```html
    <meta charset="utf-8">
    <meta name="rights" content="Charles Darwin © 1859">
    <meta name="author" content="Charles Darwin">
    <meta name="robots" content="noindex, nofollow">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="description" content="Publiciteit voor The Origin of Species.">
    <meta name="generator" content="Joomla! - Open Source Content Management">
    <title>Publiciteit</title>
```
Let op dat het uitgaande veld voor trefwoorden ontbreekt.

*Vertaald door openai.com*

