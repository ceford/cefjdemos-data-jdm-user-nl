<!-- Filename: J4.x:Installing_Joomla / Display title: Joomla installeren -->

## Introductie

Het voor de eerste keer installeren van Joomla! is erg eenvoudig. Na het voltooien van de voorbereidende stappen, het opzetten van een hostingomgeving en het aanmaken van een database, zal de ingebouwde webinstaller van Joomla je nieuwe site in slechts een paar minuten opzetten. De voorgaande stappen:

### Hosting Setup

Als je nog geen hostingomgeving hebt ingesteld, moet je dat nu doen, hetzij bij een hostingservice of op je lokale computer.

Er zijn ook enkele PHP-instellingen die voldoende moeten zijn om Joomla te installeren. De instellingen staan meestal in een *php.ini* of *user.ini* configuratiebestand op de server. Als je op gedeelde hosting zit, neem contact op met je hostingservice over hoe je deze instellingen kunt wijzigen als dat mogelijk is. Als je op een localhost werkt, bijvoorbeeld met XAMPP, of een VPS of dedicated host, zou je niet beperkt moeten zijn door deze instellingen en kun je ze zelf instellen.

De minimumwaarden voor het *php.ini* bestand zijn hieronder weergegeven:

- *memory_limit:* 256M
- *upload_max_filesize:* 64M
- *post_max_size:* 64M
- *max_execution_time:* 30

Het is mogelijk om met lagere waarden van upload_max_filesize en post_max_size te werken, maar grotere extensies zullen niet kunnen uploaden en kunnen onvoorspelbare problemen veroorzaken.

### Database Setup

Als je nog geen database hebt ingesteld, doe dat nu. Dit wordt behandeld voor een cPanel hostingservice in de [cPanel Hosting](jdocmanual?article=user/hosting/cpanel-hosting) handleiding. Er is ook een *Database aanmaken voor Joomla!* handleiding die de localhost en phpMyAdmin methodes behandelt.

Je moet de basisgegevens van de database noteren die nodig zijn wanneer de daadwerkelijke Joomla-installatie wordt gestart.

- Locatie van de database, meestal *localhost*, zelfs op een hostingservice. Het kan een specifieke server van een host zijn zoals *`dbserver1.jouwhost.com`*.
- De naam van de database
- De naam van de databasegebruiker
- Het wachtwoord van de databasegebruiker

## Voorbereiden voor Installatie

### Joomla! Pakketbestanden downloaden en uploaden

