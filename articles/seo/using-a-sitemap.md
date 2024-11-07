<!-- Filename: Using_A_Sitemap / Display title: Een Sitemap Gebruiken  -->

## Een Sitemap Gebruiken

Hoewel zoekmachines uw pagina's meestal kunnen vinden door de manier waarop ze elders op het internet zijn gekoppeld, is het een goede gewoonte om een sitemap te maken die zoekmachine-'bots' een lijst van de pagina's op uw website biedt - beschouw het als een kaart om alle content op uw site te vinden. Sitemaps zijn niet alleen belangrijk voor zoekmachines, ze zijn ook erg behulpzaam voor mensen met een handicap die misschien een eenvoudige interface nodig hebben om uw site-structuur te bekijken en door de site te navigeren zonder uw menu-structuren te gebruiken. <a href="https://www.w3.org/TR/WCAG20-TECHS/G63.html" rel="nofollow noreferrer noopener">W3C Werkgroep Notitie over Sitemaps</a>

Een sitemap dient verschillende doelen:

- Biedt een gestructureerde lijst die een overzicht toont van alle content op uw website
- Stelt een bezoeker in staat om snel een overzicht van uw site-structuur te krijgen
- Biedt een alternatieve manier om door uw website te navigeren, zonder de behoefte aan complexe menu-structuren
- Geeft zoekmachines een middel om content te vinden die misschien niet beschikbaar is via uw menu-structuren (bijv. landingspagina's)

### Types sitemaps

Het is mogelijk om sitemaps te verstrekken voor specifieke soorten informatie, waaronder:

- Video <a href="https://support.google.com/webmasters/answer/80471" rel="nofollow noreferrer noopener">Google hulp over videositemaps</a>
- Afbeeldingen <a href="https://support.google.com/webmasters/answer/answer.py?answer=178636" rel="nofollow noreferrer noopener">Google hulp over afbeeldingssitemaps</a>
- Nieuws <a href="https://support.google.com/news/publisher/answer/75717" rel="nofollow noreferrer noopener">Google hulp over Nieuwssitemaps</a>
- Internationaal <a href="https://support.google.com/webmasters/answer/2620865?hl=en&amp;ref_topic=2370587" rel="nofollow noreferrer noopener">Google hulp over Internationale sitemaps</a>

Deze gespecialiseerde sitemaps stellen u in staat om informatie te verstrekken met betrekking tot het specifieke mediatype - bijvoorbeeld bij een videositemap kunt u informatie geven over de looptijd, categorie en gezinsvriendelijke status; bij afbeeldingssitemaps kunt u het onderwerp van de afbeelding specificeren, de licentie voor gebruik en het type afbeelding.

### Een sitemap maken

Op een statische website is het maken van een sitemap eenvoudigweg een kwestie van handmatig een XML-bestand maken volgens de juiste standaarden, en het opslaan als een XML-bestand. Voor een dynamische site, waar de inhoud regelmatig verandert, is dit niet echt een optie - u zou het sitemapbestand elke keer dat u nieuwe content toevoegt handmatig moeten bijwerken!

Om deze reden zijn er verschillende sitemapextensies beschikbaar in de Joomla Extensions Directory (<a href="https://extensions.joomla.org/category/structure-a-navigation/site-map" rel="noreferrer noopener">Sitemapcategorie op Joomla Extensions Directory</a>) waarmee u dynamisch een sitemap kunt maken die voldoet aan de sitemapstandaarden die zoekmachines verwachten.
<a href="https://www.sitemaps.org/" rel="nofollow noreferrer noopener">Sitemaps protocol</a>

De meeste van deze extensies werken door het kiezen van menu-items die u wilt opnemen in een sitemap, en het specificeren hoe vaak ze veranderen (zie Updatefrequentie). Het is ook mogelijk subpagina's op te nemen van die menu-items (bijvoorbeeld, een menu-item kan leiden naar een categorieblogpagina, maar u wilt alle artikelen die op deze pagina worden getoond als individuele items weergeven - een ander voorbeeld kan een menu-item zijn dat verwijst naar een winkelcategoriepagina, en in de sitemap wilt u de categorie vermelden, en vervolgens elk product erin als een afzonderlijke link).

### Updatefrequentie

Hoewel u handmatig in uw Sitemap kunt specificeren hoe vaak zoekmachines de spiders uw website moeten bezoeken, hebben de meeste zoekmachines ingebouwde systemen die de frequentie van terugbezoeken automatisch aanpassen op basis van hoe vaak de betreffende pagina is gewijzigd.

Dus, bijvoorbeeld, als u zoekmachinebots vertelt uw pagina dagelijks te bezoeken, maar wanneer het de pagina bezoekt er niets is veranderd gedurende een week, kan het de frequentie van revisits dienovereenkomstig aanpassen en niet zo vaak terugkeren als u het had verteld. U kunt via de verschillende webmastersportalen verzoeken om de revisitsnelheid aan te passen indien nodig.

Dit zou dus suggereren dat als u regelmatig veranderende inhoud heeft, uw website vaker wordt 'gespidered' - wat leidt tot sneller indexeren van de inhoud dan websites die niet vaak veranderen.

Het is over het algemeen verstandig om pagina's die statisch zijn minder vaak te laten crawlen dan die welke regelmatig veranderen. Bijvoorbeeld, een statisch tekstartikel kan worden ingesteld met een updatefrequentie van eenmaal per maand, terwijl uw blog- of nieuwspagina een updatefrequentie van eens per dag of eens per week kan hebben, afhankelijk van hoe vaak u nieuwe inhoud toevoegt.

### HTML Sitemaps

Een HTML-sitemap is in wezen een inhoudsopgave voor uw site die u beschikbaar kunt maken voor bezoekers van uw website. Dit dient twee doelen:

1.  Het biedt bezoekers een plek waar ze gemakkelijk bij alle content op uw site kunnen komen, zelfs als die niet noodzakelijkerwijs makkelijk toegankelijk is met andere navigatiehulpmiddelen op de site
2.  Het biedt een gecentraliseerde opslagplaats van links naar de content op uw site die eenvoudig geïndexeerd kan worden door zoekmachines
3.  Het stelt gebruikers met een handicap in staat om snel door uw website te navigeren met een eenvoudige lijst van links, in plaats van door complexe menu's

Tenminste, een sitemap moet linken naar de hoofdsecties en pagina's binnen uw site, maar hoe gedetailleerder u het kunt maken, hoe beter.

Er zijn eerder genoemde extensies beschikbaar die automatisch sitemaps maken op basis van Joomla-content.

### XML Sitemaps

XML-sitemaps zijn een gemakkelijke manier voor webmasters om zoekmachines te informeren over nieuwe en bestaande pagina's op hun sites die beschikbaar zijn voor crawling. In zijn eenvoudigste vorm is een sitemap een XML-bestand dat URL's voor een site opsomt, samen met aanvullende metadata over elke URL (wanneer het voor het laatst is bijgewerkt, hoe vaak het gewoonlijk verandert, en hoe belangrijk het is, ten opzichte van andere URL's op de site) zodat zoekmachines de site intelligenter kunnen crawlen.

Het gebruik van het sitemapprotocol garandeert niet dat webpagina's in zoekmachines worden opgenomen, maar biedt aanwijzingen voor webcrawlers om het crawlen van uw site beter te doen.

1.  Een XML-sitemap biedt een lijst van links naar de content op uw site die gemakkelijk kan worden geïndexeerd door zoekmachines
2.  Het is mogelijk om specifieke XML-sitemaps te maken voor Nieuws, Mobiele URL's, Afbeeldingen en Video

Er zijn beschikbare extensies die automatisch XML-sitemaps maken op basis van Joomla-content.

*Vertaald door openai.com*

