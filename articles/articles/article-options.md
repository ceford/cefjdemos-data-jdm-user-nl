<!-- Filename: J6.x:_Article_Options / Display title: Artikel: Bewerken - Opties  -->

## Inleiding

Het woord *Opties* is dubbelzinnig in Joomla! Het is soms verwisselbaar met *Parameters* en de meeste componentenlijstweergaven hebben een *Opties* knop in de werkbalk. Dat leidt naar een Opties pagina waar parameters voor het component als geheel worden ingesteld. Daarnaast hebben veel component item-bewerkingsformulieren een tabblad genaamd *Opties* dat wordt gebruikt om parameters voor dat ene item in te stellen.

Dit artikel gaat over het *Opties* tabblad in het *Artikel: Bewerken* formulier. Hier worden parameters ingesteld die van invloed zijn op het algemene uiterlijk van het artikel dat wordt bewerkt. De opties voor artikelen als geheel worden behandeld in een apart artikel.

## Schermafbeelding

Het tabblad *Opties* van het formulier *Artikel: Bewerken* bevat een reeks panelen, meestal met een keuze uit *Gebruik Global (Verbergen of Tonen)*, *Verbergen* of *Tonen*. De volgende gedeeltelijke schermafbeelding toont de algemene indeling.

![Bewerkingsopties tabblad voor artikel](../../../en/images/articles/articles-edit-options-tab.png)

## Lay-outpaneel

Een artikel, of een deel ervan, kan als een enkele pagina verschijnen of in een categorie bloglay-out, aangestuurd door een menu-item. In een blogmenu-item hebben de meeste lay-outvelden de opties *Gebruik Globaal*, *Ja/Nee* of *Tonen/Verbergen* en *Gebruik Artikelinstellingen*. De opties in dit paneel hebben geen effect in bloglay-outs tenzij de optie *Gebruik Artikelinstellingen* is geselecteerd in het menu-item.

Anders beïnvloeden deze opties het uiterlijk van het enkele artikel dat bewerkt wordt.

- **Lay-out** In een standaardinstallatie worden de eerste twee keuzes aangeboden:
  - **---Vanuit Globale Opties--- / Gebruik Globaal** Dit verwijst naar de 
    *Artikelen: Opties* instelling die beschikbaar is via de *Opties* knop in de 
    Werkbalk van de *Artikelen* lijstweergave. De *Kies een Lay-out* waarde is 
    ingesteld op *Standaard*.
  - **---Vanuit Component--- / Standaard** Dit verwijst naar de instelling in de
    *Artikelen: Opties* instellingen. In een standaardinstallatie is dit in feite
    hetzelfde als de *Gebruik Globaal* optie. Maar als er een overschrijving 
    bestaat die default.php heet, dan wordt die overschrijving gebruikt voor de 
    lay-out.
  - **---Van cassiopeia Sjabloon--- / overschrijvingsnaam** Als er een sjabloon-
    overschrijving is gemaakt met een andere naam dan *standaard*, verschijnt deze 
    hier en kan als alternatieve lay-out worden geselecteerd.
- **Titel** Het is normaal om de titel van een artikel te tonen, maar er kunnen 
  omstandigheden zijn waarin dat niet gepast is. Selecteer *Verbergen* om de 
  artikel titel weg te laten uit de paginaweergave.
- **Gekoppelde Titels** Het standaardgedrag is om een artikel titel een link 
  te maken naar het artikel waar het verschijnt in blog- of lijstlay-outs. Deze 
  instelling wordt aangestuurd door het menu-item. Het kan worden ingesteld op 
  *Gebruik Globaal (Ja)*, *Gebruik Artikelinstellingen*, *Nee* of *Ja*. Als het 
  menu-item is ingesteld op *Gebruik Artikelinstellingen* dan wordt de 
  *Gekoppelde Titels* waarde in het artikel gebruikt. Anders heeft deze instelling 
  geen effect. Als de titel niet is gekoppeld, kun je een *Lees Meer* link 
  gebruiken om toegang tot het artikel te krijgen vanuit een blog- of 
  lijstlay-out.
- **Tags** Tags tonen of verbergen op de enkele artikelpagina.
- **Inleidende Tekst** De inleidende tekst tonen of verbergen op de enkele 
  artikelpagina. Er zijn bepaalde omstandigheden waarin je misschien een geheel 
  andere inleidende tekst voor bloglay-outs wilt hebben die is weggelaten in de 
  volledige artikeltekst.
- **Positie van Artikelinfo** Dit verwijst naar het blok informatie over een 
  artikel met als kop *Details* en met daarin de informatie *Auteur*, *Categorie*, 
  *Gepubliceerd* en *Hits*. De standaardinstelling is om dit boven de artikeltekst 
  te plaatsen. Stel in op Onder om het onder de artikeltekst te verplaatsen in een 
  enkele artikelweergave. Als ingesteld op *Gesplitst* verplaatst het *Hits* 
  item zich onder de artikeltekst.
