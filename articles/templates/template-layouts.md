<!-- Filename: J4.x:Template_Layouts / Display title: Sjabloonlay-outs  -->

## Lay-out Bestandstructuren

In een **sjabloon** plaatst elke extensie die HTML-uitvoer genereert de uitvoercode in een sjabloonbestand binnen de bestandstructuur van de extensie, vaak in een map genaamd tmpl. Enkele voorbeelden:

- /modules/mod_login/tmpl/default.php
- /modules/mod_login/tmpl/default_logout.php
- /components/com_content/tmpl/article/default.php
- /plugins/content/vote/tmpl/vote.php

In een **sjabloon override**, wordt een bestand met dezelfde naam aangemaakt binnen de sjabloonbestandstructuur en dat wordt gebruikt in plaats van het bestand in de extensiebestandstructuur. Overeenkomende voorbeelden:

- /templates/cassiopeia/html/mod_login/default.php
- /templates/cassiopeia/html/mod_login/default_logout.php
- /templates/cassiopeia/html/com_content/article/default.php
- /templates/cassiopeia/html/plg_content_vote/vote.php

Dit stelt je in staat de uitvoer aan te passen aan je behoeften. Je hebt echter niet de keuze om al dan niet je override te gebruiken. Het wordt altijd gebruikt.

In een **sjabloon alternatieve lay-out**, maak je een bestand met een andere naam dan het origineel, maar in dezelfde sjabloonmap. De nieuwe naam mag geen onderstreepkarakter bevatten. Je maakt ook ieder bestand dat het eerste deel van de oorspronkelijke naam deelt. Een voorbeeld:

- /templates/cassiopeia/html/mod_login/expires.php
- /templates/cassiopeia/html/mod_login/expires_logout.php

Het wordt dan mogelijk om te kiezen of je de oorspronkelijke standaard lay-out of de alternatieve lay-out wilt gebruiken. De keuze wordt gemaakt in het module- of componentbewerkingsformulier (Geavanceerd tabblad voor modules, Opties tabblad voor Artikelen). Let op dat niet alle extensies zowel overrides als alternatieve lay-outs toestaan.

**Pas op:** plugins bieden geen mechanisme om alternatieve lay-outs te selecteren.

## Module Alternatieve Layouts

Het creëren van een alternatieve layout voor een module is vergelijkbaar met het creëren van een template override voor een module. In beide gevallen maak je een map genaamd `templates/.../html/`. Bijvoorbeeld, de map voor een "mod_login" template override of alternatieve layout voor de cassiopeia template zou `templates/cassiopeia/html/mod_login/` zijn.

Er zijn twee belangrijke verschillen tussen een template override en een alternatieve layout. De eerste is de bestandsnaam. Voor de template override zou je het bestand `default.php` noemen, om te passen bij de naam van het kernbestand. Voor een alternatieve layout gebruik je een andere naam. De enige regel is dat **de bestandsnaam geen underscores mag bevatten**.

Het tweede belangrijke verschil is dat, in tegenstelling tot template override-bestanden die automatisch worden gebruikt wanneer de module wordt weergegeven met de template met de override, een alternatieve layoutbestand alleen wordt gebruikt als je deze selecteert als parameter in de Module-parameterinstellingen.

### Een uitgewerkt voorbeeld - mod_login

- Ga naar **Systeem**→**Website Templates**→**Cassiopeia Details en Bestanden**
- Selecteer het tabblad **Overrides Maken**.
- Selecteer het **mod_login** item uit de Module-lijst.
- In het tabblad Editor, selecteer **html**→**mod_login** om je nieuw gemaakte kopieën van de mod_login output-templates te zien.
- Hernoem **default.php** naar iets anders zonder een underscore, **expires.php** in dit voorbeeld.
- Hernoem **default_logout.php** naar **expires_logout.php**.

Je hebt nu twee bestanden met precies dezelfde inhoud als de originelen. Verander de inhoud van expires_logout.php om een bericht toe te voegen dat de gebruiker informeert op welk tijdstip de sessie zal verlopen na elke paginalading.

