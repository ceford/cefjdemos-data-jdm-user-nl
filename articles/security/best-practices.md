<!-- Filename: https://magazine.joomla.org/all-issues/april-2021/best-practices-to-secure-your-joomla-website / Display title: Beste praktijken -->

## Beveiligingsartikelen

Er zijn een aanzienlijk aantal artikelen beschikbaar over Joomla-beveiliging die vele jaren teruggaan. Helaas zijn veel van deze artikelen verouderd en mogelijk misleidend. Er is bijvoorbeeld een reeks artikelen over de Beveiligingschecklist, waarvan niet allemaal daadwerkelijk over beveiliging gaan.

Dit artikel is gebaseerd op een artikel in het Joomla! Community Magazine van Ahmad Moussa in de editie van april 2021.

## Best Practices om uw Joomla-website te Beveiligen

Het Joomla Content Management System (CMS) is wijdverspreid op het internet vanwege de gebruiksvriendelijkheid en populariteit, aangezien het de op een na grootste CMS is die meer dan 110 miljoen keer is gedownload. Maar, ondanks de populariteit, bevatten Joomla en alle andere websites, apps, e-commerce sites of andere CMS'en veiligheidsrisico's. Deze kunnen niet worden vermeden, maar gelukkig kunnen de juiste voorzorgsmaatregelen vanaf het begin ervoor zorgen dat uw site beschermd is.

We hebben deze uitgebreide en stapsgewijze gids over Joomla-beveiliging voor u samengesteld. Het doel is om gemakkelijk te volgen stappen te bieden om de beveiliging van uw Joomla-website te verbeteren. Dus, als het beveiligen van uw Joomla-website tegen alle aankomende aanvallen op uw agenda staat, lees het dan door. Alle tips die in dit artikel worden genoemd, zijn bedoeld om ervoor te zorgen dat u de beste beveiligings- en onderhoudspraktijken implementeert om uw belangrijkste online middelen te beschermen.

## 1. Kies Slimme Gebruikersnamen en Wachtwoorden

Wees slim bij het kiezen van je Joomla-beheerdersgebruikersnamen en wachtwoorden. Gebruik geen "admin" als je gebruikersnaam en kies een complex wachtwoord. Dit is waarschijnlijk een van de beste manieren om je Joomla-beveiliging te verbeteren, en ironisch genoeg is het een van de makkelijkste.

Het gebruik van een veilig wachtwoord is noodzakelijk voor een goede Joomla-beveiliging. Zorg ervoor dat je inlogwachtwoord lang genoeg is (8-14 tekens) en alfabetten, cijfers en symbolen bevat. Aangezien wachtwoorden hoofdlettergevoelig zijn, maakt het gebruik van zowel hoofdletters als kleine letters het nog sterker. Verder is het goed om een gewoonte te maken om beheerderswachtwoorden minstens één keer per maand te veranderen.

## 2. Oefen het Principe van de Minst Bevoorrechte Toegang

Zorg ervoor dat je de drie verschillende permissiegroepen begrijpt:

1. Managers: Hebben de minste toegang tot de backend van Joomla. Kunnen categorieën en artikelen maken en bewerken. Hebben toegang tot de mediabeheerder en kunnen media uploaden en verwijderen. Kunnen geen extensies installeren of verwijderen.
2. Administrators: Hebben alle rechten van Managers, plus een paar extra permissies. Hebben toegang tot de Gebruikersbeheer, Menu Beheer en Extensiebeheer. Kunnen geen toegang krijgen tot het Joomla Globale Configuratie menu.
3. Supergebruikers: Hebben volledige toegang tot de Joomla Backend. Hebben alle rechten van Managers en Administrators, plus toegang tot de Globale Configuratie. Alleen Supergebruikers kunnen Supergebruikers toevoegen, bewerken en verwijderen.

Het is belangrijk dat je deze rollen zorgvuldig verdeelt onder je groep gebruikers. Iedereen met een Supergebruiker-rol kan elke actie binnen het Joomla-systeem uitvoeren. Als je taken delegeert aan een teamlid dat minder permissies vereist, wijs dan de account van het lid toe met de minimale toegangsbeschrijving.

## 3. Gebruik Joomla Multi-Factor Authenticatie

