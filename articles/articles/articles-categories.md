<!-- Filename: J4.x:Create_and_Manage_Article_Categories / Display title: Artikelen: Categorieën  -->

## Inleiding

Stel je een bibliotheek voor zonder een classificatiesysteem: boeken worden gewoon op de planken geplaatst in de volgorde waarin ze worden ontvangen. Dat is niet erg handig als de bibliotheek miljoenen boeken heeft en je zoekt naar iets over Geschiedenis, Tuinieren of Wetenschap. Hetzelfde argument geldt voor artikelen. Als je tientallen, honderden of duizenden artikelen hebt, heb je echt een methode nodig om ze te classificeren zodat je gemakkelijk kunt vinden wat je nodig hebt. Daar zijn Categorieën voor bedoeld.

Een Joomla!-categorie kan zowel artikelen als subcategorieën bevatten in een boomachtige structuur die op elke diepte genest kan worden, hoewel het onwaarschijnlijk is dat je verder wilt gaan dan een diepte van drie of vier. Als je artikelen bijvoorbeeld over de Natuur gaan, zou je ze als volgt kunnen classificeren:

- Dieren
  - Vogels
    - Haviken
    - Vinken
    - Meeuwen
  - Zoogdieren
    - Apen
    - Monniken
    - Knaagdieren
- Planten
  - Bloemen
    - Madeliefjes
    - Rozen
  - Bomen
    - Eiken
    - Iepen

In dit voorbeeld kan de categorie *Dieren* artikelen bevatten over dieren in het algemeen, evenals subcategorieën voor artikelen over verschillende soorten dieren.

Joomla biedt een standaardcategorie genaamd Niet-gecategoriseerd. Elk artikel dat niet aan een specifieke categorie wordt toegewezen die je hebt aangemaakt, wordt een lid van de categorie Niet-gecategoriseerd. Je maakt categorieën aan zoals nodig om aan te sluiten bij de aard van je artikelen.

Een artikel kan slechts in één categorie staan. In sommige gevallen is dat niet helemaal genoeg. Stel je bijvoorbeeld voor dat je op zoek bent naar boeken van allerlei soorten die in een bepaalde taal zijn geschreven, of alle planten die giftig zijn, of alle dieren die gevaarlijk zijn. Dat is waar Tags van pas komen. Deze worden elders behandeld.

### Het Gebruik van Categorieën

Op de *Artikelen*-pagina van de beheerder heeft het formulier *Filteropties* een vervolgkeuzelijst **- Selecteer Categorie -** die een categoriebos weergeeft waarmee je kunt filteren op artikelen in een geselecteerde categorie. Je kunt ook *Categorieblog*- en *Categorielijst*-menu-itemtypen creëren om artikelen uit een geselecteerde categorie aan sitebezoekers te tonen.

## Categorieën en Subcategorieën Toevoegen

Er zijn verschillende routes naar de *Artikelen: Nieuwe Categorie* pagina:

- Via het **Home Dashboard** Selecteer het **plus (+) symbool** rechts van de 
  *Artikelen Categorieën* link. Deze leidt naar de *Artikelen: Categorieën*
  lijstpagina.
- Via het **Beheerdersmenu** Selecteer het *Inhoud* item om de lijst uit te vouwen 
  en selecteer vervolgens het **plus (+) symbool** rechts van de *Categorieën* 
  link.
- Via het **Inhoud Dashboard** Selecteer het Dashboard icoon rechts van de
  *Inhoud* link in het Beheerdersmenu en selecteer vervolgens in het dashboard 
  *Inhoud* paneel het **plus (+) symbool** rechts van de *Categorieën* link.
- Via **Artikelen: Categorieën** Volg een van de routes naar de lijstpagina en
  selecteer de **Nieuw** knop in de Toolbar.

De volgende screenshot toont de Home Dashboard *Artikelcategorieën* link naar 
de lijst van categorieën en het aangrenzende *Plus Symbool* dat leidt naar het 
*Artikelen: Nieuwe Categorie* formulier.

![Het categorie toevoegen icoon gemarkeerd in het home dashboard](../../../en/images/articles/category-add-via-home-dashboard.png)

## De Artikelen: Nieuwe Categorie Formulier

![Het formulier voor nieuwe categorie bijwerken in de artikelen](../../../en/images/getting-started/article-category-edit.png)

De bovenstaande screenshot toont het ingevulde formulier. Er zijn slechts twee velden die enige inhoud nodig hebben. Alles andere heeft standaard- of nullwaarden die je voorlopig kunt laten en later kunt invullen als dat nodig is.

- **Titel** Dit is het enige verplichte veld. Het moet kort maar beschrijvend zijn voor de categorie.

### Het Categorie-tabblad

- **Beschrijving** Hoewel niet verplicht, kan dit veld worden weergegeven op sitecategorie-lijstpagina's die worden beheerd door menu-items. Mogelijk moet je later terugkomen en de Beschrijving bijwerken.
- **Ouder** Als ingesteld op *- Geen ouder -* is dit nieuwe item een potentiële hoofdcategorie voor andere categorieën. Als een andere categorie is geselecteerd als ouder, is dit nieuwe item een subcategorie.
- **Status** Standaard is een nieuwe categorie ingesteld op *Gepubliceerd*. Je kunt de status van een categorie wijzigen naar *Gepubliceerd*, *Gedepubliceerd*, *Gearchiveerd* of *Verwijderd*.
  [Te Doen] Uitleggen wat er gebeurt als een Categorie wordt Gedepubliceerd...
