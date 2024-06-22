<!-- Filename: J4.x:Installing_Joomla / Display title: Het installeren van Joomla -->

Dit is een tijdelijke pagina tot Joomla 4 is vrijgegeven. Kijk tot dan
bij de  Joomla! 3.x
installatie

Het voor het eerst installeren van Joomla! is erg eenvoudig. Na het
voltooien van de voorbereidende stappen, het opzetten van een hosting
omgeving en het aanmaken van een database, zal Joomla’s ingebouwde
installatie programmatuur je site in slechts een paar minuten opzetten.
De vorige stappen:

### Hosting instellen

Al je nog geen hosting omgeving hebt ingesteld moet je dat nu doen, of
bij een hosting bedrijf of op je lokale computer. Lees de  Hosting
instellen
handleiding voor de details.

Er zijn ook wat PHP instellingen die geschikt moeten zijn om Joomla te
installeren. De instellingen staan normaliter in een *php.ini* of
*user.ini* instellingen bestand op de server. Als je op gedeelde hosting
zit, neem dan contact op met je hosting dienst over hoe deze
instellingen aan te passen en of het mogelijk is. Als je werkt op een
localhost, bijvoorbeeld met
XAMPP, of
een VPS of dedicated host, dan ben je niet beperkt door deze
instellingen en kun je ze zelf aanpassen.

De minimum waarden voor het *php.ini* bestand staan hieronder:

- *memory_limit:* 256M
- *upload_max_filesize:* 30M
- *post_max_size:* 30M
- *max_execution_time:* 30

Het is mogelijk om met lagere waarden te werken van upload_max_filesize
en post_max_size maar grotere extensies zullen fouten geven bij het
uploaden en veroorzaken onvoorspelbare problemen.

### Database instellen

Als je nog geen database hebt aangemaakt, doe dat dan nu. Het wordt voor
een hosting bedrijf beschreven in de  Hosting
instellen
handleiding. Er is ook een  Aanmaken van een Database voor
Joomla!
handleiding die gaat over localhost en phpMyAdmin methodes.

U heeft de basisgegevens van de database nodig als de Joomla installatie
is begonnen.

- Locatie van database, meestal *localhost* zelfs bij een hosting
  dienst. Het kan een specifieke host dienst zijn zoals
  *`dbserver1.yourhost.com`*.
- De naam van de database
- De gebruikersnaam van de database
- Het wachtwoord van de gebruiker van de database

## Voorbereiding van het installeren

### Het down- en uploaden van Joomla! pakket bestanden

Download de huidige versie van Joomla! van de link op de
<a href="https://downloads.joomla.org/" class="external text"
target="_blank" rel="noreferrer noopener">Download Joomla</a> pagina

Verplaats het gedownloade Joomla! installatie-pakket zip-bestand naar de
server. Gebruik voor een hosting service de cPanel File Manager Upload
functie of je kunt een FTP Client gebruiken om het gedownloade Joomla
4.x zip bestand naar je server te brengen. Er zijn verschillende FTP
clients beschikbaar. Hier is een gedetailleerde <a
href="https://en.wikipedia.org/wiki/Comparison_of_FTP_client_software"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">vergelijking van FTP client
software</a>. Indien je twijfelt, gebruik FileZilla.

De "root" map van je server

Het is beter het gedownloade zip-pakket naar je server te verplaatsen en
het daar uit te pakken dan om het lokaal uit te pakken en daarna de
bestanden te verplaatsen. Normaliter upload je de bestanden naar je root
map van je hostingdienst. Deze heet normaal *public_html* maar andere
versies zoals *htdocs* zijn mogelijk en dit is afhankelijk van de server
instellingen van de hoster. Voor Joomla zelf is het uploaden van de
bestanden en mappen direct in de *public_html* of een submap die je hebt
aangemaakt voldoende.

