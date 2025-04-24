<!-- Filename: J4.x:Installing_Joomla / Display title: Joomla installeren -->

## Inleiding

Joomla! voor de eerste keer installeren is heel eenvoudig. Na het voltooien van de voorbereidende stappen, het instellen van een hostingomgeving en het creëren van een database, zal de ingebouwde webinstaller van Joomla je nieuwe site in slechts een paar minuten opzetten. De voorgaande stappen:

### Hosting Setup

Als je nog geen hostingomgeving hebt opgezet, moet je dat nu doen, hetzij op een hostingservice of op je lokale computer.

Bovendien zijn er enkele PHP-instellingen die voldoende moeten zijn voor de installatie van Joomla. De instellingen staan meestal in een *php.ini* of *user.ini* configuratiebestand op de server. Als je gebruikmaakt van gedeelde hosting, neem contact op met je hostingservice over hoe je deze instellingen kunt wijzigen als dat mogelijk is. Als je op een localhost werkt, bijvoorbeeld met XAMPP, of een VPS of dedicated host, zou je niet beperkt moeten worden door deze instellingen en kun je deze zelf instellen.

De minimumwaarden voor het *php.ini*-bestand worden hieronder weergegeven:

- *memory_limit:* 256M
- *upload_max_filesize:* 64M
- *post_max_size:* 64M
- *max_execution_time:* 30

Het is mogelijk om met lagere waarden voor upload_max_filesize en post_max_size te werken, maar grotere extensies zullen niet kunnen uploaden en onvoorspelbare problemen veroorzaken.

### Database-instelling

Als je nog geen database hebt opgezet, doe dat dan nu. Het wordt behandeld voor een cPanel hostingdienst in de [cPanel Hosting](jdocmanual?article=user/hosting/cpanel-hosting) handleiding. Er is ook een *Een Database maken voor Joomla!* handleiding die localhost- en phpMyAdmin-methoden behandelt.

U moet basisgegevens van de database noteren die nodig zijn wanneer de daadwerkelijke Joomla-installatie wordt gestart.

- Locatie van de database, meestal *localhost*, zelfs bij een hostingdienst.  
  Het kan een specifieke hostserver zijn zoals *`dbserver1.yourhost.com`*.
- De databasenaam
- De naam van de databasegebruiker
- Het wachtwoord van de databasegebruiker

## Voorbereiden voor Installatie

### Joomla!-pakketbestanden downloaden en uploaden

