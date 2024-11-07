<!-- Filename: jdocmanual?manual=user&heading=modules&filename=module-styles.md / Display title: Module Stijlen   -->

## Stijlconcepten

Een invoerformulier voor modulegegevens heeft een **Geavanceerd** tabblad. De velden variëren afhankelijk van het type module, en je kunt dit zelf zien door een Menu-module te selecteren en deze te vergelijken met een Inlogmodule of Broodkruimels-module. Je ziet de volgende drie formuliervelden met betrekking tot styling:

* **Moduleklasse** is een tekstveld waarmee je je eigen CSS-klasse kunt toevoegen aan de modulecontainer-tag, meestal een `<div>`.
* **Headerklasse** is een tekstveld waarmee je je eigen CSS-klasse kunt toevoegen aan de kop-tag, standaard een `<h3>`-tag.
* **Modulestijl** is een lijst waarmee je een van een aantal standaardstijlen kunt selecteren. De lijst bevat geen, html5, outline, table, card en noCard. De standaard is card van de Cassiopeia-sjabloonstijlen.

Je kunt de *Modulestijl* opties uitproberen door een module te bewerken en de waarde te wijzigen om te zien wat het doet met de weergave van de site.

* **html5** geeft `<div class="moduletable ">`
* **geen** verwijdert de buitenste `<div>` volledig en ook de module `<h3>`-tag.
* **outline** geeft `<div class="mod_preview_info">`, met positie- en stijl-informatie ter vervanging van de module `<h3>`-tag.
* **tabel** geeft een tabelindeling beginnend met `<table class="moduletable ">` waarbij de voormalige h3-tag nu een `<th>`-tag is.
* **kaart** geeft `<div class="sidebar-right card ">`, de standaard.
* **geenKaart** geeft `<div class="sidebar-right no-card ">`

## De Moduleklasse

Op dit punt moet je iets weten over Cascading Style Sheets of CSS. Als je een enkel woord invoert in het veld Moduleklasse, bijvoorbeeld **groen**, aangezien CSS-klassen volgens de conventie allemaal kleine letters zijn, en met de Modulestijl ingesteld op **overgenomen**, bevat de uitvoer `<div class="sidebar-right card green">`.

Er is geen zichtbare verandering in de weergave van de site omdat de klasse groen niet is gedefinieerd. Om het te definiëren, maak je een invoer in het bestand user.css van de template.

Vanuit het beheerdersmenu:
* Selecteer **Systeem / Site-sjablonen / Cassiopeia-sjablonen en bestanden**.
* Selecteer **Nieuw bestand** in de *Werkbalk*
* Selecteer **css** in de linker kolom, de bestemming voor het nieuwe bestand.
* Typ **user** in het veld Bestandsnaam.
* Selecteer **css** in de lijst met bestandstypen.
* Selecteer de knop **Aanmaken**.

Je kunt nu de css-map openen om het user.css-bestand te vinden en te openen voor bewerking. Voer deze stijlverklaringen in en let op de Amerikaanse spelling van *color*:
```
.sidebar-right.card.green {
    background-color: #ddffdd;
}
.sidebar-right.card.green .card-body {
    background-color: #eeffee;
}
```
De stijl had alleen `.green` kunnen gebruiken, maar dat zou andere tags met die stijl op andere pagina's kunnen beïnvloeden.

## De Headerklasse

Ga terug naar het module-bewerkingsformulier en voeg **blauw** toe in het veld Headerklasse. De module heeft geen zichtbare verandering op de site, maar de kop wordt nu weergegeven als `<h3 class="card-header blue">`. Ga terug naar het bewerken van het user.css-bestand om een invoer toe te voegen voor de opmaak van de kop:

```
.card-header.blue {
    color: navy;
}
```

De modulekop is nu in donkerblauw. Er zijn verschillende manieren om kleuren in CSS op te geven. De meest voorkomende zijn hexadecimaal en standaardkleurnamen. Lees er elders alles over!

## CSS Uitdaging

* Verander de module-randkleur naar marineblauw!
* Verander de onderste rand van de koptekst ook.
* Pas deze stijl toe op meerdere modules in plaats van één tegelijk.

![Voorbeeld van het Gearchiveerde Artikelen Module](../../../en/images/modules/modules-archived-articles.png)

*Vertaald door openai.com*

