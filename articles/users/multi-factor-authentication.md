<!-- Filename: J4.x:Multi-factor_Authentication / Display title: Multifactor Authenticatie  -->

## Introductie

Het Joomla! Multi-factor authenticatiesysteem is gebaseerd op Akeeba Loginguard en veel van deze documentatie is met toestemming afgeleid van Akeeba.

## Wat doet het?

Het voegt meerdere, optionele Twee Staps Verificatie methoden toe voor Joomla! login. Na het inloggen met alleen je gebruikersnaam en wachtwoord, word je gevraagd om je tweede stap verificatie op te geven, bijvoorbeeld een code die door Google Authenticator wordt gegenereerd. Totdat je een correcte tweede stap verificatie hebt gegeven, zul je geen toegang hebben tot enige pagina's op de site. Je wordt altijd doorgestuurd naar de "gevangenen login" pagina. Dit is vergelijkbaar met wat Google doet wanneer je probeert in te loggen bij Gmail.

Dit verschilt van de originele Joomla! twee factor authenticatiemethode die vereiste dat de tweede authenticatiefactor (bijvoorbeeld de code die door Google Authenticator wordt gegenereerd) samen met de gebruikersnaam en het wachtwoord werd ingevoerd.

De voordelen van Twee Staps Verificatie zijn:

- Het is minder verwarrend voor de gebruiker. De "Geheime Sleutel" veld dat gebruikers in verwarring brengt, is niet langer nodig.
- Het kan werken met niet-wachtwoord inlogmethodes zoals sociale login (bijv. Facebook), veilige hardware tokens, SSO (single sign-on) etc. Ter verduidelijking: Twee Staps Verificatie kan zo worden geconfigureerd dat het wordt gevraagd nadat een gebruiker via een niet-wachtwoord inlogmethode heeft ingelogd. Het implementeert geen niet-wachtwoord inlogmethoden.
- Het heeft betere toegangscontrole. Je kunt Gebruikersopties instellen om Meerfactor Authenticatie te Vereisen of Uit te Schakelen per gebruikersgroep.
- Het staat alternatieve authenticatiemethoden toe in één enkel account. Je kunt meerdere authenticatiemethoden in je account hebben. Bijvoorbeeld, je kunt een Google Authenticator-app en een YubiKey instellen.
- Het ondersteunt methoden die geen code invoeren vereisen. Bijvoorbeeld FIDO2-dongles, biometrische verificatie etc. Deze moeten interageren met de browser en/of het besturingssysteem via native HTML5 API's.
- Het ondersteunt methoden die gebruikersinteractie vereisen. Bijvoorbeeld het sturen van een code via pushbericht, SMS of e-mail. Deze methoden vereisen dat wordt geweten welke gebruiker wordt geauthenticeerd voordat de authenticatiecode naar de gebruiker wordt gestuurd.
- Het is gratis. In tegenstelling tot diensten van derden die meerfactor authenticatie bieden, hoef je geen vooraf opgestelde installatiekosten of maandelijkse / jaarlijkse onderhoudskosten te betalen voor elke site of gebruiker die Twee Staps Verificatie gebruikt. De software is gratis.

## Hoe werkt het

Je logt normaal in op je site, bijvoorbeeld door een gebruikersnaam en wachtwoord op te geven. Het is belangrijk op te merken dat je op dit moment je tweefactor-authenticatiegegevens niet hoeft in te voeren.

Het systeem detecteert dat je nu bent ingelogd, maar de tweefactor-authenticatie nog niet hebt uitgevoerd. Het slaat de URL op die je zou moeten zien en leidt je direct door naar de captive inlogpagina. Elke poging om naar een andere pagina te navigeren resulteert in het verschijnen van de captive pagina.

Modules op je site kunnen gevoelige informatie bevatten. Om de vertrouwelijkheid te waarborgen, worden modules gedwongen gedeactiveerd tijdens het renderen. Dit betekent dat er geen modulepositie op de pagina zal worden weergegeven. Onthoud dit voor het geval je merkt dat de header of andere belangrijke ontwerpgebieden van je site ontbreken op de captive inlogpagina.

Merk op dat plug-ins daarentegen NIET worden uitgeschakeld. Dit komt zowel doordat Joomla het enorm moeilijk maakt om specifieke plug-ins te verwijderen zodra ze zijn geladen, als omdat de meeste plug-ins kritieke functionaliteit op je site uitvoeren.

Nadat je je tweede stap verificatie hebt verstrekt, wordt er een vlag ingesteld in de gebruikerssessie die aangeeft dat je volledig geautoriseerd bent om de site te gebruiken. Bovendien word je doorverwezen naar de URL die het opsloeg direct nadat je oorspronkelijk was ingelogd.

## Twee-factor authenticatie versus WebAuthn-logins

Inloggen met WebAuthn is de meest veilige optie. Je geeft alleen een gebruikersnaam op die als openbare, onprivileged informatie wordt beschouwd. De site creëert een cryptografische uitdaging die wordt ondertekend door de browser met behulp van beveiligde hardware — een externe beveiligde hardwaretoken of de Trusted Platform Module / Secure Enclave van je apparaat — en die wordt teruggestuurd naar de server. De server valideert de handtekening. Deze validatie gebruikt openbare-sleutelcryptografie waarbij de site alleen de openbare sleutel opslaat. Dit maakt de login praktisch ongevoelig voor phishing en extreem veilig. Als je dat gebruikt, heb je geen tweede authenticatiefactor nodig — maar als je dat echt wilt, kun je WebAuthn ook daarvoor gebruiken.

