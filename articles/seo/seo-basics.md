<!-- Filename: jdocmanual?manual=user&heading=seo&filename=seo-basics.md / Display title: SEO Basisprincipes -->

## Definitie

Zoekmachineoptimalisatie is het proces van het verbeteren van een breed scala aan kenmerken van een website met de bedoeling de positie te verbeteren waarin deze wordt gerangschikt in zoekmachines.

Het proces van het optimaliseren van een website is veelzijdig, aangezien er veel factoren zijn die van invloed zijn op de positie van een pagina in een zoekmachine.

- Ervoor zorgen dat inhoud een juiste structuur heeft met behulp van Semantische HTML
- De kwaliteit van de inhoud van individuele pagina's verbeteren.
- Ervoor zorgen dat de website aanvragen snel kan afhandelen.
- Zoekmachinevriendelijke URL's inschakelen om het webadres van pagina's *leesbaar voor mensen* te maken.
- Contextuele semantische markup toevoegen met gebruik van Schema-data.

Resource: [Inleiding Gids Zoekmachineoptimalisatie (SEO)](https://developers.google.com/search/docs/fundamentals/seo-starter-guide)

## Sitestructuur en Beschrijvende URL's

In de beginjaren waren websites gestructureerd als individuele HTML-bestanden in een boomhiërarchie. Sommige websites zijn nog steeds zo gestructureerd. CMS'en zijn anders. Individuele pagina's worden samengesteld uit inhoud die in databasetabellen is opgeslagen. De URL's voor de vroegere en latere zijn verschillend, misschien zoals dit:

```
https://www.example.com/user/seo/seo-basics.html
https://www.example.com/index.php?option=com_jdocmanual&view=manual&manual=user&heading=seo&filename=seo-basics
```

Het is duidelijk dat de eerste gemakkelijker te onthouden en gemakkelijker te typen is. Zoekmachines geven er de voorkeur aan.

In het Joomla CMS kan een URL van de eerste vorm als volgt worden ingesteld:

1. Maak een inhoudscategorie met de naam **Gebruiker**.
2. Maak een inhoudscategorie met de naam **SEO** die een subcategorie is van *Gebruiker*.
3. Maak een artikel en ken het toe aan de *SEO* categorie.
4. Maak een **Gebruiker** menu-item van het type **Categorielijst** met behulp van de *Gebruiker* categorie.
5. Maak een menu-item **SEO** van het type **Categorielijst** met behulp van de *SEO* categorie.
6. Stel de Joomla SEO-functionaliteit in bij *Globale Configuratie*.

Test het met je SEO-URL: navigeer via de Gebruiker- en SEO-lijsten naar de SEO Basisprincipes pagina. De kruimelpad moet tonen: `U bent hier: Home / Gebruiker / SEO / SEO Basisprincipes`. Maar niet als je een type menu-item voor Een Enkel Artikel hebt gemaakt voor *SEO Basisprincipes*!

## Verminder duplicatie

Het probleem met CMS'en is dat dezelfde inhoud beschikbaar kan worden gemaakt met verschillende URL's. In het bovenstaande voorbeeld zullen beide URL's werken (maar niet op deze site), evenals `https://example.com/index.php?option=com_content&view=category&id=18&ItemID=17`. Slechts één van deze moet door zoekmachines worden herkend en ingesteld als de **canonieke** URL. Maar welke en hoe?

De **System - SEF** plugin biedt enige hulp. Het heeft drie instellingen:

- **Site Domein** Als je site via meer dan één domein toegankelijk is, voer hier het voorkeursdomein in (soms aangeduid als canoniek domein). **Opmerking:** `https://example.com` en `https://www.example.com` zijn verschillende domeinen.
- **Strikte behandeling van index.php** Deze optie maakt een striktere behandeling van `index.php` in URLs mogelijk wanneer **URL-herschrijving gebruiken** is ingeschakeld in de Globale Configuratie. Het verwijdert `index.php` als een URL deze nog bevat en leidt inkomende verzoeken met `index.php` om naar de versie zonder de `index.php`.
- **Trailing slash voor URLs** Dwing Joomla af om alleen URLs met of zonder trailing slash te gebruiken. Wanneer ingesteld, zal dit de juiste URL afdwingen met omleidingen en wordt alleen toegepast wanneer 'Achtervoegsel aan URL toevoegen' is uitgeschakeld.

Anders, zie de uitleg van **Canonieke Tags** door [Daniel Morell](https://www.danielmorell.com/blog/how-to-create-joomla-canonical-tags).

## Kwaliteit van de Inhoud

Maak wat je schrijft interessant en gemakkelijk te lezen. Lange alinea's zijn vaak overweldigend en moeilijk te lezen. Eén-regel alinea's zien er verkeerd uit! Misschien zouden het echt opsommingstekens moeten zijn. Streef naar alinea's van ongeveer drie regels. Lees wat je schrijft en schrap onnodige woorden.

Houd uw inhoud actueel en vermijd het kopiëren van informatie van andere sites. Verifieer indien mogelijk uw inhoud.

### Semantische HTML

Inhoud moet bestaan uit een hiërarchie van koppen en alinea's met andere elementen indien nodig (lijsten, tabellen enzovoort). Verwissel structuur niet met uiterlijk - gebruik dus geen kop om tekst vet te maken of vetgedrukte tekst om een kop te maken. Dit is een voorbeeld van semantische opmaak van een artikel:

```html
  <h2>Using headings</h2>
  <p>This is an article about the importance of headings.</p>

  <h2>Why use headings?</h2>
  <p>It is important to use headings so that search engine bots can tell what
  is an <strong>important</strong> part of your article.</p>

  <h3>Types of headings</h3>
  <p>You can use set types of headings, but they should be ordered, and
  structured, within your page.  H1 will be the page title inserted by Joomla,
  with H2 being used for sub-headings of the page.  Any headings within your
  sub-headings should cascade using H3, H4, and H5 as appropriate.</p>

  <h2>Is it hard to implement headings?</h2>
  <p>It is really easy to implement headings, you just use the appropriate
  HTML code.</p>
```

Merk op dat een artikel *Titel* in een `<h1>` kop zal veranderen indien nodig, dus gebruik het niet in de tekst van een artikel.

## Verwachte Zoektermen

Kies expliciete titels voor uw pagina's en koppen binnen pagina's. Bijvoorbeeld, als u niet weet wat *Semantische HTML* is of meer informatie over dat onderwerp wilt, dan zouden dat de woorden zijn die u in een zoekmachine invoert. Denk aan de mensen die mogelijk geïnteresseerd zijn in de informatie die u verstrekt. Waar zullen zij naar zoeken? Maar houd titels en koppen redelijk kort - sommige bronnen zeggen niet meer dan 60 tekens.

## Zorg met Advertenties

Niets zal sitebezoekers meer afschrikken dan advertenties die overal verschijnen en de echte informatie voor je ogen verplaatsen. Advertenties die om de paar seconden veranderen, zijn ook vervelend en een belasting voor de bronnen van de eindgebruiker. Velen zullen Ad-blockers gebruiken!

## Zorgvuldigheid met Links

Links zijn zowel een zegen als een vloek! Ze kunnen de SEO-score van je site zowel positief als negatief beïnvloeden, afhankelijk van of je links hebt naar betrouwbare of onbetrouwbare bronnen. En ze moeten onderhouden worden. Je kunt links hebben naar interne of externe artikelen die zijn verdwenen, verouderde informatie presenteren of niet langer relevant zijn. Beste advies: link als het doel echte waarde toevoegt voor je sitebezoekers en gebruik het `nofollow` linkattribuut als je niet wilt dat de doelsite wordt geassocieerd met je site.

Er zijn veel link checker tools beschikbaar, sommige gratis of freemium en andere betaald, vaak als onderdeel van een site monitoring dienst.

## Paginatitel en Beschrijving

In de `<head>` van elke pagina moet een `<title>`-tag en een `<description>`-tag staan. Joomla maakt het erg eenvoudig om een andere titel voor elke pagina in te stellen. Helaas maakt het ook erg makkelijk om te vergeten een geschikte Titel en Beschrijving op elke pagina in te stellen.

Als voorbeeld nemen we de hierboven genoemde **SEO** categorielijstpagina. De paginabron `<title>` vermeldt **SEO** en de `<description>` ontbreekt. In het formulier **Menu's: Item Bewerken** voor dit menu-item is er een tabblad **Paginaweergave** met een veld **Browserpaginatitel**. Voer daar `SEO - Lijst van Artikelen` in en dat is wat er in het `<title>`-tag en in de browsertab verschijnt.

In de **Metadata** tab, met het **Meta Description** veld ingesteld op `List of articles on Search Engine Optimisation.`, is dat precies wat er in het `<description>` veld verschijnt. De beschrijving wordt soms gebruikt om een paginatitel te vergezellen in zoekresultaten, dus het is belangrijk om deze relevant te maken.

Meer informatie:
* Tijdschriftartikel: [Joomla SEO-titeltags](https://magazine.joomla.org/all-issues/september/joomla-seo-title-tags)
* [Ontdek de Kern: Native SEO-opties](https://magazine.joomla.org/all-issues/june/explore-the-core-native-seo-options)

## Optimaliseer Afbeeldingen

Het spreekt voor zich dat aantrekkelijke afbeeldingen een site enorm kunnen verbeteren. Maar te veel afbeeldingen die te groot zijn, kunnen SEO-straffen opleveren. Hier zijn enkele tips:

- Plaats afbeeldingen naast de tekst die ze illustreren.
- Gebruik beschrijvende **alt**-tekst.
- Gebruik met een minteken gescheiden woorden voor de afbeeldingsnamen, bijvoorbeeld cat-on-hot-tin-roof.jpg.
- Gebruik het juiste type afbeelding voor de taak: png voor posters, jpg voor foto’s.
- Gebruik responsieve afbeeldingen - er is een [Joomla plugin](https://responsive-images.dgrammatiko.dev/) die dynamisch webp-versies van png en jpg-afbeeldingen in verschillende formaten creëert.

*Vertaald door openai.com*

