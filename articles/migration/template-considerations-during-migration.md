<!-- Filename: Template_Considerations_During_Migration / Display title: Template-overwegingen tijdens een migratie -->

<img
src="https://docs.joomla.org/images/thumb/4/47/Copyedit.png/25px-Copyedit.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/4/47/Copyedit.png/38px-Copyedit.png 1.5x, https://docs.joomla.org/images/thumb/4/47/Copyedit.png/50px-Copyedit.png 2x"
data-file-width="200" data-file-height="200" width="25" height="25"
alt="Copyedit.png" />This Article Needs Your Help

*This article is tagged because it* **NEEDS UPDATING***. You can help
the Joomla! Documentation Wiki by <a
href="https://docs.joomla.org//docs.joomla.org/index.php?title=Template_Considerations_During_Migration/nl&amp;action=edit"
class="external text" target="_blank"
rel="noreferrer noopener">contributing to it</a>.
<span class="small">More pages that need help similar to this one are
here.</span>
<span class="small">**NOTE-If you feel the need is satistified, please
remove this notice.**</span>*
**Reason:** See section 3.4 and 4

Templates verwarren mensen tijdens een migratie. Dat hoeft niet. Met een
beetje uitleg wordt duidelijk wat je mogelijkheden zijn.

## Introductie

Templates zijn een extensie. Net zo als componenten, modules, en plugins
extensies zijn, zijn templates dat.

Tijdens het voorbereiden van een migratie moet u besluiten wat u gaat
doen met het huidige template (wat de huidige “look-and-feel” van uw
site bepaalt).

Voor het grootste deel valt uw template scenario in een van onderstaande
opties:

- U gebruikt een template dat aangeschaft is bij een template-club.
- U gebruikt een template dat eenmalig aangeschaft is bij een template
  aanbieder.
- U heeft een aangepast template voor u laten ontwikkelen.
- U gebruikt een standaard template dat met uw Joomla installatie mee
  kwam (Joomla! 1.5 standaard templates zijn Rhuk_milkyway, JA Purity,
  Beez en Joomla! 2.5 standaard templates zijn Atomic en twee
  verschillende versies van Beez). Het kan sterk aangepast zijn of
  helemaal niet.

## Beoordeel uw Template-scenario

Voor te beslissen wat te doen, moet u beoordelen of u de bestaande
uitstraling van uw huidige website wilt behouden. Als u wilt veranderen,
dan is dit het tijdstip om dat te besluiten. Misschien is de grootste
reden om van template te veranderen om nieuwere technieken te gebruiken
in de huidige templates. Responsive templates waren niet beschikbaar in
1.5 (behalve als u recent iemand ingehuurd heeft om uw 1.5 template
mobiel-vriendelijk te maken) en zelfs aan het begin van de 2.5
levenscyclus waren mobiele versies van templates nog niet erg slank en
responsive.

Laten we deze scenario's één voor één nemen:

### You are using Protostar

Protostar is not compatible with Joomla 4.x. The migration will work on
the one-click from Joomla 3.10.x to 4.x but the template will disappear
and be replaced with Cassiopeia upon migration. You will need to plan on
using Cassiopeia or some other template in Joomla 4.

#### Why can't you carry forward Protostar into Joomla 4?

Protostar is based on an old version of Bootstrap (Bootstrap 2) and
jQuery (1.x). The versions of these components are outdated and have
known security issues (Joomla 3 maintained forked versions of these
libraries with security patches applied) - and Joomla 4 has updated
these to the latest version - Bootstrap 5. However this means that
templates need to be updated to use the new HTML syntax that Bootstrap 5
requires.

### U gebruikt een template dat aangeschaft is bij een template-club

Dit is de makkelijkst - meestal. Ga, als u een template van een
template-club heeft aangeschaft, terug naar het bedrijf en kijk of ze
een versie van uw template voor Joomla 3.x hebben. Als dat zo is,
geweldig, met een paar zaken om aan te denken. Controleer, als u met 1.5
werkt en naar 3.x gaat, of de versie voor Joomla 3 responsive is, als
dat belangrijk voor u is. Als u van 1.5 naar 3 gaat dan is de kans groot
dat er wat verschillen zijn tussen de 1.5 versie van het template en de
3 versie van het template. Wees voorbereid enkele aanpassingen te moeten
maken aan het template als het er *exact* hetzelfde moet uitzien.

Controleer, als u van 2.5 naar 3.x gaat, of de 2.5 en 3.x versies in
hetzelfde pakket zitten. Controleer, als dat niet zo is, bij de
ontwikkelaar de stappen om te upgraden van Joomla 2.5 naar 3.x. Als 2.5
en 3.x in hetzelfde pakket zitten, ben je een goudhaantje. Als dat niet
zo is, kan dat ook nog. Het hangt af van het upgrade-pad van de
ontwikkelaar.

### U gebruikt een template dat eenmalig aangeschaft is bij een template-ontwikkelaar

Ga, indien u een template heeft aangeschaft bij een template-aanbieder
als eenmalige aankoop, terug naar het bedrijf en kijk of er een versie
beschikbaar is voor Joomla 3.x. Als die er niet is, dan heeft u geen
geluk. U kunt toch contact proberen op te nemen met het bedrijf om te
kijken of ze het voor u kunnen updaten en compatibel voor Joomla 3.x
maken.

