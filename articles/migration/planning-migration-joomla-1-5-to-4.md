<!-- Filename: Planning_Migration_-_Joomla_1.5_to_4 / Display title: Het plannen van een migratie - Joomla 1.5 naar 3 -->

Het gaan van Joomla! 1.5 naar 3.x wordt beschouwd als migratie of grote
migratie. Dit betekent dat er aanzienlijke aanpassingen in hoe Joomla
werkt, tabellen en technologie zijn opgetreden, die een migratie vragen
in plaats van een upgrade of update. Zowel, de Joomla core extensies als
elke extensie van derden moet migreren naar Joomla 3.x. Dit omvat ook
het template. Er moet naar ieder individueel ding gekeken worden,
gepland, over besloten, en uitgevoerd. U moet zorgvuldig zijn en tijdens
het hele proces georganiseerd blijven.

# Introductie

Het prachtige aan een migratie is, dat het een goed moment is om doelen
te evalueren, een nieuwe look-and-feel (template) creëren, opschonen en
andere gebieden/elementen van uw site te ontwikkelen. Hoe
georganiseerder u bent met ideeën - gedachten - plannen hoe beter. Plan,
plan, plan. Het plannen maakt de uitvoering eenvoudiger.

Start met plannen door de volgende vragen te stellen of door
onderstaande taken uit te voeren. U heeft misschien meer items te
plannen afhankelijk van de complexiteit van uw site. Helaas kunnen we
niet ieder mogelijk scenario noemen.

{{{1}}}

## Plannen van acties

### Algemeen

1.  Beoordeel uw oorspronkelijke site doelstellingen. Migratie is een
    gelegenheid om je opnieuw te focussen op uw doelstellingen of van
    richting te veranderen.
2.  Voldoet uw server aan de minimum
    <a href="http://www.joomla.org/about-joomla/technical-requirements.html"
    class="external text" target="_blank"
    rel="noreferrer noopener">technische verweisten</a> voor Joomla 3?
    Indien niet, dan moet u van hoster veranderen. Geen beter moment om
    te veranderen van host als tijdens een migratie.
3.  Wat voor ontwikkelomgeving gaat u gebruiken? Een ontwikkelomgeving
    op een lokale omgeving? Een subdomein of submap op uw server? Een
    nieuw server/hosting account door technische specificaties?

### Joomla core

1.  Schoon uw huidige site op. Kijk bij uw secties, categorieën, en
    artikelen. Secties worden geconverteerd naar de hogere categorieën
    van Joomla 2.5 en hoger. Moet er een opschoon-actie worden
    uitgevoerd zodat u geen niet-noodzakelijke inhoud migreert?
    Documenteer wat u wilt verwijderen. Als alternatief kunt u
    documenteren wat u wilt overbrengen afhankelijk van de hoeveelheid.
2.  Organiseer uw inhoud op de huidige site. Zijn de categorieën die u
    heeft nog van toepassing? Documenteer nieuwe categorieën die u wilt
    toevoegen op uw nieuwe site.
3.  Heeft u nog artikelen in de prullenbak? Als dat zo is, verwijder ze
    (en eventueel gekoppelde media als ze niet elders op de site
    gebruikt worden). Artikelen (ook categorieën en menu-items) die in
    de prullenbak staan kunnen dubbele alias problemen veroorzaken na de
    migratie.
4.  Mediabeheer: Besluit of u uw hele /images map wilt overbrengen of
    slechts een deel ervan. Als Mediabeheer een ramp is geworden, kunt u
    besluiten specifieke afbeeldingen via FTP of cPanel over te brengen
    in plaats van de hele map te migreren. Organiseer in de toekomst
    mappen in Mediabeheer zodat u niet met een grote puinhoop eindigt.
5.  Als u core componenten zoals Joomla Contacten, WebLinks, of
    Nieuwsfeeds gebruikt, documenteer ze dan als u ze migreert.
