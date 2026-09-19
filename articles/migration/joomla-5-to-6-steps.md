<!--
{
    "source": "https://docs.joomla.org/https:",
    "title": "Joomla 5 naar 6 stap voor stap",
    "description": " ",
    "author": ""
}
-->

<div class="alert alert-warning">
<p class="h3">Waarschuwing</p>

Deze handleiding gaat ervan uit dat u begint met Joomla 5.4.x. Als u een eerdere versie gebruikt, zorg er dan voor dat u migreert of bijwerkt naar Joomla 5.4.x voordat u een upgrade naar Joomla 6.x uitvoert.
</div>

## Inleiding

Goed nieuws voor Joomla 5.4.x tot en met 6.x: het is een upgrade, geen migratie. Waarom? Twee belangrijke redenen:

- Joomla 5-extensies (J5) waarin alle verouderde code is verwijderd, die actuele Joomla-code gebruiken en waarvoor de plugin Behaviour - Backward Compatibility niet hoeft te worden ingeschakeld, werken in Joomla 6 (J6)
- De meeste andere extensies werken met de nieuwe plugin Behaviour - Backward Compatibility 6 ingeschakeld

Deze documentatie weerspiegelt het eenvoudigere proces door de planning en de stapsgewijze instructies in één document te combineren. Toch hebt u enige vaardigheden nodig. Bekijk de [[Migration Step by Step Self Assessment|Zelfevaluatie]] om te bepalen of u de upgrade zelf moet aanpakken.

<div class="alert alert-info">
<p class="h3">Ontwikkelaarsdocumentatie voor ontwikkelaars van extensies van derden voor 5.4 naar 6.0.</p>