Als dat niet lukt, moet u kiezen:

1.  Een nieuw template kiezen.
2.  Het template converteren om compatibel te zijn met Joomla 3.x. (Let
    op: kan niet responsive zijn.)

Het eerste spreekt voor zich. U kunt een template kiezen van een
commerciële aanbieder of het standaard Protostar template aanpassen (zie
meer over Protostar hieronder) dat meegeleverd wordt met Joomla 3.x. Het
2e is niet zo eenvoudig. Kijk, om uw bestaande template te converteren
om compatibel met Joomla 3 te zijn, in de volgende paragraaf.

## Template conversies of migraties

### Template conversies van 1.5 naar 3

-  Een Template van Joomla 1.5 naar 3.x
  migreren

### Template conversies van 1.5 naar 2.5

-  Een Joomla 1.5 template upgraden naar Joomla
  2.5
- <a
  href="http://magazine.joomla.org/issues/issue-may-2012/item/740-How-to-convert-Joomla-15-template-to-Joomla-25"
  class="external free" target="_blank"
  rel="noreferrer noopener">http://magazine.joomla.org/issues/issue-may-2012/item/740-How-to-convert-Joomla-15-template-to-Joomla-25</a>

### Template conversies van 2.5 naar 3

-  Een template uit een eerdere Joomla! versie
  converteren
- <a
  href="http://stackoverflow.com/questions/16055707/convert-joomla-2-5-template-to-3-0"
  class="external free" target="_blank"
  rel="nofollow noreferrer noopener">http://stackoverflow.com/questions/16055707/convert-joomla-2-5-template-to-3-0</a>
- <a href="https://www.youtube.com/watch?v=E13QMWgvwlA"
  class="external free" target="_blank"
  rel="nofollow noreferrer noopener">https://www.youtube.com/watch?v=E13QMWgvwlA</a>

### 3.10.x to 4 Template Conversions

This section needs content. If you have knowledge on converting
templates built for Joomla 3 to make them compatible with Joomla 4,
please write a magazine article or post a YouTube or something that can
be linked from this area. Thanks in advance.

### U had een aangepast template voor u laten ontwerpen

Als u een aangepast template voor u had laten ontwikkelen voor uw 1.5 of
2.5 site, dan moet het geconverteerd worden om compatibel met Joomla 3
te worden. Zie links in de voorgaande paragraaf. Bekijk, als u iemand
moet inhuren om uw bestaande template te converteren om compatibel met
Joomla 3.x te zijn, de Joomla! Resource Directory in óf de
<a href="https://resources.joomla.org/en/category/custom-templates"
class="external text" target="_blank" rel="noreferrer noopener">Template
ontwikkeling</a> óf de <a
href="http://resources.joomla.org/en/category/migration-and-upgrade-services"
class="external text" target="_blank" rel="noreferrer noopener">Migratie
&amp; upgrades</a> categorie.

### U gebruikt een standaard template dat met uw Joomla installatie mee kwam

Standaard Joomla! 1.5 templates zijn Rhuk_milkyway, JA Purity, en Beez.
Standaard Joomla! 2.5 templates zijn Atomic en twee verschillende
versies van Beez. Ze kunnen sterk aangepast zijn of in het geheel niet.
Als u een standaard 2.5 template gebruikt en naar Joomla 3.x gaat, kunt
u een één-klik update doen. Als u een standaard 1.5 template gebruikt,
dan moet u één van bovengenoemde stappen moeten doorlopen om hem te
updaten naar Joomla 3.x. (Als iemand deze informatie niet juist vindt,
draag dan bij en corrigeer dit).

Voor te beslissen of u uw 1.5 template wilt converteren naar Joomla 3,
moet u serieus overwegen een nieuw template te vinden dat lijkt op uw
bestaande template. De kans is dat het is een stuk goedkoper en sneller
om een nieuwe te gebruiken dan een oude te converteren. Bezoek, als u de
oude wilt converteren en u heeft niet de vaardigheden om het zelf te
doen, de <a
href="http://resources.joomla.org/en/category/migration-and-upgrade-services"
class="external text" target="_blank" rel="noreferrer noopener">Joomla!
Resource Directory™</a>.

Protostar, the template that ships with Joomla 3.x is **not** compatible
with Joomla 4.x. You will need to go through one of the steps above to
update it for Joomla 4.x.

### Bij het kiezen van templates

- Kijk naar slechts één template-aanbieder tegelijkertijd anders wordt
  het overweldigend
- Neem, als u overweldigd raakt, een pauze zelfs als dat een volgende
  dag betekent
- Probeer voorbij de drukke en flitsende demo's te kijken. U plaats uw
  inhoud in de template, u gebuikt niet alles wat het template kan.
- Kijk naar de module posities en varianten van de templates
- Drink genoeg water als u naar templates kijkt en stretch ongeveer
  ieder uur.

## Het gebruiken van het Protostar standaard template in Joomla 3.x

Deze paragraaf is niet compleet. Draag, als u kennis van dit onderwerp
heeft, bij door dit document aan te vullen. In de tussentijd zal een
Google zoekopdracht op 'customising Protostar' veel resultaat opleveren
buiten Joomla! Docs.