6.  Controleer uw menu's en bepaal of u ze allemaal overbrengt of alleen
    specifieke menu's en menu-items. Verwijder ieder menu-item uit de
    prullenbak om dubbele aliassen te voorkomen.
7.  Als u uw site herontwerpt of wijzigingen aan het ontwerp of
    navigatie van de site aanbrengt, ontstaan er dan verouderde pagina's
    die een verwijzing nodig hebben? Houd alle URLs bij die een
    verwijzing nodig hebben in een spreadsheet of kladblok.
1.  Heeft u “de core gehackt” van uw 1.5 site? Als dat zo is, dan worden
    deze aanpassingen niet gemigreerd naar Joomla 3. U zult
    alternatieven willen vinden voor het hacken van de core van Joomla 3
    (<a
    href="https://docs.joomla.org/How_to_override_the_output_from_the_Joomla!_core"
    class="new"
    title="Special:MyLanguage/How to override the output from the Joomla! core (page does not exist)">Hoe
    de uitvoer van de Joomla! core overriden</a>, [Het begrijpen van
    output
    overrides](https://docs.joomla.org/Understanding_Output_Overrides "Special:MyLanguage/Understanding Output Overrides"),
     Layout overrides in
    Joomla.
2.  Controleer uw gebruikers 'Beheerder'. Bnet u van plan ze allemaal
    over te brengen? Is er een opschoon actie noodzakelijk? Misschien
    Super gebruikers die geen toegang meer moeten hebben of spam
    gebruikers die verwijderd moeten worden? Gebruikt u extensies van
    derden die de gebruikersprofielen verbeteren? Dit deel vraagt een
    zorgvuldige planing. Vooral als de gebruikersgegevens vaak wijzigen.
3.  Zijn er nieuwe functies in Joomla die u wilt gebruiken, zoals Access
    Control Levels (ACL's) of tags? Als dat zo is, begin dan nu met
    plannen. Het plannen van ACL's is een behoedzame zaak. Grondigheid
    is erg belangrijk.

### Extensies van derden

1.  Maak een lijst met alle extensies van derden die gebruikt worden.
    Dit omvat componenten, modules, plugins, talen, en templates. U kunt
    het <a
    href="https://docs.joomla.org/images/5/59/Third-Party_Extension_Inventory_Worksheet.pdf"
    class="external text" target="_blank"
    rel="noreferrer noopener">Extensies van derden inventarisatie
    werkblad</a> gebruiken of ze alleen kopieëren/plakken in een
    document ter referentie als u dat wil. Een stuk papier en een pen
    zijn voldoende. Neem ook op of de extensie zwaar, gemiddeld,
    nauwelijks of helemaal niet gebruikt wordt.
1.  Bepaal of de extensie van derden die u gebruikt klaar is voor de
    Joomla versie waar uw naartoe migreert.
2.  Bepaal of u echt alle extensies nodig heeft die u gebruikt.
    Misschien is het dat Joomla 3 een ingebouwde functie heeft die het
    gebruik van een extensie voor derden overbodig maakt?
3.  Iets over uw template. Indien u uw template van een derde heeft, is
    er een 3.x versie voor uitgebracht? Wilt u hem blijven gebruiken? Is
    er een migratie-pad gepubliceerd door de ontwikkelaar? Is de nieuwe
    versie responsive? Is uw template een aangepast template? Of is het
    een sterk aangepast template van derden? Zie, voor uitgebreide
     Template overwegingen tijdens
    migraties.
1.  Als u uw template inwisselt voor een nieuwe, heeft het dan nieuwe
    afbeeldingen nodig? Bijvoorbeeld, als uw huidige site een witte
    achtergrond heeft en uw logo en andere afbeeldingen zijn .jpg
    afbeeldingen met een witte achtergrond ziet het er niet mooi uit in
    een nieuw template met een gebroken witte of gekleurde achtergrond.

<a
href="https://docs.joomla.org/Joomla_1.5_to_4.x_Step_by_Step_Migration"
id="content-button" class="button expand">Joomla 1.5 to 4.x Step by Step
Migration</a>