<img
src="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/25px-Stop_hand_nuvola.svg.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/38px-Stop_hand_nuvola.svg.png 1.5x, https://docs.joomla.org/images/4/41/Stop_hand_nuvola.svg.png 2x"
data-file-width="40" data-file-height="40" width="25" height="25"
alt="Stop hand nuvola.svg.png" />Waarschuwing!

Indien je de bestanden op je eigen computer uitpakt en dan naar de
server verplaatst dan moeten alleen de mappen en bestanden **binnen**
het Joomla pakket verplaatst worden (de zip zelf niet). Indien je de
mappen en bestanden uitpakt in een map, bijvoorbeeld, *`Joomla`* en dan
die map upload, dan moet de site benaderd worden via
*`yoursitename.com/Joomla`* in plaats van *`yoursitename.com`*. Je kunt
de sub-map hernoemen van Joomla in iets dat meer geschikt is voor je
site, zoals jblog en dat kun je handig vinden. **Let op** map-namen
moeten met kleine letters zijn, zonder spaties en gebruik maken van
min-tekens in plaats van onderstrepingen om woorden te scheiden.

De zip pakket bestanden kunnen direct op de host uitgepakt worden via
diverse command line tools (bijvoorbeeld unzip), welke op de server
geïnstalleerd moeten zijn. Als je hosting dienst gebruik maakt van het
admin tool cPanel, kan de uitpak knop worden ingedrukt de File Manager.
Daarnaast, kan het gratis hulpmiddel van derden
<a href="https://www.akeeba.com/products/akeeba-kickstart.html"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">Akeeba Kickstart</a> ook voor dit
doel gebruikt worden. De uitgepakte bestanden en mappen worden in de
huidige map geplaatst. Uitpakken op je lokale computer hangt af van je
operating systeem. Probeer met de rechter muisknop te klikken en kijk of
er een uipakknop is. In dat geval zet je operating systeem de bestanden
misschien in een map met dezelfde naam als het zip-bestand. Na het
uitpakken kun je het zip-bestand verwijderen en de uitpak-map een korte
naam geven die geschikt is om als URL te gebruiken.

## Start installatie

Als aan bovengenoemde eisen voldaan is, een database aangemaakt is en de
Joomla bestanden op de juiste plek gezet zijn, ben je klaar om Joomla te
installeren. Start de Joomla web installatie door je favoriete browser
te openen en naar de domeinnaam van de site te surfen. Bij het
installeren op een host gebruik je *`https://www.yoursitename.com`*.
Indien je Joomla lokaal installeert, gebruik je *`http://localhost/`* en
je ziet het installatie scherm.

<img
src="https://docs.joomla.org/images/0/06/J4x_Installation_screen_page_1.png"
class="thumbborder" decoding="async" data-file-width="500"
data-file-height="397" width="500" height="397"
alt="J4x Installation screen page 1.png" />

Joomla zal proberen automatisch het *Selecteer taal* veld te bepalen
vanuit de taal van de browser. Dit kan indien gewenst veranderd worden.

Vul de volgende informatie in.

- **Websitenaam**: De naam van jouw website — deze kan op elk moment
  gewijzigd worden op de  Algemene
  instellingen
  pagina.

Klik, wanneer alles op de eerste pagina voltooid is, op de
*Inloggegevens instellen* knop om verder te gaan.

## Inloggegevens

Je zou nu het scherm met inloggegevens moeten zien.

<img
src="https://docs.joomla.org/images/6/66/J4x_Installation_screen_page_2.png"
class="thumbborder" decoding="async" data-file-width="500"
data-file-height="481" width="500" height="481"
alt="J4x Installation screen page 2.png" />

Vul de volgende informatie in.

- **Echte naam**: De naam van de Super gebruiker. Met deze naam word je
  begroet door Joomla als je inlogt.
