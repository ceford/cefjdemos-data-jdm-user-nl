<!-- Filename: How_do_you_block_directory_scans_using_htaccess%3F / Display title: Directoryvermelding niet toestaan -->

## Achtergrond

Standaard zal een Apache-webserver in een directory zonder een gedefinieerd configuratie-indexbestand (index.html of index.php) een lijst weergeven van alle bestanden en subdirectory's in de directory. Dit kan nuttig zijn op een persoonlijke testserver, maar vormt een ernstig beveiligingsrisico op een live productieserver.

In het verleden was het gebruikelijk om in alle Joomla-directories een leeg index.html-bestand op te nemen om te voorkomen dat dit probleem zou optreden op slecht geconfigureerde servers. Dit is niet langer het geval. De verwachting is dat de server op de juiste manier geconfigureerd is, hetzij in de serverconfiguratiebestanden, hetzij in individuele .htaccess-bestanden. Het eerste is de voorkeur, omdat dit wordt toegepast op alle websites op de server.

Sites in een gedeelde hostingomgeving kunnen echter verwachten dat elke site de serverconfiguratie aanpast met behulp van .htaccess-bestanden. De server moet worden ingesteld op "AllowOverride Options" of "AllowOverride All" om overschrijvingen in .htaccess toe te staan.

## Gebruik van .htaccess

Het htaccess.txt-bestand dat bij Joomla wordt geleverd, kan op Apache-servers worden gebruikt door het te hernoemen of te kopiëren naar .htaccess. Het bevat veel instellingen om hackeraanvallen op Joomla-sites tegen te gaan. Onder andere zie je de volgende instellingen om directoryvermeldingen te voorkomen:

```
Options -Indexes

## No directory listings
<IfModule mod_autoindex.c>
	IndexIgnore *
</IfModule>
```

## Test je site

Een manier om je site te testen is door de URL van je afbeeldingenmap in de URL-balk van de browser in te voeren: `https://je-domein.nl/images/`. Aangezien de afbeeldingenmap normaal gesproken geen index.html- of index.php-bestand bevat, zou je een volledig lege pagina moeten zien. Als je een lijst van alle bestanden en mappen ziet, dan voorkom je geen directoryscans voor welk deel van je site dan ook. Los dit op!

*Vertaald door openai.com*

