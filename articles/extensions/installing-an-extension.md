<!-- Filename: Installing_an_extension / Display title: Een extensie installeren -->

## Documentatie van Extensies

Voordat je begint, is het altijd verstandig om de documentatie die bij een extensie hoort te lezen. De meeste extensies hebben startpagina's en forums, en het is een goed idee om daar eerst naar te kijken. Als er een README-bestand bij de extensie is inbegrepen, moet je dat lezen. Er kunnen speciale installatie- of configuratie-instructies zijn.

## Systeem Installatie Extensies

Het formulier Systeem / Installeren / Extensies is redelijk goed gedocumenteerd in het Helpscherm. Wat minder voor de hand ligt, is dat elk van de installatiemethoden een plugin is. In vroege edities van Joomla 4 stond de Installeren vanuit Web-plugin als eerste op de lijst en het is mogelijk dat dit nog steeds het geval is in versies die zijn bijgewerkt. Het is onhandig als die methode als eerste staat wanneer je doorgaans een van de andere methoden gebruikt, omdat het een paar seconden duurt om gegevens van de Joomla Extensions Directory-site te ophalen.

Om de volgorde te wijzigen:

- Ga naar **Home Dashboard / Plugins**
- Selecteer **installer** in de **Selecteer Type** vervolgkeuzefilter.
- Selecteer het pictogram **Sorteervolgorde** om de sorteergreepjes
  (verticale ellipsis) te onthullen.
- Sleep het item **Installer - Installeren vanuit Web** naar de onderkant van de
  lijst.
- Ga terug naar **Systeem / Installeren / Extensies** om het resultaat te bekijken.

Je bent dan klaar om een van de standaard installatiemethoden te gebruiken.

### Upload Pakketbestand

Voor de meeste extensies en de meeste gebruikers zal de procedure zijn:

- Download de extensie naar je lokale machine als een zipbestand pakket.
- Selecteer vanuit de backend van je Joomla-site (administratie)
  **Systeem → Installeren → Extensies**.
- Selecteer op het tabblad **Upload Pakketbestand** de knop *Bladeren naar bestand*
  en selecteer het extensiepakket op je lokale computer of sleep en plaats
  het bestand vanuit je bestandsbeheerder.
- Het upload- en installatieproces begint automatisch.
- Sommige extensies kunnen verdere instructies voor installatie geven.
- Merk op dat modules en plugins meestal moeten worden ingeschakeld voordat ze werken.

### Installeren vanuit Map

Sommige extensies kunnen te groot zijn om de Upload Pakketbestand-methode te gebruiken, vaak
een limiet op de *Maximale Bestand Uploadgrootte* ingesteld door je host. In dit geval
kun je de Installeren vanuit Map-methode gebruiken.

- Maak een tijdelijke map op je lokale harde schijf en pak het
  archiefbestand van de extensie uit in deze tijdelijke map.
- Gebruik FTP om de inhoud van deze map (inclusief bestanden en
  submappen) te uploaden naar de /tmp directory van de Joomla-root op je server, zodat
  je een pad hebt zoals /tmp/acmeextension.
- Geef in het Installatiemapveld de serverdirectory op waar je
  de bestanden en submappen van het pakket hebt geüpload, bijvoorbeeld
  /home/gebruikersnaam/public_html/tmp/acmeextension.
- Selecteer de knop **Controleren en Installeren** en Joomla! zal de inhoud
  van de opgegeven map installeren.

### Installeren vanuit URL

In plaats van een zipbestand naar je lokale computer te downloaden, kun je de
download-URL gebruiken. Joomla zal het zipbestand direct ophalen en de download-
en uploadstappen van de vorige methoden besparen.

### Installeren vanuit Web

Met deze optie kun je een extensie direct vanuit de Joomla!
Extensions Directory installeren. De aanvankelijke lijst is gesorteerd op aantal beoordelingen, maar
je kunt op Categorie selecteren om snel een lijst van extensies te vinden die mogelijk
aan jouw behoeften voldoen.

## Systeem Installeren Ontdekken

Zoals beschreven in het Helpscherm, stelt de Ontdek-functie je in staat om extensies te installeren die te groot zijn voor sommige systemen, met name goedkope gedeelde hostingomgevingen. Iets dat misschien niet voor de hand liggend is, is dat je mogelijk mappen moet aanmaken op verschillende locaties in je hostingservice, doorgaans:

- Upload sitebestanden naar siteroot/components/com_mybigcomponent
- Upload administratorbestanden naar siteroot/administrator/components/com_mybigcomponent
- Upload media (css en javascript) naar siteroot/media/com_mybigcomponent
- Upload taalbestanden van de site naar siteroot/language/en-GB als ze niet in een taalmap in de component-sitefolder staan.
- Upload administrator taalbestanden naar siteroot/administrator/language/en-GB als ze niet in een taalmap in de component-administratorfolder staan.

Als dat is gedaan, zou Ontdekken het component moeten vinden en installatie toe moeten staan, en het zou zelfs kunnen werken.

## Taalinstellingen voor systeeminstallatie

De standaardtaal is Engels (GB). Deze kan niet worden verwijderd of geïnstalleerd. Het is misschien niet direct duidelijk, maar elke pagina laadt eerst de juiste en-GB-strings om te voorkomen dat de taalsleutels die door programmeurs worden gebruikt, in de paginaweergave verschijnen. Als de door de gebruiker geselecteerde taal niet Engels is, wordt de gebruikers taal geladen, waardoor de Engelse strings worden overschreven. Als een taal niet volledig is vertaald, zal het resultaat een mix van gebruikers taal en Engelse strings zijn. Dit kan er vreemd uitzien, maar het is beter dan een mix van gebruikers taal en programmeursleutels.

Selecteer uit de lijst met beschikbare talen degene die u moet installeren. Sommige zijn gemarkeerd met een groene knop om aan te geven dat ze up-to-date zijn met de huidige Joomla-versie. Anderen zijn gemarkeerd met een gele knop om aan te geven dat ze niet helemaal up-to-date zijn. Ga gerust door en installeer ze toch. U kunt op sommige plaatsen Engelse woorden zien die eigenlijk in de door u geselecteerde taal zouden moeten staan. Maar dat zal zeldzaam zijn.

*Vertaald door openai.com*

