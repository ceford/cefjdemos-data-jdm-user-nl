<!-- Filename: Customising_the_Smart_Search_results_page / Display title: Slimme zoeklay-out overschrijven -->

## Resultaatpagina's

De Smart Search-component heeft vijf layoutbestanden die je kunt overschrijven om een layout naar eigen wens te maken. Om het proces te starten vanuit het beheerdersmenu:

* Selecteer **Systeem / Sitetechnieken / Cassiopeia Details en Bestanden**.
* Selecteer het tabblad **Aanmaken Overschrijvingen**.
* Selecteer **com_finder** uit het Componentenpaneel.
* Selecteer het item **Search**.
* Selecteer **html / com_finder / search** in het Editor-paneel om de lijst van aangemaakte overschrijfbestanden te bekijken.

Deze bestanden zullen niet worden beïnvloed door Joomla-updates, maar je kan eraan worden herinnerd om ze te controleren als de oorspronkelijke bronnen worden bijgewerkt.

## De Zoekweergave (Standaardindeling)

De standaardindeling van de zoekweergave is verdeeld in verschillende delen: de standaardindeling, de formulierindeling, de resultatenindeling en de sorteerindeling.

### De standaardindeling (default.php)

Deze indeling is zeer eenvoudig. Het definieert alleen de structuur waarin het zoekformulier en de zoekresultaten worden weergegeven. Deze indeling is ook verantwoordelijk voor het laden van het standaard CSS-stylesheet voor Smart Search, dat zich bevindt in `media/com_finder/css/finder.css`, dus je wilt die misschien aanpassen om je eigen CSS-regels voor Smart Search te laden.

### De formulierindeling (default_form.php)

Deze indeling definieert de code die nodig is om het zoekformulier correct te laten werken. De indeling maakt gebruik van JavaScript-code, dus je moet ervoor zorgen dat je selectors bewaart die niet gewijzigd moeten worden, tenzij je weet wat je doet.

De weergavemethode `getFields` bevat een aantal verborgen velden die nodig zijn voor betrouwbaar zoeken. De zoekterm wordt gedefinieerd door het invoerveld met de naam "q".

### De resultatenindeling (default_results.php)

Deze indeling produceert de lijst met overeenkomende resultaten voor de zoekterm. Het handelt ook de paginering af en laadt indelingen voor elk individueel zoekresultaat.

### De resultaatindeling (default_result.php)

Dit is de indeling die wordt geladen om een enkel resultaat weer te geven.

### De sorteerindeling (default_sorting.php)

Dit onderdeel is alleen aanwezig als Velden Sorteren weergeven is ingesteld op Ja en een of meer Extra Sorteervelden zijn geselecteerd in het Geavanceerd-tabblad van het menu-item.

*Vertaald door openai.com*