- [Verwijderd en achterwaartse incompatibiliteit](https://manual.joomla.org/60/removed-backward-incompatibility)
- [Nieuwe verouderingen](https://manual.joomla.org/60/new-deprecations)
- [Over migratiedocumentatie](https://manual.joomla.org/migrations)
- [Nieuwe functies](https://manual.joomla.org/60/new-features/)
</div>

## Planning van 5.4.x naar 6.x

### Hosting/Technische specificatie

1. Bepaal of uw hostingomgeving aan de vereisten voldoet. U kunt niet 
upgraden naar Joomla 6 als uw serveromgeving niet aan de 
minimale [technische vereisten](https://manual.joomla.org/docs/get-started/technical-requirements/) 
voldoet. De optie om te upgraden wordt niet weergegeven in de component Joomla Update.
    - PHP 8.3
    - MySQL 8.0.13
    - MariaDB 10.6.x
    - PostgreSQL 14.0

U kunt uw systeeminformatie op een Joomla 5-site controleren door te klikken op Systeem -> Systeeminformatie. Neem contact op met uw hostingprovider als uw server niet aan de vereisten voldoet.

![Systeemdashboard met de link Systeeminformatie gemarkeerd](../../../en/images/migration/joomla-5-to-6-steps/01-steps-5-to-6-system-dashboard.png)

Hieronder staat een voorbeeld van een omgeving die aan de technische vereisten voldoet. Deze toont MySQL 8.0.43, PHP 8.3, Joomla 5.4.x en de uitgeschakelde plug-in Achterwaartse compatibiliteit.

![Systeeminformatie met de Joomla-versie, PHP-versie, databasetype, databaseversie en de uitgeschakelde compatibiliteitsplugin voor oudere versies](../../../en/images/migration/joomla-5-to-6-steps/02-steps-5-to-6-system-information.png)

2. Controleer al uw extensies op compatibiliteit met Joomla 6. Voor deze upgrade zijn er verschillende scenario's voor extensies van derden.

    1. De extensie kan compatibel zijn met J5 en J6 ZONDER het gebruik van de compatibiliteitsplugin voor oudere versies.
    2. De extensie kan compatibel zijn met J5 en J6 MET het gebruik van de compatibiliteitsplugin voor oudere versies.
    3. De extensie lijkt mogelijk te werken in J6, maar wanneer u deze probeert te gebruiken, werkt deze niet.
    4. De extensie kan de volledige website onbruikbaar maken.

Geen zorgen! Het is niet zo erg als het klinkt! Laten we het eerst hebben over de compatibiliteitsplugins voor oudere versies.

<div class="alert alert-warning">
<p class="h3">Waarschuwing</p>

Om te upgraden van Joomla 5.4.x naar 6.x MOET de compatibiliteitsplugin voor oudere versies van Joomla 5 UITGESCHAKELD zijn.
</div>

### De plug-ins voor achterwaartse compatibiliteit

De plug-in [Behaviour - Backward Compatibility 6](https://manual.joomla.org/60/compat-plugin/) die wordt meegeleverd met Joomla 5.4.x is bedoeld om de achterwaartse compatibiliteit tussen Joomla 5 en Joomla 6 te verbeteren. De plug-in helpt extensies van derden om klassen te gebruiken die niet langer zijn opgenomen in Joomla 6. De plug-in is geïmplementeerd als een plug-intype van het type ‘Behaviour’, zodat deze gegarandeerd wordt geladen voordat een andere plug-in wordt geladen.

![Plug-inpagina met de plug-ins voor achterwaartse compatibiliteit](../../../en/images/migration/joomla-5-to-6-steps/03-steps-5-to-6-bc-plugins.png)

De bovenstaande afbeelding toont twee plug-ins voor achterwaartse compatibiliteit:

1. Behaviour - Backward Compatibility en
2. Behaviour - Backward Compatibility 6

De plug-in Behaviour - Backward Compatibility (zonder nummer in de plug-innnaam) wordt meegeleverd met Joomla 4.4.x om een laag voor achterwaartse compatibiliteit voor Joomla 5-extensies te creëren. **Deze plug-in moet worden uitgeschakeld voordat u een upgrade naar J6 uitvoert**.
De plugin Gedrag - Achterwaartse compatibiliteit 6 wordt meegeleverd met Joomla 5.4.x om een achterwaartse compatibiliteitslaag te creëren voor Joomla 6-extensies.

Ze kunnen niet allebei ingeschakeld zijn tijdens het upgraden naar J6.

Voordat je van Joomla 5 naar Joomla 6 upgradet, moet de plugin Gedrag - Achterwaartse compatibiliteit (zonder een nummer in de naam van de plugin) worden uitgeschakeld. Je moet ervoor zorgen dat al je extensies van derden op je website kunnen werken zonder dat de plugin Gedrag - Achterwaartse compatibiliteit is ingeschakeld, voordat je naar J6 kunt upgraden.

Nadat je hebt vastgesteld dat al je extensies van derden compatibel en volledig functioneel zijn in J5 zonder dat de plugin Gedrag - Achterwaartse compatibiliteit is ingeschakeld, kun je deze uitschakelen. Dat gezegd hebbende, raden we aan voorzichtig te werk te gaan. Voordat je de plugin voor achterwaartse compatibiliteit uitschakelt, wordt aangeraden een van de volgende twee dingen te doen:
1. Doe dit op een ontwikkel-/testsite. Zo zorgt u ervoor dat uw productiesite niet wordt uitgeschakeld als u per ongeluk een extensie overslaat waardoor uw backend ontoegankelijk wordt.
2. Zorg ervoor dat u toegang hebt tot de database. Zo kunt u de plug-in indien nodig snel opnieuw inschakelen via de database. Hieronder leest u hier meer over.

Bij het uitvoeren van een upgrade naar J5.4.x wordt de plug-in Behaviour - Backward Compatibility 6 automatisch ingeschakeld. Bij nieuwe installaties van J6 wordt de plug-in voor achterwaartse compatibiliteit standaard uitgeschakeld.

De plug-in Behaviour - Backward Compatibility 6, die ondersteuning biedt voor extensies die in J5 werken, blijft gedurende J6 beschikbaar. In J7 worden de J5-extensies niet via de plug-in achterwaarts compatibel gemaakt. Hierdoor krijgen ontwikkelaars van extensies twee extra jaar de tijd om hun extensies compatibel te maken met J6 zonder de plug-in voor achterwaartse compatibiliteit. Het is de bedoeling dat bij elke levenscyclusrelease een plug-in voor achterwaartse compatibiliteit de voorgaande levenscyclus ondersteunt tot aan de daaropvolgende levenscyclus.
Kun je de plug-in Gedrag - Achterwaartse compatibiliteit 6 in J6 uitschakelen? Goede vraag. Nadat je hebt vastgesteld dat al je extensies van derden compatibel en volledig functioneel zijn zonder dat de plug-in voor achterwaartse compatibiliteit is ingeschakeld, kun je de plug-in Gedrag - Achterwaartse compatibiliteit 6 uitschakelen. Dat gezegd hebbende, raden we aan voorzichtig te werk te gaan. Voordat je de plug-in Gedrag - Achterwaartse compatibiliteit 6 uitschakelt, wordt aangeraden een van de volgende twee dingen te doen:

1. Doe dit op een ontwikkel-/testsite. Op die manier haal je je productiesite niet offline als je per ongeluk een extensie over het hoofd hebt gezien die je backend ontoegankelijk maakt.
2. Zorg ervoor dat je toegang hebt tot de database. Op die manier kun je de plug-in indien nodig snel weer inschakelen. Hieronder lees je hier meer over.

### Controle vóór update of Extensies beheren

In theorie zou de controle vóór de update je vertellen of je extensies van derden compatibel zijn met J6. De controle vóór de update is echter alleen nuttig als alle ontwikkelaars van extensies hun extensies hebben bijgewerkt om de compatibiliteit ervan weer te geven. In een ideale wereld zou het gedeelte **Extensies** van de controle vóór de update je vertellen of een extensie:

* Kan worden bijgewerkt zonder dat de plugin voor achterwaartse compatibiliteit is ingeschakeld
* Kan worden bijgewerkt terwijl de plugin voor achterwaartse compatibiliteit is ingeschakeld
* Vóór de upgrade van J5 naar J6 moet worden bijgewerkt
* Volledig incompatibel is
Uit tests is gebleken dat er verschillen zijn tussen extensies die wel en niet compatibel zijn. Dit is geen probleem met het onderdeel voor de controle vóór de update. Extensieontwikkelaars sturen namelijk informatie mee via hun extensies, waarmee de controle vóór de update correct wordt ingevuld. Als hun extensies niet zo zijn gecodeerd dat ze de juiste informatie aan de controle vóór de update doorgeven, kan de controle vóór de update, noch het Joomla!-project, hier vrijwel niets aan doen. Een goede informatiebron is de website van de ontwikkelaar van de extensie van derden, om te controleren hoe de specifieke extensie moet worden behandeld tijdens de upgrade van J5 naar J6.

De afbeelding verderop in dit gedeelte toont een voorbeeld van het onderdeel voor de controle vóór de update in Joomla 5.4.x, in het gedeelte Extensies.

In het bovenste gedeelte worden de extensies weergegeven die een update vereisen. Ga naar Systeem -> Bijwerken -> Extensies en werk uw extensies bij.
De middelste sectie toont extensies waarvoor informatie over updates van de extensieontwikkelaar niet beschikbaar is. U weet niet of deze compatibel zijn zonder ze te testen of contact op te nemen met de ontwikkelaar.

De onderste sectie toont de extensies waarvoor geen update vereist is. Dit betekent dat de extensies Joomla laten weten dat ze compatibel zijn met Joomla 6. Er wordt niet aangegeven of ze de plug-in voor achterwaartse compatibiliteit nodig hebben.

Houd er rekening mee dat deze extensies niet de voorkeur hebben van het Joomla-project. Deze extensies worden alleen als voorbeeld getoond. Ze zijn willekeurig uit de JED geselecteerd als test.

![Sectie met extensies voor controle vóór de update](../../../en/images/migration/joomla-5-to-6-steps/04-steps-5-to-6-pre-update-check.png)

Het wordt aanbevolen om alleen het gedeelte **Extensies** van de component voor controle vóór de update te gebruiken als een overzicht op zeer hoog niveau, maar niet als de 100% betrouwbare bron. Anders gezegd: afhankelijk van de extensies die u gebruikt, kunt u mogelijk niet op de component voor controle vóór de update vertrouwen.
*Wat is dan de bron van waarheid?* Systemen -> Extensies beheren

![Systeemdashboard met ‘Extensies beheren’ gemarkeerd](../../../en/images/migration/joomla-5-to-6-steps/05-steps-5-to-6-system-dashboard-manage.png)

Op het scherm Extensies: Beheren kunt u alle extensies van derden zien die u op de site gebruikt. In de onderstaande schermafbeelding ziet u het hoofdscherm. In de kolom Auteur ziet u in een aantal rijen de naam van een populaire ontwikkelaar van extensies. U ziet ook in een aantal rijen de auteur van het Joomla-project.

![De hoofdpagina Extensies beheren](../../../en/images/migration/joomla-5-to-6-steps/06-steps-5-to-6-extensions-manage.png)

Controleer uw extensies van derden. Vervolgens moet u bepalen of ze compatibel zijn met J6 (met of zonder de plug-in voor achterwaartse compatibiliteit) of niet. Als ze niet compatibel zijn, zal de upgrade mislukken.

### Drie manieren om uw extensies van derden te controleren op compatibiliteit met J6

1. Controleer de website van de ontwikkelaar.
2. Maak een back-up/kopie van uw J5-site, herstel deze op een subdomein, schakel foutopsporing in en volg de stapsgewijze instructies (hieronder) om te upgraden naar J6. Controleer of er iets niet meer werkt. Als dat het geval is, schakelt u elke extensie uit die een fout veroorzaakt en noteert u om welke extensie het gaat. U moet hierover contact opnemen met de ontwikkelaar, omdat de extensie niet compatibel is met J6.
3. Installeer een schoon J6-pakket op een subdomein, schakel de plug-in Gedrag - Achterwaartse compatibiliteit in, installeer alle extensies die u gebruikt en controleer of ze werken.

OPMERKING: In de Joomla! Extensions Directory JED worden badges voor compatibiliteit met Joomla 6 weergegeven voor extensies die compatibel zijn, met of zonder het gebruik van de plug-in voor achterwaartse compatibiliteit.
Je zou een combinatie van bovenstaande kunnen gebruiken. Begin met een schone installatie en test je extensies uit. Zodra je weet welke wel of niet werken, kun je met de ontwikkelaars overleggen over de voortgang van hun ontwikkeling voor J6. **DAARNA**, zodra al je extensies op een schone site werken, weet je dat je een volledige upgrade van J5.4.x naar 6.x kunt **testen**.

Misschien wil je bepalen of een extensie werkt zonder dat de plug-in voor achterwaartse compatibiliteit is ingeschakeld. Als dat het geval is, wil je toegang hebben tot de database. Plan dit van tevoren. Zorg ervoor dat je toegang hebt tot de database.

Na het installeren van een nieuwe installatie van J6 is de plug-in voor achterwaartse compatibiliteit uitgeschakeld. Installeer elke extensie één voor één. Als je site daardoor niet meer werkt, schakel je de plug-in voor achterwaartse compatibiliteit in via de database.
De achterwaartse-compatibiliteitsplugin is te vinden in de database in de tabel #__extensions. Deze heet plg_behaviour_compat6. Stel het veld Enabled in op 0 om de plugin uit te schakelen. Stel het in op 1 om de plugin in te schakelen. Door de achterwaartse-compatibiliteitsplugin opnieuw in te schakelen, krijgt u mogelijk weer toegang tot de backend van Joomla (zolang de extensie met de achterwaartse-compatibiliteitsplugin werkt).

OF

U kunt afzonderlijke extensies in de database uitschakelen, zodat u uw andere extensies kunt blijven testen om te zien of ze functioneren zonder dat de compatibiliteitsplugin is ingeschakeld. Deze vermeldingen bevinden zich in de tabel #__extensions. Wijzig het veld Enabled in 0 om de extensie uit te schakelen.
In sommige gevallen moet u, wanneer u een extensie in J6 installeert die niet compatibel is, met of zonder de achterwaartse-compatibiliteitsplug-in ingeschakeld, de vermeldingen voor die extensie in de database opzoeken (het kunnen er enkele of veel zijn) en deze uitschakelen totdat u weer toegang heeft tot de backend. Deze vermeldingen bevinden zich in de tabel `#__extensions`. U wijzigt het veld Enabled in 0 om de extensie uit te schakelen. Zodra u weer toegang heeft tot de backend van Joomla, kunt u de extensie correct verwijderen via Systeem -> Beheren -> Extensies. Neem vervolgens contact op met de ontwikkelaar.

### Cassiopeia en Weblinks

#### Cassiopeia

Cassiopeia blijft de frontendtemplate voor Joomla 6. Uw aanpassingen zouden goed moeten blijven werken, maar we raden u toch aan om ze op een ontwikkelwebsite te testen om dit zeker te weten.

#### com_weblinks

De extensie Weblinks werkt in J6 zonder dat de achterwaartse compatibiliteitsplug-in is ingeschakeld in versie 5.4.0+:

- [Weblinks geëvolueerd in de JCM](https://magazine.joomla.org/all-issues/september-2025/joomla-weblinks-evolved-insights-from-gsoc-2025). 
- [Weblinks op de JED](https://extensions.joomla.org/extension/weblinks/).

### Proefuitvoering

Als onderdeel van uw planning wordt aanbevolen om uw upgrade op een subdomein of lokaal te testen om vast te stellen of deze perfect werkt. Houd bij welke stappen u moet nemen om uw upgrade **perfect** te laten verlopen.

Nadat u uw upgrade op een subdomein of localhost hebt getest en deze **perfect** werkt, kunt u een back-up van uw productiesite maken en de upgrade daarop uitvoeren. Hieronder vindt u stapsgewijze instructies.

## Stap voor stap upgraden

De site die u gaat upgraden moet aan alle technische vereisten voldoen en Joomla 5.4.x gebruiken om te kunnen upgraden. Als uw site nog niet op Joomla 5.4.x draait, werkt u deze vóór de upgrade naar J6 bij naar 5.4.x.

1. Volg alle instructies in het gedeelte Planning (hierboven) voordat u gaat upgraden.
2. **Maak een back-up van uw website.**
3. Werk extensies die moeten worden bijgewerkt bij.
4. Schakel extensies die niet compatibel zijn met J6 uit of verwijder ze.
5. Schakel Debug in (Globale configuratie -> tabblad Systeem -> instelling Systeem debuggen op Ja).
6. **Maak opnieuw een back-up van uw website.**
7. **Test uw back-up om er zeker van te zijn dat deze kan worden teruggezet.** (Ja, doe dit. U zult zich beter voelen.)
8. Ga naar Systeem -> Update -> Joomla
![Het systeemdashboard met gemarkeerde optie Joomla bijwerken](../../../en/images/migration/joomla-5-to-6-steps/07-steps-5-to-6-system-dashboard-joomla.png)
9. Klik rechts in de bovenste werkbalk op de knop Opties.
![De Joomla-updatepagina met gemarkeerde knop Opties](../../../en/images/migration/joomla-5-to-6-steps/08-steps-5-to-6-joomla-update.png)
10. Wijzig het updatekanaal in Joomla Next.
![Joomla-updateopties met omlijnd updatekanaal](../../../en/images/migration/joomla-5-to-6-steps/09-steps-5-to-6-joomla-update-options.png)
11. Klik op Opslaan en sluiten in de bovenste werkbalk.
12. Als je server aan de technische specificaties voldoet, zie je het volgende scherm met koppelingen in de linkerzijbalk voor Vereiste instellingen, Aanbevolen instellingen en Extensies.
![Pre-updatecontrole met omlijnde zijbalk](../../../en/images/migration/joomla-5-to-6-steps/10-steps-5-to-6-pre-update-check-for-6.png)
13. De kans is groot dat je Vereiste instellingen en Aanbevolen instellingen in orde zijn, omdat dit scherm niet wordt weergegeven als je omgeving niet aan de technische vereisten voldoet. Bij Extensies kan dat anders zijn. Zie het gedeelte in Planning (hierboven) over de pre-updatecontrole en waarom deze mogelijk geen groen vinkje heeft, maar toch alle compatibele extensies bevat. Je hebt je tests al uitgevoerd (toch?), dus je weet al of ze compatibel zijn of niet.
14. De plugin Backward Compatibility 6 is ingeschakeld in Joomla 5.4.x. Om naar J6 te upgraden, moet de plugin Gedrag - Backward Compatibility worden uitgeschakeld.
15. **Als u de instructies in Planning (hierboven) voor de proefrun niet hebt gevolgd, stop dan nu en ga terug naar het gedeelte Planning om de instructies te volgen. Planning is het belangrijkste onderdeel van deze upgrade.**
16. Zodra u zeker weet dat al uw extensies compatibel zijn met J6 en u de upgrade hebt getest en het resultaat perfect was, kunt u het vakje aanvinken om de waarschuwingen over mogelijk incompatibele extensies te bevestigen en door te gaan met de update. Klik op OK in het pop-upvenster en klik vervolgens op de knop Update.
![Melding Waarschuwingen bevestigen](../../../en/images/migration/joomla-5-to-6-steps/11-steps-5-to-6-pre-update-warnings.png)
17. Vervolgens vraagt uw site u opnieuw om te bevestigen dat u een back-up hebt gemaakt (wat u hebt gedaan en waarvan u hebt getest of deze kan worden teruggezet).
![Pagina Uploaden en bijwerken naar Joomla 6](../../../en/images/migration/joomla-5-to-6-steps/12-steps-5-to-6-upload-and-update.png)
18. Je site voert de upgrade naar J6 uit.
![Pagina met de voortgang van de upgrade](../../../en/images/migration/joomla-5-to-6-steps/13-steps-5-to-6-joomla-update-progress.png)
19. Na een geslaagde upgrade krijg je een scherm zoals dit te zien:
![Pagina met de updatestatus waarop succes wordt weergegeven](../../../en/images/migration/joomla-5-to-6-steps/14-steps-5-to-6-joomla-update-success.png)
20. Rechtsboven in het scherm zie je dat je site Joomla 6 gebruikt.
21. Test de frontend van je site.
22. Test de backend van je site.
23. Schakel Debug uit via Systeem -> Algemene configuratie -> tabblad Server.
24. Pas je nieuwe Smart Search indien nodig aan.
25. Geniet van een lekker drankje en bewonder hoe geweldig je bent.

## Wat als het misgaat?

Als je alles vooraf hebt getest, zou dat niet moeten gebeuren. Maar het is mogelijk dat er iets in de omgeving is gewijzigd of dat er code in een extensie is gewijzigd tussen het moment waarop je hebt getest en je upgrade.

Omdat je Debug hebt ingeschakeld voordat je begon, zou je de extensie moeten kunnen zien die het probleem veroorzaakt en deze kunnen uitschakelen (dit moet mogelijk vanuit de database gebeuren als je geen toegang meer hebt tot de backend om deze uit te schakelen). Zo blijft je site actief terwijl je uitzoekt wat er mis is gegaan en dit oplost.

In het ergste geval herstel je je back-up, zodat je tijd hebt om uit te zoeken wat er is gebeurd in een testomgeving.

Database Fix kan sommige van je problemen oplossen. Navigeer naar het Systeemdashboard en klik op Database.

![Systeemdashboard met gemarkeerde link naar Database](../../../en/images/migration/joomla-5-to-6-steps/15-steps-5-to-6-system-dashboard-database.png)

Op de pagina Onderhoud: Database worden eventuele problemen met de databasestructuur van je site weergegeven. Vink het juiste selectievakje aan en klik vervolgens op de knop Structuur bijwerken in de bovenste werkbalk.

![Onderhoudspagina voor de database met één probleem](../../../en/images/migration/joomla-5-to-6-steps/16-steps-5-to-6-maintenance-database.png)

## Andere plaatsen om hulp te krijgen

- [Joomla-forum: Migratie- en upgradeforum 6.x](https://forum.joomla.org/viewforum.php?f=866&sid=47959551fb677ee3690f8b61eece277b)
- [Joomla-community op Mattermost](https://joomlacommunity.cloud.mattermost.com/main/channels/town-square)

*Vertaald door openai.com*