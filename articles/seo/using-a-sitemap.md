<!-- Filename: Using_A_Sitemap / Display title: Een sitemap gebruiken -->

## Een sitemap gebruiken

Terwijl zoekmachines uw pagina's normaal kunnen vinden door de manier
waarop ze met elkaar gelinkt zijn op het internet, is het goede praktijk
om een Sitemap te creëren die de zoekmachine 'bots' een lijst geeft met
de pagina's van uw website - zie het als een kaart om alle content op uw
website te kunnen vinden.  
Sitemaps zijn niet alleen belangrijk voor zoekmachines, ze zijn ook erg
nuttig voor mensen met een handicap die misschien een eenvoudige
interface nodig hebben om uw websitestructuur te zien en te navigeren
zonder de menustructuur te gebruiken.
<a href="https://www.w3.org/TR/WCAG20-TECHS/G63.html"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">W3C Working Group Notitie over
sitemaps</a>  

Een sitemap dient verschillende doelen:

- Zorgt voor een gestructureerde lijst met een overzicht van alle
  content op uw website
- Kan een bezoeker snel een overzicht laten zien van uw websitestructuur
- Biedt een alternatieve manier van op uw website navigeren zonder de
  noodzaak van complexe menustructuren
- Biedt zoekmachines een manier van het vinden van content die niet via
  uw menustructuur beschikbaar is (b.v. landing pagina's)

### Soorten sitemaps

Het is mogelijk om sitemaps voor specifieke soorten informatie aan te
bieden, zoals:

- Video <a href="https://support.google.com/webmasters/answer/80471"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">Google help voor video-sitemaps</a>
- Afbeeldingen <a
  href="https://support.google.com/webmasters/answer/answer.py?answer=178636"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">Google help voor
  afbeelding-sitemaps</a>
- Nieuws
  <a href="https://support.google.com/news/publisher/answer/75717"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">Google help voor nieuws-sitemaps</a>
- Internationaal <a
  href="https://support.google.com/webmasters/answer/2620865?hl=en&amp;ref_topic=2370587"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">Google help voor internationale
  sitemaps</a>

Met deze gespecialiseerde sitemaps kunt u informatie verstrekken over de
specifieke mediatypes - bijvoorbeeld met een video-sitemap kunt u
informatie geven over de looptijd, categorie en kindvriendelijkheid; met
afbeelding-sitemaps kunt u het onderwerp specificeren, de licentie
waarvoor de afbeelding gebruikt mag worden en het soort afbeelding.

### Een sitemap maken

Op een statische website is het creëren van een sitemap het eenvoudig
aanmaken van een XML-bestand, volgens de standaardnormen, en het als een
XML-bestand op te slaan. Op een dynamische website, waar content
regelmatig verandert, is dit niet echt een optie - u zou bij nieuwe
content deze elke keer handmatig moeten bijwerken!

Hierdoor zijn er verschillende sitemap extensies beschikbaar in de
Joomla! Extensions Directory (<a
href="https://extensions.joomla.org/category/structure-a-navigation/site-map"
class="external text" target="_blank" rel="noreferrer noopener">Sitemap
categorie op Joomla Extensions Directory</a>) waarmee u dynamisch een
sitemap kan maken die voldoet aan de standaard normen die worden
verwacht door de zoekmachines.
<a href="https://www.sitemaps.org/" class="external text"
target="_blank" rel="nofollow noreferrer noopener">Sitemaps protocol</a>

De meeste extensies werken door het kiezen van menu-items die u in de
sitemap wilt opnemen, en te specificeren hoe vaak deze wijzigen (zie
Frequentie updates). Het is ook mogelijk om sub-pagina's van deze
menu-items toe te voegen (bijvoorbeeld, een menu-item kan naar een
categorie-blog verwijzen, maar u wilt alle artikelen die op die pagina
getoond worden als individuele items laten zien - een ander voorbeeld
kan een menu-item zijn die naar een webwinkel categoriepagina verwijst,
en in de sitemap wilt u deze categorie tonen, en dan elk product hier in
als apart link).

### Frequentie updates

Terwijl u in uw sitemap handmatig kan specificeren hoe vaak zoekmachine
spiders uw website kunnen bezoeken, hebben de meeste zoekmachines een
ingebouwd systeem die automatisch de frequentie van bezoeken baseert op
hoe vaak de pagina in kwestie is veranderd.

Dus, bijvoorbeeld, kunt u de zoekmachine vertellen dat de bots uw pagina
dagelijks kunnen bezoeken, ze deze frequentie van herhalingsbezoeken
overeenkomstig aanpassen en niet zo vaak terug komen als u ze hebt
verteld.

Dit zou suggereren dat als u regelmatig veranderde content heeft, uw
website vaker een herhalingsbezoek krijgt - waardoor de inhoud vaker en
sneller wordt geïndexeerd dan websites die niet zo vaak wijzigen.

Het is over het algemeen verstandig om statische pagina's te
specificeren die minder regelmatig gecrawld hoeven te worden.
Bijvoorbeeld, een statische artikel kan worden ingesteld op maandelijks
bezoeken, terwijl uw blog of nieuwspagina ingesteld kan worden op
dagelijks of wekelijks bezoeken, afhankelijk van hoe vaak nieuwe inhoud
toegevoegd wordt.

### HTML Sitemaps

Een HTML-sitemap is in feite een inhoudsopgave voor uw website die u
beschikbaar kan maken voor de bezoekers van uw website. Dit dient twee
doelen:

1.  Het biedt een plek waar bezoekers makkelijk alle inhoud van uw
    website kunnen vinden, ook al is het niet noodzakelijk makkelijk om
    door een andere navigatiehulpmiddel op uw website te benaderen.
2.  Het biedt een gecentraliseerde plek met links naar content op uw
    website die makkelijk door zoekmachines geïndexeerd kunnen worden
3.  Het helpt gebruikers met een handicap om op uw website makkelijk te
    navigeren met een simpele lijst van links, dan door een complexe
    menustructuur

Op zijn minst zal een sitemap naar de hoofdcategorieën en pagina's op uw
website linken, maar hoe gedetailleerder de sitemap is, hoe beter het
is.

Er zijn extensies beschikbaar, zoals eerder vermeld, die sitemaps
automatisch creëren op basis van Joomla content.

### XML Sitemaps

XML Sitemaps zijn een makkelijke manier voor webmasters om zoekmachines
te informeren over nieuwe en bestaande pagina's op hun websites die
beschikbaar zijn voor crawling. Op zijn eenvoudigst is een sitemap een
XML-bestand met een lijst van URL's van een website samen met de
metagegevens van elke URL (wanneer het voor het laatst is bijgewerkt,
hoe vaak deze meestal wijzigt, hoe belangrijk deze is, relatief naar
andere URL's van deze website). zodat zoekmachines intelligenter de
website kunnen crawlen.

Een sitemap gebruiken garandeert niet dat pagina's in zoekmachines
worden opgenomen, maar biedt wel tips voor webcrawlers om uw website
beter te kunnen doorzoeken.

1.  Een XML sitemap biedt een overzicht van links naar de content van uw
    website die makkelijk door zoekmachines geïndexeerd kan worden
2.  Het is mogelijk om een specifieke XML sitemap te maken voor nieuws,
    mobiele URL's, afbeeldingen en video

Er zijn extensies beschikbaar die XML sitemaps automatisch creëren
gebaseerd op Joomla content
