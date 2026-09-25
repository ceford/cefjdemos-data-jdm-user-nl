<!--
{
    "source": "https://docs.joomla.org/WebAuthn_Passwordless_Login",
    "title": "Inloggen met passkey",
    "description": " ",
    "author": ""
}
-->

## Inleiding

Met inloggen met een passkey, voorheen bekend als Web Authentication of kortweg
WebAuthn, kan een gebruiker veilig inloggen op een site zonder een wachtwoord te
gebruiken, hoewel een gebruikersnaam nog steeds nodig is. Het maakt gebruik van
sterke cryptografie op een manier die uiterst goed bestand is tegen de meest
voorkomende problemen met wachtwoorden:

* iemand heeft het geraden (brute-forceaanval)
* iemand heeft het onderschept (man-in-the-middle-aanval)
* iemand heeft u misleid om het prijs te geven (phishingaanval)
* iemand heeft het gekraakt nadat hij een kopie van uw databasegegevens in handen had gekregen
(SQL-injectieaanvallen)
* iemand heeft het gestolen.

Inloggen met een passkey is niet alleen zeer veilig; het is ook zeer
gebruiksvriendelijk! U hoeft geen lange wachtwoorden meer te onthouden of een
wachtwoordmanager te gebruiken. Het enige wat u nodig hebt, is een
*authenticator*, soms ook een *passkey* genoemd.

Een authenticator kan vele vormen aannemen, fysiek of virtueel. Het kan een
afzonderlijke hardware-sleutel zijn die via USB, Bluetooth of NFC verbinding
maakt met uw apparaat. Het kan ook uw apparaat zelf zijn, waarbij u de ingebouwde
authenticator ontgrendelt met een pincode, vingerafdruklezer, gezichtsscan of
een vergelijkbare biometrische controle.

Deze functie werkt al op Android- en iOS/iPadOS-apparaten en we werken eraan om
deze ook op Windows beschikbaar te maken. Het kan zelfs uw telefoon zijn —
momenteel is dit mogelijk met Android-telefoons, maar deze functie komt ook naar
iOS-/iPadOS-apparaten.

Inloggen met een passkey werkt alleen via HTTPS en alleen wanneer uw site daarvoor
een geldig, vertrouwd certificaat gebruikt. Geen zorgen, u hoeft geen extra
geld uit te geven; gratis diensten zoals Let's Encrypt zijn doorgaans
geïntegreerd in configuratieschermen van webhosting en werken uitstekend met
inloggen met een passkey.

Bij inloggen met een passkey wordt cryptografie met openbare sleutels gebruikt,
dezelfde bewezen technologie die uw sites veilig houdt met HTTPS, uw
bankgegevens beschermt enzovoort. De privésleutel verlaat de authenticator
nooit. Uw site slaat alleen een openbare sleutel op. Zelfs als u te maken krijgt
met een datalek, houdt de aanvaller een praktisch nutteloze openbare sleutel
over; het zou duizenden tot miljoenen cpu-jaren kosten om deze te kraken,
tegenover de paar minuten of uren die nodig zijn om de hash van een vast
wachtwoord te kraken dat u kunt onthouden.

Inloggen met een passkey is de toekomst van authenticatie. Eenvoudig, veilig en
zonder gedoe. Alles wat vaste wachtwoorden niet zijn.

De volgende afbeelding toont een hardwareapparaat dat in de USB-poort van een
laptop is gestoken. Het kostte £15 in februari 2022.

![foto van hardwareapparaat](../../../en/images/users/passkey-login/01-hardware-device.jpg)

Bij inloggen met een passkey wordt een systeemplug-in gebruikt die standaard is
ingeschakeld. In de standaard inlogschermen van Joomla 4 en later is een knop
**Inloggen met passkey** aanwezig, zoals geïllustreerd in het inlogscherm van de
beheerder:

![veilig inlogformulier voor beheerder](../../../en/images/users/passkey-login/02-login-form.png)

