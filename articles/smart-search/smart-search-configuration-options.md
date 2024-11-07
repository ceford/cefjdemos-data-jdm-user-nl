<!-- Filename: Smart_Search_configuration_options / Display title: Slimme Zoekopties  -->

## Over Opties

Opties stellen je in staat om de globale instellingen van Slim Zoeken te beheren. De Optie-instellingen worden overgenomen door weergaven, maar de instellingen in een Menu-item overschrijven de Globale instellingen.

Het Opties-paneel is gescheiden in twee delen. Wanneer je klaar bent met het maken van aanpassingen, selecteer je de knop Opslaan. Kies anders de knop Annuleren om eventuele wijzigingen te annuleren.

## Zoekopties

De zoekopties bepalen het gedrag van de zoekformulieren en zoekresultaten voor de Finder front-end.

- **Resultaatbeschrijving** - Deze optie bepaalt of zoekresultaten met beschrijvingen moeten worden getoond. Standaard ingesteld op Tonen.
- **Beschrijving Lengte** - Deze optie bepaalt de maximale tekenlengte van de beschrijvingen van zoekresultaten. De beschrijvingen worden ingekort tot de maximale lengte, maar de inkorting gebeurt altijd bij het laatste spatiekarakter om te voorkomen dat er midden in een woord wordt ingekort. Deze optie is alleen van kracht wanneer de optie Resultaatbeschrijving is ingesteld op Tonen. Standaard ingesteld op 255 tekens.
- **Resultaat URL** - Deze optie bepaalt of zoekresultaten met URL's onder de beschrijving moeten worden getoond (indien ingeschakeld). Standaard ingesteld op Tonen.
- **Geavanceerd Zoeken** - Deze optie bepaalt of de geavanceerde zoekopties moeten worden getoond. Standaard ingesteld op Tonen.
- **Uitklappen Geavanceerd Zoeken** - De geavanceerde zoekopties zijn opgenomen in een uitklapbare container. Deze optie bepaalt of de container met geavanceerde zoekopties standaard moet worden uitgeklapt. Standaard ingesteld op Nee.
- **Datumfilters** - Deze optie bepaalt of de datumfilters moeten worden getoond in de geavanceerde zoekopties. Standaard ingesteld op Verbergen.
- **Resultaatlabels** - Deze optie bepaalt of zoekresultaten met labels moeten worden getoond. Vereist dat JXtended Labels is geïnstalleerd. Standaard ingesteld op Tonen.
- **Markeer Zoektermen** - Deze optie bepaalt of zoektermen moeten worden gemarkeerd in zoekresultaten. Standaard ingesteld op Ja.

## Indexopties

De indexopties beheersen het gedrag van de indexer die wordt gebruikt om inhoud te verwerken en te analyseren voor zoeken. De meeste instellingen, zoals de gewichtsvermenigvuldiger en stemmeropties, zullen niet onmiddellijk wijzigingen vertonen, aangezien ze worden gebruikt tijdens het indexeren en de effecten van deze instellingen alleen zichtbaar zijn nadat de index is geleegd en opnieuw is uitgevoerd.

- **Indexer Batchgrootte** - Deze optie beheerst de batchgrootte van de indexer. De slimme zoekindexer verdeelt het totale indexeerproces in een aantal batches om de serverbelasting te verminderen en de geheugen- en uitvoertijdlimieten van PHP te vermijden. Als de inhoud items die worden geïndexeerd bijzonder kort zijn en/of de server bijzonder snel is, kan de indexer meer items per batch verwerken. Echter, als de inhoud items die worden geïndexeerd bijzonder lang zijn en/of de server bijzonder traag is, moet de indexer minder items per batch verwerken. Standaard is 50.
- **Geheugentabel Limiet** - Deze optie beheerst de limiet van de geheugentabel. De slimme zoekindexer gebruikt MySQL-geheugentabellen om tijdelijk inhoudsgegevens op te slaan in plaats van de gegevens op te slaan in de geheugenbuffers van PHP, omdat grote inhouditems snel de standaard geheugenlimietinstellingen van PHP zullen uitputten. Echter, MySQL-geheugentabellen hebben ook aanpasbare groottebeperkingen en het aanpassen ervan is niet betrouwbaar. Deze instelling wordt meegeleverd om om te gaan met geheugentabellen met minder gebruikelijke groottebeperkingen en moet alleen worden aangepast wanneer er "Table Full"-fouten optreden tijdens het indexeren. Standaard is 30.000. Als u "table full"-fouten tegenkomt, probeer dan deze parameter te **verlagen**. De optimale waarde zou resulteren in geheugentabellen die iets kleiner zijn dan de <a href="http://dev.mysql.com/doc/refman/5.1/en/server-system-variables.html#sysvar_max_heap_table_size" rel="nofollow noreferrer noopener"><em>max_heap_table_size</em></a> parameter in MySQL, die standaard op 16 megabytes staat.
- **Titeltekst Gewichtsvermenigvuldiger** - Deze optie beheerst hoeveel invloed de titeltekst heeft op de totale relevantiescore van een zoekresultaat. Standaard is 1,7.
- **Hoofdtekst Gewichtsvermenigvuldiger** - Deze optie beheerst hoeveel invloed de hoofdtekst heeft op de totale relevantiescore van een zoekresultaat. Standaard is 0,7.
- **Metadata Gewichtsvermenigvuldiger** - Deze optie beheerst hoeveel invloed de metadata-tekst heeft op de totale relevantiescore van een zoekresultaat. Standaard is 1,2.
- **Padtekst Gewichtsvermenigvuldiger** - Deze optie beheerst hoeveel invloed de pad/URL-tekst heeft op de totale relevantiescore van een zoekresultaat. Standaard is 2,0.
- **Diverse Tekst Gewichtsvermenigvuldiger** - Deze optie beheerst hoeveel invloed de diverse tekst heeft op de totale relevantiescore van een zoekresultaat. Standaard is 0,3.
- **Stemmer** - Deze optie beheerst welke taalstemmer moet worden gebruikt tijdens het indexeren. De Engelse Alleen stemmer is een pure PHP-implementatie die geen afhankelijkheden heeft. De Snowball-stemmer vereist de Stem PHP-extensie maar biedt ondersteuning voor 14 talen, waaronder Deens, Duits, Engels, Spaans, Fins, Frans, Hongaars, Italiaans, Noors, Nederlands, Portugees, Roemeens, Russisch en Turks. Standaard is Engels Alleen.
- **Loggen Inschakelen** - maakt een logbestand tijdens het indexeerproces. Standaard is nee.

*Vertaald door openai.com*

