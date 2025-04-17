<!-- Filename: jdocmanual?manual=user&heading=performance&filename=page-analysis.md / Display title: Pagina-analyse   -->

## Lighthouse

> Lighthouse is een open-source, geautomatiseerd hulpmiddel voor het verbeteren van de kwaliteit van webpagina's. Je kunt het gebruiken op elke webpagina, openbaar of met vereiste authenticatie. Het voert audits uit voor prestaties, toegankelijkheid, progressive web apps, SEO en meer.

Het is beschikbaar als een extra hulpmiddel voor Google Chrome en Firefox en kan worden uitgevoerd vanaf de opdrachtregel. Dat is handig voor testen in een lokale ontwikkelomgeving.

Meer informatie vind je op de Lighthouse-website van Chrome voor ontwikkelaars.

Je kunt de tool online gebruiken via de PageSpeed Insights-website.

De volgende screenshot toont het eerste deel van het PageSpeed Insights-rapport:

![PageSpeed Insights Rapport](../../../en/images/performance/performance-pagespeed-insights.png)

## Prestatieverbeteringen

Het tweede deel van het rapport stelt methoden voor om de prestaties te verbeteren:

* **Elimineer render-blocking resources** - Potentiële besparing van 540 ms. Eerlijk gezegd is dit te veel werk voor te weinig beloning.
* **Schakel tekstcompressie in** - Potentiële besparing van 11 KiB. Stel in de globale configuratie, in het Server-paneel, de GZip Pagina Compressie in op *Ja*. Dat laat kleine JavaScript- en CSS-bestanden over die nog geminimaliseerd en gecomprimeerd moeten worden.
* **Verminder ongebruikte CSS** - Potentiële besparing van 62 KiB. De boosdoeners zijn template.min.css en joomla-fontawesome.min.css, maar dat impliceert het aanpassen van de CSS voor elke pagina op de site, wat te foutgevoelig werk is voor te weinig beloning.
* **Bedien statische assets met een efficiënt cachebeleid** - 21 middelen gevonden. Referenties zijn verstrekt, waaronder Joomla-specifieke referenties.

De algemene boodschap is dat sommige suggesties de moeite waard zijn om op te lossen en andere niet.

## Mobiel vs Desktop Rapport

Het Desktop-rapport verschilt meestal van het Mobiele rapport. Enkele extra problemen die in dit geval zijn geïdentificeerd:

* **Afbeeldingen correct van formaat voorzien** - Potentiële besparing van 48 KiB. De afbeeldingstag is eigenlijk geoptimaliseerd met webp-afbeeldingen van 768 en 1200 pixels breed. Het lijkt erop dat iets daartussenin gewenst is.

## Toegankelijkheid

* **Links hebben geen duidelijke naam** Dit verwijst naar de pijlen naar links en rechts onderaan de pagina die voor- of achteruit navigeren. De tekst is weggelaten om vertaalproblemen te voorkomen. Moet opnieuw over nagedacht worden!
* **Aanraakdoelen hebben niet voldoende grootte of tussenruimte** Dit verwijst naar de grootte van de menu-items in de linker- en rechterkolommen. Ze hebben meer verticale ruimte nodig - een aanpassing van de CSS is nodig.

## Best Practices en SEO

Hoewel beide een score van 100 hebben voor mobiel en desktop, moeten ze opnieuw worden gecontroleerd na elke ontwerpwijziging.

## Samenvatting

Alle problemen op deze site zijn opgelost, behalve het demonteren van de css-bestanden en het verkleinen van de kleine component Javascript- en CSS-bestanden.
*Vertaald door openai.com*