## Gebruikersconfiguratie

De gebruiker moet zich eerst registreren met een normale gebruikersnaam en
wachtwoord. Ga na het inloggen naar het formulier Gebruikersprofiel. Voor een
beheerder:

- Selecteer **Gebruikersmenu → Account bewerken → Inloggen met passkey** om het formulier te zien, 
  aanvankelijk zonder geregistreerde authenticators.
- Selecteer **Nieuwe passkey toevoegen**

De precieze weergave van de volgende stap is afhankelijk van uw browser.
Doorgaans ziet u een waarschuwing, bericht of venster waarin u wordt gevraagd
een type authenticator te selecteren of, als u een hardware-authenticator
gebruikt die op uw apparaat is aangesloten, waarin u eraan wordt herinnerd om
op de knop van de hardware-authenticator te drukken. Om veiligheidsredenen en
praktische redenen is er relatief weinig tijd beschikbaar om de authenticator
te activeren: 60 seconden.

![veilige prompt voor hardware bij beheerderlogin](../../../en/images/users/passkey-login/03-hardware-prompt.png)

Zodra u uw authenticator ontgrendelt — door op een knop te tikken, uw
vingerafdruk of gezicht te scannen, een pincode in te voeren of een combinatie
van bovenstaande, afhankelijk van uw authenticator — verdwijnt het bericht,
wordt de authenticator geregistreerd en verschijnt het scherm als volgt:

![veilige beheerderlogin met geregistreerde authenticator](../../../en/images/users/passkey-login/04-registered-authenticator.png)

Het is zeer belangrijk om op te merken dat u alleen authenticators op uw eigen
gebruikersaccount kunt registreren of verwijderen. Om veiligheidsredenen mag
zelfs een Super User geen authenticators registreren, bewerken of toevoegen op
andere gebruikersaccounts.

### Authenticators

Je kunt elke FIDO U2F- of FIDO2-authenticator gebruiken. FIDO U2F is een oudere
standaard die een beperktere, minder veilige selectie van
cryptografische methoden ondersteunt. FIDO2 is de nieuwere standaard die veel
veiligere cryptografische methoden ondersteunt, waaronder Elliptic Curve Cryptography,
een cryptografische methode waarvan wordt aangenomen dat deze zelfs bestand is tegen
quantumcomputing (als en wanneer dit werkelijkheid wordt). Bovendien kunnen FIDO2-
authenticators worden ingesteld met extra beveiligingen, zoals een
pincode of biometrische controle (bijvoorbeeld een vingerafdrukscan). Dit betekent dat zelfs
als je de fysieke authenticator zelf verliest, degene die deze vindt niet bij je sites
kan inloggen.

Als je een hardware-authenticator wilt kopen, kun je in je favoriete marktplaats,
zoals Amazon, zoeken naar
"FIDO2". Er is een ruime keuze.

Je kunt ook een softwarematige FIDO-sleutel zoals Krypton gebruiken als
authenticator.

Veel apparaten hebben ingebouwde FIDO2-compatibele authenticatie:

- Windows 10 en 11 hebben Windows Hello met een pincode, vingerafdrukscanner,
  camera voor gezichtsherkenning of een combinatie van hardwarematige sleutel en pincode.
- macOS heeft TouchID op alle laptops met de T2-chipset of op laptops die zijn gebaseerd op
  Apple Silicon en de ingebouwde TouchID-sensor gebruiken, evenals op alle desktops
  die zijn gebaseerd op Apple Silicon en het nieuwe Apple Aluminium-toetsenbord met een
  vingerafdrukscanner gebruiken.
- iOS / iPadOS heeft TouchID op alle apparaten met een vingerafdrukscanner en
  FaceID op alle nieuwere apparaten met een infraroodcamera voor
  FaceID-puntprojectie.
- Sommige Android-apparaten hebben een vingerafdrukscanner of een camera voor
  gezichtsherkenning. Deze kunnen ook werken als FIDO2-authenticators, op Android 9 of
  hoger en met ten minste Google Chrome.