- **Toegang** Standaard is toegang ingesteld op *Openbaar*. Andere opties om toegang te beperken zijn *Gast*, *Geregistreerd*, *Speciaal* en *Supergebruikers*.
  [Te Doen] Uitleggen hoe Toegang tot een Categorie kan worden gebruikt...
- **Taal** In meertalige sites zal het instellen op *Alle* de nieuwe categorie onafhankelijk maken van de site-taal. Als ingesteld op een specifieke taal, zal het alleen beschikbaar zijn op pagina's die die taal gebruiken.
- **Tags** Als je ze gebruikt, kun je een of meer tags aan de categorie toevoegen. Tags instellen op categoriëniveau is een goede manier om consistentie te behouden. Voor deze tutorial is een *Natuur* tag aangemaakt en gebruikt om lijsten te filteren om alleen items gerelateerd aan de tutorials weer te geven.
- **Notitie** en **Versie Notitie** Gebruik deze om relevante notities toe te voegen indien nodig.

### Het Opties-tabblad

Instellingen in dit tabblad beïnvloeden het uiterlijk van deze Categorie op sitepagina's.

- **Layout** Dit verwijst naar de plaatsing van inhoud op de pagina. Er kan een keuze zijn uit layouts afhankelijk van de component en sjabloon die worden gebruikt.
  [Te Doen] Voorbeelden...
- **Afbeelding** Je wilt misschien een afbeelding gebruiken als een pictogram zodat deze categorie direct herkenbaar is in een lijst met categorieën. Als deze voor zo'n doel wordt gebruikt, is een *Afbeeldingsbeschrijving (Alt-tekst)* niet nodig, maar moet het *Geen Beschrijving* selectievakje worden aangevinkt.

### Opslaan & Sluiten

- **Opslaan & Sluiten** Om het bewerken van deze categorie te voltooien. Of in de uitklaplijst...
  - **Opslaan & Nieuw** Sla deze categorie op en open een nieuw bewerkingsformulier voor een nieuwe categorie. Je wilt bijvoorbeeld beginnen met het bouwen van een categoriebomenstructuur door een *Apes* categorie toe te voegen met *Zoogdieren* als ouder.
  - **Opslaan naar Menu als Lijst** ...
  - **Opslaan naar Menu als Blog** ...
  - **Opslaan als Kopie** ...

Het sluiten van het bewerkingsformulier leidt naar de **Artikelen: Categoriën** lijstpagina.

![Een categoriënlijst gefilterd door Natuur-tag](../../../en/images/articles/categories-list.png)

### Opslaan naar Menu als Lijst

Het selecteren van dit item uit de *Opslaan & Sluiten* uitklaplijst zal het categorie-bewerkingsformulier opslaan en sluiten en een nieuw menu-itemformulier openen met alle gegevens die nodig zijn om een *Categorielijst* voor deze categorie te maken. Je wilt misschien de *Titel* wijzigen. Bijvoorbeeld, het kan *Zoogdier artikelen lijst* zijn om duidelijk te maken dat het waarschijnlijk een lijst van artikelen is.

Probeer in het tabblad *Paginaweergave* het veld *Pagina-kop weergeven* in te stellen op *Weergeven*. Dit toont *Zoogdier artikelen lijst* als een dikgedrukt kopje bovenaan de pagina, wat het een over het algemeen completere uitstraling geeft.

### Opslaan naar Menu als Blog

Het selecteren van dit item uit de *Opslaan & Sluiten* uitklaplijst zal het categorie-bewerkingsformulier opslaan en sluiten en een nieuw menu-itemformulier openen met alle gegevens die nodig zijn om een *Categorie Blog* voor deze categorie te maken. Je wilt misschien de *Titel* wijzigen. Bijvoorbeeld, het kan *Zoogdier artikelen blog* zijn, zodat de nieuwste artikelen over zoogdieren worden uitgelicht.

Probeer in het tabblad *Paginaweergave* het veld *Pagina-kop weergeven* in te stellen op *Weergeven*. Dit toont *Zoogdier artikelen blog* als een dikgedrukt kopje bovenaan de pagina, wat het een over het algemeen completere uitstraling geeft.

De volgende screenshot toont de weergave op de site van een categorie blogpagina in ontwikkeling.

![Blogpagina van de zoogdiercategorie](../../../en/images/articles/article-mammals-articles-blog-site-view.png)

## Tips

- Je kunt ook artikelcategorieën maken vanuit een artikel.
- Onthoud dat je een artikel slechts aan één categorie kunt toewijzen.
- Aangezien zowel hoofdcategorieën als subcategorieën verdere
  subcategorieën kunnen hebben, plan en organiseer categorieën zorgvuldig. Een ingewikkelde
  categorie-hiërarchie kan een uitdaging worden om te beheren.
- Een andere methode om content in Joomla te groeperen is het gebruik van de
  **Tags**-component, waarmee je meerdere tags aan je artikelen kunt toevoegen.
  Het gebruik van categorieën en tags kan helpen het aantal
  subcategorieën te minimaliseren en biedt een efficiënte manier om website-inhoud
  te structureren en bezoekers meer mogelijkheden te bieden om door de website-inhoud te navigeren.

