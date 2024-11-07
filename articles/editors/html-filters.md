<!-- Filename: Entering_raw_HTML_in_editors / Display title: HTML-filters  -->

## HTML Textarea Tag

In HTML staat een invoerveld voor meerdere regels bekend als een textarea. Alle tekst tussen de start- en eindtags wordt weergegeven als tekst die HTML-opmaak kan bevatten.
Voorbeeld:
```
<textarea><p class="poem">De snelle bruine vos<br>
springt over de luie hond.</textarea>
```
Editors, zoals TinyMCE of Code Mirror, gebruiken JavaScript om de textarea te overlayen met een andere weergave en zo WYSIWYG-gegevensinvoer of syntaxisaccentuering mogelijk te maken. De Schakelknop onder een editorveld wisselt tussen de textarea-weergave en de WYSIWYG-weergave.

Editorweergaven worden gebruikt voor de inhoud van Artikelen en sommige Modules. U moet er echter van bewust zijn dat niet alle HTML-tags en -attributen (zoals class="xyz") voor alle gebruikers zijn toegestaan. Sommige of alle kunnen verdwijnen wanneer u de inhoud van een textarea of bewerkveld opslaat.

Dit wordt veroorzaakt door filtermechanismen, hetzij in de Joomla! Globale Configuratie of in de editorconfiguratie. Een editorfilter kan worden omzeild door *Geen Editor* te selecteren in uw *Gebruikersprofiel* instellingen. U kunt de globale filters niet omzeilen, maar u kunt ze wijzigen om aan de behoeften van uw site te voldoen.

## Gebruikerseditor-selectie

Je kunt een van de beschikbare editors selecteren, inclusief Geen, via je Gebruikersprofiel dat beschikbaar is via het menu Gebruikersaccount / Profiel bewerken rechtsboven in het beheerdersscherm. Het formulier Profiel bewerken bevat een tabblad Basisinstellingen met een veld om een editor te selecteren. Dit staat normaal ingesteld op *- Gebruik standaard -*, wat meestal TinyMCE is. Je kunt *Editor Geen* selecteren. Dat zal elke filtering van HTML-tags en attributen die niet zijn toegestaan door TinyMCE-configuratie-instellingen omzeilen.

**Waarschuwing:** als je *Editor - Geen* selecteert om inhoud te maken die HTML-tags bevat die door een editorfilter zijn verboden en vervolgens terugschakelt naar de standaardeditor, moet je ervoor oppassen om die inhoud niet opnieuw te bewerken en op te slaan, anders verlies je gefilterde tags en attributen. Het is gemakkelijk om dit per ongeluk te doen en er is geen waarschuwing.

## Globale Configuratie: Tekstfilters

Selecteer vanaf het Startdashboard Globale Configuratie en vervolgens het tabblad Tekstfilters. De standaardinstellingen hebben *Geen HTML* geselecteerd voor Gast-, Publieke en Geregistreerde gebruikersgroepen. Elk van deze groepen kan de mogelijkheid hebben om een tekstveld in te vullen, bijvoorbeeld in een contactformulier voor extra informatie over een probleem, dus automatische verwijdering van alle HTML-tags is meestal geschikt. Andere groepen, behalve Supergebruikers, worden beperkt door de Standaard Verboden Lijst. Supergebruikers hebben geen filtering.

![globale configuratie van tekstfilters](../../../en/images/configuration/global-configuration-filters-tab.png)

De notities leggen uit wat er is opgenomen in de standaard verboden lijst en hoe je de andere lijsten kunt gebruiken.

## TinyMCE-configuratie voor tekstfilters

Editors worden geïmplementeerd als plugins in Joomla. De CodeMirror-editor heeft geen tekstfilterinstellingen. Om de TinyMCE-editor aan te passen, zoek en selecteer deze in de lijst met plugins. Halverwege de lange lijst met instellingen zie je een veld met de label *Gebruik Joomla tekstfilter*, dat standaard is **Uitgeschakeld**. De volgende drie velden zijn:
* **Verboden elementen** een lijst van tags die altijd zullen worden verwijderd. De standaardlijst van *script, applet, iframe* heeft allemaal veiligheidsrisico's.
* **Geldige elementen** gebruik deze lijst om geldige tags te beperken tot een subset van alle gebruikelijke HTML-tags. Voorbeeld: `a[href|target=_blank],strong/b,div[align],br`
* **Uitgebreide geldige elementen** gebruik deze lijst om een element toe te voegen aan de bestaande standaardregels of om een element in de standaardregels aan te passen. Voorbeeld: `img[class|src|border=0|alt|title|hspace|vspace|width|height|align|onmouseover|onmouseout|name]`

Zie de TinyMCE-documentatie voor meer uitleg.

Om de TinyMCE tekstfilters te omzeilen en Joomla tekstfilters te gebruiken, stel *Gebruik Joomla tekstfilter* in op **Ingeschakeld**. De drie hierboven beschreven extra velden verdwijnen, aangezien ze niet worden gebruikt.

*Vertaald door openai.com*

