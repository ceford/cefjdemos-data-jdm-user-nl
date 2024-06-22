<!-- Filename: Backup_Basics_for_a_Joomla!_Web_Site / Display title: Back-up beginselen voor een Joomla! website -->

Houd altijd een recente back-up van uw site. Ongelukken gebeuren, maar
er zijn vele andere redenen waarom het helpt om uw back-up bestanden
beschikbaar te hebben voor als de nood aan de man komt.

Oorzaken van het verlies van gegevens. Joomla sites kunnen worden
beschadigd door kwaadaardige aanvallers als de beheerder van de site
geen aandacht besteedt aan beveiliging, of in zeldzame gevallen dat
hackers de beveiliging weten te omzeilen. Joomla! is ontworpen voor
teamwork, en zelfs goede bewerkingen kunnen een site schade berokkenen.

Er zijn vele redenen denkbaar waarom beheerders van de website moeten
kunnen terugkeren naar een eerdere werkende staat.

Oefen zowel backup als restore. Niemand zou voor het oefenen van
vaardigheden in noodsituaties moeten wachten op een daadwerkelijke
noodsituatie. Veel mensen maken een backup van een reeds beschadigde
situatie, en ontdekken dan pas dat er eigenlijk geen backup was. Niemand
stelt het op prijs als een schip zinkt met lege reddingsboten, en het is
ook aan te bevelen om te oefenen met mensen uit reddingsboten halen en
over zetten op een ander werkend systeem.

Het hebben van een back-up is niet alleen over ongevallen, omdat een
persoon die goed overweg kan met backups ook kan helpen met veilige
ontwikkeling van nieuwe functies. Backup en restore helpt webbeheerders
met het maken van een staging website waar nieuwe wijzigingen kunnen
worden toegepast zonder gevaar voor de productie website. De kloon kan
worden gemaakt op een lokale machine die fungeert als een test-server,
of een andere map of een web hosting account ondersteunen met de SQL en
PHP versies die worden gebruikt door de website die u hebt gebeackupped.

Het is voor iedereen gemakkelijk om de live site en de tijdelijke site
door elkaar te halen, dus verander de kleur van je staging site template
om de ontwikkelaars te herinneren dat de staging site is niet live voor
het publiek.

## Back-up maken van een Joomla website (algemene methode)

This is the preferred method using the Akeeba Backup Extension.

- Akeeba Backup produceert een `.jpa`-bestand
- Het .jpa-bestand bevat alle mappen/bestanden en database-bestanden.
- Het .jpa-bestand bevat ook een installatiebestand
- Kkickstart.php (van Akeeba) pakt het jpa-bestand uit
- U moet dan het installatieprogramma uitvoeren en installeer uw website
  als een gewone Joomla! installatie
- Het installatieprogramma wijzigt de configuratie om het herstellen op
  een nieuwe locatie en vraagt om de nieuwe databasegegevens.

Nadat de database gecreëerd is voor je Joomla! installatie kan je Akeeba
installeren, het kan van <a
href="https://extensions.joomla.org/extensions/extension/access-a-security/site-security/akeeba-backup/"
class="external text" target="_blank" rel="noreferrer noopener">de
Joomla extension directory</a> gedownload worden. Er is een link met de
volledige instructies beschikbaar.

## Methode in twee delen

Er zijn twee delen van een volledige back-up van uw Joomla website. Ze
zijn:

1.  De database informatie, meestal een mysql-database.
1.  De bestanden en mappen op uw website, net als statische html
    websites gehost.

Als u geen back-up van uw bestanden en database maakt, is uw back-up
onvolledig.

#### Database backup - Deel 1 van 2

Een van de eerste stappen om een back-up van uw Joomla website te maken,
is om de site te sluiten voor het publiek, back-ups te maken van de
bestanden, en vervolgens opnieuw openen van de site. De stappen van
phpmyadmin.net missen deze broodnodige stap. Ga naar de backend van uw
Joomla controle panel, onder de globale configuratie, onder het tabblad
site, stel dan "website offline" = ja in.

Dit zal het uiterlijk van uw configuration.php veranderen in de root van
uw Joomla website.

Een beheerder moet gebruik maken van het hosting control panel om dit
bestand te bekijken of FTP gebruiken om dit bestand te downloaden en te
bekijken. In configuration.php u vindt de naam van de database die
ge-back-upped moet worden.

Zoek naar de regel met code welke lijkt op `var $db = 'x1234';` of
`public $db = 'x1234';` Hierbij is "x1234" de naam van uw database.

Met de aanmeldingsgegevens van uw server of hosting bedrijf opent u de
PhpMyAdmin tool. Open de database en zoek de tabel met de naam "users"
en klik vervolgens op het pictogram van de "weergave" van de gegevens in
die tabel.