Op regel 16, direct onder de bestaande gebruik-stellingen, voeg het volgende toe:

```php
use Joomla\CMS\Factory;

date_default_timezone_set('Europe/London');
$config = Factory::getContainer()->get('config');
$lifetime = $config->get('lifetime', 0);
$time = time() + $lifetime * 60;
$endTime = date('H:i:s', $time); // time() geeft al een tijd in seconden
```

En op regel 36, direct na de regel met een endif-statement, voeg deze code toe:

```html
<p class="text-center">
Je sessie zal verlopen om <br><?php echo $endTime; ?>
</p>
```

Sluit de Cassiopeia-bestanden. Selecteer **Inhoud**→**Website Modules** en open de Login-module. In het tabblad Geavanceerd, Layout-item, zul je de keuze hebben tussen **-- Vanuit Module -- / Standaard** en **-- Vanuit cassiopeia Template -- / expires**.

![login module met alternatieve layouts](../../../en/images/templates/layouts-module-login.png)

Een manier waarop je deze functie kunt gebruiken is door twee Inlogformulieren te hebben, één met Publieke toegang en de ander met Super Gebruikers toegang. Kies in het laatste geval de **expires** optie en alleen Super Gebruikers zullen de herinnering van de sessievervaltijd zien.

Het is belangrijk te begrijpen dat, indien gespecificeerd in het Module-parameterscherm, een alternatief layoutbestand voor een module zal worden gebruikt voor die module, ongeacht welke template wordt gebruikt om de pagina weer te geven waar de module wordt getoond. Het is daarom de verantwoordelijkheid van de beheerder om ervoor te zorgen dat het layoutbestand naar wens werkt in alle templates waar deze module mogelijk wordt getoond.

### Vertaling

Je kunt de bestandsnaam vertalen met Taal Overrides. Probeer de volgende procedure:

- Selecteer **Systeem**→**Beheer Paneel**→**Taal Overrides**
- Selecteer je taal en de Beheerder-locatie.
- Selecteer de **Nieuw** knop en vul het formulier in. In dit voorbeeld is de taalsleutel **TPL_CASSIOPEIA_MOD_LOGIN_LAYOUT_EXPIRES** en de tekst zou kunnen zijn **Login / Logout met vervaltijd**
- Opslaan en Sluiten en ga terug naar het Login-module formulier.

![talen bewerken override formulier](../../../en/images/templates/layouts-language-override-form.png)

Het formulier voor modulaire lay-outselectie met **expires** vertaald:

![module alternatieve layouts selecteren](../../../en/images/templates/layouts-example-translated.png)

## Alternatieve Layouts voor Componenten

Alternatieve layouts voor componenten werken op dezelfde manier als modulelayouts. Een bestand wordt geplaatst in dezelfde map waar je een template override-bestand zou plaatsen. Bijvoorbeeld, om een alternatieve layout voor een artikel voor de template "cassiopeia" te maken, plaats je een bestand in de map `templates/cassiopeia/html/com_content/article/`. Net als bij modulelayouts mag het bestand niet dezelfde naam hebben als het kernbestand en mogen er geen underscores in de naam zitten. Bovendien mag er geen XML-bestand met dezelfde naam in deze map zijn. (We bespreken XML-bestanden hieronder bij Alternatieve Layouts voor Menu Items.)

Je kunt een globale waarde instellen voor componentlayouts in het Opties-venster van de component. Bijvoorbeeld, in het venster Artikel: Opties is er een parameter *Kies een Layout* zoals hieronder getoond:

![opties voor artikelen formulier met alternatieve layouts lijst](../../../en/images/templates/layouts-articles-options.png)

Net als bij modulelayouts worden de componentlayouts getoond als parameteropties in het individuele componentbewerkingsscherm. Bijvoorbeeld, voor een artikel verschijnt de parameter in de Artikelen: Bewerken Opties tab zoals hieronder getoond.

![artikel bewerk formulier met alternatieve layouts lijst](../../../en/images/templates/layout-article-edit.png)

