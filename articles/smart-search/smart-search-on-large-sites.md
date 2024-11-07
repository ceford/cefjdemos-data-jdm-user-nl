<!-- Filename: Smart_Search_on_large_sites / Display title: Slim Zoeken op Grote Sites -->

## Site-indexering

Slim zoeken werkt door een onafhankelijke index te creëren en te onderhouden van zoektermen in een aantal databasetabellen. Het probleem voor grote sites is dat het indexeerproces behoorlijk zwaar kan zijn in CPU-, geheugen- en schijfgebruik. Zelfs na de eerste opbouw van de index kunnen incrementele updates ook zwaar zijn. Het goede nieuws is dat het opvragen van de index een relatief snelle en lichte operatie is.

Slim zoeken is geschikt voor de meeste Joomla-sites. Echter, zoeken levert specifieke uitdagingen op voor grote sites. Het moet worden herinnerd dat Slim zoeken een pure PHP-implementatie is van een zoekmachine en dat bijzonder grote sites mogelijk beter af zijn met een op zichzelf staande zoekmachine zoals Solr.

Om Slim zoeken op een grote site te gebruiken, zul je waarschijnlijk enkele configuratie-instellingen moeten aanpassen. Wat volgt, is algemeen advies over waar je op moet letten en wat je kunt proberen te optimaliseren. Er zijn een aantal bekende openstaande kwesties met betrekking tot het gebruik van Slim zoeken op grote sites die hopelijk in toekomstige versies zullen worden aangepakt, en deze worden hier ook beschreven.

## Gebruik Altijd de CLI Indexer

Omdat het initiële indexeringsproces lang kan duren, is het het beste om de indexer vanaf de commandoregel uit te voeren om problemen met browser-sessies die verlopen te voorkomen. De CLI indexer zal niet verlopen, ongeacht hoe lang het duurt om te voltooien, en hij kan eenvoudig worden afgebroken als er problemen optreden. Bovendien zijn foutmeldingen zichtbaar bij de CLI indexer, terwijl ze verborgen zijn wanneer deze vanuit de Administrator wordt uitgevoerd.

Om de CLI te gebruiken, open je een terminal, navigeer je naar de cli-map in de root van je site en geef je het volgende commando in:

```
php joomla.php finder:index
```

## Batchverwerking

De indexeerder verdeelt de indexeeropdracht in batches van inhoudsitems. Standaard is de batchgrootte ingesteld op 30, wat betekent dat er maximaal 30 inhoudsitems per batch worden geïndexeerd. Het vergroten van de batchgrootte kan het indexeerproces mogelijk sneller maken, maar het zal meer geheugen en mogelijk meer tijdelijke schijfruimte gebruiken.

## Geheugenproblemen

Als de indexeerder geen geheugen meer heeft, probeer dan de volgende aanpassingen één voor één te maken totdat het probleem is opgelost.

1. Verminder de batchgrootte. Als je bijzonder grote inhoudsitems hebt, kan de indexeerder zelfs voor een enkele inhoudsitem zonder geheugen komen te zitten, dus probeer het eerst te verlagen naar 5 en als je nog steeds zonder geheugen komt te zitten, verlaag het dan naar 1.
2. Als je meer geheugen aan de indexeerder kunt toewijzen, doe dat dan. Je kunt het toegewezen geheugen aan de command-line indexeerder verhogen met behulp van een extra parameter op de command-line. Om bijvoorbeeld de geheugengrens te verhogen naar 256Mb gebruik je de volgende opdracht, waarbij je *256M* vervangt met zoveel geheugen als je veilig aan een proces op je systeem kunt toewijzen.  
   *php -d memory_limit=256M finder_indexer.php*
3. Verminder de geheugenlimiet voor de tabel. De standaard is 30000 termen, wat betekent dat zodra de tijdelijke in-geheugen *#__finder_tokens* tabel dit aantal rijen bereikt, de indexeerder zal overschakelen naar het gebruik van een schijftabel in plaats van een geheugentabel. Het kan zijn dat je niet genoeg geheugen hebt om een volledige of bijna volledige geheugentabel te verwerken, dus door de limiet te verlagen zal de indexeerder eerder naar de schijf overschakelen en zo minder geheugen gebruiken. Probeer 10000 of zelfs veel kleinere aantallen.
4. Verander de database-engine die wordt gebruikt voor de *__finder_tokens* en *#__finder_tokens_aggregate* tabellen van MEMORY naar InnoDB. Dit kan de prestaties ernstig beïnvloeden, omdat meer van het indexeringsproces de schijf zal gebruiken in plaats van geheugen, maar het kan de indexeerder in staat stellen om te voltooien zonder zonder geheugen te komen. Verwacht dat het indexeringsproces veel langer duurt. Dit zal de zoekprestaties echter niet beïnvloeden.
5. Probeer te identificeren welke inhoudsitems ervoor zorgen dat de indexeerder geen geheugen meer heeft. Als het niet duidelijk is, probeer dan alle Smart Search-plug-ins uit te schakelen behalve één. Door de indexeerder met slechts één plug-in tegelijkertijd in te schakelen, zou je moeten kunnen ontdekken welke inhoudstypen het probleem veroorzaken. Als laatste redmiddel kun je overwegen om enkele uitzonderlijk grote inhoudsitems in afzonderlijke items te splitsen. Als het probleem zich voordoet bij een aangepast inhoudstype, bekijk dan de plug-in code en overweeg om minder van de beschikbare inhoud per item te indexeren.  

## Problemen met Geen Schijfruimte Meer

De Smart Search-indextabellen kunnen snel groeien! De *#__finder_links_termsX*-tabellen (waarbij *X* een enkel hexadecimaal teken is) bevatten één rij per term/zinsdeel per inhoudselement. Een enkele Joomla-artikel met 1000 woorden resulteert meestal in ongeveer 3000 rijen die aan deze tabellen worden toegevoegd. Een tweede artikel van vergelijkbare grootte voegt een vergelijkbaar aantal rijen toe, zelfs als beide artikelen dezelfde woorden bevatten. Een site met tienduizenden artikelen, waarvan sommige duizenden woorden kunnen bevatten, zal waarschijnlijk eindigen met deze mapping-tabellen die miljoenen rijen bevatten. Het is niet ongebruikelijk dat de indextabellen onder dergelijke omstandigheden meerdere gigabytes aan schijfruimte in beslag nemen.

Met de huidige versie van Smart Search kun je hier niet veel aan doen. Er wordt echter gehoopt dat je in de volgende release het aantal woorden per zinsdeel dat wordt geïndexeerd kunt aanpassen. Op dit moment is dit hard gecodeerd op 3, wat betekent dat elk woord dat wordt geïndexeerd tevens wordt geïndexeerd als onderdeel van een paar aangrenzende woorden en als onderdeel van een trio van aangrenzende woorden. Dit is nuttig voor de automatisch aanvullen-functie en verbetert over het algemeen de kwaliteit van zoekresultaten. Op sites waar schijfruimte een probleem is, zou het goed zijn om dit te verminderen naar 2 of zelfs 1, zodat de mapping-tabellen dienovereenkomstig kleiner zouden zijn.

## Notities

1. Er is momenteel geen concurrency-vergrendeling om te voorkomen dat meer dan één proces de indexer tegelijkertijd laat draaien. Dit zal vrijwel zeker resulteren in een corrupte index. Zelfs iemand die wijzigingen opslaat in een inhoudsitem terwijl een volledige index wordt uitgevoerd, kan potentieel de index beschadigen.

*Vertaald door openai.com*

