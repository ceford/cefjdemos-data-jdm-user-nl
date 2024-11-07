<!-- Filename: J6.x:Workflow_Scenarios_Example_1 / Display title: Werkstroom Voorbeeld 1 -->

## Inleiding

Een workflow bestaat uit *fasen* en *overgangen* tussen die fasen. Voor elk artikel wordt de huidige fase in de database vastgelegd en gebruikt om de workflow en de overgangen daarvan te identificeren.

Een enkele site kan veel workflows hebben. Hier wordt een *Nieuwsbrief Workflow* gebruikt als voorbeeld om uit te leggen hoe drie personen met verschillende rollen betrokken kunnen zijn bij de productie van een nieuwsbriefartikel. Het voorbeeld gebruikt de Joomla standaard gebruikersgroepen Auteur, Editor en Uitgever. Dat heeft een probleem: een Auteur kan alleen Gepubliceerde artikelen zien en kan daarom geen Ongedocumenteerde artikelen herbewerkingen. Een methode om dat probleem te vermijden wordt behandeld in [Voorbeeld 2](jdocmanual?article=user/workflows/workflow-example-2).

![Workflows lijst](../../../en/images/workflows/example-1-workflows-list.png)

Let op dat de *Eenvoudige Workflow* is ingesteld als de *Standaard*. Dit kan lastige gevolgen hebben die later in dit artikel worden behandeld!

## De Gebruikers

- *Arthur* is een gebruiker die is toegewezen aan de Joomla **Auteur Groep**. Hij kan nieuwe artikelen maken en zijn eigen artikelen bewerken, maar hij kan geen artikelen bewerken die door andere gebruikers zijn geschreven of de status van artikelen wijzigen. Dus hij kan zijn eigen artikelen niet publiceren. Zijn taak is het opstellen van nieuwe artikelen.
- *Eddie* is een gebruiker die is toegewezen aan de Joomla **Redacteur Groep**. Hij kan artikelen bewerken die door een andere gebruiker, inclusief Arthur en zichzelf, zijn aangemaakt. Hij kan ook de status van een artikel niet wijzigen. Zijn taak is om de door Eddie ingediende artikelen te beoordelen, te controleren op nauwkeurigheid, spelling en grammatica, de kwaliteit van afbeeldingen enzovoort.
- *Pru* is een gebruiker die is toegewezen aan de Joomla **Uitgever Groep**. Zij kan alles doen wat Eddie en Arthur kunnen doen. Bovendien kan zij de status van een artikel wijzigen. Het is haar taak te beslissen of een artikel geschikt is voor publicatie en het te publiceren.

## De Stadia

Er zijn vier stadia in deze Workflow:

![Lijst van Workflows](../../../en/images/workflows/example-1-workflow-stages.png)

- **Concept** is het stadium dat door Arthur is gemaakt voor een nieuw artikel.
- **Review** is het stadium waarin Eddie de inhoud naleest.
- **Goedkeuren** is het stadium waarin Pru beslist of het artikel goed genoeg is om te publiceren.
- **Publiceren** is het stadium waarin het artikel is goedgekeurd en gepubliceerd.

De gegevensinvoerformulieren voor de stadia vergen weinig uitleg, alleen een Naam en Beschrijving.

## De Overgangen

Twee overgangen zijn vereist tussen elke fase: één om de fase terug te brengen als er meer werk nodig is in de vorige fase; en een tweede om naar de volgende fase te migreren. Extra overgangen zijn nodig om de beëindiging van een artikel te verwerken:

![Workflows lijst](../../../en/images/workflows/example-1-workflow-transitions.png)

- **Concept/Beoordeling** om de fase van Concept naar Beoordeling te verplaatsen.
- **Beoordeling/Concept** om de fase terug te brengen van Beoordeling naar Concept.
- **Beoordeling/Goedkeuring** om de fase van Beoordeling naar Goedkeuring te verplaatsen.
- **Goedkeuring/Beoordeling** om de fase terug te brengen van Goedkeuring naar Beoordeling.
- **Beoordeling/Publiceren** om de fase naar Gepubliceerd te verplaatsen en de artikelstatus te veranderen naar *Gepubliceerd*.
- **Publiceren** om de artikelstatus in te stellen op *Gepubliceerd* wanneer de overgang wordt uitgevoerd door een Auteur of Redacteur.
- **Depubliceren** om de artikelstatus te veranderen naar *Gedepubliceerd*.
- **Archiveren** om de artikelstatus te veranderen naar *Gearchiveerd*.
- **Verwijderen** om de artikelstatus te veranderen naar *Verwijderd*.

De laatste drie overgangen stellen Pru in staat om de status van een artikel te wijzigen wanneer het niet langer nodig is.

### Bewerk de Overgang

