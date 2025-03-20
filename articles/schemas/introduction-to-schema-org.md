<!-- Filename: J5.x:Schema_org / Display title: Inleiding tot Schema's -->

## Rijke Snippets

Rijke snippets (ook bekend als *rijke resultaten*) zijn normale Google-zoekresultaten met extra gegevens weergegeven. Deze extra gegevens worden meestal samengesteld uit gestructureerde gegevens die in de HTML van een pagina worden gevonden. Veelvoorkomende typen rijke snippets omvatten recensies, recepten en evenementen. Rijke snippets kunnen helpen websites op te laten vallen in zoekresultaten, meer klikken aan te trekken en gebruikers een beter begrip van de inhoud te geven voordat ze doorklikken.

Joomla implementeert Rich Snippets met behulp van JSON-LD. Dit is een JavaScript-notatie die is ingebed in een `<script>`-tag in het `<head>`-element van een HTML-pagina. De markup is niet verweven met de voor de gebruiker zichtbare tekst. De inhoud van de snippets wordt ingevoerd in formuliervelden die zijn geïmplementeerd met plug-ins.

## Schema.org

>Schema.org is een samenwerkingsactiviteit van de gemeenschap met als missie het creëren, onderhouden en promoten van schema's voor gestructureerde gegevens op het internet, op webpagina's, in e-mailberichten en daarbuiten.

Gestructureerde gegevens zijn een gestandaardiseerd formaat voor het organiseren en representeren van informatie op het web. Het biedt een manier om de inhoud en betekenis van gegevens op een gestructureerde manier te beschrijven, waardoor het voor zoekmachines en andere toepassingen gemakkelijker wordt om de informatie te begrijpen en te verwerken. Er is meer gedetailleerde informatie op de [Schema.org website](https://schema.org/).

## Joomla-Implementatie

In Joomla worden Rich Snippets gegenereerd met behulp van gestructureerde data-opmaak op basis van de Schema.org-schema's. Elk schematype wordt geïmplementeerd als een apart plugin. Dit zorgt voor een meer modulaire en uitbreidbare architectuur. Elke plugin is verantwoordelijk voor het genereren van de schema-opmaak voor een specifiek type inhoud, wat meer flexibiliteit en aanpassingsmogelijkheden biedt. Dit maakt het gemakkelijker voor externe ontwikkelaars om bij te dragen aan de ontwikkeling van de gestructureerde data-mogelijkheden van Joomla.

Om te beginnen ga je naar **Systeem -> Plugins** en schakel je de *Systeem - Schema.org* plugin in. Als deze plugin niet is ingeschakeld, zal er geen Schema-tabblad zijn in een artikelbewerkingsformulier, zelfs als alle afzonderlijke plugins zijn ingeschakeld.

![List of schema plugins](../../../en/images/schemas/schema-plugins-list.png)

### Systeem bewerken - Schema.org Plugin

- **Basistype** Kies of uw website een organisatie of een individuele persoon vertegenwoordigt.
- **Naam** Voer de naam in van de organisatie of persoon die de website vertegenwoordigt.
- **Afbeelding** Voeg uw bedrijfs- of persoonlijke afbeelding toe
- **Social media-accounts** Voeg uw bedrijfs- of persoonlijke social media-accounts toe. Selecteer de groene knop met plusteken om rijen aan het formulier toe te voegen. 
- Selecteer **Opslaan & Sluiten**.

![edit system schema org plugin](../../../en/images/schemas/edit-system-schema-org-plugin.png)

### Een artikel bewerken

Ga naar een van je artikelen en vul de velden van het Schema-formulier in. Als het *Schema Type* is ingesteld op *Geen*, de standaardinstelling, zijn er geen velden in te vullen. Selecteer een Schema om een lijst van velden te zien die geschikt zijn voor dat schema. De onderstaande screenshot toont een artikel met het Artikel-schema geselecteerd:

![edit article scheme form](../../../en/images/schemas/schema-form-in-an-article.png)

### Uitvoer

Je zult niets zien dat gerelateerd is aan het schema op de webpagina. Als je echter naar de paginabron kijkt, zul je een scriptvermelding zien, zoals in het volgende voorbeeld:

```json
	<script type="application/ld+json">{
    "@context": "https://schema.org",
    "@graph": [
        {
            "@type": "Organization",
            "@id": "http://localhost/jcms-testing/#/schema/Organization/base",
            "name": "Joomla Documentation Team",
            "url": "http://localhost/jcms-testing/"
        },
        {
            "@type": "WebSite",
            "@id": "http://localhost/jcms-testing/#/schema/WebSite/base",
            "url": "http://localhost/jcms-testing/",
            "name": "JCMS Testing",
            "publisher": {
                "@id": "http://localhost/jcms-testing/#/schema/Organization/base"
            }
        },
        {
            "@type": "WebPage",
            "@id": "http://localhost/jcms-testing/#/schema/WebPage/base",
            "url": "http://localhost/jcms-testing/index.php/en/article-en-gb",
            "name": "Article (en-gb)",
            "isPartOf": {
                "@id": "http://localhost/jcms-testing/#/schema/WebSite/base"
            },
            "about": {
                "@id": "http://localhost/jcms-testing/#/schema/Organization/base"
            },
            "inLanguage": "en-GB",
            "breadcrumb": {
                "@id": "http://localhost/jcms-testing/#/schema/BreadcrumbList/139"
            }
        },
        {
            "@type": "Article",
            "headline": "Article Schema Test",
            "description": "Latin text used to simulate layouts.",
            "author": {
                "@type": "person",
                "name": "Superman"
            },
            "@id": "http://localhost/jcms-testing/#/schema/com_content/article/1",
            "isPartOf": {
                "@id": "http://localhost/jcms-testing/#/schema/WebPage/base"
            }
        }
    ]
}</script>
```

U kunt uw gestructureerde gegevens testen via de Google [Test uw gestructureerde gegevens pagina](https://developers.google.com/search/docs/appearance/structured-data).

## Beschikbare plugins

| Plugin | Beschrijving |
|--------|-------------|
| Artikel Plugin | Het startpunt voor het gebruik van schema.org |
| Blogposting Plugin | Voor blogpost-inhoud |
| Boek Plugin | Voor boekinhoud |
| Aangepaste Plugin | Voor directe invoer van JSON-LD-code |
| Evenement Plugin | Voor evenementinhoud |
| Vacature Plugin | Voor inhoud van vacatures |
| Organisatie Plugin | Voor bedrijfs- en organisatie-inhoud |
| Persoon Plugin | Voor persooninhoud |
| Recept Plugin | Voor receptinhoud |

*Vertaald door openai.com*

