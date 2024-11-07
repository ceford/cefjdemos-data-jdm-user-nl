<!-- Filename: J4.x:Module_and_Menu_Styles / Display title: Module- en Menu Stijlen -->

## Over Cascading Style Sheets

Een webpagina uitgegeven door Joomla! bestaat uit HTML-tags met stijlkenmerken in de vorm van klassedeclaraties. Bijvoorbeeld, een kop binnen een artikel zou `<h3 class="special-warning">Kijk uit!</h3>` kunnen zijn. Deze kop zou in een groter lettertype kunnen verschijnen, met verschillende kleuren voor tekst en achtergrond, en misschien een rand en waarschuwingsicoon. De klassestijlen zouden worden gedefinieerd in het user.css-bestand in de template, zoals dit:
```css
    h3.special-warning {
      color: #900;
      background-color: #fee;
      border: 1px solid #900;
      padding: 1rem;
      font-size: 2rem;
    }
```
Dit werkt omdat het user.css-stylesheet als laatste wordt geladen en eventuele stijlen die het bevat voorrang krijgen op dezelfde stijlen in eerder geladen css-bestanden. De `special-warning` stijl is niet van toepassing op andere `<h3>` tags, alleen op die met deze specifieke klasse. Het werkt binnen een artikel omdat je daar zelf de klassenaam invoert.

Maar wat als je een module of een hele pagina wilt stijlen? Bijvoorbeeld, je zou verschillende achtergrondkleuren op verschillende modules of pagina's kunnen toepassen. Of je zou de kop op je voorpagina anders kunnen stylen dan de koppen op andere pagina's. Dit alles kan worden bereikt door klassenamen toe te voegen in het modulebewerkingsformulier of het menu-itembewerkingsformulier. De stijlklassen worden vervolgens ingevoerd in het user.css-bestand.

## Module Stijlen

Dit eenvoudige voorbeeld past aangepaste stijlen toe op de Login-module en de titel ervan. De volgende schermafbeelding toont de stijlnamen die zijn ingevoerd op het tabblad Geavanceerd van het Modules: Login bewerkformulier. De Moduleklasse is ingesteld op `make-me-light-green` en de Koptekstklasse is ingesteld op `make-me-dark-green`. Houd er rekening mee dat je in klassennamen streepjes of onderstrepingen kunt gebruiken, maar spaties scheiden verschillende klassennamen.

![bewerkscherm van login module geavanceerd tabblad met aangepaste klasse](../../../en/images/templates/templates-edit-module-style.png)

De volgende stijlverklaringen worden gebruikt in het user.css-bestand:
```css
    .make-me-light-green {
      background-color: #efe;
      border-color: darkgreen;
    }
    .make-me-dark-green {
      color: darkgreen;
      border-color: #264f71;
    }
```
Let op het punt (.) dat wordt gebruikt in css om een klasse met die naam te definiëren. Het punt mag niet worden gebruikt in het modulegegevensinvoerscherm. Het resultaat in dit voorbeeld is als volgt:

![siteweergave van de aangepaste module met ontwikkelaarstools](../../../en/images/templates/templates-edit-module-style-result.png)

De onderkant van de afbeelding toont het ontwikkelaarstoolspaneel van de browser met het omhulsel-`<div>`-tag van de Login-module geselecteerd. Je kunt zien dat de aangepaste Moduleklasse-stijl is toegevoegd aan de stijlen die al in de moduletemplate zijn gedefinieerd. De volgende regel toont de `<h3>`-tag, ook met de aangepaste Koptekstklasse toegevoegd aan al gedefinieerde stijlen.

Je vindt deze modulestijl misschien wel of niet leuk! Maar dit is slechts een les in hoe je het doet, niet in wat een goed kleurenschema maakt!

## Pagina Stijlen

Er zijn verschillende manieren om het algemene uiterlijk van een pagina aan te passen. Alles werkt via de Menus: Bewerken Item formulier:

- Het tabblad Details heeft een Template Stijl optie waarmee je een specifiek sjabloon kunt selecteren om te gebruiken.
- Het tabblad Blog Layout heeft een Toonaangevende Artikel Klasse en Artikel Klasse velden waarin je een klassennaam kunt invoeren.
- Het tabblad Opties heeft Kies een Layout veld waarmee je kunt kiezen uit beschikbare layouts voor alle items.
- Het tabblad Koppelingstype heeft velden voor een Link Klasse, een Link Icoon Klasse en een Afbeelding Klasse.
- Het tabblad Paginadisplay heeft velden voor een Pagina Klasse.

Het is het laatste in deze lijst dat in dit artikel wordt behandeld. Wat gebeurt er met `make-me-aliceblue` ingevoerd in dit veld? En het volgende wordt ingevoerd in user.css:
```css
    .make-me-aliceblue {
      background-color: aliceblue;
    }
```
De klasse wordt toegevoegd aan de body tag van de pagina:

![site uiterlijk van de aangepaste pagina met ontwikkelaarstools](../../../en/images/templates/templates-edit-page-class-result.png)

QED!

*Vertaald door openai.com*

