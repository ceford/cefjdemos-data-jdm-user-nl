<!--
{
    "source": "https://docs.joomla.org/J4.x:How_To_Use_Content_Tags_in_Joomla",
    "title": "Inhoudstags",
    "description": " ",
    "author": ""
}
-->

## Inleiding

Tags bieden een gebruiksvriendelijke en efficiënte manier om inhoud te ordenen en weer te geven. 
Met de **Tags-component** kunnen afzonderlijke tags worden gebruikt voor verschillende 
inhoudstypen, waaronder artikelen, categorieën, contacten en nieuwsfeeds. Ook kunnen er bovenliggende en onderliggende tags worden aangemaakt.

In tegenstelling tot Joomla **Categorieën**, waarbij slechts één categorie aan
een item kan worden toegewezen, kunnen meerdere tags aan één item worden toegewezen. Het is echter niet
verplicht om tags aan items toe te wijzen.

Zodra een item van een specifieke tag is voorzien, brengt het klikken op de tagknop bij
inhoud waarin tags worden weergegeven u naar een pagina met een lijst van
alle items die met die specifieke tag zijn voorzien. Om deze
reden worden tags vaak gebruikt als een manier om *gefilterde* lijsten met
inhoud weer te geven.

Tags kunnen op verschillende plaatsen worden toegevoegd, wat flexibiliteit biedt bij het aanmaken van tags.

## Overwegingen

Bedenk voordat u begint wat het doel van tags op de website is, vooral
als anderen inhoud zullen toevoegen. Als tags niet correct worden toegevoegd en beheerd,
kunnen ze contraproductief worden. Veelvoorkomende problemen zijn onder andere
inhoudschrijvers die nieuwe, onnodige tags en verkeerd gespelde tagnamen toevoegen.
Sommige sitebeheerders kiezen ervoor om de toegangsrechten te wijzigen, zodat
alleen specifieke gebruikers nieuwe tags kunnen toevoegen.

De volgende schermafbeelding toont tags die worden gebruikt op een site met artikelen over 
UNESCO-werelderfgoedlocaties. In dit geval heeft elke tag een kenmerkende kleur. 

![de pagina met de taglijst](../../../en/images/tags/content-tags/01-tags-example.png)

Wanneer tags worden aangemaakt, worden ze als koppelingen weergegeven in de items met tags. 
De stijlen en posities van tags worden bepaald door de sitesjabloon. Ze worden vaak 
opgemaakt als knoppen of labels.

De weergave van tags kan voor afzonderlijke artikelen of voor alle artikelen worden uitgeschakeld! Dit
lijkt misschien onlogisch, maar het is een nuttige functie wanneer tags bijvoorbeeld worden gebruikt om
inhoud te filteren voor specifieke gebruikssituaties.

## De taglijst

- Selecteer **Componenten → Tags** in het beheerdersmenu.

Deze schermafbeelding toont tags in een structuur die wordt gebruikt voor een meertalige site.
Elke taal heeft een lijst met tags, met een taaltag als bovenliggende tag. 
De bovenliggende tag wordt gebruikt in de modules *Populaire tags* en *Vergelijkbare tags*.

![de pagina met de taglijst](../../../en/images/tags/content-tags/02-tags-list.png)

Ongeacht hoe tags zijn aangemaakt, ze zijn in deze lijst te vinden.

- Selecteer de knop **Nieuw** op de werkbalk om een nieuwe tag aan te maken.
- Selecteer een **Titel** van een tag om een bestaande tag te bewerken.

### Het tabblad Taggegevens

![formulieropties voor het bewerken van tags met bootstrap-css-klassen](../../../en/images/tags/content-tags/03-edit-tag-details-tab.png)

- **Titel** Dit is het enige *verplichte* veld. 
- **Alias** Deze wordt bij het opslaan uit de titel aangemaakt.
- **Beschrijving** Het is altijd het beste om een beschrijving toe te voegen. Deze wordt weergegeven in 
  beheerdersformulieren en kan nuttig zijn wanneer er veel tags worden gebruikt.
- **Bovenliggende tag** Laat dit ingesteld op *Geen* als deze tag geen bovenliggende tag heeft. Of kies een 
  bovenliggende tag uit de lijst om hiervan een onderliggende tag te maken.
- **Status** Dit veld is standaard ingesteld op *Gepubliceerd*. Het kan worden ingesteld op 
  *Gedepubliceerd*, *Gearchiveerd* of *Naar prullenbak*.
- **Toegang** Het toegangsniveau is standaard Openbaar.
- **Notitie** en **Versienotitie:** Indien nodig kunt u notities toevoegen.
- **Opslaan en sluiten** Als u meerdere tags aanmaakt, kunt u **Opslaan en nieuw** selecteren om een nieuwe tag aan te maken.

### Het tabblad Opties

