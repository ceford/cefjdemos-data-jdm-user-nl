<!-- Filename: J4.x:Hosting_Setup / Display title: cPanel Hosting  -->

## Inleiding

## cPanel Hosting

Wanneer u inlogt op uw cPanel-hostingdienst, is dit wat u zou moeten
zien:

![cpanel hosting controlepaneel](../../../en/images/hosting/cpanel-hosting.png)

### Database-setup

Het Databases-paneel wordt gebruikt om een database en databasegebruiker voor
Joomla te maken.

Selecteer het MySQL Databases-item en voer een databasenaam in op het formulier.
Het eerste deel van het formulier is vooraf gedefinieerd. De rest is aan u. Het
zou kort moeten zijn en misschien niet voor de hand liggend - *jblog* bijvoorbeeld.

In hetzelfde formulier, ga naar beneden naar de sectie *Nieuwe gebruiker toevoegen*. Voer een gebruikersnaam in. Dit kan alles zijn wat u wilt. Het zal worden gebruikt in uw Joomla-configuratiebestand, dus het is niet iets wat u moet onthouden. Gebruik de
wachtwoordgenerator om een niet te onthouden wachtwoord te maken en kopieer het naar een teksteditor - u heeft het nodig tijdens de Joomla-installatie.

Ga in hetzelfde formulier naar beneden naar *Gebruiker aan Database toevoegen*. Selecteer de gebruiker die u hebt aangemaakt en de database die u hebt aangemaakt uit de vervolgkeuzelijsten en klik vervolgens op de knop Toevoegen. Er opent zich een formulier om Rechten te beheren. Vink het selectievakje *Alle Rechten* aan en klik vervolgens op de knop *Wijzigingen aanbrengen*.

Dat is alles - u heeft nu een database klaar voor een Joomla-installatie.

### Joomla-bron uploaden

Op een gegeven moment heeft u het zip-bestand met de Joomla-broncode
gedownload naar uw eigen laptop of desktopcomputer. U moet nu beslissen hoe u
uw site wilt structureren. De documentroot voor uw site is de
*public_html*-map. U zou Joomla daar kunnen plaatsen. Echter, dat verhindert
u ervan om een andere applicatie op dezelfde site te gebruiken. Bijvoorbeeld, u
zou twee volledig afzonderlijke Joomla-installaties kunnen hebben, één voor
productie (voor openbaar gebruik) en één voor testen (privégebruik). U zou dus
een map kunnen maken binnen *public_html*, met de naam *j4* bijvoorbeeld, en Joomla daar uploaden. U zou een andere map met de naam *j4test* kunnen hebben en daar een andere kopie van Joomla plaatsen. De afbeelding hieronder toont zo'n structuur met twee Joomla-websites.

![cpanel hosting bestandsbeheer](../../../en/images/hosting/cpanel-file-manager.png)

Wanneer u heeft besloten over uw structuur, selecteer dan de door u gekozen Joomla-map
in Bestandsbeheer en klik op de knop Uploaden. In het uploadformulier selecteert u
het Joomla source-zipbestand op uw lokale computer om het te uploaden naar de
geselecteerde map. Na het uploaden gaat u terug naar Bestandsbeheer, selecteer
het *zip*-bestand en klik op de knop Uittrekken. Na het uitpakken kunt u het *zip*-bestand
selecteren en verwijderen.

Dat is alles! U bent klaar om Joomla te installeren.

*Vertaald door openai.com*

