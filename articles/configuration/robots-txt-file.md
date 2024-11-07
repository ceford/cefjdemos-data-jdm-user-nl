<!-- Filename: Robots.txt_file / Display title: Het robots.txt-bestand  -->

## Over Robots

Webrobots, ook bekend als crawlers, webzwervers of spiders, zijn programma's die automatisch het web doorzoeken. Ze worden onder andere gebruikt door zoekmachines om webinhoud te indexeren.

Het robots.txt-bestand implementeert het [Robots Exclusion Protocol](https://nl.wikipedia.org/wiki/Robots.txt), waarmee een websitebeheerder kan bepalen welke delen van de site niet mogen worden geïnspecteerd door specifieke robotgebruikersagenten. Toegang tot de inhoud van openbare pagina's is bijvoorbeeld normaal toegestaan, maar toegang tot cgi, privé en tijdelijke mappen waarvan de pagina's niet moeten worden geïndexeerd, wordt vaak geweigerd.

## Waar de *robots.txt* File te Plaatsen

Een standaard *robots.txt* file is inbegrepen in de Joomla-root. De
*robots.txt* file moet in de hoofdmap van het domein of subdomein staan en
moet `robots.txt` genoemd worden.

### Joomla in een Subdirectory

Een robots.txt bestand dat zich in een subdirectory bevindt, is niet geldig. Robots
controleren dit bestand alleen in de root van het domein. Als de Joomla-website
is geïnstalleerd binnen een subdirectory zoals *example.com/joomla/*, moet de
*robots.txt* file **verplaatst** worden naar de site-root op
*example.com/robots.txt*.

**Opmerking:** In het robots.txt bestand moet de subdirectory naam **voorafgaan** aan alle
niet-toegestane Joomla paden. Bijvoorbeeld, de uitsluitingsregel voor de `/administrator/`
directory moet worden aangepast naar `Disallow: /joomla/administrator/`.  

## Joomla *robots.txt* Inhoud

Dit is de inhoud van een [standaard Joomla robots.txt-bestand](https://raw.githubusercontent.com/joomla/joomla-cms/refs/heads/5.2-dev/robots.txt.dist):

```
# Als de Joomla-site in een map is geïnstalleerd
# bijvoorbeeld www.voorbeeld.com/joomla/ dan moet het robots.txt-bestand
# verplaatst worden naar de site root
# bijvoorbeeld www.voorbeeld.com/robots.txt
# EN de joomla mapnaam MOET worden voorgevoegd aan al de
# paden.
# bijvoorbeeld de Disallow-regel voor de map /administrator/ MOET
# gewijzigd worden naar
# Disallow: /joomla/administrator/
#
# Voor meer informatie over de robots.txt standaard, zie:
# https://www.robotstxt.org/orig.html

User-agent: *
Disallow: /administrator/
Disallow: /api/
Disallow: /bin/
Disallow: /cache/
Disallow: /cli/
Disallow: /components/
Disallow: /includes/
Disallow: /installation/
Disallow: /language/
Disallow: /layouts/
Disallow: /libraries/
Disallow: /logs/
Disallow: /modules/
Disallow: /plugins/
Disallow: /tmp/
```

## Uitsluiting van Robots

Je kunt directories uitsluiten of robots blokkeren van je site door een Disallow-regel toe te voegen aan het *robots.txt* bestand. Om bijvoorbeeld te voorkomen dat robots de */tmp* directory bezoeken, voeg je deze regel toe:

    Disallow: /tmp/

Zie ook:

- [Toegang tot je inhoud blokkeren](https://support.google.com/webmasters/topic/4598466?hl=nl&amp;ref_topic=9427949) op het Helpcentrum van Google.

## Syntaxcontrole

Voor syntaxcontrole kun je een validator voor *robots.txt* bestanden gebruiken. Probeer een van de volgende:

- [Test je <em>robots.txt</em> met de robots.txt Tester](https://support.google.com/webmasters/answer/6062598) bij Google.
- [<em>robots.txt</em> Checker](http://www.searchenginepromotionhelp.com/m/robots-text-tester/robots-checker.php) van Search Engine Promotion Help.

### Algemene Informatie

- [The Web Robots Pages](http://www.robotstxt.org/) is de hoofdwebsite voor *robots.txt*.
- [A Standard for Robot Exclusion](http://www.robotstxt.org/orig.html) is de originele standaard.
- [Specifications van de robots meta tag, data-nosnippet, en X-Robots-Tag](https://developers.google.com/search/docs/advanced/robots/robots_meta_tag)

*Vertaald door openai.com*

