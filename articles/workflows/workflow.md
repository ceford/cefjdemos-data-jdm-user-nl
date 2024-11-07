<!-- Filename: J4.x:Workflow / Display title: Publicatieworkflow   -->

## Introductie

In Joomla is een workflow een reeks stappen in het leven van een artikel van conceptie tot ondergang. De stappen worden meestal uitgevoerd door verschillende individuen met verschillende verantwoordelijkheden. In de krantenwereld, bijvoorbeeld, neemt een subredacteur een verhaal van een verslaggever en controleert het op nauwkeurigheid, grammatica, leesbaarheid, lengte, en mogelijk meer. De subredacteur geeft het verhaal vervolgens door aan de redacteur, die het verhaal kan accepteren of afwijzen, beslissen waar het in de krant wordt geplaatst, enzovoort. 

De Workflow-component wordt gebruikt om **stappen** aan artikelen toe te voegen om de statische staten (niet-gepubliceerd, gepubliceerd, verwijderd en gearchiveerd) te verbeteren met **transities**. De statische staten en transities worden apart vastgelegd, zodat workflows kunnen worden in- of uitgeschakeld zonder de status van inhoudselementen te beïnvloeden. Workflows worden in- of uitgeschakeld op het tabblad *Integratie* van de pagina *Artikelen: Opties*. 

