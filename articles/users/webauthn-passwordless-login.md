<!-- Filename: WebAuthn_Passwordless_Login / Display title: WebAuthn-inloggen -->

## WebAuthn Wachtwoordloze Aanmelding

Web Authenticatie, of kortweg WebAuthn, stelt een gebruiker in staat om veilig in te loggen op een site zonder een wachtwoord te gebruiken — hoewel een gebruikersnaam nog steeds nodig is. Het maakt gebruik van sterke cryptografie op een manier die uiterst bestand is tegen de meest voorkomende problemen met wachtwoorden:
* iemand heeft het geraden (brute force-aanval)
* iemand heeft het onderschept (man-in-the-middle-aanval)
* iemand heeft je ertoe gebracht het vrij te geven (phishing-aanval)
* iemand heeft het gekraakt nadat hij een kopie van je databasegegevens te pakken kreeg (SQL-injectie-aanvallen)
* iemand heeft het gestolen.

WebAuthn is niet alleen erg veilig; het is ook zeer gebruiksvriendelijk! Je hoeft geen lange wachtwoorden meer te onthouden of een wachtwoordbeheerder te gebruiken. Alles wat je nodig hebt, is een *authenticator*, soms ook een *pass key* genoemd.

Een authenticator kan vele vormen aannemen, fysiek of virtueel. Het kan een aparte hardware-sleutel zijn die via USB, Bluetooth of NFC met je apparaat verbonden is. Het kan je apparaat zelf zijn, dat zijn ingebouwde authenticator ontgrendelt met een pincode, vingerafdruklezer, gezichtsherkenning of een vergelijkbare biometrische controle.

Deze functie werkt al op Android- en iOS/iPadOS-apparaten en we werken eraan om het ook op Windows in te schakelen. Het kan zelfs je telefoon zijn - momenteel is dit mogelijk met Android-telefoons, maar deze functie komt ook naar iOS/iPadOS-apparaten.

WebAuthn werkt alleen via HTTPS en alleen wanneer je site een geldig, vertrouwd certificaat gebruikt. Maak je geen zorgen, je hoeft geen extra geld uit te geven; gratis services zoals Let's Encrypt zijn doorgaans geïntegreerd in webhostingcontroles en werken perfect samen met WebAuthn.

WebAuthn maakt gebruik van openbare sleutelscryptografie, dezelfde beproefde technologie die je sites veilig houdt met HTTPS, je bankgegevens beschermt, enzovoort. De privésleutel verlaat nooit de authenticator. Je site slaat alleen een openbare sleutel op. Zelfs als je slachtoffer wordt van een datalek, blijft de aanvaller met een vrijwel nutteloze openbare sleutel achter; het zou hen duizenden tot miljoenen CPU-jaren kosten om het te kraken, in tegenstelling tot de paar minuten of uren die nodig zijn om de hash van een vast wachtwoord dat je kunt onthouden te kraken.

WebAuthn is de toekomst van authenticatie. Eenvoudig, veilig en zorgeloos. Alles wat vaste wachtwoorden niet zijn.

De volgende afbeelding toont een hardware-apparaat dat in de USB-poort van een laptopcomputer is gestoken. Het kostte £15 in februari 2022.

![foto van Hardware apparaat](../../../en/images/users/passwordless-login-hardware-device.jpg)

WebAuthn gebruikt een systeemplugin die standaard is ingeschakeld. Er zal een **Web Authenticatie**-knop aanwezig zijn in de standaard Joomla 4 en latere inlogschermen, zoals geïllustreerd in het beheerdersinlogscherm:

![veilig beheerdersinlogformulier](../../../en/images/users/passwordless-login-login-form.jpg)

## Gebruikersconfiguratie

De gebruiker moet zich eerst registreren met een normale gebruikersnaam en wachtwoord. Na het inloggen gaat u naar het gebruikersprofiel formulier. Voor een beheerder:

- Selecteer **Gebruikersmenu → Account bewerken → W3C Web Authenticatie (WebAuthn) Inloggen** om het formulier op te roepen, aanvankelijk zonder geregistreerde authenticators.
- Selecteer **Nieuwe Authenticatie toevoegen**

De exacte presentatie van de volgende stap hangt af van uw browser. Meestal ziet u een waarschuwing, bericht of venster waarin u wordt gevraagd een authenticatortype te selecteren of, als u een hardware-authenticator gebruikt die aan uw apparaat is gekoppeld, eraan wordt herinnerd op de knop van de hardware-authenticator te drukken. Om veiligheids- en praktische redenen is er een relatief korte tijdsspanne toegestaan voor het activeren van de authenticator: 60 seconden.

