<!-- Filename: J4.x:Managing_Media / Display title: Media beheren -->

## Introductie

In Joomla zijn media afbeeldingen en bestanden die als illustraties of links verschijnen in artikelen, modules, sjablonen enzovoort. Een belangrijke eigenschap van media is dat ze direct door de webserver worden geleverd zonder door Joomla-code te worden verwerkt. Dit is snel en efficiënt. Houd er ook rekening mee dat media meestal worden opgeslagen in de **images**-map van je Joomla-website. Verwissel dit niet met de **media**-map, die javascript- en stijlbladbestanden bevat.

Afbeeldingen en bestandsmedia worden beheerd met de Media-component van Joomla. Hiermee kun je mediacontent in een mappenstructuur organiseren, individuele items uploaden, enkele elementaire afbeeldingsbewerkingsfuncties uitvoeren en afbeeldingen en links direct in artikelen plaatsen.

## Toegang Verkrijgen

Vanaf de Joomla-beheerinterface zijn er verschillende manieren om de Mediacomponent te openen:

- Selecteer **Inhoud → Media** in het Administrator-menu.
- Selecteer **Sitepaneel → Media** vanaf het Startdashboard.
- Selecteer **CMS Inhoud → Media** op een artikelbewerkingsscherm.

In de eerste twee gevallen verschijnt de Mediakomponent in een normaal komponentenscherm. In het laatste geval verschijnt het in een modale dialoog.

## Screenshot

De volgende afbeelding toont de MediPagina net na de installatie van Joomla, maar met de map cassiopeia/sampledata geselecteerd. Een map *files* is toegevoegd om niet-afbeeldingsbestanden op te slaan en een extra map genaamd *garbage* is toegevoegd om het verwijderen van mappen te illustreren:

![MediPagina met voorbeeldgegevens cassiopeia](../../../en/images/media/media-sample-data-cassiopeia.png)

## Mappen beheren

De namen van de submappen in je afbeeldingenmap worden deel van de afbeeldings-URL, dus het is belangrijk voor linkdoelen en zoekmachineoptimalisatie dat de namen voldoen aan een conventie:

- alles in kleine letters
- geen spaties of interpunctie
- gebruik indien nodig een minteken om leesbare woorden te maken, bijvoorbeeld loofbomen in plaats van loof_bomen.

Voordat je veel inhoud voor je site maakt, kan het nuttig zijn om vooruit te denken over hoe je je inhoud zou kunnen categoriseren en misschien een afbeeldingenmapstructuur te maken die lijkt op je categoriebomen. Anders zou je uiteindelijk een zeer groot aantal afbeeldingen en bestanden in de hoofdmap van je afbeeldingenboom kunnen hebben en dat kan moeilijk te beheren worden. Als je ervoor kiest om afbeeldingen later in een betere structuur te verplaatsen, moet je de links naar die afbeeldingen in je artikelen vinden en wijzigen. Dat kan een tijdrovende en ontmoedigende taak zijn!

### Navigeren in mappen

Gebruik de mappenboom in de **Lokaal** kolom om een map te selecteren. In het hierboven geïllustreerde geval werd eerst de cassiopeia-map geselecteerd. Dat onthulde de *sampledata* map die vervolgens werd geselecteerd om de inhoud te tonen.

De huidige locatie wordt ook aangegeven in de broodkruimels boven de afbeeldingen. In dit geval **afbeeldingen → cassiopeia → sampledata**.

Als je een andere map selecteert, sluit de vorige map op hetzelfde niveau.

### Een map maken

- Selecteer de bovenliggende map waaronder de nieuwe map moet worden gemaakt.
- Selecteer de **Nieuwe map maken** knop.
- Voer in het *Nieuwe map maken* pop-upvenster een naam voor de map in het **Mapnaam** veld in.
- Klik op de **Aanmaken** knop.
- De nieuwe map verschijnt in de geselecteerde bovenliggende map samen met een groen succesbericht van het systeem.

### Een map verwijderen

**Waarschuwing: het verwijderen van een map verwijdert ook alle inhoud van de map!**

- Selecteer de bovenliggende map van de map die moet worden verwijderd met behulp van de mappenboom onder **Lokaal**. Dat toont alle mappen en bestanden in de bovenliggende map.
- Beweeg de cursor over de map die in het media-gebied moet worden verwijderd. Deze wordt grijs en er verschijnt een knop linksboven.
- Selecteer de knop. Er verschijnt een vinkje om aan te geven dat deze is geselecteerd.
- Selecteer de **Verwijderen** knop van de Werkbalk.
- Selecteer in de **Verwijderen bevestigen** pop-updialoog de **Verwijderen** knop. De map wordt verwijderd samen met al zijn bestanden, submappen en hun bestanden.

De map geselecteerd voor verwijdering is hieronder geïllustreerd:

![Mediapagina met prullenbakmap](../../../en/images/media/media-sample-data-garbage-select.png)

## Werkbalk voor Media Gebied

Dit is de balk boven de lijst met afbeeldingen, bestanden en mappen die knoppen bevat voor verschillende taken.

### Selectievak

Een selectievakje waarmee je alle items in de map die in het mediagebied wordt weergegeven kunt selecteren. Je kunt dit gebruiken om alle huidige items te verwijderen zonder de map te verwijderen.

### Kruimelpad

Gebruik de mapnamen boven het mediagebied om terug te gaan in de mappenhiërarchie.

Dubbelklik op een mapnaam in het mediagebied om die map te openen.

### Zoeken

Als je een lange lijst met afbeeldingen en bestanden hebt, kun je zoeken naar items die een bepaalde groep karakters bevatten. De zoekopdracht is progressief: terwijl je meer karakters aan de zoekterm toevoegt, wordt de lijst beperkt tot alleen die met die tekenreeks.

### Vergroten

Gebruik de vergrootknoppen om de miniatuurformaat te vergroten of te verkleinen. Afhankelijk van de grootte van je scherm kun je 2, 4, 6 of 8 miniatuurafbeeldingen naast elkaar zien.

### Lijst- of Miniatuurweergave

In de miniatuurweergave selecteer je het lijsticoon om naar de lijstweergave te schakelen. In de lijstweergave selecteer je het miniatuuricoon om naar de miniatuurweergave te schakelen. In de lijstweergave zie je informatie over afbeeldingsgrootte en -afmetingen, naast andere gegevens.

### Informatie-icoon

Selecteer het Informatie-icoon om een zijpaneel te openen met informatie over het geselecteerde item.

*Vertaald door openai.com*