Net als bij andere parameters gebruikt de instelling Gebruik Globaal de instelling van de Opties-parameter. De instelling Van Component's Standaard gebruikt de standaardlayout van de component. Alternatieve layouts die je hebt gemaakt voor verschillende templates worden onder elke templatekop weergegeven.

Bestandsnamen kunnen worden vertaald. De regel hieronder:
```ini
    TPL_CASSIOPEIA_COM_CONTENT_ARTICLE_LAYOUT_MYLAYOUT="Alleen Titel Geen XML"
```
zal een bestand genaamd "mylayout.php" vertalen als "Alleen Titel Geen XML".

Je kunt meer dan één bestand voor een layout hebben. Het initiële bestand mag geen underscores bevatten en eventuele extra bestanden moeten underscores hebben.

Alternatieve layouts voor componenten kunnen worden gebruikt met artikelen, contactpersonen of nieuwsfeeds.

Alternatieve layouts voor componenten worden alleen gebruikt wanneer aan twee voorwaarden is voldaan: (1) ze zijn gespecificeerd in de componentparameters; en (2) er is geen menu-item voor deze specifieke component. Bijvoorbeeld, als je een of meer menu-items van het type "Enkel Artikel" hebt ingesteld voor een bepaald artikel, dan zal de alternatieve layout voor dat artikel niet worden gebruikt. In plaats daarvan zal de layout die in het menu-item is opgegeven worden gebruikt. Dit is consistent met de algemene manier waarop componentparameters werken, waarbij de meest specifieke (in dit geval een enkel-artikel menu-item) de minder specifieke (in dit geval de artikelparameters) overschrijft.

## Categorie Alternatieve Layouts

Categorie alternatieve layouts werken net zoals componentlayouts. De regels voor het specificeren van layoutbestanden zijn hetzelfde. Het enige verschil is dat de map de categorimap is en niet de componentmap. Bijvoorbeeld, een alternatieve layout voor een contactcategorie voor cassiopeia zou in de map `templates/cassiopeia/html/com_contact/category` gaan.

Je kunt categorie layouts op globaal niveau instellen, in het Opties-scherm van elk component. Hieronder is een voorbeeld uit de Contacten: Opties / Categorie formulier:

![optiesformulier van het contactencomponent dat alternatieve layouts toont](../../../en/images/templates/layouts-contacts-options.png)

Categorie alternatieve layouts verschijnen wanneer je een categorie toevoegt of bewerkt in het Component: Bewerken Categorie / Opties formulier zoals hieronder getoond.

![optiesformulier van het contactencomponent dat alternatieve layouts toont](../../../en/images/templates/layouts-contacts-category-options.png)

Categorie alternatieve layouts kunnen worden gebruikt voor artikelen, banners, contacten en nieuwsfeeds.

Net als bij componentlayouts, zal een categorie layout alleen worden gebruikt als:

1. het is geselecteerd in de globale of categorieparameters.
2. er is geen menu-item specifiek voor de categorie.

Als er een menu-item is ingesteld voor een specifieke categorie, zal die layout geselecteerd in het menu worden gebruikt in plaats van de alternatieve categorie layout.

## Artikelcategorie Blog en Lijst

Voor artikelen zijn er twee kerncategorie-indelingen beschikbaar: Blog en Lijst. Elk van deze indelingen verschijnt in het formulier Artikelen: Opties onder de tab Categorie onder de kop "Van Component". Alternatieve indelingen verschijnen ook in de lijst, zodat Blog, Lijst of alternatieve sjabloonindelingen kunnen worden geselecteerd als de standaard categorie-indeling, hetzij globaal, hetzij bij het bewerken van een enkele artikelcategorie.

![contacten componentopties formulier met alternatieve indelingen](../../../en/images/templates/layouts-articles-options-category.png)

Dit betekent dat, net als bij andere indelingsopties, je kunt bepalen of artikelcategorie-links blog- of lijstindelingen gebruiken. Het is belangrijk om te begrijpen dat deze optie, net als andere indelingsparameters, alleen van kracht zal zijn wanneer er geen menu-item voor een enkele categorie voor de categorie bestaat.





