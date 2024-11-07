<!-- Filename: Multiple_Domains_and_Web_Sites_in_a_single_Joomla!_installation / Display title: Meerdere domeinen en websites in één enkele Joomla!-installatie  -->

**Opmerking:** Dit artikel is voor het laatst bijgewerkt in 2012!

Hoewel het een best practice is om elke website zijn eigen domein, Joomla!-installatie en database te geven, kunnen er speciale omstandigheden zijn waarin een multi-site oplossing onder één enkele Joomla!-installatie gerechtvaardigd is.

## Een Voorbeeldtoepassing

Een klein bedrijf, 'Johnson Candies', heeft twee afzonderlijke maar gerelateerde merken: *Red Candy* en *Yellow Candy*. Ze hebben een enkele Joomla!-gebaseerde website nodig waar beide soorten snoep zichtbaar zijn, elk met een eigen startpagina op de Joomla!-site die overeenkomt met de domeinen `www.redjohnsoncandy.com` en `www.yellowjohnsoncandy.com`.

Daarnaast **vereist elk merk en elke site een eigen ontwerp**: een gele sjabloon voor de één; een rode sjabloon voor de ander.

## Voordelen

Door beide merken in één enkele Joomla! webinstallatie op te nemen, kan Johnson Candies tijd besparen bij het bewerken (slechts één keer inloggen), artikelen en gegevens delen over beide merken (of sites) en een enkele functie gebruiken, zoals een contactformulier, voor beide merken.

## Implementatieprocedure

### Bereid je domeinen voor

Gebruik een enkel domein voor je hostingaccount, zoals normaal. Maak de vereiste toevoegdomeinen aan in het controlepaneel van je hostingaccount. Voor dit tutorial gebruiken we `www.redjohnsoncandy.com` naast de basisdomeinnaam `www.yellowjohnsoncandy.com`.

### Installeer en configureer Joomla!

Installeer en configureer Joomla! zoals normaal. Ontwikkel vervolgens artikelen, menu's en modules voor elke site.

### Maak sjablonen

Ontwikkel en installeer daarna de noodzakelijke sjablonen - één voor elke site die je wenst te hebben. In het bovenstaande voorbeeld zou je een sjabloon maken voor *rode snoepjes* genaamd *Rood Sjabloon* en een sjabloon voor *gele snoepjes* genaamd *Geel Sjabloon*. Zodra de sjablonen zijn geïnstalleerd, wijs je ze toe aan de relevante menu-items, met behulp van de Joomla! sjabloonmanager in het Joomla! Beheerdersgebied.

### Voeg een doorverwijzing toe

#### Optie #1: Maak een .htaccess (Apache) doorverwijzing

**Opmerking** *Schakel eerst SEF-URL's in Joomla! in*

Een optie is om .htaccess (Apache) te gebruiken om verzoeken aan een bepaald domein naar een specifieke Joomla!-pagina te leiden.

Ons doel is om alle verzoeken naar het Rode Snoepjes-domein door te verwijzen naar een specifieke pagina op de Joomla!-site. In dit voorbeeld verwijzen we alle verzoeken naar `www.redjohnsoncandy.com` door naar een categorie-blogpagina. Je zou eerder het 'rode snoepjes' sjabloon aan dit menu-item hebben toegewezen om de illusie van een aparte site te creëren.
```
#De volgende regel werkt, maar het verandert welke domeinnaam wordt weergegeven.
RewriteCond %{HTTP_HOST} ^(www\.)?redjohnsoncandy\.com$
RewriteRule (.*) http://www.yellowjohnsoncandy.com/index.php?option=com_content&view=category&layout=blog&id=3&Itemid=12 [R=301,L]
```
Nou, dat werkt - maar je ziet meteen het nadeel. Hoewel de gebruiker succesvol de Rode Snoepjes-site bekijkt, ziet hij nog steeds de Gele Snoepjes-domeinnaam. Helaas, als je zowel .htaccess als domein-parkeren (technisch gezien een doorverwijzing) gebruikt, is dit noodzakelijk om een LUS te voorkomen.

#### Optie #2: Maak een PHP Header Redirect

Deze oplossing heeft het voordeel dat het de illusie van gescheiden domeinen/websites voor de bezoeker behouden blijft. In plaats van .htaccess (Apache) voor onze doorverwijzing te gebruiken, gebruiken we een van de sjablonen op de site.

In dit voorbeeld is het basidomein `www.redjohnsoncandy.com`. Je hebt een sjabloon voor dat gebied gemaakt genaamd *Rood Sjabloon*. De truc is om de index.php-bestand van 'Rood Sjabloon' te openen en de volgende regels **als allereerste regels** van de installaties in de primaire index.php toe te voegen.

```php
<?php
$domain = $_SERVER["HTTP_HOST"];
$uri = $_SERVER["REQUEST_URI"];
$url = $domain . $uri;

if (($url == "redjohnsoncandy.com/") ||
   ($url == "www.redjohnsoncandy.com/")) {
   header("Status: 301 Moved Permanently");
   header("Location: http://www.redjohnsoncandy.com/index.php?option=com_content&view=category&layout=blog&id=3&Itemid=12");
}
?>
```

Hier is het voordeel: De bezoeker wordt nu doorgestuurd naar de juiste *Rode Site*-pagina, waaraan het *Rood Sjabloon* is toegewezen **alleen** in het geval dat ze op het 'rode site'-domein zijn aangekomen. Anders wordt de conditionele PHP-regel genegeerd en laadt de Gele Site.

Het is belangrijk om ook het URI (de URL die op het pure domein volgt) op te vragen, zodat je omleidingen naar hetzelfde domein kunt maken. Wanneer de URI onzichtbaar is in de URL, wordt de variabele een "/" teken. Daarom moet je je pure URL vergelijken met een "/" teken aan het einde. Op deze manier kun je 301 redirects binnen hetzelfde domein maken. Anders creëer je een oneindige loop in het doorverwijzingsproces.

#### Optie #3: Maak een PHP Header Redirect voor meerdere domeinen met specifieke domein redirects voor aangepaste sjablonen

Oplossing voor enkele webspace, met verschillende domeinen, één Joomla-installatie en afhankelijk van het domein waar de gebruiker landt, doorverwijzingen naar een andere standaardpagina. Plak de volgende PHP-code **als allereerste** in het primaire index.php-bestand van de installatie. Om een ander domein toe te wijzen, kun je eenvoudig de "if" functie kopiëren/plakken en deze bewerken met de waarden van het andere domein op dezelfde manier. Verder moet je de sjabloonweergaven instellen door verschillende module-item/koppelingsaliasen in te stellen en sjabloonweergaven binnen de Joomla! sjabloonmanager te configureren. De aliasinstelling is nodig wanneer je SEF-instellingen gebruikt.
```php
<?php
$domain = $_SERVER["SERVER_NAME"];
$requri = $_SERVER['REQUEST_URI'];
if (($domain == "www.example.de" && $requri == "/" ||
   $domain == "example.de"))  {
   header("Status: 301 Moved Permanently");
   header("Location: http://www.example.de/index.php?option=com_content&view=article&id=6");
}
?>
```
*Vertaald door openai.com*