Het datuminvoerformulier heeft vier tabbladen, beginnend met het *Overgang* tabblad:

![Workflows lijst](../../../en/images/workflows/example-1-edit-transition.png)

- **Naam** Het is het beste om de Huidige en Doelfasen in de naam te gebruiken.
- **Huidige Fase** De fase voordat de overgang plaatsvindt.
- **Doelfase** De fase nadat de overgang heeft plaatsgevonden.
- **Notitie** Eventuele verklarende notities om te helpen bij het uitleggen van de overgang.

#### Het *Overgangsacties* tabblad:

![Workflows lijst](../../../en/images/workflows/example-1-edit-transition-actions.png)

- **Voorkeursstatus** Definieer de voorkeursstatus die een item moet hebben na het uitvoeren van deze overgang. Laat dit op *-Niet Geselecteerd-* staan als de gebruiker die deze overgang waarschijnlijk uitvoert geen toestemming heeft om artikelen als voorkeursitems aan te merken.
- **Publicatiestatus** Definieer de publicatiestatus die een item moet hebben na het uitvoeren van deze overgang. Laat dit op *-Niet Geselecteerd-* staan als de gebruiker die deze overgang waarschijnlijk uitvoert geen toestemming heeft om de artikelstatus te wijzigen.

#### Het *Notificaties* tabblad:

![Workflows lijst](../../../en/images/workflows/example-1-edit-transition-notification.png)

- **Stuur Notificatie** Stel dit in op *Ja* waar notificaties nodig zijn, bijvoorbeeld wanneer Arthur Eddie moet informeren dat een artikel klaar is voor beoordeling.
- **Extra Berichttekst** Dit is generieke extra tekst om de ontvanger te helpen.
- **Gebruikersgroepen** U kunt ervoor kiezen om de notificatie naar een of meer gebruikersgroepen te sturen, of naar geen enkele en in plaats daarvan naar individuen.
- **Gebruikers** Selecteer individuele gebruikers uit de lijst met gebruikers.

#### Het *Rechten* tabblad:

Merk op dat voor *Auteur* de instelling voor *Overgang Uitvoeren* is ingesteld op Toegestaan (Geërfd). Verander deze instellingen niet voor andere overgangen die een Auteur niet mag gebruiken, aangezien dit ook van invloed zal zijn op Redacteuren en Uitgevers.

## De Artikelcategorie

Elk artikel wordt aan een workflow toegewezen bij de eerste keer opslaan. Als het artikel eerst wordt toegewezen aan een categorie waarbij een workflow is geselecteerd, wordt het aan die workflow toegewezen. Anders wordt het toegewezen aan de standaard workflow. Dat kan lastig zijn omdat de workflowcomponent geen methode biedt om de workflow te wijzigen zodra deze is toegewezen. Het kan worden veranderd door een Super User met behulp van de Batch Actie op de artikelenlijstpagina.

### Een Nieuwsbriefcategorie Maken

Er is een nieuwe Nieuwsbriefcategorie nodig om de nieuwsbrief weer te geven als een Categorie Blog en om ervoor te zorgen dat de nieuwsbrieffartikelen worden toegewezen aan de Nieuwsbrief Workflow.

![Workflows lijst](../../../en/images/workflows/example-1-newsletter-category.png)

## Het Nieuwsbrief Menu-item

Zodat sitebezoekers de Nieuwsbrief kunnen zien, moet het de startpagina zijn of gekoppeld met een menu-item. Volg dit voorbeeld en maak een nieuw menu-item aan van het type *Categorie Blog* met de categorie *Nieuwsbrief*.

Probeer het menu-item op de site uit. Het zal waarschijnlijk een lege pagina zijn met dit bericht:

<div class="alert alert-info">
Er zijn geen artikelen in deze categorie. Als subcategorieën op deze pagina worden weergegeven, kunnen ze artikelen hebben.
</div>

## Inloggen als Arthur

Herinner je je Arthur de Auteur nog? Na het inloggen zou de nieuwsbriefpagina een knop met het label **Nieuw Artikel** moeten hebben. Selecteer deze om een nieuw artikel te schrijven.

### Een Artikel Schrijven

Vul het artikel bewerkingsformulier in zoals je dat bij elk artikel zou doen. Kijk echter eerst naar het tabblad *Publiceren* voordat je voor het eerst opslaat.

- **Werkstroomfase** moet worden ingesteld op **Overgang Uitvoeren** *Concept/Review*.
- **Categorie** moet worden ingesteld op *Nieuwsbrief*.

Wanneer je klaar bent met het bewerken van het artikel, selecteer je *Opslaan* of *Opslaan & Sluiten*.

<div class="alert alert-danger">Na het sluiten van het artikel kan Arthur het niet meer bewerken omdat gebruikers in de Auteur groep geen Ongepubliceerde artikelen kunnen bekijken.</div>

