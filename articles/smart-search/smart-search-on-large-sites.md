<!-- Filename: Smart_Search_on_large_sites / Display title: Slim Zoeken op Grote Sites -->

## Site-indexering

Slim Zoeken werkt door een onafhankelijke index van zoektermen in een aantal databasetabellen te creëren en te onderhouden. Het probleem voor grote sites is dat het indexeringsproces behoorlijk zwaar kan zijn in CPU-, geheugen- en schijfgebruik. Zelfs na de initiële constructie van de index kunnen incrementele updates ook zwaar zijn. Het goede nieuws is dat het opvragen van de index een relatief snelle en lichte operatie is.

Smart Search is geschikt voor de meerderheid van de Joomla-sites. Echter, zoeken levert specifieke uitdagingen op voor grote sites. Er moet aan worden gedacht dat Smart Search een pure PHP-implementatie van een zoekmachine is en bijzonder grote sites kunnen beter af zijn met het gebruik van een zelfstandige zoekmachine zoals Solr.

Om Slim Zoeken op een grote site te gebruiken, moet u waarschijnlijk enkele van de configuratie-instellingen aanpassen. Hieronder volgt wat algemeen advies over waar u op moet letten en wat u kunt proberen aan te passen.

## Gebruik Altijd de CLI-indexer

Omdat het initiële indexeringsproces veel tijd kan kosten, is het het beste om de indexer vanaf de opdrachtregel uit te voeren om problemen te voorkomen die kunnen ontstaan wanneer browsersessies verlopen. De CLI-indexer zal niet verstrijken, ongeacht hoe lang het duurt om te voltooien, en kan gemakkelijk worden afgebroken als er problemen optreden. Bovendien zijn foutmeldingen zichtbaar met de CLI-indexer, terwijl ze mogelijk verborgen zijn bij uitvoering vanuit de beheerder.

Om de CLI te gebruiken, open je een terminal, navigeer naar de cli-map in de root van je site en voer je het volgende commando uit:

```
php joomla.php finder:index
```

## Groeperen

De indexeerder verdeelt de indexeeropdracht in batches van inhoudsitems. Standaard is de batchgrootte ingesteld op 50, wat betekent dat er maximaal 50 inhoudsitems per batch worden geïndexeerd. Het vergroten van de batchgrootte kan het indexeerproces mogelijk sneller maken, maar het zal meer geheugen gebruiken en mogelijk meer tijdelijke schijfruimte.

## Problemen met onvoldoende geheugen

Als de indexer geen geheugen meer heeft, probeer dan de volgende aanpassingen één voor één te maken totdat het probleem is opgelost.

1. Verlaag de batchgrootte. Als je bijzonder grote inhoudsitems hebt, kan de indexeerder zelfs voor één enkel inhoudsitem door het geheugen raken, dus probeer het aanvankelijk te verlagen naar 5 en als je nog steeds zonder geheugen komt te zitten, verlaag het dan naar 1.
2. Als je meer geheugen aan de indexeerder kunt toewijzen, doe dat dan. Je kunt het geheugen dat aan de opdrachtregelindexeerder wordt toegewezen verhogen met een extra parameter op de opdrachtregel. Om bijvoorbeeld de geheugenlimiet te verhogen naar 256Mb, gebruik je de volgende opdracht, waarbij je de *256M* vervangt door zoveel geheugen als je veilig aan een proces op je systeem kunt toewijzen.
```php
    php -d memory_limit=256M joomla.php finder:index
```
3. Probeer te identificeren welke inhoudsitems ervoor zorgen dat de indexeerder door het geheugen raakt. Als het niet duidelijk is, kun je proberen alle Smart Search-plug-ins uit te schakelen behalve één. Het uitvoeren van de indexeerder met slechts één ingeschakelde plug-in tegelijk zou moeten onthullen welke inhoudstype(n) het probleem veroorzaken. Als laatste redmiddel kun je overwegen een paar uitzonderlijk grote inhoudsitems in afzonderlijke items op te splitsen. Als het probleem zich voordoet bij een aangepast inhoudstype, bekijk de plug-incode en overweeg om minder beschikbare inhoud per item te indexeren.

## Problemen met onvoldoende schijfruimte

De Smart Search-indexeertabellen kunnen snel groeien! De *#__finder_links_termsX* tabel bevat één rij per term/zinsdeel per inhoudsitem en een enkel Joomla-artikel met 1000 woorden zal doorgaans resulteren in ongeveer 3000 rijen die aan deze tabellen worden toegevoegd. Een tweede artikel van vergelijkbare grootte zal een vergelijkbaar aantal rijen toevoegen, zelfs als beide artikelen dezelfde woorden bevatten. Een site met tienduizenden artikelen, waarvan sommige duizenden woorden kunnen bevatten, zal waarschijnlijk eindigen met deze mappingtabel die miljoenen rijen bevat. Het is niet ongebruikelijk dat de indexeertabellen in dergelijke gevallen verschillende gigabytes aan schijfruimte in beslag nemen.

De index heeft een optie om te kiezen tussen zoekprecisie en indexgrootte. Wanneer je "Zoek naar zinnen" inschakelt in de globale opties van de component, zal je index groter zijn, maar het zal ook zorgen voor preciezere zoekresultaten. Als je het uitschakelt, betekent dat een veel kleinere index, maar ook geen mogelijkheid om naar volledige zinnen te zoeken.

## Notities

1. Er is momenteel geen gelijktijdigheidsvergrendeling om te voorkomen dat meer dan één proces de indexeerder tegelijkertijd uitvoert. Dit zal bijna zeker resulteren in een corrupte index. Zelfs iemand die wijzigingen opslaat aan een inhoudsitem terwijl er een volledige index wordt uitgevoerd, kan mogelijk de index beschadigen.

*Vertaald door openai.com*