Download de huidige release van Joomla! via de link op de
[Download Joomla](https://downloads.joomla.org/) pagina.

Verplaats het gedownloade Joomla-installatiepakket zip-bestand naar de server.
Voor een hostingservice kun je de cPanel Bestandbeheerder Uploadfunctie
gebruiken of een FTP-client gebruiken om het gedownloade Joomla
5.x zip-bestand naar je server te verzenden. Er zijn verschillende FTP-clients beschikbaar.
Hier is een gedetailleerde [Vergelijking van FTP-clientsoftware](https://en.wikipedia.org/wiki/Comparison_of_FTP_client_software).
Bij twijfel, gebruik FileZilla.

De *root* map van je server

Het is beter om het gedownloade zip-pakket naar je server te verplaatsen en
daar uit te pakken dan om het lokaal uit te pakken en vervolgens de bestandsstructuur te verplaatsen.
Normaal upload je je webbestanden naar de rootmap van je hostingservice.
Deze wordt meestal `public_html` genoemd, maar andere variaties zoals `htdocs` komen voor,
afhankelijk van hoe je host de server heeft ingesteld. Voor Joomla-doeleinden kun je de bestanden
direct laden in *public_html* of een submap die je hierin hebt aangemaakt.

**Waarschuwing:** Als je de bestanden op je eigen computer uitpakt en ze vervolgens naar
je server kopieert, zorg er dan voor dat je alleen de mappen en bestanden **binnenin** het Joomla-pakket verplaatst.
Als je de mappen en bestanden in een map uitpakt, bijvoorbeeld genaamd *`Joomla`*, en vervolgens die map uploadt,
moet je site worden benaderd via *`jouwsitenaam.com/Joomla`* in plaats van
*`jouwsitenaam.com`*. Je kunt de subdirectory naam veranderen van Joomla naar
iets meer passend voor je site, zoals jblog, wat handig kan zijn. **Let op:** directorynamen dienen
kleine letters te bevatten, zonder spaties en met streepjes in plaats van onderstrepingen om woorden te scheiden.

De zip-pakketbestanden kunnen direct op de host worden uitgepakt met
verschillende opdrachtregeltools (bijv. unzip), die geïnstalleerd moeten zijn op
de server. Als je hostingservice de admin tool cPanel gebruikt, kan de
Extraheer-knop ingedrukt worden in de Bestandsbeheerder. Daarnaast kan
de gratis externe Akeeba Kickstart-tool ook voor dit doel gebruikt worden. De uitgepakte bestanden en directories
worden in de huidige map geplaatst. Het uitpakken op je lokale computer is afhankelijk
van je besturingssysteem. Probeer met de rechtermuisknop te klikken en kijk of er een extractiemenu is. In dat geval
kan je besturingssysteem de bestanden plaatsen in een map met dezelfde naam als het zip-bestand. Na het uitpakken kun je het zip-bestand verwijderen en de
uitpakmap hernoemen naar iets korts en geschikt voor gebruik in een url.

## Start Installatie

Met aan de bovenstaande vereisten voldaan, een database aangemaakt en de vereiste Joomla-bestanden op hun plaats, ben je klaar om Joomla te installeren. Start de Joomla webinstaller door je favoriete browser te openen en naar de domeinnaam van de site te gaan. Bij een hostinginstallatie gebruik je *`https://www.jouwsitenaam.com`*. Als je Joomla lokaal installeert, gebruik je *`http://localhost/`* en zou je het installatiescherm moeten zien.

![Joomla installer deel 1, installatietaal en sitenaam](../../../en/images/getting-started/installing-joomla-installer-1.png)

Joomla zal proberen automatisch het veld *Selecteer taal* te identificeren op basis van de taal van je browser. Je kunt dit indien nodig wijzigen.

Vul de volgende informatie in.

- **Sitenaam** De naam van je website — dit kan op elk moment later worden gewijzigd in de Site Global Configuratie pagina.

Wanneer alles op de eerste pagina is ingevuld, druk je op de knop *Login Gegevens Instellen* om verder te gaan.

## Inloggegevens

Je zou nu het scherm met inloggegevens moeten zien.

![Joomla-installatie deel 2, inloggegevens](../../../en/images/getting-started/installing-joomla-installer-2.png)

Vul de volgende informatie in.

- **Echte Naam** De naam van de Supergebruiker. Zo zal Joomla je begroeten wanneer je inlogt.
- **Supergebruiker accountgebruikersnaam** De gebruikersnaam voor de *Supergebruiker*. Vermijd het gebruik van *admin* als de beheerdersnaam!
- **Beheerderswachtwoord** Vergeet niet dat een Supergebruiker maximale controle heeft over de site- en beheerdersinterfaces, dus gebruik een moeilijk wachtwoord. Gebruik **Mijn Profiel** in de *Beheer* interface om het later te wijzigen.
- **Supergebruiker e-mailadres** Het e-mailadres van de Supergebruiker. Voer een geldig e-mailadres in voor het geval je je wachtwoord vergeet. Dit is het e-mailadres waar je een link zult ontvangen om het Supergebruiker wachtwoord te wijzigen.

Wanneer alles op de tweede pagina is ingevuld, klik dan op de knop *Verbindingsinstellingen voor database* om verder te gaan.

## Databaseconfiguratie

Voer de database-informatie in die je hebt genoteerd toen je de database voor deze installatie hebt aangemaakt.

![Joomla-installatie, deel 3, databaseconfiguratie](../../../en/images/getting-started/installing-joomla-installer-3.png)

Voor vereenvoudiging zijn deze instructies een referentie naar de installatie met een MySQLi-database. De instructies op de installatiepagina spreken voor zich, maar hier zijn ze nogmaals:

- **Databasetype** MySQLi is de gebruikelijke database
- **Hostnaam** Waar je database zich bevindt. Vaak is dit *localhost*, zelfs bij hostingdiensten. Sommige hosts gebruiken echter een specifieke databaseserver zoals *dbserver1.jouwhost.com*.
- **Gebruikersnaam** De gebruikersnaam die wordt gebruikt om verbinding te maken met de database
- **Wachtwoord** Het wachtwoord voor de databasegebruiker (niet je beheerderswachtwoord)
- **Databasenaam** De naam van de database
- **Tabelvoorvoegsel** Dit wordt automatisch gegenereerd als een beveiligingsfunctie. Je kunt de willekeurig gegenereerde standaard accepteren of wijzigen. Vergeet niet het underscore-teken (`_`) aan het einde van het voorvoegsel te plaatsen.
- **Versleuteling van verbinding** specificeert hoe de verbinding met de database moet worden versleuteld. Als je het niet weet, kun je het beste de standaardinstelling houden. Dit biedt echter de mogelijkheid aan bedrijven die een een- of tweezijdige authenticatie gebruiken voor de databaseverbinding om het te voorzien.

Al deze keuzes en meer kunnen worden bewerkt op de pagina Site Globale Configuratie, onder *Serveropties* nadat de installatie is voltooid. Let op, je installatie zal niet meer werken als je deze instellingen wijzigt na de installatie, tenzij je een complete kopie hebt van de huidige database die door de Joomla-installatie wordt gebruikt. Veelvoorkomende toepassingen zouden zijn om de gebruikersnaam en het wachtwoord van de database bij te werken of om een bestaande installatie naar een nieuwe host met andere parameters te verplaatsen.

Nadat je op de *Joomla Installeren* knop hebt geklikt, zou je de voortgangsbalk van de Joomla-installatie moeten zien.

![Joomla-installatie, deel 4, installatie voortgangsbalk](../../../en/images/getting-started/installing-joomla-installer-4.png)

Zodra de installatie is voltooid, zou je de succespagina moeten zien.

## Afronden

### Succes en de installatie afronden

Gefeliciteerd! Je Joomla-site is klaar.

![Joomla installer deel 5, je joomla-site is klaar](../../../en/images/getting-started/installing-joomla-installer-5.png)

De bovenstaande screenshot toont een ontwikkelaarsinstallatie. Een productie-installatie 
verwijdert automatisch de Installatiemap.

Als je direct met Joomla aan de slag wilt zonder extra talen te installeren, 
kun je *Open Administrator* selecteren om naar het *Administrator Dashboard* 
te gaan of *Open Site* selecteren om naar de Startpagina van de site te gaan. 
Je ziet mogelijk een sectie met aanbevolen PHP-instellingen.

- **Aanbevolen Instellingen** Deze instellingen worden aanbevolen in je PHP-configuratie, 
  maar zullen de installatie van Joomla! niet verhinderen. Je kunt de bovenstaande 
  instructies raadplegen voor hoe ze kunnen worden gewijzigd indien nodig.

### Extra Talen

Als onderdeel van het Joomla-installatieproces krijg je de kans om extra 
talen te installeren voordat je de installatie voltooit.

Om dit te doen, selecteer je de knop Extra Talen Installeren

Dit brengt je naar een extra installatiescherm waar je de benodigde 
talen kunt selecteren.

#### Extra Talen Installeren

Een lijst met taalpakketten wordt weergegeven.

![Joomla installer deel 6, extra talen installeren](../../../en/images/getting-started/installing-joomla-installer-6.png)

Selecteer maximaal 3 talen die je wilt installeren. (Meer dan 3 tegelijk 
kan timeout-problemen veroorzaken; je kunt later meer installeren.)

Onthoud het volgende:

- Taalpakketten die in aangepaste distributies zijn opgenomen, worden in 
  dit stadium niet vermeld omdat ze al zijn geïnstalleerd.
- Een versie van de voorgestelde pakketten komt overeen met de Joomla 
  Hoofdversie (5.0.x, 5.1.x, etc.). De subversie van het pakket kan niet 
  overeenkomen, bijvoorbeeld je installeert versie 5.0.3 en een 5.0.2 
  taalpakket wordt weergegeven.
- Niet-overeenkomende taalpakketten in het bovenstaande voorbeeld kunnen 
  niet-vertaalde strings bevatten.
- De niet-overeenkomende taalpakketten zullen als een update worden aangeboden wanneer 
  de pakketten worden bijgewerkt door de geregistreerde Vertalingsteams. 
  De beschikbare update wordt weergegeven in het Configuratiescherm en ook in 
  **Uitbreidingen → Update**. Dit gedrag is vergelijkbaar met **Uitbreidingen → Talen Installeren**.

 *Volgende* en een voortgangsbalk worden weergegeven terwijl het taalpakket 
of de pakketten worden geïnstalleerd.

#### Kies de Standaardtaal

Wanneer de installatie van de talen is voltooid, wordt een vergelijkbaar 
*Gefeliciteerd! Je Joomla-site is klaar.* scherm weergegeven. Het verschil 
zal een lijst zijn van de geïnstalleerde talen die je in staat stellen om 
de standaardtaal voor de Site en de Administrator-interface te selecteren.

![Joomla installer deel 7, kies standaardtaal](../../../en/images/getting-started/installing-joomla-installer-7.png)

- Selecteer de standaardtaal die je wilt gebruiken.
- Wanneer je de standaardtaal hebt geselecteerd, klik op de knop *Zet standaardtaal* 
  om te bevestigen.
- Er wordt een systeemmelding weergegeven die bevestigt dat Joomla de 
  standaard BEHEERDER en SITE-taal heeft ingesteld. Die melding kan worden gesloten.

#### Voltooien

Je kunt nu naar het *Administrator Dashboard* navigeren. Log in door *Open Administrator* 
te selecteren of ga direct naar de Startpagina van je site door *Open Site* te selecteren.