Afgezien van het gebruik van federatieve loginmethoden (zoals inloggen met je sociale media-account, een Single Sign-On-service, een LDAP-server, enzovoort) is een conventionele gebruikersnaam + wachtwoord-login bij lange na niet zo veilig als een WebAuthn-login. Het invoeren van een gebruikersnaam en een wachtwoord kan worden onderschept, gestolen of geraden. Dit maakt het vertrouwen op alleen een gebruikersnaam en een wachtwoord zeer problematisch.

Voor multi-factor authenticatie geef je alleen je gebruikersnaam en wachtwoord op. Een geslaagde phishing-aanval zou alleen deze eerste authenticatiefactor verkrijgen maar niet je tweede authenticatiefactor. Na succesvolle login krijg je een captive pagina te zien. Je kunt niets anders op de site doen totdat je je tweede factor geeft. Omdat de input van de tweede factor op een eigen pagina wordt gepresenteerd, kan deze interactief zijn (bijv. WebAuthn), asynchroon (bijv. een OTP ontvangen via e-mail, sms of pushmelding) of door de gebruiker geïnitieerd (bijv. een TOTP of een Yubikey OTP). Nog beter, een gebruiker kan meerdere methoden voor de tweede factor op zijn account hebben ingeschakeld om onbedoelde vergrendelingen van de site te voorkomen. Je kunt bijvoorbeeld WebAuthn gebruiken met een externe beveiligde hardware dongle als je primaire, meest veilige tweede factor. Je zou ook een reguliere TOTP kunnen instellen voor het geval je de dongle verliest of vergeet mee te nemen. Sommige methoden voor de tweede factor staan meerdere instanties toe, bijvoorbeeld je kunt meerdere WebAuthn-authenticators hebben, zodat je de ingebouwde authenticator in je Windows-computer, je iPhone en je Android-tablet kunt gebruiken zonder dat je elke keer dat je je bureau verlaat een hardware dongle en adapters moet meenemen.

Laten we het samenvatten. Van meest veilig naar minst veilig zijn je opties:

- WebAuthn als je primaire loginmethode met secundaire multi-factor authenticatie.
- WebAuthn als je enige loginmethode.
- Gebruikersnaam en wachtwoord als je primaire loginmethode met secundaire multi-factor authenticatie.
- Alleen een gebruikersnaam en wachtwoord als je enige loginmethode.

## Plugins

Elk van de factoren in Multi-factor Authenticatie wordt geïmplementeerd via plugins. Ze kunnen naar behoefte worden ingeschakeld of uitgeschakeld. En nieuwe kunnen worden toegevoegd wanneer er nieuwe methoden beschikbaar komen. De plugins die met de Joomla-kern worden geleverd, omvatten:

- **Verificatiecode**: zescijferige verificatiecodes gegenereerd door een authenticatie-app (Google Authenticator, Authy, LastPass Authenticator, enzovoort), een wachtwoordbeheerder (1Password, BitWarden, Keeper, KeePassXC, Strongbox, enzovoort) of, in sommige gevallen, hun browser.
  
- **YubiKey**: Hiermee kunnen gebruikers op uw site Multi-factor Authenticatie gebruiken met een YubiKey veilig hardware-token. Gebruikers hebben hun eigen YubiKey nodig, beschikbaar via www.yubico.com.

- **Webauthenticatie**: ondersteund door alle moderne browsers. De meeste browsers bieden apparaten-specifieke authenticatie, beschermd door een wachtwoord en/of biometrie (vingerafdruksensor, gezichtsherkenning, ...).

- **Authenticatiecode via e-mail**: Gebruik tijdelijke, zescijferige beveiligingscodes die via e-mail naar u worden gestuurd. De standaardinstelling is 2 minuten.

- **Vaste code**: dit is bedoeld voor testen en illustratie en is standaard uitgeschakeld. Het moet niet worden ingeschakeld op een productiesite.

Let op dat er een aparte **Systeem - WebAuthn Wachtwoordloos Inloggen** plugin is om inloggen via de Webauthenticatieknop in het loginformulier af te handelen.

## Gebruikersopties

Het formulier Gebruikers: Opties bevat een Multi-Factor Authenticatie-formulier om te configureren hoe Multi-factor Authenticatie werkt in Joomla. Selecteer de knop Informatie Inline Help weergeven voor informatie over elke optie.

![gebruikersopties multi-factor authenticatie formulier](../../../en/images/users/users-configuration-mfa.png)

## Gebruikersprofiel

Het formulier Beheerder / Gebruikers: Profiel bewerken heeft aparte tabbladen voor WebAuthn Login en Multi-factor Authenticatie, maar het laatste is alleen zichtbaar voor de eigenaar van het account. Zelfs Supergebruikers zien dit tabblad niet voor andere gebruikers.

Het formulier Site / Bewerk je profiel heeft de formulier tabs van de backend boven elkaar geplaatst, wat verwarrend kan zijn omdat Web Authenticatie twee keer verschijnt, eerst voor wachtwoordloze login en als tweede voor Multi-factor Authenticatie. De volgende illustratie toont het Multi-factor Authenticatie gedeelte van het formulier nadat een methode is aangemaakt. Dit stelt automatisch de functie in op Ingeschakeld en toont de optie om Back-upcodes te maken.

![siteweergave van gebruikers multi-factor authenticatieformulier](../../../en/images/users/multi-factor-authentication-site-profile.jpg)

Zoals hierboven vermeld, kun je elk uitproberen door op de knop + Toevoegen ... te klikken, maar selecteer Annuleren in het daaropvolgende formulier als je besluit niet verder te gaan.

*Vertaald door openai.com*