## Inloggen als Eddie

Eddie de Redacteur heeft toestemming om Niet-gepubliceerde artikelen te bekijken, dus op de Nieuwsbriefpagina worden alle Niet-gepubliceerde items weergegeven die hij kan bewerken.

### Het Artikel Beoordelen

Selecteer het artikel dat door Eddie is opgesteld en breng eventuele wijzigingen aan die nodig zijn om het te verbeteren. Wanneer je tevreden bent, in het *Tabblad Publiceren*:

- **Werkstroomstadium** moet worden ingesteld op **Uitvoering Transitie** *Beoordelen/Goedkeuren*.

In tegenstelling tot Arthur, die zijn artikel niet kan zien na het opslaan, kan Eddie het artikel opnieuw zien en bewerken. Hij kan ook de transitie voor de volgende fase instellen op Goedkeuren/Publiceren. De transitie zal werken, maar het artikel zal niet worden gepubliceerd, aangezien Eddie geen publicatierechten heeft.

## Inloggen als Pru

Toen de Approve-fase in de workflow werd ingesteld, had Pru een bericht moeten ontvangen dat om actie vroeg. Log in als Pru om het artikel te beoordelen en om de Workflow Fase in te stellen op **Run Transition** *Publiceren*. *Opslaan & Sluiten* van het artikel om het gepubliceerde resultaat te zien. Log uit om het resultaat te zien zonder de Bewerken-link.

Nabeschouwing: er is een extra fase nodig om Pru in staat te stellen de fase van Publiceren naar Review terug te zetten als zij wil dat Eddie iets repareert.

## Backend Workflow

De gebruikersgroepen Auteur, Editor en Uitgever zijn bedoeld voor gebruik aan de voorkant. Het probleem voor Arthur is dat hij geen toegang heeft tot zijn conceptartikelen vanaf de voorkant omdat zijn gebruikersgroep geen kijkrechten heeft voor niet-gepubliceerde artikelen.

Je kunt backend-toegang toestaan voor alle leden van deze groepen op de volgende manier:

- Ga naar de pagina **Globale Configuratie**.
- Selecteer het tabblad **Permissies**.
- Selecteer *Auteur* en stel **Administrator Login** in op *Toegestaan*.
- **Opslaan**
- Ga naar de pagina **Artikelen: Opties**.
- Selecteer het tabblad **Permissies**.
- Selecteer *Auteur* en stel **Toegang administratie-interface** in op *Toegestaan*.

Hierdoor kunnen Arthur, Eddie en Pru inloggen op de backend met toegang tot de inhoudselementen. Een sterk verkleind Startscherm:

![Startscherm voor Arthur](../../../en/images/workflows/example-1-backend-home.png)

Maar Arthur heeft toegang tot zijn conceptartikelen:

![Artikellijst voor Arthur](../../../en/images/workflows/example-1-backend-articles.png)

Let op dat Arthur het laatste item in de lijst niet kan bewerken omdat het niet een van zijn eigen artikelen is. De titel van het artikel is niet gelinkt. Evenzo kan Arthur geen bestaande categorieën bewerken omdat hij daar geen toestemming voor heeft en deze zijn ook niet gelinkt. Hij kan een nieuwe Categorie aanmaken, maar deze is niet gepubliceerd en hij kan deze niet publiceren!

## Oplossing voor Verkeerde Workflow

Als je een artikel aan de verkeerde workflow toewijst, zijn er twee methoden beschikbaar om het probleem op te lossen.

### Super User Methode

- Ga naar de **Artikelen** lijst.
- Selecteer het selectievakje voor het probleemartikel.
- Selecteer de **Acties** knop in de werkbalk.
- Selecteer de **Batch** knop uit de lijst.
- Selecteer **Wijzig Fase** in het *Batchproces Geselecteerde Artikelen* dialoogvenster.
- Selecteer een geschikte doelworkflow en fase.
- Selecteer de **Verwerken** knop.

![Artikellijst voor Arthur](../../../en/images/workflows/example-1-backend-batch.png)

### Alternatieve Methode

Je kunt ook een databasetabel bewerken met phpMyAdmin of een vergelijkbaar programma.

Benodigde informatie:

- De ID van het artikel uit de laatste kolom in de Artikelen lijst.
- De ID van een fase in de vereiste workflow uit de laatste kolom van de
  Faselijst van de workflow die je wilt gebruiken.

In phpMyAdmin:

- Blader door de #__workflow_associations tabel om het item_id te vinden dat
  de ID van je artikel bevat.
- Verander de stage_id waarde naar de fase ID die je hebt opgezocht in de vereiste
  workflow.

Ga terug naar je artikelenlijst en controleer of het probleemitem nu
de juiste workflow gebruikt.

*Vertaald door openai.com*