![beveiligde beheerderslogin hardware prompt](../../../en/images/users/passwordless-login-hardware-propmpt.png)

Zodra u uw authenticator ontgrendelt — door op een knop te tikken, uw vingerafdruk / gezicht te scannen, een PIN-code in te voeren of een combinatie van het bovenstaande, afhankelijk van uw authenticator — verdwijnt het bericht, wordt de authenticator geregistreerd en verschijnt het scherm als volgt:

![beveiligde beheerderslogin geregistreerde authenticator](../../../en/images/users/passwordless-login-registered-authenticator.png)

Het is erg belangrijk om op te merken dat u alleen authenticators kunt registreren of verwijderen op uw eigen gebruikersaccount. Om veiligheidsredenen is het zelfs voor een Super User niet toegestaan om authenticators op andere gebruikersaccounts te registreren, te bewerken of toe te voegen.

### Authenticators

U kunt elke FIDO U2F- of FIDO2-authenticator gebruiken. FIDO U2F is een oudere standaard die een meer beperkte, minder veilige selectie van cryptografische methoden ondersteunt. FIDO2 is de nieuwere standaard die veel veiligere cryptografische methoden ondersteunt, inclusief elliptische curvecryptografie, een cryptografische methode die zelfs als resistent wordt beschouwd tegen kwantumcomputing (als en wanneer dat een praktische realiteit wordt). Bovendien kunnen FIDO2-authenticators zodanig worden ingesteld dat zij extra beveiligingen hebben, zoals een PIN-code of een biometrische controle (bijv. vingerafdrukscan), wat betekent dat zelfs als u het fysieke bezit van de authenticator zelf verliest, degene die het vindt niet kan inloggen op uw sites.

Als u op zoek bent naar het kopen van een hardware-authenticator, kunt u zoeken naar "FIDO2" in uw favoriete marktplaats, zoals Amazon. Er is een ruime keuze beschikbaar.

U kunt ook een software FIDO-sleutel zoals Krypton gebruiken als uw authenticator.

Veel apparaten hebben ingebouwde FIDO2-conforme authenticatie:

