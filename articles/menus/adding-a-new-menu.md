<!-- Filename: J4.x:Adding_a_New_Menu / Display title: Een Nieuw Menu Toevoegen -->

## Introductie

Om toegang te krijgen tot inhoud op je Joomla! website moeten items aan een Menu worden toegewezen. Een standaardinstallatie van Joomla! maakt een **Hoofdmenu** voor je aan. In veel gevallen zul je slechts één menu gebruiken, maar je kunt er meer dan één hebben. Dit stelt je in staat om menu's te maken voor verschillende soorten inhoud, verborgen inhoud, rol specifieke inhoud en meer.

Er zijn drie stappen bij het maken van een bruikbaar menu:

1. Maak het Menu. Dit is een container voor Menu-items.
2. Maak een Menu Module. Hiermee kun je het Menu op een pagina plaatsen.
3. Maak Menu-items. Dit zijn de door de gebruiker selecteerbare items die naar specifieke pagina's leiden.

Deze screenshot toont de beschikbare menu's in een meertalige site. In een initiële Joomla-installatie is er een enkel *Hoofdmenu*.

![Menu's lijst](../../../en/images/menus/menus-manage.png "Menu's lijst")

De lijst stelt je in staat om op een van de groene of rode knoppen te klikken om direct naar de lijst van menu-items in dat menu en die staat te gaan.

Deze tutorial behandelt de stappen die betrokken zijn bij het maken van een Menu in een Joomla! site.

## Een Nieuw Menu Maken

Gebruik een van de volgende stappen om een nieuw menu te maken:

- Selecteer in het Administrator-menu het *Menu Dashboard-pictogram* om naar het Menu-dashboard te gaan en selecteer vervolgens **Beheren**. Of...
- Breid in het Administrator-menu de sectie *Menu's* uit en selecteer vervolgens **Beheren**.
- Selecteer de knop **+ Nieuw** in de werkbalk.
- Vul in het gegevensinvoerformulier voor het menu de volgende velden in:
  - **Titel**: Een geschikte titel voor het menu. Dit wordt gebruikt om het menu te identificeren in de Menu Manager.
  - **Unieke Naam**: Dit moet een unieke identificatienaam zijn die door Joomla! wordt gebruikt om dit menu te identificeren. Spaties zijn niet toegestaan, maar u mag het '-' teken gebruiken zoals in resources-menu.
  - **Beschrijving**: Hoewel het niet vereist is, is dit vaak nuttig op een site met veel menu's. Het verschijnt onder de *Titel* in de menulijst zoals hierboven geïllustreerd.<br>
    ![Nieuw Menu](../../../en/images/menus/menus-new.png "Nieuw Menu")
- **Opslaan & Sluiten**

In de lijst met menu's heeft het nieuw gemaakte menu een knop met het label **Voeg een module toe voor dit menu**, wat de volgende stap in het maken van een menu is. U kunt beginnen met het toevoegen van menu-items en later terugkomen om de menumodule te maken.

## Maak een Module voor het Menu

In de lijst met menu's kun je in de kolom *Gekoppelde Modules* een bestaand menumodule selecteren voor bewerkingsdoeleinden. Je kunt deze bekijken en vervolgens *Sluiten* zonder wijzigingen aan te brengen. Voor je nieuwe menu moet je de knop **Voeg een module toe voor dit menu** selecteren om een modaal venster te openen met het gegevensinvoerformulier van de menu-module.

![Gegevensinvoerformulier van de menu-module](../../../en/images/menus/menus-module.png "Gegevensinvoerformulier van de menu-module")

Velden om in te vullen:

* Het veld **Titel** is verplicht, dus maak een beschrijvende titel aan.
* De knop **Toon Titel** aan de rechterkant wordt gebruikt om de moduletitel *te tonen* of *te verbergen*, een algemene functie van alle modules.
* Het veld **Selecteer Menu** moet de naam tonen van het menu dat je zojuist hebt gemaakt.
* Het veld **Positie** wordt gebruikt om een positie in je sjabloon te selecteren waar je wilt dat je menu verschijnt.
* Selecteer **Opslaan & Sluiten** zodra de essentiële informatie is toegevoegd.

Er zijn veel opties om uit te kiezen in het formulier *Module-instellingen bewerken*. Deze worden vermeld in het Helpmenu dat beschikbaar is in het formulier *Module: Bewerken*. Dit is hetzelfde formulier, maar dan op een normale pagina in plaats van in een modaal venster. Je krijgt er toegang toe via het Beheerdersmenu, de route Inhoud / Site-modules naar de lijst met site-modules.

Opmerking: hoe je menu eruitziet, hangt af van de opmaak van je sjabloon.

## Items toevoegen aan het Menu

Om links in je menu te maken, moet je **Menu Items** toevoegen. Er zijn veel
*Menu-itemtypen* in Joomla en componenten van derden kunnen meer typen toevoegen. Voor
deze tutorial wordt een link naar een enkel artikel toegevoegd.

Je kunt van tevoren een artikel maken of een artikel creëren tijdens het
menucreatieproces. In beide gevallen moet het artikel bestaan voordat er een menu-item
voor kan worden gemaakt. In dit voorbeeld krijgt het artikel ook de naam
*Resources*. Het is bedoeld om een lijst van links naar PDF-bestanden te bevatten.

In de **Menu's** lijst, selecteer vanuit de **Menu Items** kolom het icoon voor het
nieuw aangemaakte menu, *Resources* in dit voorbeeld. Aanvankelijk zijn er geen menu
items, dus zegt de lijst slechts *Geen overeenkomende resultaten*.

- Selecteer de **Nieuw** knop van de werkbalk om een nieuw menu-item te creëren.
- Voeg in het **Titel** veld de titel toe die je in het Menu wilt laten zien.
- In het **Menu-itemtype** veld selecteer je de **Selecteer** knop om een modale
dialoog te openen met een lijst van componenten. Elk heeft een vervolgkeuzelijst die
een lijst van beschikbare menu-itemtypen onthult.
  - Selecteer **Artikelen** en vervolgens **Enkel Artikel**.
- In het **Selecteer Artikel** veld: **Of:**
  - Gebruik de **Selecteer** knop om een bestaand artikel te selecteren. Het zal
  een lijst van artikelen openen om uit te kiezen. **Of:**
  - Gebruik de **Creëer** knop om een nieuw artikel te maken. Het enige dat je hoeft
  in te voeren is de artikel titel. Het is waarschijnlijk het beste om gedetailleerde
  inhoud later toe te voegen.
- Controleer of het **Menu** veld is ingesteld op het nieuwe Menu.
- Het **Status** veld moet worden ingesteld op **Gepubliceerd**.
- Selecteer **Opslaan & Sluiten**.

![Gegevensinvoerformulier voor menu-items](../../../en/images/menus/menus-single-article.png "Gegevensinvoerformulier voor menu-items")

Voeg indien nodig meer Menu Items toe aan het nieuwe Menu.

Zodra items aan het Menu zijn toegevoegd, controleer of het Menu op de website in de juiste positie wordt weergegeven.

![Menu weergave](../../../en/images/menus/menus-display.png "Menu weergave")

*Vertaald door openai.com*

