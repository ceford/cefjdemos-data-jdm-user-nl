<!-- Filename: jdocmanual?manual=user&heading=seo&filename=seo-basics.md / Display title: SEO Basisprincipes -->

## Definitie

Zoekmachineoptimalisatie is het proces van het verbeteren van een breed scala aan kenmerken van een website met de bedoeling de positie te verbeteren waarin deze wordt gerangschikt in zoekmachines.

Het proces van het optimaliseren van een website is veelzijdig, omdat er veel factoren zijn die van invloed zijn op waar een pagina in een zoekmachine kan worden gerangschikt.

- Ervoor zorgen dat content een geschikte structuur heeft met behulp van Semantische HTML
- De kwaliteit van de inhoud van individuele pagina's verbeteren
- Zorgen dat de website verzoeken snel kan verwerken
- Mogelijk maken van Zoekmachinevriendelijke URLs om het webadres van pagina's ‘menselijk leesbaar’ te maken
- Toevoegen van contextuele semantische markup met behulp van Schema-data

Bron: Zoekmachineoptimalisatie (SEO) Startersgids

## Sitestructuur en Beschrijvende URLs

In de begintijd waren websites gestructureerd als individuele HTML-bestanden in een boomhiërarchie. Sommige websites zijn nog steeds zo gestructureerd. CMS'en zijn anders. Individuele pagina's worden samengesteld uit inhoud die in databasetabellen is opgeslagen. De URLs voor de voormalige en de latere zijn verschillend, misschien zoals dit:
```
https://www.example.com/user/seo/seo-basics.html
https://www.example.com/index.php?option=com_jdocmanual&view=manual&manual=user&heading=seo&filename=seo-basics
```
Duidelijk is dat de eerste gemakkelijker te onthouden en gemakkelijker te typen is. Zoekmachines geven de voorkeur aan hen.

In het Joomla CMS kan een URL van de eerste vorm als volgt worden ingesteld:

1. Maak een inhoudscategorie met de naam **User**.
2. Maak een inhoudscategorie met de naam **SEO** die een kind is van *User*.
3. Maak een artikel en wijs het toe aan de *SEO*-categorie.
4. Maak een **User** menu-item van het type **Category List** met behulp van de *User*-categorie.
5. Maak een menu-item **SEO** van het type **Category List** met behulp van de *SEO*-categorie.
6. Stel de Joomla SEO-functionaliteit in via *Global Configuration*.

Test het met je SEO URL: navigeer via de User en SEO-lijsten naar de SEO Basics pagina. De kruimelpaden moeten tonen: `Je bent hier: Home / User / SEO / SEO Basics`. Maar niet als je een menu-item van het type Enkele Artikel hebt aangemaakt voor *SEO Basics*!

## Verminder duplicatie

Het probleem met CMS'en is dat dezelfde inhoud beschikbaar kan worden gemaakt met verschillende URLs. In het bovenstaande voorbeeld zullen beide URLs werken (maar niet op deze site), net als `https://example.com/index.php?option=com_content&view=category&id=18&ItemID=17`. Slechts één van deze zou door zoekmachines herkend moeten worden en ingesteld moeten worden als de **canonieke** URL. Maar welke en hoe?

De **Systeem - SEF** plugin biedt enige hulp. Het heeft drie instellingen:

* **Site Domein:** Als je site via meer dan één domein toegankelijk is, voer hier het voorkeurdomein (soms bekend als canoniek) in. **Opmerking:** `https://example.com` en `https://www.example.com` zijn verschillende domeinen.
* **Strikte behandeling van index.php:** Deze optie maakt een striktere behandeling van 'index.php' in URLs mogelijk wanneer 'URL herschrijven gebruiken' is ingeschakeld in de Globale Configuratie. Het zal 'index.php' verwijderen als een URL deze nog bevat en inkomende verzoeken met 'index.php' omleiden naar de versie zonder 'index.php'.
* **Sluitende schuine streep voor URLs:** Forceer Joomla om alleen URLs met of zonder sluitende schuine streep te gebruiken. Wanneer ingesteld, zal dit de juiste URL met redirects afdwingen en wordt alleen toegepast wanneer 'Voeg achtervoegsel toe aan URL' is uitgeschakeld.

**Canonieke Tags** uitleg van Daniel Morell:

* Hoe Joomla Canonieke Tags te creëren
* Plugin en Documentatie:

Voor Joomla 4 en 5, voordat je het inschakelt, moet de plugin `if ($app->isAdmin()) {` veranderd worden naar `if ($app->isClient('admin')) {` op regel 72 en 99 van *plugins /system / customcanonical / customcanonical.php*.

In een artikel selecteer je het Publicatie tabblad en vervolgens de **Auto** knop voor *Canonieke URL*. Dit zal een link als de volgende plaatsen op elke pagina die het enige artikel weergeeft:
```
	<link href="/jdm3/nl/user/seo/seo-basics.html" rel="canonical" />
```

## Kwaliteit van de Inhoud

Maak wat je schrijft interessant en gemakkelijk leesbaar. Lange alinea's zijn vaak
overweldigend en moeilijk te lezen. Alinea's van één regel zien er niet goed uit! Misschien moeten ze eigenlijk opsommingen zijn. Streef naar alinea's van ongeveer drie regels. Lees wat je schrijft en verwijder overbodige woorden.

Houd je inhoud up-to-date en vermijd het kopiëren van informatie van andere sites.
Als het mogelijk is, verifieer je content.