- **Artikelinfo Titel** Het woord *Details* tonen of verbergen boven de lijst van 
  artikelinformatie in de enkele artikelweergave.

## Categoriepaneel

De velden in dit paneel werken zoals je zou verwachten. In blogweergaven hebben de instellingen voor menu-items voorrang, tenzij deze zijn ingesteld op *Artikelinstellingen gebruiken*.

- **Categorie** Toon of verberg de categorienaam.
- **Link Categorie** Link (Ja of Nee) de categorienaam. Als dit is ingesteld op *Ja*, wordt de categorienaam gelinkt aan de categorieblog.
- **Bovenliggende Categorie** Als dit is ingesteld op Ja, verschijnt de bovenliggende categorie als een apart item boven de categorie in de artikelinformatie *Details* in de lay-out van een enkel artikel.
- **Link Bovenliggende Categorie** Als dit is ingesteld op Ja, linkt de naam van de bovenliggende categorie naar de bijbehorende categorieblogpagina.

## Associatiespaneel

Dit paneel is alleen aanwezig op meertalige sites.

- **Associaties** Als dit op Weergeven is ingesteld, wordt er een extra item geplaatst in de artikelinformatie dat begint met *Ook beschikbaar:* gevolgd door vlaggen om de versies van dit artikel in andere talen te vertegenwoordigen.
- **Afbeeldingsvlaggen gebruiken** Dit item verschijnt als *Associaties* is ingesteld op *Weergeven*. De standaardinstelling *Ja* toont knoppen als taalvlaggen. Het alternatief *Nee* toont knoppen als taalcodes, bijvoorbeeld *en-GB*.  

## Auteurs paneel

- **Auteur** Toon of verberg de naam van de auteur van dit artikel in de weergave
  van een enkel artikel. De regel in de artikelinformatie luidt 
  *Geschreven door: Auteurnaam*
- **Link naar contactpagina van auteur** Ja of nee om de Auteurnaam te linken naar de
  contactpagina van de auteur, indien deze bestaat.

## Datum paneel

Joomla-artikelen slaan meerdere data op. Als ze worden weergegeven, verschijnen elk van de volgende als aparte regels in de artikelinformatie voor een enkel artikel. Vergeet niet, bloglayouts gebruiken de instellingen van het menu-item, tenzij het is ingesteld op *Gebruik artikelinstellingen*. Het datumformaat is 03 november 2024, maar dat kan worden aangepast ...[TeDoen]

- **Aanmaakdatum** Standaard verborgen.
- **Wijzigingsdatum** Standaard verborgen.
- **Publicatiedatum** Standaard weergegeven.

## Optiepaneel

- **Navigatie** Voor een artikel dat deel uitmaakt van een reeks artikelen in een categorie, zijn er *Vorige* en *Volgende* knoppen onder de artikeltekst om naar de vorige of volgende pagina's te navigeren. Als ingesteld op *Verbergen* worden de navigatieknoppen niet weergegeven op pagina's met een enkel artikel.
- **Hits** Het totaal aantal keren dat het artikel als enkel artikel is weergegeven, getoond in de artikelinformatielijst.
- **Onautoriseerde Links** Dit heeft invloed op blogindelingen, dus het relevante categorieblogmenu-item moet de waarde *Opties: Ongeautoriseerde Links* ingesteld hebben op *Ja* of *Gebruik Artikelinstellingen*. Als dan de *Toegang* van dit artikel is ingesteld op *Geregistreerd* en de instelling in het artikel niet *Nee* is, zal de *Introtekst* voor het artikel in de blogindeling worden weergegeven, maar het label van de Lees meer-knop zal zijn *Registreer om verder te lezen...*. Klikken op de Lees meer-link vereist inloggen om de volledige artikelinhoud te bekijken.
- **Positie van de links** Dit verwijst naar de positionering van de links in het tabblad Afbeeldingen en Links, Links A, B en C. De standaardpositie is boven de artikeltekst. Deze optie staat toe dat de links onder de artikeltekst worden geplaatst of helemaal niet worden weergegeven.
- **Lees Meer Tekst** De normale tekst, *Lees Meer:* gevolgd door de artikelkop is afkomstig van de taal's sleutel/tekstwaarden. Een aangepaste vervanging voor alleen dit artikel kan hier worden ingevoerd, bijvoorbeeld *Bekijk volledig artikel:* gevolgd door de artikelkop.
- **Browser Pagina Titel** De paginatitel is meestal de artikelkop. Als dat ongemakkelijk is, kan hier een alternatieve paginatitel worden ingevoerd voor gebruik op de pagina van het enkele artikel. Deze verschijnt in het browsertabblad en het `<head>...</head>`-gebied van de pagina. Deze zal worden gebruikt door zoekmachines.
*Vertaald door openai.com*

