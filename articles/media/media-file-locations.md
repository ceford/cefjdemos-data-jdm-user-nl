<!-- Filename: J6.x:Media_File_Locations / Display title: Media-bestandslocaties   -->

## Introductie

Standaard slaat Joomla zowel gebruikersafbeeldingen als documentbestanden op in de */images*-map van de Joomla-installatie. Eventuele links naar dergelijke media worden niet direct door Joomla verwerkt. De webserver stuurt ze wanneer er door de browser om wordt gevraagd.

Als je veel documenten hebt, wil je ze misschien in een aparte map bewaren, bijvoorbeeld een */files*-map, ook in de root van de Joomla-site.

Om een locatie voor bestanden in te stellen die gescheiden is van afbeeldingen, maak je eerst een nieuwe map in de root van je installatie, bijvoorbeeld **files**. Vergeet niet dat het onderdeel zal uitmaken van een URL-link, dus gebruik kleine letters en geen spaties of leestekens.

### FileSystem - Local Plugin

Zoek de *FileSystem - Local* plugin in de lijst met plugins en open deze. Voeg je nieuw aangemaakte *files*-map toe aan de lijst met plaatsen waar je media kunt bewaren. Klik gewoon op de + knop en selecteer **files** uit de lijst met beschikbare mappen.

![File System Plugin](../../../en/images/plugins/plugin-group-file-system-local.png)

De optie **Create Thumbnails** ingesteld op **Yes** zorgt voor de aanmaak van kleine afbeeldingen met een maximale hoogte of breedte van 200 pixels in media/cache/com_media/thumbs met dezelfde mapstructuur als de mediamap. Het zou de weergavesnelheid van een map met veel afbeeldingen aanzienlijk moeten verhogen. Het is niet nodig voor bestanden aangezien deze worden vertegenwoordigd door pictogrammen.

Zorg ervoor dat de plugin is ingeschakeld. **Opslaan & Sluiten**.

*Vertaald door openai.com*