- Windows 10 en 11 hebben Windows Hello met een PIN-code, vingerafdrukscanner, gezichtsherkenningscamera of een combinatie van hardware-sleutel en PIN-code. Ondersteuning voor Windows Hello wordt aan de plugin toegevoegd met een release-doel van Joomla 4.2.0.
- macOS heeft TouchID op alle laptops met de T2-chipset of die gebaseerd zijn op Apple Silicon met de ingebouwde TouchID-sensor, evenals alle op Apple Silicon gebaseerde desktops met het nieuwe Apple Aluminium-toetsenbord met een vingerafdrukscanner.
- iOS / iPadOS heeft TouchID op alle apparaten met een vingerafdrukscanner en FaceID op alle nieuwere apparaten met een FaceID-infraroodpuntprojector.
- Sommige Android-apparaten hebben een vingerafdrukscanner of een gezichtsherkenningscamera. Deze kunnen ook als FIDO2-authenticators werken, op Android 9 of hoger met Google Chrome ten minste.
- Andere apparaten kunnen ook beschikbaar zijn. Bijvoorbeeld Android-telefoons die gebruik maken van ![caBLE](https://groups.google.com/a/fidoalliance.org/g/fido-dev/c/go6GoFW27Dw/m/9flCLR5pBQAJ?pli=1)

### WebAuthn-compatibele browsers

Browsers gebaseerd op Chromium en Firefox ondersteunen WebAuthn sinds begin 2019.

Safari en alle iOS/iPadOS-browsers (die in feite Safari zijn met een ander uiterlijk) ondersteunen WebAuthn volledig sinds iOS/iPadOS 13 eind 2019 is uitgebracht.

Praktisch gezien, als uw besturingssysteem en browser zijn uitgebracht na midden 2020, zou u geen problemen moeten ondervinden. Alleen enkele zeer ongebruikelijke browsers hebben nog geen ondersteuning voor WebAuthn.

## Authenticatie

Om in te loggen moet je je gebruikersnaam invoeren in het veld Gebruikersnaam van het inlogformulier. Je hoeft je wachtwoord niet in te voeren, maar als je browser het voor je invult, laat het dan gewoon staan. Het wachtwoord wordt NIET naar de server gestuurd wanneer het formulier wordt verzonden via de knop Webauthenticatie.

Hieruit volgt dat je kunt inloggen met je Gebruikersnaam en Wachtwoord of met Gebruikersnaam en Webauthenticatie.

## Hoe de Plugin Uitschakelen

Als je WebAuthn niet wilt toestaan, ga dan naar de lijst met plugins en zoek System - WebAuthn Wachtwoordloos Inloggen in de System-groep en schakel het uit. Er zijn geen parameters in te stellen.  

## Serververeisten

Opdat WebAuthn zou werken, moeten de volgende voorwaarden vervuld zijn:

- HTTPS met een geldig, ondertekend certificaat. De meeste hostingproviders laten je gratis certificaten gebruiken die zijn uitgegeven door Let's Encrypt. Deze werken prima met WebAuthn.
- De OpenSSL-extensie voor PHP moet geïnstalleerd en ingeschakeld zijn.  
- De PHP-extensie GMP of de PHP-extensie BCmath moet geïnstalleerd en ingeschakeld zijn (één van beide is voldoende).  
- De Sodium-bibliotheek moet idealiter ingeschakeld zijn; het stelt het gebruik van Elliptic Curve Cryptography op compatibele FIDO2-authenticators in staat, wat, zoals gezegd, de meest veilige cryptografische methode is.  

## Veelgestelde Vragen en Probleemoplossing

### Ik kan de “Web Authentication” inlogknop niet zien

Je bezoekt je site niet via HTTPS. WebAuthn is alleen beschikbaar voor HTTPS-sites met een geldig certificaat. Dit is een beveiligingsmaatregel die in de WebAuthn-standaard is opgenomen. De plug-in controleert feitelijk of de site via HTTPS wordt benaderd met behulp van Joomla's Uri-klasse. In zeldzame gevallen waarin de server het protocol verkeerd aangeeft, zie je de knop mogelijk niet, zelfs als je site (claimt) HTTPS te zijn. Hetzelfde geldt als je je configuration.php-bestand hebt bewerkt en de optionele \$live_site-configuratieparameter hebt ingesteld met een http://-protocolprefix in plaats van https://.

Let ook op dat inlogmodules en -componenten van derden, die hun eigen inlogformulier implementeren, deze knoppen mogelijk nog niet weergeven. We hebben nieuwe infrastructuur toegevoegd om ze te ondersteunen, net zoals we moesten doen in Joomla! 3.2 om ondersteuning te bieden voor Tweefactorauthenticatie.

### Ik moet nog steeds een gebruikersnaam opgeven. Zou WebAuthn niet van gebruikersnamen afkomen?

Niet echt, nee. De huidige specificatie van WebAuthn biedt geen identiteitsbeheer. Web browsers vereisen dat wij hen een lijst van acceptabele WebAuthn-publieke sleutels sturen tijdens de inlogfase. Dit betekent dat we je gebruikersnaam nodig hebben om ze op te halen.

Dat gezegd hebbende, maakt het gebruik van WebAuthn eindelijk duidelijk dat gebruikersnamen *niet als geheimen moeten worden beschouwd*. Ze worden beschouwd als openbare informatie die vrij aan een tegenstander kan worden doorgegeven, net zoals de openbare sleutels die in de database van de site zijn opgeslagen. Het enige geheim is opgeslagen in de authenticator zelf en verlaat de authenticator nooit!

### Ik heb een authenticator geregistreerd, maar als ik probeer in te loggen, zegt het dat ik dat niet heb gedaan. Is dit een bug?

Het is een bug maar niet met de WebAuthn-plugin zelf.

Een of meer plug-ins op je site veroorzaken PHP Notices, Warnings of Errors, waardoor het antwoord dat door je server wordt teruggestuurd, wordt beschadigd. Hierdoor kan de JavaScript op de pagina het serverantwoord niet parseren en is het onzeker of er authenticators door de gebruiker zijn geregistreerd.

Ga naar de backend van je site, Systeem, Wereldwijde configuratie en stel Foutrapportering in op Geen. In de meeste gevallen van slecht functionerende kern- en 3PD-plug-ins is dit voldoende. Controleer anders de uitvoer van het verzoek met behulp van de ontwikkelaarstools van je browser om te zien wat het verzoek beschadigt.

### Er is geen prompt in Safari om mijn authenticator te gebruiken

Dit zou niet langer moeten gebeuren met iOS 13, iPadOS 13 en macOS Catalina of een latere versie.

Dit is een Safari-bug in oudere versies van Safari. Oudere versies van Safari bevatten alleen ondersteuning voor WebAuthn als een experimentele functie en deze was nog niet helemaal voltooid.

### Ik kan geen biometrische sensor gebruiken (TouchID, vingerafdruk, Windows Hello)

Sommige oudere op Chromium gebaseerde browsers (behalve de officiële Google Chrome) hadden geen volledige ondersteuning voor ingebouwde authenticators. Ze zouden crashen of vastlopen wanneer je probeerde er een te gebruiken. Deze problemen zijn rond medio 2020 verholpen in deze browsers.

Als je Windows gebruikt, onthoud dan dat je apparaat een Trusted Platform Module (TPM)-chip MOET hebben en deze moet in de BIOS zijn ingeschakeld. Alleen een Windows Hello-compatibele biometrische sensor zal niet voldoende zijn. Dit is een beveiligingsmaatregel in de WebAuthn-standaard zelf: de authenticatie-informatie moet worden verwerkt met behulp van veilige, manipulatieresistente hardware om sleutelvervalsing te voorkomen (bijv. malware die op de computer draait, kan de sleutel die voor authenticatie wordt gebruikt, niet stelen).

Vergeet tenslotte niet dat de ondersteuning voor Windows Hello nog in ontwikkeling is en beschikbaar zal zijn bij de release van Joomla 4.2.

### Als ik een software-authenticator kan gebruiken, waarom zou ik me dan druk maken om een hardware-token?

Het belangrijkste van WebAuthn is de absolute geheimhouding van de privésleutel. Deze is alleen bekend bij de authenticator en mag onmogelijk te communiceren zijn met de buitenwereld.

In het geval van een hardware-authenticator, of het nu een afzonderlijk hardwareapparaat is of een TPM/Secure Enclave die in je apparaat is ingebouwd, is dit vanzelfsprekend door de aard van die hardware.

Een software-authenticator genereert een geheime sleutel en slaat deze op in het bestandssysteem. Het blijft echter een reguliere softwaretoepassing die binnen je gebruikelijke besturingssysteem draait, of dat nu je telefoon of computer is. Daarom is het vatbaar voor verschillende soorten aanvallen die kunnen worden gebruikt om op slinkse wijze informatie te stelen (beveiligingsproblemen in de software zelf, malware die Spectre-achtige kwetsbaarheden in moderne CPU's benut, enz.).

Een software-authenticator is dus veel handiger en veiliger dan een regulier wachtwoord, maar een hardware-authenticator biedt de beste beveiliging. Kies je authenticator op basis van je budget en beveiligingsbehoeften.

Gezien het feit dat de prijs van een FIDO-sleutel – die compatibel is met WebAuthn – minder dan €10 is op Amazon, kun je in de meeste praktische gebruikssituaties een hardware-authenticator gebruiken.

### Waarom zijn de inloggegevens versleuteld in de database? Is dit geen overkill?

Het enige dat wordt opgeslagen in de database is de publieke sleutel die door de authenticator wordt teruggestuurd wanneer we de attesteringsceremonie uitvoeren (dat is de formele naam voor het registreren van een authenticator volgens de WebAuthn-specificatie). Als publieke sleutel hoeft deze niet te worden beschermd tegen lezingen. Zelfs als een onbevoegde gebruiker deze informatie zou kunnen lezen, zouden ze de authenticator niet kunnen imiteren, bijvoorbeeld door deze te klonen.

Als een kwaadaardige gebruiker echter schrijfrechten zou hebben op slechts de `#__webauthn_credentials`-databasetabel, zonder leesrechten op het bestandssysteem en zonder schrijfrechten op een andere tabel, zouden ze theoretisch hun eigen authenticator kunnen **toevoegen**, waardoor ze de mogelijkheid hebben om zich voor te doen als de doelgebruiker op het systeem. Dit is een zeer theoretische aanval, aangezien ze ook de gebruikershandle van de gebruiker die ze aanvallen zouden moeten kennen, wat moeilijker is af te leiden zonder enige kennis van de site zelf. Bovendien is het zeer onwaarschijnlijk dat je alleen schrijfrechten hebt op deze tabel en niet op de hele database (in welk geval ze een nieuwe supergebruiker zouden kunnen aanmaken). Toch versleutelen we de inloggegevens om ervoor te zorgen dat zelfs deze geheel theoretische aanval niet slaagt.

We zijn ons er volledig van bewust dat als een gebruiker leesrechten heeft op het serverbestandssysteem, ze toegang hebben tot de versleutelingssleutel en de databaseconnectie-informatie, die allemaal zijn opgeslagen in configuration.php. In dit geval ben je echter al gehackt: de aanvaller kan configuration.php lezen en weet dus hoe hij verbinding kan maken met je database. In dit geval kunnen ze alles doen wat ze willen met je site, inclusief het verwijderen van alle bestaande supergebruikers en het aanmaken van hun eigen supergebruikersaccount. Daarom is er geen reden om te proberen deze situatie aan te pakken; je zou volledig gecompromitteerd (gehackt) zijn. Het enige dat een uitkomst zou kunnen bieden, zijn regelmatige, geteste, off-site back-ups.

### Ik heb Tweefactorauthenticatie ingesteld, maar ik ben ingelogd zonder mijn geheime sleutel op te geven. Is dit niet onveilig?

Nee, dit is opzettelijk en volgens ontwerp.

Toen we Tweefactorauthenticatie (TFA) toevoegden in Joomla! 3.2 kon je alleen inloggen op je site met een gebruikersnaam en wachtwoord. Wachtwoorden kunnen gestolen of geraden worden. Daarom was TFA de enige manier om een mate van beveiliging te bieden op doelen met hoog risico en hoge waarde. Dat was terug in 2013.

WebAuthn is een geheel andere authenticatieoplossing die geen van de problemen van vaste wachtwoorden heeft. Het gebruikt sterke cryptografie en beveiligde hardware om het praktisch onmogelijk te maken de cryptografische sleutels voor authenticatie te ondermijnen. Het is ook niet gevoelig voor phishing, d.w.z. je kunt niet worden misleid om het te gebruiken op een imiterende site omdat het WebAuthn-certificaat is gekoppeld aan de exacte domeinnaam waarvoor het is uitgegeven (ja, als je meerdere domeinen voor je site gebruikt of je site overzet naar een ander domein, moet je al je WebAuthn-authenticators opnieuw registreren!). Als gevolg hiervan is authenticatie met WebAuthn ongelooflijk veilig en overtreft het de redenen die TFA noodzakelijk maakten. Dit betekent dat als je succesvol authenticeert met WebAuthn, de TFA-geheime sleutel niet hoeft te worden en daarom ook niet wordt gecontroleerd.

In een ideale wereld zou je alleen in staat zijn om op je site in te loggen met WebAuthn. Dit is een functie waaraan we werken en die je mogelijk niet wilt inschakelen; als je domeinnaam verandert of je toegang verliest tot of al je WebAuthn-authenticators reset, zou je namelijk buitengesloten zijn van je site. Daarom moet je nog steeds TFA inschakelen op je gebruikersaccount op basis van het feit dat inloggen met een wachtwoord nog steeds kan worden gebruikt als een back-up voor het inloggen op je site en moet worden beschermd tegen bekende aanvallen op vaste wachtwoorden.

### Is TFA niet goed genoeg? Waarom hebben we WebAuthn nodig?

TFA alleen is in de meeste gevallen goed genoeg, maar lijdt aan twee problemen.

Ten eerste heeft het een behoorlijk onhandige gebruikerservaring. Je moet je steeds veranderende geheime sleutel opgeven met je gebruikersnaam en wachtwoord. De meeste mensen gebruiken TOTP (de zescijferige PIN die elke 30 seconden verandert), wat het inloggen vertraagt en gebruikers meestal frustreert. Het gebruik van een YubiKey is veel sneller, maar ook duurder en ingewikkelder om in te stellen wanneer je meer dan een paar gebruikers op de site hebt. Een YubiKey heeft ook een verwachte levensduur van ongeveer 2 jaar bij dagelijks gebruik bij het genereren van eenmalige wachtwoorden (deze raakt uit het eenmalige geheugen dat het gebruikt om bij te houden welke handtekeningen het heeft uitgegeven).

Ten tweede, als je TOTP gebruikt, ben je nog steeds vatbaar voor beveiligingsproblemen zoals keyloggers, phishing en de mogelijkheid dat de geheime sleutel die wordt gebruikt voor het genereren van de TOTP wordt gestolen. Bovendien, met een miljoen mogelijkheden en dertig seconden om ze te proberen, is het denkbaar dat een aanvaller geluk kan hebben aangezien Joomla je account niet vergrendelt of anderszins een rate limiting toepast voor mislukte inlogpogingen. Hoewel deze beschermingsmaatregelen zouden kunnen worden geïmplementeerd, zou de implementatie zelf kunnen worden misbruikt om een denial-of-service situatie te creëren die een legitieme gebruiker buitensluit van hun site terwijl de aanvaller druk bezig is deze te infiltreren. Het is een kwestie van de remedie die erger is dan de kwaal.

WebAuthn verbetert de gebruikerservaring aanzienlijk. Grote browsers hebben WebAuthn omarmd en bieden een overtuigende gebruikerservaring, waarbij de gebruikers worden begeleid om authenticators succesvol te gebruiken. Inloggen met WebAuthn is handiger, zelfs in vergelijking met het auto-aanvullen van een wachtwoordenbeheerder. Met recente versies van mobiele besturingssystemen wordt die ervaring, die ooit enigszins verwarrend was, snel gemakkelijker dan wachtwoorden en TFA ooit waren.

Waar WebAuthn echt op uitblinkt, is op het gebied van beveiliging. Door het gebruik van veilige hardware en de sterke validatie van de domeinnaam van de site is het praktisch immuun voor keyloggers, phishing en sleutelvervalsing. Het heeft zelfs ingebouwde bescherming tegen het klonen van sleutels. Ja, je kunt nog steeds je hardware verliezen – maar FIDO2-authenticators, of ze nu externe apparaten of ingebouwde apparaten zijn, kunnen worden vergrendeld met een PIN of biometrie. Over het algemeen is het gebruik van WebAuthn met FIDO2-authenticators meer diefstal- en verliesbestendig dan je huis- of autosleutels.

## Ontwikkelaarsnotities

### Extra inlogknoppen

De pluginmodule en com_users gebruiken nu de onUserLoginButtons-gebeurtenis, gedefinieerd en aangeroepen in `Joomla\CMS\Helper\AuthenticationHelper::getLoginButtons`, om de definities op te halen van extra knoppen die na de reguliere inlogknop moeten worden geplaatst.

Alle ontwikkelaars die een inlogmodule of, meer algemeen, een inlogformulier implementeren, moeten ook de publieke statische methode `Joomla\CMS\Helper\AuthenticationHelper::getLoginButtons` gebruiken om deze definities op te halen en deze knoppen weer te geven, zodat hun software volledig compatibel is met Joomla 4.

Ontwikkelaars die aangepaste knoppen willen implementeren, moeten kijken hoe de WebAuthn-systeemplugin deze functionaliteit implementeert. Dergelijke knoppen kunnen worden gebruikt voor de implementatie van single-sign-on-diensten van derden of zelfs voor inloggen met identiteitsdiensten van derden, zoals die worden aangeboden door populaire sociale media (Facebook, Google, Twitter, GitHub etc).

Deze wijziging heeft geen nadelige invloed op de achterwaartse compatibiliteit. Inlogmodules en inlogformulieren van derden blijven normaal functioneren, ook als ze de extra inlogknoppenfunctionaliteit niet implementeren, met als opvallende uitzondering de integraties die door die functionaliteit worden geboden, zoals Web Authenticatie zelf. Dat wil zeggen, ze zullen niet stoppen met functioneren (wat een b/c-breuk zou zijn), maar ze zullen niet volledig feature-compleet zijn.

### Toestaan van com_ajax op de backend-inlogpagina

De beheerdersinlogpagina voert een whitelisting uit van com_ajax in AdministratorApplication, zodat deze kan worden gebruikt om verzoeken van gastgebruikers af te handelen.

Deze wijziging veroorzaakt geen problemen met achterwaartse compatibiliteit, zolang ontwikkelaars verstandige praktijken gebruiken en niet aannemen dat het feit dat ze door com_ajax in de backend worden aangeroepen, bewijst dat de gebruiker is ingelogd op de backend. Dat zou een slechte beveiligingspraktijk zijn. De verstandige praktijk is om Joomla's User-object te gebruiken om te detecteren of het een gastgebruiker is en, zo niet, of de gebruiker toestemming heeft voor de actie die via com_ajax wordt gevraagd. Dat wil zeggen, als deze wijziging uw code heeft gebroken, dan was uw code al gebroken en moet deze toch opnieuw worden ontworpen.

## Verdere Informatie

De oorspronkelijke documentatie van deze functie bevindt zich in de pull request bij
[PR #28094](https://github.com/joomla/joomla-cms/pull/28094)

*Vertaald door openai.com*