- **Super gebruiker gebruikersnaam**: De gebruikersnaam voor de *Super
  User*. Vermijdt admin (wat een goede  Mijn
  Profiel
  in de *beheer* interface om het later te veranderen.
- **Administrator Wachtwoord**: Onthoud dat de Super user de maximale
  rechten heeft op de website en de beheer omgeving, gebruik dus een
  moeilijk wachtwoord. Gebruik  Mijn
  Profiel
  in de *Administrator* interface om het later te wijzigen. Bevestig het
  wachtwoord in het **Bevestig Administrator Wachtwoord** veld.
- **Super user Email Addres**: Het email adres van de Super user. Vul
  een geldig email adres in voor het geval je het wachtwoord vergeet.
  Dit is het email adres waarop je een link zult ontvangen om je super
  gebruiker wachtwoord te wijzigen.

Klik, wanneer alles op de eerste pagina voltooid is, op de *Database
configuratie* knop om verder te gaan.

## Database configuratie

Voer de database informatie in die je hebt genoteerd toen de database
werd aangemaakt. Je kunt ook kijken bij  Maak een database aan voor
Joomla!.

<img
src="https://docs.joomla.org/images/4/4f/J40_Installation_screen_page_3.png"
class="thumbborder" decoding="async" data-file-width="500"
data-file-height="637" width="500" height="637"
alt="J40 Installation screen page 3.png" />

Voor de eenvoud verwijzen deze instructies naar de installatie met een
<a href="http://nl.wikipedia.org/wiki/MySQLi" class="extiw"
title="nl.wp:MySQLi">MySQLi</a> database. De instructies op de
installatiepagina verklaren zichzelf, maar hier zijn ze nogmaals:

- **Databasetype:** MySQLi is de standaard database die gebruikt wordt
- **Naam host:** Waar de database staat. Normaal is dat *localhost*,
  zelfs bij hosting diensten, maar sommige hosts gebruiken een
  specifieke databaseserver zoals *dbserver1.yourhost.com*.
- **Gebruikersnaam:** De gebruikersnaam die gebruikt wordt om verbinding
  te maken met de database
- **Wachtwoord:** Het wachtwoord van de database gebruiker (niet je
  Administrator wachtwoord)
- **Naam database:** De naam van de database
- **Tabelvoorvoegsel:** Wordt automatisch gegenereerd als beveiliging.
  Je kunt het willekeurig gegeneerde accepteren of het veranderen.
  Vergeet niet het onderstrepingsteken te gebruiken. (`_`) aan het einde
  van het voorvoegsel.
- *Connectie encryptie'*: specificeer hoe de connectie met de database
  versleuteld moet zijn. Als je dit niet weet - dan kun je het best de
  standaard gebruiken. Echter kunnen ondernemingen die een of twee
  richtingen authenticatie voor de database verbinding hebben, deze
  verstrekken.

Al deze keuzes kunnen bewerkt worden op de  Algemene
instellingen
pagina, onder *Server opties* nadat de installatie voltooid is. Let op,
de installatie breekt indien je deze instellingen wijzigt na de
installatie tenzij je een kopie van de huidige database hebt die door de
Joomla! installatie gebruikt wordt. Over het algemeen wordt de
gebruikersnaam en het wachtwoord van de database gewijzigd bij het
verplaatsen van een bestaande installatie naar een nieuwe host met
andere parameters.

Nadat je op de *Installeer Joomla* knop hebt geklikt, zou je het Joomla
logo moeten zien draaien. Zodra de installatie gereed is, zou je de
succes pagina moeten zien.

## Voltooien

### Succes en het voltooien van de installatie

Gefeliciteerd! Joomla! 4 is nu geïnstalleerd.

<img
src="https://docs.joomla.org/images/e/e0/J40_Installation_screen_page_4.png"
class="thumbborder" decoding="async" data-file-width="500"
data-file-height="318" width="500" height="318"
alt="J40 Installation screen page 4.png" />

Als je Joomla direct wilt gaan gebruiken zonder [het installeren van
extra
talen](https://docs.joomla.org/J4.x:Installing_Joomla#Installing_Extra_Languages "Special:MyLanguage/J4.x:Installing Joomla")
dan kun je kiezen voor *Open Administrator* om naar het *Beheerder
dashboard* te gaan of kies voor *Open site* om naar de Home pagina te
gaan. Je kunt een sectie zien met de aanbevolen PHP instellingen.

- **Aanbevolen instellingen**: Dit zijn instellingen die aanbevolen zijn
  in jouw PHP configuratie, maar zal de installatie van Joomla! niet
  stoppen. Je kunt in de bovenstaande instructies lezen hoe de
  instellingen gewijzigd kunnen worden als dat nodig is.

### Extra talen

Als onderdeel van het Joomla installatieproces wordt de mogelijkheid
geboden om extra talen te installeren voordat je de installatie
voltooid.

Selecteer om dit te doen de 'Installeer extra talen' knop

Dit brengt je bij een extra installatie pagina waar de gewenste talen
kunnen worden geselecteerd.

#### Installeer extra talen

Een lijst met taalpakketten wordt getoond.

<img
src="https://docs.joomla.org/images/c/ce/J40_Installation_screen_page_5.png"
decoding="async" data-file-width="500" data-file-height="755"
width="500" height="755" alt="J40 Installation screen page 5.png" />

Selecteer tot 3 talen die je wilt installeren. (meer dan 3 tegelijk kan
time-out problemen veroorzaken; je kunt er later meer installeren)

Denk aan het volgende:

- Taalpakketten in aangepaste distributies zullen niet getoond worden op
  dit moment aangezien deze al geïnstalleerd zijn.
- Een versie van de voorgestelde pakketten komen overeen met de Joomla
  Major versie (4.0.x, 4.1.x, etc.). De minor versie van het pakket kan
  mogelijk niet corresponderen, d.w.z. je installeert versie 4.0.3 en
  een 4.0.2 taalpakket wordt getoond.
- Taalpakketten in het bovenstaande voorbeeld die niet compatibel zijn
  zullen wellicht onvertaalde strings bevatten.
- De taalpakketten die niet geschikt zijn zullen als een update worden
  aangeboden wanneer de pakketten zijn vertaald door de geregistreerde
  vertaal teams. De beschikbare update zal in het Controle paneel
  getoond worden als ook in **Extensions Manager **→** Update**. Dit is
  gelijk aan **Extensions Manager **→** Install Languages**.

Klik op **Volgende** en een voortgangsbalk wordt zichtbaar, terwijl het
taalpakket of pakketten worden geïnstalleerd.

#### Kies de standaard taal

Wanneer de installatie van de talen klaar is, zul je een
**Gefeliciteerd! Jouw Joomla! Site is klaar.** scherm zien. Het verschil
zal een lijst met geïnstalleerde talen zijn waaruit je de standaard taal
voor de Site en de Beheerder interface kunt selecteren.

<img
src="https://docs.joomla.org/images/d/d2/J40_Installation_screen_page_4_default_langs.png"
class="thumbborder" decoding="async" data-file-width="500"
data-file-height="650" width="500" height="650" alt="500" />

- Selecteer de standaardtaal die je wilt gebruiken.
- Klik, wanneer je de standaardtaal hebt geselecteerd op de *Selecteer
  standaard taal* knop om te bevestigen.
- Er wordt een systeemboodschap getoond dat Joomla de standaard
  ADMINISTRATOR en SITE taal heeft ingesteld. Dit bericht kan worden
  gesloten.

#### Afronden

Je kunt nu navigeren naar het *Administratie dashboard*. Log in door te
klikken op *Open Administrator* of direct naar de startpagina van de
website gaan door te kiezen voor *Open website*.

## Verwante informatie

-  Hosting
  instellen
-  Hosting en Server
  instellen
-  Maak een VPS
  Test-server
-  Instellen van je lokale
  omgeving
-  Joomla CLI
  installatie
