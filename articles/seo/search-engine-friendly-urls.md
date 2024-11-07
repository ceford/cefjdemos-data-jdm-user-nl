<!-- Filename: Search_Engine_Friendly_URLs / Display title: Zoekmachinevriendelijke URL's  -->

## Paden en Routes

SEF-URL's zijn logisch voor zowel mensen als zoekmachines, omdat ze het pad naar de specifieke pagina die ze aanwijzen, uitleggen. Een **pad** is de locatie van een bestand in een directorystructuur of de simulatie daarvan in code. Intern wordt het lokale deel van een SEF URL (het deel na de domeinnaam) een **route** genoemd. Het maken en verwerken van SEF URL's wordt daarom **routing** genoemd, en de relevante code wordt een **router** genoemd.

Zoekmachinevriendelijke URL's kunnen als volgt geactiveerd worden:
* In **Globale Configuratie**
    - zet de optie **Zoekmachinevriendelijke URL's** op **Ja**.
    - Zet de optie **Gebruik URL herschrijven** op **Ja**.
    - Optioneel: Zet de optie **Voeg Suffix toe aan URL** op **Ja**.
* In de hoofdmap van de site hernoemt u htaccess.txt naar .htaccess als u een
Apache-server gebruikt, of raadpleeg de externe documentatie voor NginX of andere servers.

Een voorbeeld van routing is te zien in het stapsgewijze effect dat deze wijzigingen hebben op de URL van de **Artikelen** Categorie Blog pagina in de voorbeeldgegevens.

- Met SEF-URL's uitgeschakeld in Globale Configuratie en .htaccess uitgeschakeld, is de URL iets als `https://www.example.com/index.php?option=com_content&view=category&layout=blog&id=16&Itemid=125` en de broodkruimels tonen:<br>
 *U bent hier: Start / Voorbeeldindelingen / Artikelen*
- Met SEF-URL's aan maar geen URL-herschrijven, wordt het:
  `https://www.example.com/index.php/sample-layouts/articles`
- Met zowel SEF-URL's aan, URL-herschrijven aan en .htaccess ingeschakeld, wordt het
  `https://www.example.com/sample-layouts/articles.html` (Voeg Suffix toe aan URL ingesteld op Ja).

## Nummers in niet-SEF URL's

In het deel van de URL dat zegt `id=16&Itemid=125` zijn de nummers de parameters die nodig zijn om de interne URL te lokaliseren en de vereiste pagina weer te geven. In dit geval is het eerste nummer het ID van een Categorie en het tweede nummer is het ID van het Categorie Blog-menu-item voor die Categorie.

*Vertaald door openai.com*