- Er zijn mogelijk ook andere apparaten beschikbaar. Bijvoorbeeld Android-telefoons die
  [caBLE](https://groups.google.com/a/fidoalliance.org/g/fido-dev/c/go6GoFW27Dw/m/9flCLR5pBQAJ?pli=1) gebruiken

### Browsers die compatibel zijn met inloggen met een passkey

Praktisch gezien zou je geen problemen moeten hebben als je besturingssysteem en browser
na medio 2020 zijn uitgebracht. Alleen enkele zeer ongebruikelijke
browsers ondersteunen inloggen met een passkey nog niet.

## Authenticatie

Om in te loggen moet je je gebruikersnaam invoeren in het veld Username van het
inlogformulier. Je hoeft je wachtwoord niet in te voeren, maar als je browser het voor
je invult, laat je het gewoon staan. Het wachtwoord wordt NIET naar de server verzonden wanneer het formulier
via de knop Web Authentication wordt verzonden.

Daaruit volgt dat je kunt inloggen met je Username en Password of
met Username en inloggen met een passkey.

## De plug-in uitschakelen

Als je inloggen met een passkey niet wilt toestaan, ga je naar de lijst met plug-ins en
zoek je de plug-in **System - Passkey (Passwordless) Login** in de groep System en
schakel je deze uit. Er zijn geen parameters die je hoeft in te stellen.

## Serververeisten

Om inloggen met een passkey te laten werken, moet aan de volgende voorwaarden worden voldaan:

- HTTPS met een geldig, ondertekend certificaat. Bij de meeste hosts kun je gratis
  certificaten gebruiken die zijn uitgegeven door Let's Encrypt. Deze werken prima
  met inloggen met een passkey.
- De OpenSSL-extensie voor PHP moet zijn geïnstalleerd en ingeschakeld.
- De PHP-extensie GMP of de PHP-extensie BCmath moet zijn geïnstalleerd
  en ingeschakeld (een van beide volstaat).
- De Sodium-bibliotheek moet idealiter zijn ingeschakeld; hiermee wordt het gebruik van
  Elliptic Curve Cryptography mogelijk gemaakt op compatibele FIDO2-authenticators, wat,
  zoals gezegd, de veiligste cryptografische methode is.

## Veelgestelde vragen en probleemoplossing

### Ik zie de knop *Sign in with passkey* niet

Je opent je site niet via HTTPS. Inloggen met een passkey is alleen beschikbaar
voor HTTPS-sites met een geldig certificaat. Dit is een beveiligingsmaatregel die
is ingebouwd in de standaard voor inloggen met een passkey. De plug-in controleert daadwerkelijk
of de site via HTTPS wordt geopend met behulp van de Uri-klasse van Joomla. In zeldzame gevallen
waarin de server onjuiste informatie over het protocol geeft, zie je de knop mogelijk niet,
ook al beweert je site (dat deze) HTTPS gebruikt. Hetzelfde geldt als je je
configuration.php-bestand hebt bewerkt en de optionele \$live_site-configuratieparameter
hebt ingesteld met een http://-protocolprefix in plaats van https://.

Houd er ook rekening mee dat modules en componenten voor aanmelding door derden die
hun eigen inlogformulier implementeren deze knoppen mogelijk nog niet weergeven. We hebben
nieuwe infrastructuur toegevoegd om dit te ondersteunen, vergelijkbaar met wat we in
Joomla! 3.2 moesten doen om tweefactorauthenticatie te ondersteunen.

### Ik moet nog steeds een gebruikersnaam opgeven. Was Passkey-aanmelden niet bedoeld om gebruikersnamen overbodig te maken?

Niet echt. De huidige specificatie van Passkey-aanmelden biedt geen identiteitsbeheer. Webbrowsers vereisen dat we ze tijdens de aanmeldingsfase een lijst met acceptabele openbare sleutels voor Passkey-aanmelden sturen. Dit betekent dat we je gebruikersnaam nodig hebben om deze op te halen.

Dat gezegd hebbende, maakt het gebruik van Passkey-aanmelden eindelijk duidelijk dat gebruikersnamen *niet als geheimen moeten worden beschouwd*. Ze worden beschouwd als openbare informatie die vrijelijk naar een aanvaller kan worden verzonden, net als de openbare sleutels die in de database van de site zijn opgeslagen. Het enige geheim wordt in de authenticator zelf opgeslagen en verlaat de authenticator nooit!

### Ik heb een authenticator geregistreerd, maar wanneer ik probeer aan te melden, krijg ik te horen dat ik dat niet heb gedaan. Is dit een bug?

Het is inderdaad een bug, maar niet in de Passkey-aanmeldingsplug-in zelf.

Een of meer plug-ins op je site genereren PHP-meldingen, waarschuwingen of fouten, waardoor het antwoord dat door je server wordt teruggestuurd, wordt beschadigd. Daardoor kan de JavaScript op de pagina het serverantwoord niet parseren en weet deze niet zeker of de gebruiker authenticators heeft geregistreerd.

Ga naar de backend van je site, Systeem, Globale configuratie en stel Foutrapportage in op Geen. In de meeste gevallen van slecht functionerende core- en 3PD-plug-ins is dit voldoende. Controleer anders de uitvoer van het verzoek met de ontwikkelaarstools van je browser om te zien wat het verzoek beschadigt.

### Er verschijnt geen prompt in Safari om mijn authenticator te gebruiken

Dit zou niet meer moeten gebeuren met iOS 13, iPadOS 13 en macOS Catalina of een latere versie.

Dit is een Safari-bug in oudere versies van Safari. Oudere versies van Safari boden alleen ondersteuning voor Passkey-aanmelden als experimentele functie en waren nog niet helemaal af.

### Ik kan geen biometrische sensor gebruiken (TouchID, vingerafdruk, Windows Hello)

Sommige oudere browsers op basis van Chromium (met uitzondering van Google Chrome zelf) hadden geen volledige ondersteuning voor ingebouwde authenticators. Ze crashten of liepen vast wanneer je er een probeerde te gebruiken. Deze problemen zijn rond medio 2020 in deze browsers opgelost.

Als je Windows gebruikt, moet je onthouden dat je apparaat BESLIST een Trusted Platform Module (TPM)-chip moet hebben en dat deze in het BIOS moet zijn ingeschakeld. Alleen een biometrische sensor die compatibel is met Windows Hello is niet voldoende. Dit is een beveiligingsmaatregel in de Passkey-aanmeldingsstandaard zelf: de authenticatorinformatie moet worden verwerkt met behulp van veilige, manipulatiebestendige hardware om ondermijning van de sleutel te voorkomen (bijvoorbeeld: malware die op de computer draait, kan de sleutel die voor authenticatie wordt gebruikt niet stelen).

Houd er ten slotte rekening mee dat er nog steeds aan ondersteuning voor Windows Hello wordt gewerkt en dat deze met Joomla 4.2 wordt uitgebracht.

### Als ik een software-authenticator kan gebruiken, waarom zou ik dan een hardwaretoken gebruiken?

De absolute geheimhouding van de privésleutel vormt de spil van Passkey-aanmelden. Deze is alleen bekend bij de authenticator en het moet onmogelijk zijn om de sleutel naar de buitenwereld te communiceren.

Bij een hardware-authenticator, of dit nu een afzonderlijk hardwareapparaat is of een TPM / Secure Enclave die in je apparaat is ingebouwd, is dit door de aard van die hardware vanzelfsprekend.

Een software-authenticator genereert een geheime sleutel en slaat deze op in het bestandssysteem. Het blijft echter een gewone softwaretoepassing die binnen je gewone besturingssysteem draait, of dat nu het besturingssysteem van je telefoon of van je computer is. Daardoor is deze vatbaar voor verschillende soorten aanvallen die kunnen worden gebruikt om heimelijk informatie te stelen (beveiligingsproblemen in de software zelf, malware die Spectre-achtige kwetsbaarheden in moderne CPU's gebruikt, enzovoort).

Een software-authenticator is dus veel handiger en veiliger dan een gewoon wachtwoord, maar een hardware-authenticator biedt de beste beveiliging. Kies je authenticator op basis van je budget en beveiligingsbehoeften.

Aangezien de prijs van een FIDO-sleutel (die compatibel is met Passkey-aanmelden) op Amazon minder dan €20 bedraagt, kun je in de meeste praktische gebruiksscenario's een hardware-authenticator gebruiken.

### Waarom zijn de referenties versleuteld in de database? Is dit niet overdreven?

Het enige dat in de database wordt opgeslagen, is de openbare sleutel die door de
authenticator wordt teruggegeven wanneer we de attestationceremonie uitvoeren (dat
is de formele naam voor het registreren van een authenticator volgens de
Passkey-inlogspecificatie). Omdat het een openbare sleutel is, hoeft deze niet
tegen lezen te worden beschermd. Zelfs als een onbevoegde gebruiker deze informatie
zou kunnen lezen, zou die de authenticator niet kunnen imiteren, bijvoorbeeld door
deze te klonen.

Als een kwaadwillende gebruiker echter alleen schrijftoegang zou hebben tot de
`#__webauthn_credentials`-databasetabel, zonder leestoegang tot het bestandssysteem
en zonder schrijftoegang tot een andere tabel, zou die in theorie zijn eigen
authenticator kunnen **toevoegen** en zich daardoor op het systeem kunnen voordoen
als de beoogde gebruiker. Dit is een zeer theoretische aanval, omdat die gebruiker
ook de gebruikershandle van de aangevallen gebruiker zou moeten kennen. Die is
moeilijk te achterhalen zonder enige voorkennis van de site zelf. Bovendien is het
uiterst onwaarschijnlijk dat iemand alleen schrijftoegang tot deze tabel heeft en
niet tot de volledige database (in welk geval die een nieuwe Super User zou kunnen
aanmaken). Toch versleutelen we de referenties om te voorkomen dat zelfs deze
volledig theoretische aanval kan slagen.

We zijn ons er volledig van bewust dat een gebruiker met leestoegang tot het
serverbestandssysteem toegang heeft tot de versleutelingssleutel en de
databaseverbindingsgegevens, die allemaal zijn opgeslagen in configuration.php.
In dat geval bent u echter al gehackt: de aanvaller kan configuration.php lezen en
weet daardoor hoe verbinding moet worden gemaakt met uw database. In dat geval kan
de aanvaller met uw site doen wat die wil, waaronder alle bestaande Super Users
verwijderen en een eigen Super User-account aanmaken. Daarom heeft het geen zin om
deze situatie te proberen op te lossen; u zou volledig gecompromitteerd
(gehackt) zijn. Het enige dat nog uitkomst kan bieden, zijn regelmatige, geteste
back-ups op een externe locatie.

### Ik heb tweefactorauthenticatie ingesteld, maar ik ben ingelogd zonder mijn geheime sleutel op te geven. Is dit niet onveilig?

Nee, dit is opzettelijk en zo ontworpen.

Toen we tweefactorauthenticatie (TFA) toevoegden in Joomla! 3.2, kon u alleen op
uw site inloggen met een gebruikersnaam en wachtwoord. Wachtwoorden kunnen worden
gestolen of geraden. Daarom was TFA de enige manier om een zekere mate van
beveiliging te bieden voor doelwitten met een hoog risico en een hoge waarde. Dat
was in 2013.

Inloggen met een passkey is een volledig andere authenticatieoplossing die geen
van de problemen van vaste wachtwoorden kent. Deze gebruikt sterke cryptografie en
beveiligde hardware om het praktisch onmogelijk te maken de cryptografische
authenticatiesleutels te ondermijnen. Deze is ook niet vatbaar voor phishing, d.w.z.
u kunt niet worden misleid om deze op een imiterende site te gebruiken, omdat de
passkey-inlogreferentie is gekoppeld aan de exacte domeinnaam waarvoor deze is
uitgegeven (ja, als u meerdere domeinen voor uw site gebruikt of uw site naar een
ander domein overbrengt, moet u al uw passkey-inlogauthenticators opnieuw
registreren – dat hebt u goed begrepen!). Als gevolg hiervan is authenticatie met
inloggen via een passkey uiterst veilig en vervangt deze de redenen waarvoor TFA
noodzakelijk was. Dit betekent dat wanneer u zich met succes aanmeldt met inloggen
via een passkey, de geheime TFA-sleutel niet hoeft te worden en daarom helemaal
niet wordt gecontroleerd.

In een ideale wereld zou u alleen op uw site kunnen inloggen met inloggen via een
passkey. Dit is een functie waaraan we werken en die u mogelijk niet wilt
inschakelen; als uw domeinnaam verandert of u de toegang tot al uw
passkey-inlogauthenticators verliest of deze opnieuw instelt, zou u immers geen
toegang meer hebben tot uw site. Daarom moet u TFA nog steeds inschakelen voor uw
gebruikersaccount, op basis van het feit dat inloggen met een wachtwoord nog steeds
als terugvaloptie kan worden gebruikt om op uw site in te loggen en moet worden
beschermd tegen bekende aanvallen op vaste wachtwoorden.

### Is TFA niet goed genoeg? Waarom hebben we Passkey-aanmelding nodig?

TFA is in de meeste gevallen op zichzelf goed genoeg, maar heeft twee problemen.

Ten eerste zorgt het voor een nogal omslachtige gebruikerservaring. U moet
uw steeds veranderende geheime sleutel samen met uw gebruikersnaam en
wachtwoord opgeven. De meeste mensen gebruiken TOTP (de zescijferige pincode
die elke 30 seconden verandert), waardoor het aanmelden trager wordt en
gebruikers zich vaak ergeren. Het gebruik van een YubiKey is veel sneller,
maar ook duurder en ingewikkelder om beschikbaar te stellen wanneer u meer
dan een paar gebruikers op de site hebt. Een YubiKey heeft bij dagelijks
gebruik voor het genereren van eenmalige wachtwoorden bovendien een verwachte
levensduur van ongeveer 2 jaar (het eenmalig beschrijfbare geheugen dat wordt
gebruikt om bij te houden welke handtekeningen zijn uitgegeven, raakt dan
op).

Ten tweede bent u bij het gebruik van TOTP nog steeds vatbaar voor
beveiligingsproblemen zoals keyloggers, phishing en de mogelijkheid dat de
geheime sleutel die wordt gebruikt om de TOTP te genereren, wordt gestolen.
Bovendien is het, met één miljoen mogelijkheden en dertig seconden om ze uit
te proberen, voorstelbaar dat een aanvaller geluk heeft, aangezien Joomla uw
account niet vergrendelt en ook geen snelheidsbeperking toepast voor mislukte
aanmeldpogingen. Hoewel deze beveiligingen kunnen worden geïmplementeerd, kan
de implementatie zelf worden misbruikt om een denial-of-service-situatie te
creëren waarbij een legitieme gebruiker geen toegang meer heeft tot zijn site
terwijl de aanvaller bezig is deze binnen te dringen. Het is een geval waarin
het middel erger is dan de kwaal.

Passkey-aanmelding verbetert de gebruikerservaring aanzienlijk. Grote
browsers hebben Passkey-aanmelding omarmd en bieden een overtuigende
gebruikerservaring, waarbij ze gebruikers begeleiden bij het succesvol
gebruiken van authenticators. Aanmelden met Passkey-aanmelding is handiger,
zelfs in vergelijking met het gebruik van de functie voor automatisch invullen
van een wachtwoordbeheerder. Met recente versies van mobiele
besturingssystemen wordt zelfs die ervaring, die aanvankelijk enigszins
verwarrend was, snel eenvoudiger dan wachtwoorden en TFA ooit zijn geweest.

Op het gebied van beveiliging blinkt Passkey-aanmelding pas echt uit. Door
gebruik te maken van beveiligde hardware en sterke validatie van de
domeinnaam van de site is het praktisch immuun voor keyloggers, phishing en
sleutelcompromittering. Het biedt zelfs ingebouwde bescherming tegen het
klonen van sleutels. Ja, u kunt uw hardware nog steeds kwijtraken — maar
FIDO2-authenticators, of het nu externe apparaten of ingebouwde authenticators
zijn, kunnen met een pincode of biometrie worden vergrendeld. Over het geheel
genomen is Passkey-aanmelding met FIDO2-authenticators beter bestand tegen
diefstal en verlies dan uw huissleutels of autosleutels.

## Notities voor ontwikkelaars

### Extra aanmeldknoppen

De plug-inmodule en com_users gebruiken nu de gebeurtenis onUserLoginButtons,
die is gedefinieerd in en wordt aangeroepen door
`Joomla\CMS\Helper\AuthenticationHelper::getLoginButtons`, om de definities op
te halen van eventuele extra knoppen die na de reguliere aanmeldknop moeten
worden geplaatst.

Alle ontwikkelaars die een aanmeldmodule of, meer in het algemeen, een
aanmeldformulier implementeren, moeten ook de openbare statische methode
`Joomla\CMS\Helper\AuthenticationHelper::getLoginButtons` gebruiken om deze
definities op te halen en deze knoppen weer te geven, zodat hun software
volledig compatibel is met Joomla 4.

Ontwikkelaars die aangepaste knoppen willen implementeren, kunnen bekijken
hoe de Passkey-systeemplug-in deze functionaliteit implementeert. Dergelijke
knoppen kunnen worden gebruikt voor het implementeren van
single-sign-on-services van derden of zelfs voor het aanmelden met
identiteitsservices van derden, zoals die worden aangeboden door populaire
sociale media (Facebook, Google, Twitter, GitHub enzovoort).

Deze wijziging heeft geen negatieve gevolgen voor achterwaartse
compatibiliteit. Aanmeldmodules en aanmeldformulieren van derden blijven
normaal functioneren, zelfs als ze de functie voor extra aanmeldknoppen niet
implementeren, met als opmerkelijke omissie dat integraties die door deze
functie mogelijk worden gemaakt, zoals Web Authentication, ontbreken. Dat wil
zeggen dat ze niet stoppen met functioneren (wat een b/c-breuk zou zijn), maar
dat ze niet alle functies bieden.

### com_ajax toestaan op de aanmeldpagina van de backend

De aanmeldpagina van de Administrator zet com_ajax op de witte lijst in
AdministratorApplication, zodat het kan worden gebruikt om verzoeken van
gastgebruikers af te handelen.

Deze wijziging veroorzaakt geen problemen met achterwaartse compatibiliteit,
zolang ontwikkelaars verstandige werkwijzen gebruiken en er niet van uitgaan
dat het feit dat com_ajax in de backend wordt aangeroepen, bewijst dat de
gebruiker bij de backend is aangemeld. Dat zou een slechte
beveiligingspraktijk zijn. De verstandige werkwijze is om het User-object van
Joomla te gebruiken om vast te stellen of het om een gastgebruiker gaat en,
zo niet, of de gebruiker toestemming heeft voor de machtiging die nodig is om
de via com_ajax aangevraagde actie uit te voeren. Met andere woorden: als
deze wijziging uw code heeft gebroken, was uw code al gebroken en moest deze
toch worden herzien.

## Meer informatie

De oorspronkelijke documentatie van deze functie staat in de pull request op
[PR #28094](https://github.com/joomla/joomla-cms/pull/28094)

*Vertaald door openai.com*