Het wordt sterk aanbevolen om Joomla Multi-factor authenticatie in te schakelen. Dit voegt een extra beveiligingslaag toe aan je Joomla-website. Traditioneel moet je om in te loggen op je website je gebruikersnaam en wachtwoord opgeven om jezelf in het systeem te identificeren. Het grootste probleem met deze aanpak is dat je gebruikersnaam en wachtwoord gestolen of geraden kunnen worden. Daarom kunnen de Joomla Multi-factor authenticatieplugins je website beschermen tegen hackers door een tweede beveiligingslaag toe te voegen. Er zijn vijf verschillende methoden waaruit je kunt kiezen nadat je je gebruikersnaam hebt ingevoerd.

## 4. Beperk Toegang tot Joomla Admin Backend

Het is verstandig om toegang tot de Joomla admin backend te beperken met behulp van IP-filtering, aangezien het een gevoelige bron is. Dit kan ook worden gedaan voor andere gevoelige mappen van Joomla door de onderstaande stappen te volgen:

Stap 1: Maak eerst een .htaccess-bestand aan als er nog geen aanwezig is in de map die u wilt beschermen.

Stap 2: Voeg de volgende code toe aan het .htaccess-bestand:
```
Order Deny, Allow
Deny from all
Allow from xx.xx.xx.xx
```

Stap 3: Voer in plaats van xx.xx.xx.xx het specifieke IP-adres in waarvan u toegang wilt toestaan.

Meer informatie over het beperken van maptoegang via IP-adres met behulp van htaccess is te vinden in dit Joomla! Documentatieartikel. U kunt ook beveiligingsuitbreidingen gebruiken die de toegang tot de Joomla admin backend kunnen beperken met behulp van de IP-filterfunctie en vele andere functies bevatten die de beveiliging van uw Joomla-website versterken.

## 5. Gebruik Veilige FTP-Verbindingen

Zorg ervoor dat de verbindingen die gebruikt worden om toegang te krijgen tot de bestanden van je Joomla-website, beveiligd zijn. Je moet SFTP-encryptie gebruiken als je hostingprovider dit aanbiedt, of SSH. Als je een FTP-client gebruikt, dan is de standaardpoort voor SFTP meestal 22.

Sommige FTP-clients slaan wachtwoorden op in platte tekst of gecodeerd op je computer. Zelfs sommige gecodeerde wachtwoorden kunnen terug worden geconverteerd naar het origineel. We raden ten zeerste aan om geen FTP-wachtwoorden in de client op te slaan om te voorkomen dat je gehackt wordt.

## 6. Maak Regelmatig Back-ups

Bespaar tijd door je voor te bereiden op het ergste geval als je website wordt aangevallen. Daarom wordt geadviseerd om een complete werkende back-up van je Joomla-website te maken. Een functionele back-up kan je website binnen enkele minuten na een cyberaanval herstellen.

De twee hoofdcomponenten van een back-up zijn:

- Joomla-kern en andere belangrijke bestanden
- De database

Daarnaast kunnen de methoden voor het maken van back-ups ook flexibel zijn. Je kunt op twee manieren een back-up maken: handmatig en automatisch, zoals hieronder beschreven:

### Handmatig Proces

Voor de handmatige back-up van de Joomla-site zijn twee componenten nodig: bestanden en de database. Gebruik een FTP-hulpprogramma of de bestandsbeheerder om je Joomla-bestanden en -mappen te back-uppen, vooral als je een externe hostingdienst gebruikt.

FTP-clients kunnen alle bestanden één voor één naar je lokale machine downloaden. Dit proces kan echter traag zijn. Zodra de bestanden zijn gedownload, comprimeer de map tot een enkel zip-bestand en beveilig het met een wachtwoord.

De database kan worden geback-upt door een kopie van de database naar je computer te exporteren. Log in op de database die je wilt exporteren met phpMyAdmin. Klik aan de linkerkant van de pagina op de databasenaam. Nadat je op je Joomla-database hebt geklikt, kom je op een scherm met een tabblad met de naam "Exporteren". Selecteer het tabblad Exporteren en klik vervolgens op de knop "Start". Sla het dan op een veilige locatie op.

### Automatisch Proces

