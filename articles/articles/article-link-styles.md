<!-- Filename: J5.x:Add_a_class_selector_to_the_create_link_dialog / Display title: Artikel: Bewerken - Koppelingsstijlen -->

## Beschrijving

Aangepaste linkklassen die zijn toegevoegd aan de TinyMCE-editoropties, stellen je in staat om snel een artikel-link om te zetten in een knop of andere visuele effecten toe te voegen zonder de HTML-code direct te hoeven aanpassen.

### Stappen om de Klasse Selector te Gebruiken

1. Ga vanaf het Startdashboard naar de lijst met Plugins en vind de TinyMCE-plugin.
2. Open de TinyMCE-plugin en met het Plugin-tabblad geselecteerd, scrol je naar de onderkant.
3. Voeg klassen toe aan de *Link Classes List*. Bijvoorbeeld Bootstrap-klassen om stijlvolle knoppen te maken. Mogelijk moet je de lijst van links naar rechts scrollen of de schermvergroting wijzigen om de knoppen toevoegen, verwijderen en ordenen aan het einde te zien.
4. Opslaan & Sluiten.

![Set link classes in tinymce](../../../en/images/articles/article-edit-link-style-tinymce.png)

Je kunt voorbeelden van sjablonen vinden die Bootstrap native gebruiken in de officiële [Bootstrap Documentatie](https://getbootstrap.com/docs/5.3/components/buttons/)

Hier zijn enkele klassen die je kunt gebruiken voor Bootstrap-knopvarianten:

- `btn btn-primary` voor een primaire knop
- `btn btn-secondary` voor een secundaire knop
- `btn btn-success` voor een successknop
- `btn btn-danger` voor een gevarenknop
- `btn btn-warning` voor een waarschuwingsknop
- `btn btn-info` voor een infoknop
- `btn btn-light` voor een lichte knop
- `btn btn-dark` voor een donkere knop
- `btn btn-link` voor een linkknop

#### Alternatieven voor omtrekknoppen

Je kunt ook de varianten van de omtrekknop gebruiken:

- `btn btn-outline-primary` voor een omrande primaire knop
- `btn btn-outline-secondary` voor een omrande secundaire knop
- … (enz.)

#### Voor knopformaten voeg je deze klassen toe

- `btn-lg` voor een grote knop
- `btn-sm` voor een kleine knop

**Voorbeeld:** `btn btn-dark btn-lg` (een grote donkere knop)

## Een link maken in een artikel

1. Open een artikel en selecteer een stuk tekst, een woord of een zin voor het maken van een link.
2. Selecteer het Link-pictogram dat verschijnt wanneer je tekst selecteert.
3. Voer de URL in voor de link.
4. Selecteer onderaan in het linkcreatiedialoogvenster een van de geconfigureerde klassen.
5. Bewaar de Link.
6. Bewaar het Artikel.
7. Bekijk een Voorvertoning van het Artikel.

![Apply link style in an article](../../../en/images/articles/article-edit-link-style-apply.png)

En dit is een voorbeeld waar de Link Button-klasse was ingesteld op `btn btn-sm btn-outline-info` en de gelinkte tekst is *Bootstrap*:

![Preview of a custom Link Button](../../../en/images/articles/article-edit-link-style-preview.png)

## Geavanceerd Gebruik: Aangepaste Klassen Toepassen

Deze functie is niet beperkt tot Bootstrap-klassen. Je kunt ook je eigen aangepaste CSS-klassen toepassen voor specifieke behoeften. Bijvoorbeeld, je kunt een pictogram toevoegen vóór de link met een hover-effect. Dit maakt het gemakkelijk om links te stijlen zonder dat de broncode van het artikel hoeft te worden aangepast.  
*Vertaald door openai.com*

