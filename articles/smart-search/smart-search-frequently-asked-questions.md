<!-- Filename: Smart_Search_Frequently_Asked_Questions / Display title: Veelgestelde Vragen over Slim Zoeken -->

## Waarom Zou Ik Slim Zoeken Gebruiken?

Zoektechnologie is in de loop der jaren aanzienlijk verbeterd sinds Joomla voor het eerst werd gelanceerd en toch is het standaard, basiszoekcomponent in die tijd niet veel veranderd. Het is nog steeds erg eenvoudig en mist de soort zoekfuncties die webgebruikers zijn gaan verwachten, vooral gezien de alomtegenwoordigheid van geavanceerde zoekmachines zoals Google. Slim Zoeken stelt je in staat om enkele van die meer geavanceerde zoekfuncties in je website op te nemen.

## Waarom Een Slimme Zoekplugin Maken?

Over het algemeen, als je een type inhoud hebt dat niet wordt afgehandeld door de kerncomponenten van Joomla, en je wilt je sitebezoekers de mogelijkheid geven om in die inhoud te zoeken, zul je een Slimme Zoekplugin moeten schrijven om dit te ondersteunen. Stel bijvoorbeeld dat je een component hebt die informatie opslaat over verschillende diersoorten. De component onderhoudt een databasetabel met velden zoals wetenschappelijke naam, volkse naam, classificatie en een beschrijving. Dan moet je een Plugin maken die de Slimme Zoekindexering vertelt hoe de gegevens in die tabel geïndexeerd moeten worden. Naast het indexeren van individuele woorden en zinnen, kun je ook de Plugin laten zorgen dat elke record wordt toegevoegd aan een inhoudskaart, die in dit geval wellicht de <a href="https://en.wikipedia.org/wiki/Taxonomy_(biology)" rel="nofollow noreferrer noopener">biologische classificaties koninkrijk, stam, klasse, orde en familie</a> omvat. Inhoudskaarten kunnen vervolgens worden gebruikt om zoekresultaten te filteren.

## Kunnen Meerdere Nodes Geselecteerd Worden uit de Filterkeuzelijsten?

Ja, dit wordt volledig ondersteund door Smart Search zelf. Je kunt
daadwerkelijk elke gebruikersinterface gebruiken die je wilt ontwerpen voor de filters. Bekijk gewoon de code in de standaard Frontend-module en -component, en je zult zien hoe je het moet doen.

## Ik Heb een Grote Website. Kan Ik Smart Search Gebruiken?

Grote websites zijn wellicht beter af met een toegewijde, zelfstandige zoekmachine, zoals Solr, in plaats van de pure PHP-implementatie die in Smart Search wordt gebruikt. In deze eerste iteratie van geavanceerd zoeken in Joomla is het waarschijnlijk dat er problemen met schaalbaarheid en prestaties aan het licht zullen komen. Er is ook de mogelijkheid dat er racecondities optreden bij het bijwerken van de index tijdens frequente inhoudsveranderingen. Verwacht wordt dat deze problemen in een toekomstige versie van Joomla uitgebreider worden aangepakt.

## Waarom Heeft Smart Search Zo Veel Tabellen?

Smart Search voegt behoorlijk wat nieuwe tabellen toe aan een Joomla-installatie, waaronder 16 "mapping-tabellen". Deze mapping-tabellen lossen de veel-op-veelrelatie op tussen zoektermen en de inhoudselementen die ze bevatten. In theorie zouden die 16 tabellen samengevoegd kunnen worden tot één enkele tabel, en op kleine sites zou dat een verwaarloosbare impact hebben. Echter, op grotere sites zou er een aanzienlijke impact zijn op de prestaties, omdat de mapping-tabel een zeer groot aantal vermeldingen zou hebben en het bijwerken van zo'n grote tabel tijdrovend kan zijn.

## Waarom Gebruikt Slim Zoeken Zoveel Schijfruimte?

Het bijhouden van een zoektermenindex vereist een aanzienlijke hoeveelheid schijfruimte, die toeneemt naarmate de inhoudselementen meer termen bevatten. Aangezien zinnen ook worden geïndexeerd, geldt dat hoe langer de zinnen zijn, hoe meer schijfruimte er nodig is. Voor Slim Zoeken in Joomla 2.5 is de maximale lengte van een zin vastgezet op 3 termen als een redelijk compromis tussen zoekgebruiksvriendelijkheid en schijfruimtegebruik. Het is waarschijnlijk dat dit een parameter zal zijn die in een toekomstige versie van Slim Zoeken kan worden aangepast.

## Waarom Zijn de Invoeren in de Toewijzingstabellen Niet Uniform Verdeeld?

Het is misschien verrassend dat het aantal invoeren in elk van de toewijzingstabellen niet eens ruwweg hetzelfde is. Zou de prestatie niet verbeterd worden met een uniforme verdeling? Eigenlijk niet, er is een afweging tussen invoerprestatie en zoekprestatie waarbij een uniforme verdeling goed is voor het eerste maar slecht voor het laatste. Dit is een gebied van voortdurend onderzoek waarbij het aantal tabellen en het verdelingsalgoritme onderhevig zijn aan veranderingen in het licht van ervaring.

## Waarom is er een Apart Smart Search Content - Plugin?