Voor een automatische back-up kan een Joomla-extensie zoals Akeeba Backup helpen. Installeer de Akeeba Backup-extensie op je Joomla-website nadat je deze hebt gedownload van de officiële website van de ontwikkelaar. Zodra de installatie is voltooid, ga naar het Dashboard van de extensie en maak een back-up van je site. Wanneer de back-up is voltooid, word je doorgestuurd naar een pagina. Klik hier op "Beheer Back-ups". Dit opent een pagina met alle back-ups. Je kunt de back-up hier downloaden en lokaal opslaan.

## 7. Houd Uw Joomla-website Bijgewerkt

Het bijwerken van uw Joomla-website kan de site veiliger en stabieler maken. Verder zijn niet alle updates volledige versie-updates van de site; sommige updates kunnen klein zijn en enkel bugfixes bevatten, terwijl andere versie-updates zijn.

Joomla heeft een toegewijd beveiligingsteam dat bekend staat om het snel uitbrengen van patches. Als u uw Joomla-website niet patcht, kan deze kwetsbaar worden voor hacking.

Om te controleren op updates op uw site kunt u het volgende doen:

Stap 1: Log in op uw Joomla-site als de beheerder

Stap 2: Navigeer vervolgens naar Componenten>Joomla Update

Stap 3: Nu zal Joomla controleren of er een nieuwe update beschikbaar is. Als er een nieuwe update is, klikt u eenvoudig op de optie "Installeer de Update".

Voordat u een nieuwere versie van Joomla bijwerkt, moeten bepaalde zaken worden gecontroleerd:

- Sjablonen bijwerken: Controleer of uw Joomla-sjablonen compatibel zijn met de nieuwere Joomla-versie. Zo niet, vraag dan de auteur van het sjabloon om het bij te werken of gebruik een alternatief.
- Extensies bijwerken: Controleer en zorg ervoor dat alle Joomla-extensies compatibel zijn met de nieuwere Joomla-versie. Verwijder alle extensies die niet compatibel zijn. Om de extensies bij te werken, navigeert u naar Extensies>Beheren en klikt u op bijwerken.
- Cache wissen: Nadat u de nieuwere versie van Joomla hebt bijgewerkt, wist u de cache van uw Joomla-site. Dit kan worden gedaan met de ingebouwde functionaliteit van Joomla.

## 8. Gebruik Betrouwbare 3rd-Party Extensies en Templates:

Het wordt aanbevolen om een minimaal aantal extensies op uw website te gebruiken om het optimale beveiligingsniveau voor Joomla te bereiken. Het gebruik van onbetrouwbare 3rd-party extensies of templates kan kwetsbaarheden veroorzaken en de prestaties van uw Joomla-website beïnvloeden. Niet alle 3rd-party extensies zijn probleemvrij; als u de luxe heeft om een 3rd-party extensie te vermijden, doe dat dan! Kies en gebruik professionele extensies en templates van gerenommeerde bedrijven en houd ze up-to-date om uw website te beschermen.

## 9. Update PHP-versie van je Joomla-website

Bescherm je website tegen verschillende hackaanvallen en versterk de beveiliging van je Joomla-site door de PHP-versie van je site bij te werken naar de laatste stabiele release. Zorg ervoor dat je een PHP-versie selecteert die compatibel is met je Joomla-templates en extensies om te voorkomen dat je site kapot gaat. Er zijn verschillende manieren om je PHP-versie bij te werken. De belangrijkste worden behandeld in een artikel in de editie van september 2020 van Joomla Community Magazine: Hoe werk ik mijn PHP-versie bij?.

## 10. Versterk HTTP-beveiligingsheaders

Het wordt sterk aanbevolen om HTTP-beveiligingsheaders te implementeren of bij te werken, omdat ze een extra beveiligingslaag bieden voor je Joomla-site door te helpen bij het verminderen van aanvallen en beveiligingskwetsbaarheden. Meestal vereisen ze slechts een kleine configuratiewijziging op je webserver. Deze headers geven je browser instructies over hoe te handelen bij het verwerken van de inhoud van je site. Hieronder staan zes veelvoorkomende HTTP-beveiligingsheaders die moeten worden beoordeeld:

- Content-Security Policy
- X-XSS-Protection
- Strict-Transport-Security
- X-Frame-Options
- Public-Key-Pins
- X-Content-Type

## 11. Gebruik een Joomla beveiligingsuitbreiding

