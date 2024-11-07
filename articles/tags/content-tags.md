<!-- Filename: J4.x:How_To_Use_Content_Tags_in_Joomla / Display title: Inhoudstags -->

## Inleiding

Tags bieden een eenvoudige en efficiënte manier om content te organiseren en weer te geven. De **Tags Component** maakt het mogelijk om tags te gebruiken bij verschillende soorten content, waaronder artikelen, categorieën, contactpersonen en nieuwsfeeds. Het biedt ook de mogelijkheid om ouder- en kind-tags aan te maken.

In tegenstelling tot Joomla **Categorieën**, waar slechts één categorie aan een item kan worden toegewezen, kunnen meerdere tags aan een enkel item worden toegekend, maar het is niet verplicht om tags aan items toe te wijzen.

Zodra een item met een specifieke tag is gemarkeerd, leidt het klikken op de tagknop in content met tags naar een pagina die een lijst weergeeft van alle items die met die specifieke tag zijn gemarkeerd. Om deze reden worden tags vaak gebruikt om *gefilterde* lijsten van content te presenteren.

Tags kunnen op verschillende plaatsen worden toegevoegd, wat flexibiliteit biedt bij het maken van tags.

## Overwegingen

Voordat je begint, overweeg het doel van tags op de website, vooral als anderen inhoud zullen toevoegen. Tenzij ze correct worden toegevoegd en beheerd, kunnen tags contraproductief worden. Veelvoorkomende problemen zijn dat inhoudsschrijvers nieuwe onnodige tags toevoegen en dat er typefouten in de tagnamen zitten. Sommige sitebeheerders kunnen ervoor kiezen om toegangsrechten te wijzigen zodat alleen specifieke gebruikers nieuwe tags kunnen toevoegen.

Wanneer tags worden aangemaakt, verschijnen ze als links in de getagde items. De tagstijlen en posities worden gedefinieerd door de sitetemplate. Ze worden vaak gestyled als knoppen of labels.

Het weergeven van tags kan worden uitgeschakeld! Dit lijkt misschien onlogisch, maar het is een nuttige functie waar tags worden gebruikt, bijvoorbeeld om inhoud te filteren voor specifieke gebruikssituaties.

## De Tags Lijst

- Selecteer **Componenten → Tags** in het Administrator-menu.

![de tags lijst pagina](../../../en/images/tags/tags-list.png)

Hoe tags ook zijn aangemaakt, ze zijn te vinden in deze lijst.

## Tags Toevoegen

### Via de Taglijst

Selecteer de knop **Nieuw** in de Werkbalk van de Taglijst.

![nieuwe tag genaamd predator](../../../en/images/tags/new-tag-predator.png)

- **Titel** Dit is het enige *verplichte* veld.
- **Alias** Dit wordt aangemaakt vanuit de Titel bij het opslaan.
- **Beschrijving** Het is altijd goed om een Beschrijving toe te voegen. Het wordt weergegeven in
  de Administrator-formulieren en kan nuttig zijn wanneer er veel tags in gebruik zijn.
- **Ouder** Laat ingesteld op *Geen* als dit een hoofdtag is. Of kies een
  bovenliggende tag uit de lijst als dit een kindtag is.
- **Status** Dit veld is standaard ingesteld op *Gepubliceerd*. Het kan worden ingesteld op
  *Niet-gepubliceerd*, *Gearchiveerd* of *Verwijderd*.
- **Toegang** Het toegangsniveau is standaard Openbaar.
- **Notitie** en **Versie Notitie:** Indien nodig kunt u notities toevoegen.
- **Opslaan & Sluiten** De nieuwe tag verschijnt in de Taglijst. Als u
  meerdere tags maakt, kunt u kiezen om **Opslaan & Nieuw** te klikken om
  er nog een te maken.

Na het opslaan is de tag beschikbaar voor gebruik in de verschillende inhoudstypen die ze gebruiken.

### Vanuit een Artikel

Het is mogelijk om nieuwe tags toe te voegen tijdens het maken of bewerken van een artikel. In
het tabblad Artikelinhoud, voer in het **Tagsveld** de naam van de nieuwe tag in en
druk op **Enter** om de tag op te slaan en toe te wijzen aan het artikel.

### Vanuit een Categorie

Tags kunnen worden toegevoegd bij het aanmaken of bewerken van een categorie. In het **Categorie**-tabblad
voer de tagnaam in het **Tagsveld** in en druk op **Enter** om
de nieuwe tag aan te maken en toe te wijzen.

### Vanuit een Contact