Dit is gewoon een gemak dat het gemakkelijker maakt om alle Smart Search Plugins met één handeling in of uit te schakelen. Dit werd als wenselijk beschouwd omdat Smart Search niet standaard is ingeschakeld in Joomla 2.5.

## Waarom Gebruiken Slimme Zoekplugins Aparte Gebeurtenissen zoals *onFinderContentAfterSave*?

Slimme Zoekfunctie gebruikt zijn eigen gebeurtenissen, zoals onFinderContentAfterSave, in plaats van de algemene tegenhanger onContentAfterSave, puur als gemak om het gemakkelijk te maken Slimme Zoekindexering in of uit te schakelen door een enkele plugin in of uit te schakelen.

## Waarom is Slimme Zoekopdracht niet standaard ingeschakeld in Joomla 2.5 en Joomla 3.x?

Omdat Joomla 2.5 de laatste in de 1.x/2.x serie is, moet het een hoge mate van achterwaartse compatibiliteit handhaven met de vorige release in de serie. Aangezien Slimme Zoekopdracht iets geheel nieuws is en geen enkele gelijkenis vertoont met de reguliere zoekcomponent van deze of eerdere releases, werd het belangrijk geacht dat gebruikers die upgraden van die eerdere versies niet gedwongen zouden worden om de manier waarop zoeken werkt op hun sites te veranderen. Inderdaad, de activering van Slimme Zoekopdracht is iets dat op een zorgvuldig overwogen manier dient te gebeuren.

## Waarom is er geen Search API?

De focus van de huidige versie van Smart Search lag op het verplaatsen van code van de oude JXtended Finder-component naar de nieuwste versie van Joomla. Aangezien die code al als stabiel werd beschouwd en er slechts een kort tijdsbestek was om de code over te zetten, werd het gevoel dat een grote herontwikkeling van Finder buiten het bestek van de Joomla 2.5-release viel. Daarom gebruikt de code Plugins om wijzigingen aan de kern van de CMS-code te vermijden, in plaats van een echte zoek-API te ontwikkelen. We zullen proberen om een dergelijke API te creëren voor een toekomstige iteratie van Joomla.

## Kan Slim Zoeken Geavanceerd Zoeken Uitvoeren?

Ja. De geavanceerde zoekfunctie beschikbaar op de zoekresultatenpagina en de slimme zoekmodule bieden een voorbeeld van hoe je zoekresultaten kunt filteren om geavanceerd zoeken mogelijk te maken. Er is niets dat je ervan weerhoudt om je eigen variaties op deze basisideeën te creëren. Je zou bijvoorbeeld de eenvoudige keuzemenu's kunnen aanpassen om meerdere selecties toe te laten, of je zou de keuzemenu's kunnen vervangen door een reeks selectievakjes.  

## Waarom Worden Wildcard-zoekopdrachten Niet Ondersteund?

De oude Joomla-zoekfunctie gebruikte een zeer primitieve manier van zoeken die was gebaseerd op de FULLTEXT-zoekfunctie die door de database werd geleverd. Dit was zeer inefficiënt, maar bood een eenvoudige manier om wildcard-zoekopdrachten af te handelen. Smart Search biedt een automatische aanvulfunctie die feitelijk een wildcard-zoekopdracht uitvoert op termen in de index. Volledige wildcard-zoekopdrachten worden echter niet ondersteund vanwege het risico op overbelasting van de server als de functie zou worden misbruikt. In de meeste gevallen wordt wildcard-zoeken gebruikt om variaties in een zoekterm te verwerken. Bijvoorbeeld om te zoeken naar *jongleer\** om zowel naar verwijzingen naar *jongleren* als *jongleur* te zoeken. Smart Search probeert de noodzaak voor wildcard-zoeken te vermijden door in plaats daarvan woordstammen te ondersteunen, waarbij woorden die dezelfde stam hebben als equivalent worden beschouwd, zodat zoeken naar *jongleur* ook gevallen van *jongleren* ophaalt zonder de noodzaak van wildcards.

## Kan Slim Zoeken Worden Gebruikt op Meertalige Sites?

Ja, maar er zijn nog steeds een aantal problemen die moeten worden opgelost, vooral met betrekking tot ondersteuning voor Aziatische talen.

- Om correct te worden geïndexeerd, moet je ervoor zorgen dat alle inhoud geldige UTF-8 is.
- De *Bedoelde je?* functie gebruikt de Soundex-functie om fonetisch vergelijkbare zoekzinnen te vinden. Echter, Soundex werkt niet goed voor niet-Engelse talen en voor veel talen werkt het helemaal niet. We onderzoeken momenteel alternatieve methoden om deze functie aan te bieden.

Als je Slim Zoeken gebruikt op een meertalige site en problemen tegenkomt, meld ze dan op de tracker zodat we de problemen die moeten worden opgelost beter kunnen begrijpen.

## Werken *jXTended* Finder-plugins met Smart Search?

Nee. U zult de Finder-plugins moeten updaten om te werken met Smart Search. De wijzigingen zouden echter niet moeilijk te implementeren moeten zijn en zullen in de meeste gevallen resulteren in aanzienlijk minder code. Als u kijkt naar de huidige Smart Search-plugins, zou u moeten zien dat het updaten van een Finder-plugin behoorlijk eenvoudig is.

*Vertaald door openai.com*