Er is een tutorialpagina met stappen voor het creëren van een voorbeeldworkflow: [Workflow Scenario's](jdocmanual?article=user/workflows/workflow-scenarios).

## Termen & Definities

- *Workflow:* Een workflow is een volledige reeks stappen. Er kunnen verschillende workflows worden gecreëerd voor verschillende doeleinden. De Workflow-component bevat een *Basis Workflow* en de blog voorbeelddata heeft een meer complexe *Blog Workflow*.
- *Stadium:* Een stadium is een locatie binnen een workflow. Bijvoorbeeld, een ongepubliceerd artikel kan zich bevinden in Stadium 1: In Voorbereiding of Stadium 2: Klaar voor Beoordeling, enzovoort. Het is het stadium van het item dat in de database wordt vastgelegd.
- *Transitie:* Een transitie is een verandering van het ene stadium naar het andere, vaak naar het volgende in de workflow, maar kan ook naar het vorige of het beginstadium zijn.
- *Status:* De status van een artikel kan ongepubliceerd, gepubliceerd, naar prullenbak verplaatst of gearchiveerd zijn. Een status kan worden gewijzigd door een workflow transitie uit te voeren, op voorwaarde dat de gebruiker toestemming heeft om de status te wijzigen.
- *Categorie:* Wanneer er workflows in gebruik zijn, kan een specifieke Workflow worden geselecteerd voor een categorie in het *Artikel: Bewerken Categorie* formulier *Workflow* tabblad.

## De Workflowlijst

Wanneer workflows zijn ingeschakeld, kan de lijst van beschikbare workflows worden bekeken door te kiezen voor **Inhoud → Workflows** in het Administrator-menu.

![Workflows lijst](../../../en/images/workflows/workflows-list.png)

- De **Status** van een workflow kan Ingeschakeld, Uitgeschakeld of Verwijderd zijn.
- De **Naam** is een link naar het formulier om de workflow te bewerken.
- Het **Standaard** item wordt gebruikt voor nieuwe items die niet zijn toegewezen aan een categorie die een gedefinieerde workflow heeft.
- Het **Stadia** item is een knop die het aantal stadia toont en een link naar de lijst van stadia voor de workflow.
- Het **Overgangen** item is een knop die het aantal overgangen toont en een link naar de lijst van overgangen voor de workflow.
- De **ID** is de numerieke waarde van de workflow die intern wordt gebruikt.

## Stadia

De stadia zijn toegankelijk via de *Workflows* lijst. Selecteer de gele knop die het aantal stadia toont.

![Workflow stadia lijst](../../../en/images/workflows/workflow-stages-list.png)

Selecteer de naam van een stadium om het te bewerken.

![Workflow stadium bewerkformulier](../../../en/images/workflows/workflow-stage-edit.png)

## Overgangen

In workflows gaan artikelen van de ene fase naar de andere. De overgangen worden beheerd via de *Overgangen*-lijst.

![De overgangenlijst](../../../en/images/workflows/workflow-transitions-list.png)

- De *Huidige Fase* definieert waar deze overgang begint.
- De *Doelfase* definieert waar deze overgang eindigt.

### Overgangsfasen

De *Huidige* en *Doel*-fasen worden ingesteld in het *Bewerk Overgang*-formulier:

![Bewerk overgang formulier](../../../en/images/workflows/workflow-transition-edit.png)

Het *Overgangsacties*-tabblad wordt gebruikt om de *Status* te definiëren waarin het item zich na de overgang zal bevinden.

![Bewerk overgang formulier acties tab](../../../en/images/workflows/workflow-transition-edit-actions-tab.png)

- **In De Schijnwerpers Status** Of het item wel of niet *In De Schijnwerpers* zal zijn.
- **Publicatiestatus** Selecteer de doelstatus uit de lijst.

Het *Overgangsmeldingen*-tabblad wordt gebruikt om te bepalen of er een melding voor die status wordt verzonden. Bijvoorbeeld, als een artikel is geschreven maar moet worden nagelezen, kan een e-mail worden verzonden om de redacteur te informeren.

![Bewerk overgang formulier meldingen tab](../../../en/images/workflows/workflow-transition-edit-notifications-tab.png)

- **Stuur Melding** Als ingesteld op *Ja* verschijnen er extra velden.
- **Aanvullende Berichttekst** Voeg extra berichttekst toe of gebruik een taalstring om de berichttekst vertaalbaar te maken.
- **Gebruikersgroepen** Selecteer wie de melding zal ontvangen, bijvoorbeeld alle gebruikers in de *Redacteur*-gebruikersgroep.
- **Gebruikers** Selecteer individuele gebruikers die deze melding zullen ontvangen.

### Rechten

Het rechten-tabblad beheert de toegang tot deze overgang door geselecteerde gebruikersgroepen. Normaal worden de rechten overgenomen van de rechten in de *Artikelen: Opties* permissie-instellingen.

### Workflow Overgang Plugins

De workflow plugins worden gebruikt voor acties die worden opgeroepen door overgangen. Ga naar **Systeem → Plugins** en verander het *- Selecteer Type -* filter naar *workflow*. Elk van deze plugins kan worden uitgeschakeld als ze niet nodig zijn.

![Workflow plugins-lijst](../../../en/images/workflows/workflow-plugins.png)

- **Workflow In De Schijnwerpers** Deze actie implementeert de verandering van de *In De Schijnwerpers* status van een artikel van *Ja* naar *Nee*.
- **Workflow Melding** Deze actie implementeert de melding aan een gebruiker dat een verandering van fase aandacht vereist.
- **Workflow Publiceren** Deze actie implementeert een verandering van staat van een artikel van een naar een andere status zoals *Gepubliceerd*, *Ongepubliceerd*, *In De Prullenbak* of *Gearchiveerd*. Als de gebruiker geen toestemming heeft om de status te veranderen, zal het falen met een verklarend bericht. De overgang die om de verandering van status vroeg, zal nog steeds slagen!

## Categorieën

Artikelen kunnen aan categorieën worden toegewezen. Ze komen overeen met een bepaalde workflow en kunnen op verschillende manieren worden aangepast. Je kunt een status instellen, een hoofdcategorie kiezen en ook de toegang en de rechten beperken. Deze optie bevindt zich niet op het workflows-scherm. Voor deze optie moet je naar **Inhoud → Categorieën** gaan. Eenmaal daar open je een categorie en zie je een tabblad *Workflows*.

![Artikelen categorie workflow bewerken](../../../en/images/workflows/workflow-categories-blog.png)

### Voorbeeld

Bepaalde artikelen moeten alleen beschikbaar zijn voor beheerders of gebruikers van een hogere rang.

- Maak een categorie met de naam *Beperkt*
- Stel alle rechten in op *Toegestaan* voor beheerders of hoger.
- Verplaats de betreffende artikelen naar de categorie *Beperkt*.

Dit bespaart het instellen van rechten op individuele artikelen.

## Versiebeheer

Wanneer de workflow is ingeschakeld, worden velden die door de workflow worden beheerd uitgesloten van de versiebeheer (zoals "status" en "uitgelicht") om toestemmingsconflicten te vermijden.

## Voorbeelden

Er zijn enkele specifieke voorbeelden beschikbaar om te illustreren hoe Workflows gebruikt kunnen worden voor verschillende gebruikersgroepen:

- [Voorbeeld 1](jdocmanual?article=user/workflows/workflow-example-1) maakt gebruik van de standaard gebruikersgroepen Auteur, Redacteur en Uitgever om items voor te bereiden voor een Nieuwsbrief.
- [Voorbeeld 2](jdocmanual?article=user/workflows/workflow-example-2) maakt gebruik van aangepaste gebruikersgroepen om items voor te bereiden voor commissievergaderingen.

*Vertaald door openai.com*