Het is noodzakelijk om het aantal inlogpogingen op de Joomla admin achterkant te beperken om brute force-aanvallen op je Joomla website te voorkomen. Dit kan worden geïmplementeerd met behulp van verschillende Joomla beveiligingsuitbreidingen die de achterkant van je websitebeheerder beschermen tegen hackpogingen. Je kunt dergelijke uitbreidingen vinden in de categorie beveiligingslijst van Joomla Extensies.

## 12. Kies een Beveiligde Hostingprovider

Zorg ervoor dat de hostingprovider die je kiest, Joomla beveiligingsmaatregelen implementeert. Als je kiest voor gedeelde hosting, zorg er dan voor dat subnetting wordt uitgevoerd met inachtneming van de Joomla-beveiliging. Het kopen van een goedkope gedeelde hostingprovider is misschien niet het ideale startpunt, aangezien je site langzamer zal zijn, onderhevig kan zijn aan spam vanwege een 'slechte buurt' van sites met een lage reputatie, en mogelijk gecompromitteerd kan raken als andere sites zijn gehackt. Controleer ook bij het kiezen van een hostingplan verschillende parameters zoals aanpassingsmogelijkheden, ondersteuning, beoordelingen, enzovoort.

## 13. Gebruik SSL om Joomla-beveiliging te verbeteren

Het wordt sterk aanbevolen om een SSL (Secure Socket Layer)-certificaat op je website te installeren, omdat dit de communicatie tussen je Joomla-site en de browsers van je bezoekers zal versleutelen. Verkrijg een SSL-certificaat van een geverifieerde certificerende autoriteit en zorg ervoor dat al je HTTP-verkeer wordt omgeleid naar HTTPS. Voeg hiervoor de volgende code toe aan je .htaccess-bestand:

```
# Redirect HTTP naar HTTPS
RewriteEngine On
RewriteCond %{HTTPS} off
RewriteCond %{HTTP:X-Forwarded-Proto} !https
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
```

## 14. Regelmatige Joomla-beveiligingsaudit

Het is uiterst belangrijk om kwetsbaarheden te ontdekken voordat een hacker dat doet, om je Joomla-website veilig en beveiligd te houden. Dit kan worden gedaan door een professionele beveiligingsauditetool te kiezen die je veel tijd kan besparen bij het beheren van je websites. Grondige beveiligingsaudits zijn een geweldige manier om de beveiliging van je Joomla-site te verbeteren. Veel diensten doen dit door taken te automatiseren, zoals het maken van websiteback-ups, het scannen op tekenen van inbraak en het in bulk updaten van de extensies die je vertrouwt. Ze kunnen je site ook scannen op het gebruik van beveiligingsbest practices en een diepgaande scan uitvoeren om mogelijke beveiligingsbedreigingen op te sporen. Deze diensten gebruiken een geoptimaliseerde mix van handmatige en geautomatiseerde mechanismen om kwetsbaarheden in je Joomla-site te ontdekken.

## 15. Controleer berichten na installatie

Het wordt sterk aanbevolen om alle berichten na de installatie te lezen, aangezien het Joomla-team je belangrijke informatie geeft die je aandacht nodig heeft na het upgraden of na het voor de eerste keer installeren van Joomla. Deze berichten bevatten meestal Joomla-beveiligingsconfiguraties of bestandswijzigingen die handmatig moeten worden aangebracht en die een upgrade niet kan wijzigen.

## 16. Maak kennis met de kwetsbare extensies

Controleer altijd de website van de Kwetsbare Extensies Lijst en de bijbehorende sociale mediapagina's om op de hoogte te blijven van de nieuwste beveiligingsrisico's en mogelijke patches. Het wordt aanbevolen om elke extensie die vermeld staat in de Kwetsbare Extensies Lijst en waarvoor geen patch bekend is, te verwijderen. Zorg ervoor dat je je kwetsbare extensie bijwerkt zodra er een patch beschikbaar is. Als je site een kwetsbare versie van een extensie gebruikt waarvoor geen patch-update beschikbaar is, wordt aangeraden deze te vervangen.

## Conclusie

Omdat er altijd risico's zullen zijn, zal de beveiliging van Joomla een continu proces blijven, dat frequente beoordeling van mogelijke aanvalsvectoren vereist. Website-eigenaren en beheerders moeten de beveiliging van hun website altijd verbeteren om het risico op inbreuk te verkleinen.

*Vertaald door openai.com*