Tags kunnen worden toegevoegd bij het aanmaken of bewerken van een Contact. In het **Nieuw/Bewerken Contact**-tabblad
voer de tagnaam in het **Tagsveld** in en druk op **Enter**
om de nieuwe tag aan te maken en toe te wijzen. U kunt ook nieuwe tags toevoegen bij het maken
van Contactcategorieën.

### Vanuit een Nieuwsfeed

Tags kunnen worden toegevoegd bij het aanmaken of bewerken van een nieuwe Nieuwsfeed. In het 
**Nieuw/Bewerken Nieuwsfeed**-tabblad voert u de tagnaam in het **Tagsveld** in en druk
op **Enter** om de nieuwe tag aan te maken en toe te wijzen. U kunt ook nieuwe tags toevoegen bij
het maken van Nieuwsfeedcategorieën.

## Tags Beheren

Waar je ook nieuwe Tags toevoegt binnen Joomla, ze zullen allemaal verschijnen in de Tags-lijst. Gebruik de Tags-lijst om taginstellingen te vinden, openen en aanpassen.

### De Tags Lijstfilter

![tags lijst filter op type](../../../en/images/tags/tags-list-filter.png)

Je kunt de lijst op verschillende manieren manipuleren:

- Zoek naar een tag door een deel van de titel in te voeren in het Zoekveld.
- Herorder de lijst met slepen en neerzetten om de uitvoerorde te optimaliseren.
- Publiceer of Depubliceer tags met de knop in de kolom Status.
- Selecteer een of meer tags en gebruik de **Acties**-knop om de geselecteerde tags te Publiceren, Depubliceren, Archiveren, Inchecken of Verwijderen.
- Selecteer een of meer tags en gebruik de **Acties → Batch**-knop om de Taal of Toegangsrechten in te stellen.

### Taginstellingen

- Selecteer een tag **Titel** om wijzigingen aan te brengen in de instellingen.

In het tag bewerkingsformulier:

- De instellingen van het tabblad **Tagdetails** zijn hierboven besproken.
- Het tabblad **Opties**:
  - Wijzig de lay-out van de tagpagina (de pagina die verschijnt wanneer je op de taglink klikt - bijvoorbeeld, mijnsite.com/tags/mijn-tag). Deze lay-out is normaal gesproken de standaardinstelling en afhankelijk van de sjabloon.
  - Voeg een CSS-klasse toe om een andere stijl (uiterlijk) toe te passen op de link voor de tag. Dit zou normaal gesproken alleen worden gebruikt door de Sitebeheerder.
  - Stel afbeeldingen in voor de tag - een teaserafbeelding voor de tagslijst en/of een volledige afbeelding voor de tagpagina.
- Het tabblad **Publiceren**: Stel metadata in voor de tagpagina voor Zoekmachineoptimalisatie (SEO).

## Hoe Joomla Tags Uitvoert

Zodra tags op je site zijn aangemaakt, zijn ze beschikbaar voor gebruik, niet alleen in de inhoud maar ook in enkele nuttige modules zoals **Populaire Tags** en **Vergelijkbare Tags**. De volgende voorbeelden laten zien hoe deze eruitzien op een standaardinstallatie met de standaard **Cassiopeia**-sjabloon.

![tags gebruik site voorbeeld gele labrador](../../../en/images/tags/tag-examples-yellow-labrador.png)

Wanneer je op een van de tags klikt, word je naar een pagina gebracht die alle items opsomt die aan die specifieke tag zijn toegewezen:

![tags gebruik site voorbeeld zwarte labrador](../../../en/images/tags/tag-examples-black-labrador.png)

Door op een tag te klikken, kom je op een pagina die een lijst uitvoert van alle items die aan die specifieke tag zijn toegewezen - in feite is het een gefilterde lijst van je getagde website-inhoud. Er wordt een filtervak aangeboden om het gemakkelijker te maken items te vinden naarmate de lijst groeit. Je kunt ook het aantal resultaten instellen dat je in één weergave wilt zien.

## Tags-configuratie

Individuele tags erven instellingen over van de Tags-componentopties. Dit wordt behandeld in een aparte tutorial. [TeDoen] Selecteer de knop **Opties** in de werkbalk van de Tags-lijstpagina.

De configuratie van de Tags-component kan op menu-itemniveau worden overschreven.

## Tips

- Onthoud dat tags worden gebruikt voor meerdere soorten inhoud
- Je kunt meer dan één tag aan een item toevoegen
- Gebruik de Help-knop wanneer je het niet zeker weet

*Vertaald door openai.com*