Ziet u de namen van de medewerkers die accounts hebben op je Joomla
site? Deze weergave biedt u het vertrouwen dat u een back-up van de
juiste database gaat maken.

Klik op het tabblad export, vervolgens uitvoeren.

Uw browser zal uw database downloaden in een SQL-bestand.

Kijk waar je browser dat bestand opslaat, vervolgens verplaatst u het
bestand naar een veel veiliger drive of locatie.

SQL Server databases kunnen een back-up zonder PhpMyAdmin maken en in
plaats daarvan met behulp van de SQL commando-regel. Als u weet hoe dat
te doen, heeft u waarschijnlijk geen behoefte aan deze documentatie.

Het is aan te raden een back-up van de database minstens twee keer per
week te maken of zelfs dagelijks (en meer) als u een actieve site heeft.

### Bestandssysteem backup - Deel 2 van 2

Ga verder met uw site als deze offline is, zie hierboven. Uw joomla
mappen en bestanden kunnen worden ondersteund door het downloaden van
een FTP-programma of met behulp van de file manager van uw webhoster.
Beide van deze opties werken, de een is niet beter dan de ander..

FTP-tools verplaatsen duizenden Joomla bestanden en kosten meer tijd.
Het FTP-proces kan worden vertraagd en onderbroken. De meeste hosting
bedrijven bieden een control panel om duizenden bestanden in één map te
zetten en vervolgens zeer snel een zip-bestand te kunnen maken.

Dit betekent dat uw site offline is voor een kortere tijdsduur, en u
heeft slechts één zip-bestand. Ga naar uw hosting control panel en zoek
het file manager icoon.

Als u uw hosting file manager gebruikt, oefen dan met die interface om
uw server map te selecteren en een zip-bestand te maken. Download het
zip-bestand lokaal en pak het lokaal uit om te zien welke bestanden in
het zip-bestand aanwezig zijn. Deze optie maakt het ook mogelijk om
hetzelfde zip-bestand te gebruiken voor herstel van een staging site.

Een back-up van de Joomla bestanden met FTP is niet anders dan een
back-up van een statische HTML-website. Download alle bestanden en
mappen die aanwezig zijn in de hoofd Joomla map. De gedownloadlocatie is
een map op uw lokale computer. Zorg ervoor dat het bestand en de
directory structuur hetzelfde blijft als in de live-site. Wanneer u
bestanden herstelt, gebruikt u de FTP-utility om de bestanden te
uploaden naar een nieuwe server.

"Zodra u uw bestanden heeft gedownload via zip-of FTP, kunt u uw site
weer online zetten."'

## Meer backup documentatie

De meeste beheerders van een Joomla website hebben toegang tot hun MySQL
gegevens met behulp van de GUI-interface, genaamd PhpMyAdmin, zie <a
href="https://phpmyadmin.readthedocs.org/en/latest/faq.html#how-can-i-backup-my-database-or-table"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">Hoe kan ik een backup van mijn
database of tabel maken?</a> voor meer informatie.

Er zijn verschillende geautomatiseerde back-up-extensies voor Joomla!
beschikbaar in de
<a href="http://extensions.joomla.org" class="external text"
target="_blank" rel="noreferrer noopener">Joomla! Extensions
Directory</a>. Hier is een link naar <a
href="http://extensions.joomla.org/extensions/extension?searchall=backup&amp;controller=filter"
class="external text" target="_blank" rel="noreferrer noopener">Joomla!
Backup Extensions</a>.

Wanneer servers zijn ondergebracht in hetzelfde gebouw als het
personeel, dienen de web-beheerders er extra zorg voor te dragen dat de
back-up kopieën van de database/bestanden in een ander gebouw wordedn
bewaard. Brand, diefstal, water of andere schade wist vaak zowel de live
website als de back-ups. Op regelmatige basis worden de web-beheerders
geacht zowel de database als bestanden op CD te branden of op te slaan
op een externe vaste offsite schijf.

## Aanvullende notities

### 2FA (Twee-factor authenticatie)

Als u gebruik maakt van 2-factor authenticatie (beschikbaar sinds
Augustus 2014) en je bent uitgesloten van uw site kunt u de naam van de
map plugins/twofactorauth veranderen in twofactorauth.BAK en in loggen
op uw beheersgedeelte. Schakel alle plug-ins onder de "twofactorauth"
groep uit. Tot slot, verander de naam van de plug-ins/twofactorauth.BAK
map van uw site terug naar twofactorauth.

- Zie ook: Twee-factor authenticatie
  handleiding