### Semantische HTML

De inhoud moet bestaan uit een hiërarchie van koppen en alinea's met andere
elementen indien nodig (lijsten, tabellen, enzovoort). Verwar structuur niet met
uiterlijk - gebruik daarom geen kop voor vetgedrukt maken of vetgedrukt maken voor een kop.
Dit is een voorbeeld van semantische opmaak van een artikel:

```html
  <h2>Koppen gebruiken</h2>
  <p>Dit is een artikel over het belang van koppen.</p>

  <h2>Waarom koppen gebruiken?</h2>
  <p>Het is belangrijk om koppen te gebruiken zodat zoekmachinebots kunnen herkennen wat
  een <strong>belangrijk</strong> onderdeel van je artikel is.</p>

  <h3>Soorten koppen</h3>
  <p>Je kunt vaste soorten koppen gebruiken, maar ze moeten in je pagina geordend en
  gestructureerd zijn. H1 wordt de paginatitel die door Joomla wordt ingevoegd,
  waarbij H2 voor subkoppen van de pagina wordt gebruikt. Alle koppen binnen je
  subkoppen moeten oplopend zijn met H3, H4 en H5, indien van toepassing.</p>

  <h2>Is het moeilijk om koppen te implementeren?</h2>
  <p>Het is heel eenvoudig om koppen te implementeren, je gebruikt gewoon de geschikte
  HTML-code.</p>
```
Let op dat een artikel *Titel* een `<h1>`-kop wordt als dat nodig is, dus gebruik het niet in de hoofdtekst van een artikel.

## Voorzie Zoektermen

Kies expliciete titels voor je pagina's en koppen binnen pagina's. Bijvoorbeeld, als je niet weet wat *Semantische HTML* is of meer informatie over dat onderwerp wilt, zouden dat de woorden zijn die je in een zoekmachine invoert. Denk aan de mensen die geïnteresseerd zouden kunnen zijn in de informatie die je biedt. Waar zullen zij naar zoeken? Maar houd titels en koppen redelijk kort - sommige bronnen zeggen niet meer dan 60 tekens.

## Voorzichtig met Advertenties

Niets zal sitebezoekers meer afschrikken dan advertenties die overal verschijnen en de echte informatie voor je ogen verplaatsen. Advertenties die elke paar seconden veranderen zijn ook irritant en een belasting voor de middelen van de eindgebruiker. Velen zullen Ad-blockers gebruiken!

## Let op met Links

Links zijn zowel een zegen als een vloek! Ze kunnen je site-SEO-score positief of negatief beïnvloeden, afhankelijk van of je links hebt naar betrouwbare of onbetrouwbare bronnen. En ze moeten worden onderhouden. Je kunt links hebben naar interne of externe artikelen die zijn verdwenen, verouderde informatie presenteren of niet langer relevant zijn. Beste advies: link als het doelwit echte voordelen biedt voor je sitebezoekers en gebruik het `nofollow`-linkattribuut als je niet wilt dat de doelsite wordt geassocieerd met je site.

Er zijn veel tools voor het controleren van links beschikbaar, sommige gratis of freemium en andere betaald, vaak als onderdeel van een sitebewakingsdienst.

## Paginatitel en Beschrijving

In de `<head>` van elke pagina zou een `<title>`-tag en een `<description>`-tag moeten staan. Joomla maakt het heel gemakkelijk om een andere titel voor elke pagina in te stellen. Helaas maakt het ook heel gemakkelijk om te vergeten om een geschikte Titel en Beschrijving op elke pagina in te stellen.

Neem als voorbeeld de hierboven genoemde **SEO**-categorielijstpagina. De broncode van de pagina `<title>` zegt **SEO** en de `<description>` ontbreekt. In het formulier **Menu's: Item bewerken** voor dit menu-item is er een tabblad **Paginweergave** met een veld **Browserpaginatitel**. Voeg daar `SEO - Lijst van Artikelen` in en dat is wat verschijnt in de `<title>`-tag en in het browsertabblad.

In het tabblad **Metadata**, met het veld **Meta Beschrijving** ingesteld op `Lijst van artikelen over zoekmachineoptimalisatie.` is dat precies wat verschijnt in het `<description>` veld. De Beschrijving wordt soms gebruikt om een Paginatitel in zoekresultaten te begeleiden, dus het loont de moeite om deze relevant te maken.

Meer informatie:
* Tijdschriftartikel: Joomla SEO titel tags
* Verken de Kern: Ingebouwde SEO Opties

## Optimaliseer Afbeeldingen

Het spreekt voor zich dat aantrekkelijke afbeeldingen een site enorm kunnen verbeteren. Maar te veel afbeeldingen die te groot zijn, kunnen SEO-boetes opleveren. Hier zijn enkele tips:

* Plaats afbeeldingen naast de tekst die ze illustreren.
* Gebruik beschrijvende **alt**-tekst.
* Gebruik met een minteken gescheiden woorden voor de bestandsnamen van afbeeldingen, bijvoorbeeld kat-op-heet-tin-dak.jpg.
* Gebruik het juiste type afbeelding voor de taak: png voor posters, jpg voor foto’s.
* Gebruik responsieve afbeeldingen - er is een Joomla-plugin die dynamisch webp-versies maakt van png- en jpg-afbeeldingen in verschillende formaten.

*Vertaald door openai.com*