- **Lay-out** Er kunnen verschillende lay-outs zijn om uit te kiezen en u kunt uw eigen lay-out maken met een template override.
- **CSS-klasse voor tagkoppeling** Standaard worden tags weergegeven als een blauwe knop. U kunt hier klassedeclaraties invoeren om het uiterlijk van tags aan te passen en verschillende tags verschillende kleuren te geven. Voorbeeld: `bg-danger-subtle border border-danger` zijn Bootstrap-klassen die een roze knop met een rode rand opleveren.
- **Teaserafbeelding en volledige afbeelding** Stel afbeeldingen in voor de tag: een teaserafbeelding voor de taglijst en/of een volledige afbeelding voor de tagpagina.

![formulieropties voor het bewerken van tags met bootstrap-css-klassen](../../../en/images/tags/content-tags/04-edit-tag-options-tab.png)

### Het tabblad Publiceren

- Stel metagegevens in voor de tagpagina ten behoeve van zoekmachineoptimalisatie (SEO).

## Alternatieve methoden voor aanmaken

### Vanuit een artikel

Het is mogelijk om nieuwe tags toe te voegen tijdens het aanmaken of bewerken van een artikel. Voer in het tabblad Inhoud van het artikel, in het **Tags-veld**, de naam van de nieuwe tag in en druk op **Enter** om de tag op te slaan en aan het artikel toe te wijzen.

### Vanuit een categorie

Tags kunnen worden toegevoegd tijdens het aanmaken of bewerken van een categorie. Voer in het tabblad **Categorie**
de tagnaam in het **Tags-veld** in en druk op **Enter** om
de nieuwe tag aan te maken en toe te wijzen.

### Vanuit een contact

Tags kunnen worden toegevoegd tijdens het aanmaken of bewerken van een contact. Voer in het tabblad 
**Nieuw contact/Contact bewerken** de tagnaam in het **Tags-veld** in en druk op 
**Enter** om de nieuwe tag aan te maken en toe te wijzen. U kunt ook nieuwe tags toevoegen tijdens het aanmaken van contactcategorieën.

### Vanuit een nieuwsfeed

Tags kunnen worden toegevoegd bij het maken of bewerken van een nieuwe nieuwsfeed. Voer in het tabblad 
**Nieuwe/nieuwsfeed bewerken** de tagnaam in het **Tags-veld** in en druk op
**Enter** om de nieuwe tag te maken en toe te wijzen. U kunt ook nieuwe tags toevoegen bij 
het maken van nieuwsfeedcategorieën.

## Tags beheren

Waar u ook nieuwe tags toevoegt binnen Joomla, ze verschijnen allemaal in de taglijst.
Gebruik de taglijst om taginstellingen te vinden, te openen en aan te passen.

U kunt de lijst op verschillende manieren bewerken:

- Zoek naar een tag door een deel van of de volledige titel of alias ervan in het veld Zoeken in te voeren.
- Wijzig de volgorde van de lijst door middel van slepen en neerzetten om de uitvoervolgorde te optimaliseren.
- Publiceer of depubliceer tags met de knop in de kolom Status.
- Selecteer een of meer tags en gebruik de knop **Acties** om de geselecteerde tags te publiceren, te depubliceren, te archiveren, in te checken of naar de prullenbak te verplaatsen.
- Selecteer een of meer tags en gebruik de knop **Acties → Batch** om de taal of het toegangsniveau in te stellen.

## Tagweergaven

Nadat tags op uw site zijn gemaakt, zijn ze beschikbaar voor gebruik in inhoud en in modules zoals **Populaire tags** en **Vergelijkbare tags**. De volgende voorbeelden laten zien hoe deze eruit kunnen zien op een site die de standaardtemplate **Cassiopeia** gebruikt.

![tags weergegeven in een artikel en de modules voor populaire tags en vergelijkbare tags](../../../en/images/tags/content-tags/05-tag-modules-site-view.png)

Wanneer u een van de tags selecteert, gaat u naar een pagina met een lijst van
alle items die aan die specifieke tag zijn toegewezen:

![voorbeeld van taggebruik op een site met een zwarte labrador](../../../en/images/tags/content-tags/06-items-with-cultural-site-tag.png)

De lijst met items is een gefilterde lijst van website-inhoud met de geselecteerde tag.
Er is een filtervak beschikbaar om items gemakkelijker te kunnen vinden wanneer de lijst groeit. 
U kunt ook het aantal resultaten instellen dat u in één weergave wilt zien.

## Tagconfiguratie

Afzonderlijke tags nemen instellingen over uit de opties van de Tags-component. Selecteer de 
knop **Opties** in de werkbalk van de taglijstpagina om de beschikbare standaardopties 
voor tags te bekijken.

De configuratieopties van de Tags-component kunnen op het niveau van het inhoudsitem en/of menu-item worden overschreven.

## Tips

- Houd er rekening mee dat tags voor meerdere inhoudstypen worden gebruikt.
- U kunt meer dan één tag aan een item toevoegen.
- Gebruik de knop Help op de werkbalk als u twijfelt.

*Vertaald door openai.com*