Download de huidige release van Joomla! via de link op de [Download Joomla](https://downloads.joomla.org/) pagina.

Verplaats het gedownloade zip-bestand van het Joomla-installatiepakket naar de server. Voor een hostingservice kun je de Upload-functie van cPanel File Manager gebruiken of je kunt een FTP-client gebruiken om het gedownloade Joomla 5.x zip-bestand naar je server over te zetten. Er zijn verschillende FTP-clients beschikbaar. Als je twijfelt, gebruik dan FileZilla.

Het is beter om het gedownloade zip-pakket naar je server te verplaatsen en het daar uit te pakken dan het lokaal uit te pakken en vervolgens de bestandsstructuur te verplaatsen. Normaal gesproken upload je je webbestanden naar de hoofdmap van je hostingdienst. Deze wordt doorgaans `public_html` genoemd, maar andere varianten zoals `htdocs` zijn ook mogelijk, afhankelijk van hoe je host de server heeft ingesteld. Voor Joomla-doeleinden kun je de bestanden direct in *public_html* laden of in een submap die je daarin hebt aangemaakt.

**Waarschuwing:** Als je de bestanden op je eigen computer uitpakt en deze vervolgens naar je server kopieert, zorg er dan voor dat je alleen de mappen en bestanden die **binnenin** het Joomla-pakket zitten, verplaatst. Als je de mappen en bestanden in een map uitpakt, bijvoorbeeld genaamd *`Joomla`*, en die map vervolgens uploadt, moet je site worden benaderd via *`jouwsitenaam.com/Joomla`* in plaats van *`jouwsitenaam.com`*. Je kunt de subdirectory van Joomla hernoemen naar iets dat meer bij de site past, zoals jblog, en dat kan handig zijn. **Opmerking:** mapnamen moeten in kleine letters zijn, zonder spaties en met gebruik van mintekens in plaats van onderstrepingen om woorden te scheiden.

De zip-pakketbestanden kunnen rechtstreeks op de host worden uitgepakt met behulp van verschillende opdrachtregeltools (bijv. unzip), die op de server moeten worden geïnstalleerd. Als je hostingdienst het beheertool cPanel gebruikt, kan de Extract-knop in de Bestandsbeheerder worden ingedrukt. Daarnaast kan het gratis externe Akeeba Kickstart-tool ook voor dit doel worden gebruikt. De uitgepakte bestanden en mappen worden in de huidige map geplaatst. Extractie op je lokale computer hangt af van je besturingssysteem. Probeer met de rechtermuisknop te klikken en kijken of er een extractiemenu is. In dat geval kan je besturingssysteem de bestanden in een map met dezelfde naam als het zip-bestand plaatsen. Na het uitpakken kun je het zip-bestand verwijderen en de extractiemap een korte en geschikte naam geven voor gebruik in een URL.

## Start Installatie

Met de bovenstaande vereisten voldaan, een aangemaakte database en de vereiste Joomla-bestanden op hun plaats, ben je klaar om Joomla te installeren. Start de Joomla web installer door je favoriete browser te openen en naar de domeinnaam van de site te browsen. Bij een hostinginstallatie gebruik je *`https://www.yoursitename.com`*. Als je Joomla lokaal installeert, gebruik je *`http://localhost/`* en zou je het installatiescherm moeten zien.

![Joomla installer part 1, installation language and site name](../../../en/images/getting-started/installing-joomla-installer-1.png)

Joomla zal proberen het veld *Selecteer taal* automatisch te identificeren vanuit de taal van je browser. Je kunt dit indien nodig wijzigen.

Vul de volgende informatie in.

- **Sitenaam** De naam van uw website — dit kan op elk moment later gewijzigd worden op de pagina voor de globale siteconfiguratie.

Wanneer alles op de eerste pagina is voltooid, selecteer de knop *Instellingen Aanmeldgegevens* om verder te gaan.

## Inloggegevens

Je zou nu het inloggegevensscherm moeten zien.

![Joomla installer part 2, login data](../../../en/images/getting-started/installing-joomla-installer-2.png)

Vul de volgende informatie in.

- **Echte naam** De naam van de Super User. Dit is hoe Joomla je zal begroeten wanneer je inlogt.
- **Super User accountgebruikersnaam** De gebruikersnaam voor de *Super User*. Vermijd het gebruik van *admin* als de beheerdernaam!
- **Beheerderswachtwoord** Onthoud dat een Super User maximale controle heeft over de Site- en Beheerinterfaces, dus gebruik een moeilijk wachtwoord. Gebruik **Mijn Profiel** in de *Beheerinterface* om het later te wijzigen.
- **Super User e-mailadres** Het e-mailadres van de Super User. Voer een geldig e-mailadres in voor het geval je je wachtwoord vergeet. Dit is het e-mailadres waarop je een link ontvangt om het Super User-wachtwoord te wijzigen.

Wanneer alles op de tweede pagina is voltooid, selecteer de knop *Setup Database Connection* om verder te gaan.

## Databaseconfiguratie

Voer de database-informatie in die je hebt genoteerd toen je de database aanmaakte voor deze installatie.

![Joomla installer part 3, database configuration](../../../en/images/getting-started/installing-joomla-installer-3.png)

Voor vereenvoudiging zijn deze instructies een referentie voor het installeren met een MySQLi-database. De instructies op de installatiepagina zijn vanzelfsprekend, maar hier zijn ze opnieuw:

- **Database Type** MySQLi is de gangbare database die wordt gebruikt
- **Hostname** Waar uw database zich bevindt. Gewoonlijk is dat *localhost*,
  zelfs bij hostingdiensten. Sommige hosts gebruiken echter een specifieke database
  server zoals *dbserver1.yourhost.com*.
- **Gebruikersnaam** De gebruikersnaam die wordt gebruikt om verbinding te maken met de database
- **Wachtwoord** Het wachtwoord voor de databasegebruiker (niet uw
  Beheerderswachtwoord)
- **Databasenaam** De naam van de database
- **Tabelvoorvoegsel** Dit wordt automatisch gegenereerd als een beveiligings-
  functie. U kunt de willekeurig gegenereerde standaard accepteren of wijzigen.
  Vergeet alleen niet om het underscorekarakter (`_`) aan het einde van
  het voorvoegsel te zetten.
- **Verbindingsversleuteling** specificeert hoe de verbinding met de
  database moet worden versleuteld. Als u het niet weet - is het het beste om bij
  de standaardinstelling te blijven. Dit stelt echter ondernemingen die een of
  tweewegverificatie voor de databaseverbinding gebruiken in staat om het te leveren.

Al deze keuzes en meer kunnen worden bewerkt op de pagina Site Globale Configuratie, onder *Serveropties* nadat de installatie is voltooid. Let op, je zult je installatie breken als je deze instellingen na de installatie verandert, tenzij je een volledige kopie hebt van de huidige database die door de Joomla-installatie wordt gebruikt. Veelvoorkomende toepassingen zouden zijn om de gebruikersnaam en het wachtwoord van de database bij te werken of om een bestaande installatie te verplaatsen naar een nieuwe host met andere parameters.

Nadat u de knop *Joomla Installeren* hebt geselecteerd, zou u de voortgangsbalk van de Joomla-installatie moeten zien.

![Joomla installer part 4, installation progress bar](../../../en/images/getting-started/installing-joomla-installer-4.png)

Zodra de installatie is voltooid, zou je de succespagina moeten zien.

## Afronden

### Succes en het Voltooien van de Installatie

Gefeliciteerd! Je Joomla-site is klaar.

![Joomla installer part 5, your joomla site is ready](../../../en/images/getting-started/installing-joomla-installer-5.png)

De bovenstaande screenshot toont een ontwikkelaarsinstallatie. Een productie-installatie verwijdert automatisch de Installatiemap.

Als je direct wilt beginnen met het gebruiken van Joomla zonder extra talen te installeren, kun je *Open Administrator* selecteren om naar het *Administrator Dashboard* te gaan of *Open Site* selecteren om naar de Startpagina van de site te gaan. Mogelijk zie je een sectie met aanbevolen PHP-instellingen.

- **Aanbevolen instellingen** Deze instellingen worden aanbevolen in je PHP-configuratie, maar zullen niet voorkomen dat Joomla! wordt geïnstalleerd. Je kunt naar de bovenstaande instructies verwijzen over hoe ze kunnen worden gewijzigd indien nodig.

### Extra Talen

Als onderdeel van het Joomla installatieproces krijg je de mogelijkheid om extra talen te installeren voordat je de installatie voltooit.

Om dit te doen, selecteert u de knop Extra talen installeren.

Dit brengt u naar een extra installatiescherm waar u de gewenste talen kunt selecteren.

#### Extra talen installeren

Een lijst met taalpakketten wordt weergegeven.

![Joomla installer part 6, install additional languages](../../../en/images/getting-started/installing-joomla-installer-6.png)

Selecteer maximaal 3 talen die je wilt installeren. (Meer dan 3 tegelijk kan time-out problemen veroorzaken; je kunt later meer installeren.)

Onthoud het volgende:

- Taalpakketten die zijn opgenomen in aangepaste distributies worden in deze fase niet vermeld omdat ze al zijn geïnstalleerd.
- Een versie van de voorgestelde pakketten zal overeenkomen met de Joomla Major-versie (5.0.x, 5.1.x, enz.). De kleinere versie van het pakket komt mogelijk niet overeen, bijv. je installeert versie 5.0.3 en een 5.0.2 taalpakket wordt getoond.
- Niet-overeenkomende taalpakketten in het bovenstaande voorbeeld kunnen niet-vertaalde strings bevatten.
- De niet-overeenkomende taalpakketten worden als een update aangeboden wanneer de pakketten worden bijgewerkt door de geregistreerde Vertaalteams. De beschikbare update wordt weergegeven in het Configuratiescherm evenals in **Extensies → Update**. Dit gedrag is vergelijkbaar met **Extensies → Talen Installeren**.

Selecteer *Volgende* en een voortgangsbalk wordt weergegeven terwijl het taalpakket of de pakketten worden geïnstalleerd.

#### Kies de Standaardtaal

Wanneer de installatie van de talen is voltooid, zal je nu een vergelijkbaar scherm te zien krijgen met de tekst *Gefeliciteerd! Je Joomla-site is klaar.* Het verschil zal een lijst zijn van de geïnstalleerde talen waarmee je de standaardtaal voor de Site en de Beheerder-interface kunt selecteren.

![Joomla installer part 7, choose default language](../../../en/images/getting-started/installing-joomla-installer-7.png)

- Selecteer de standaardtaal die u wilt gebruiken.
- Wanneer u de standaardtaal hebt geselecteerd, selecteert u de knop *Standaardtaal instellen* om te bevestigen.
- Er wordt een systeembericht weergegeven ter bevestiging dat Joomla de standaardtaal voor de BEHEERDER en de SITE heeft ingesteld. Dat bericht kan worden gesloten.

#### Afronden

Je kunt nu navigeren naar het *Beheerder Dashboard*. Log in door te selecteren *Beheerder openen* of ga direct naar de startpagina van je site door te selecteren *Site openen*.

*Vertaald door openai.com*

