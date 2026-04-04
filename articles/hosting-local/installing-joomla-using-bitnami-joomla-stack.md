<!-- Filename: Installing_Joomla!_using_BitNami_Joomla!_stack / Display title: Bitnami Installatie   -->

## Voorwoord

**OPMERKING:** BitNami Joomla! stack bestaat niet langer als een zelfstandige installer. In plaats daarvan wordt het aangeboden als: 1) Een cloud-gebaseerde instantie, 2) In een container, ofwel Kubernetes of Docker, of 3) Een virtuele machine. De virtuele machine zal draaien op uw besturingssysteem in een hypervisor zoals Virtual Box of VMware Player. Het wordt nog steeds geleverd met alle vereiste afhankelijkheden zoals in de zelfstandige installer.

Optie 1 hieronder is niet meer van toepassing. Ook in Optie 2, BitNami Lamp Stack verderop, wordt geleverd in de cloud of een virtuele machine. In elk geval maakt Bitnami het eenvoudig en compleet om een goede lokale installatie van Joomla! te hebben.

U kunt de nieuwste versie van het Bitnami-pakket voor Joomla! voor Windows, Linux en Mac downloaden op <a href="http://bitnami.org/stack/joomla" rel="nofollow noreferrer noopener">http://bitnami.org/stack/joomla</a>.

**Herziening Nodig!**

BitNami Joomla! Stack is een alles-in-één installer die het eenvoudig maakt om Joomla op je computer te installeren. Het is gratis, gemakkelijk te gebruiken en zelfstandig. Dat betekent dat het alle benodigde software (afhankelijkheden) bundelt en automatisch configureert die nodig is om Joomla te laten draaien voor ontwikkelings- of productie-doeleinden, inclusief Apache HTTP Server, MySQL en PHP.

## Optie 1: Joomla! stack (Aanbevolen)

Deze methode gaat ervan uit dat je al een
(**W**indows/**L**inux/**M**ac)...**AMP**-omgeving (Apache HTTP Server, MySQL, &
PHP) hebt geïnstalleerd.

### Joomla! Stack installeren

Ongeacht welk besturingssysteem je gebruikt (Windows / Linux /
Mac), het installatieproces is hetzelfde.

Download de nieuwste versie van Joomla! Stack van de
<a href="http://bitnami.org/stack/joomla"
rel="nofollow noreferrer noopener">BitNami website</a>.

Vind de installer die je net hebt gedownload (de bestandsnaam zal vergelijkbaar zijn met
bitnami-joomla-VERSIE-linux-installer.run). Dubbelklik op het pictogram om de installer te starten.

Als je Linux gebruikt, moet je de bestandseigenaren uitvoeringsrechten geven, gebruik daarvoor dit commando:

chmod +x /pad/naar/bitnami-joomla-VERSIE-linux-installer.run

<img src="https://docs.joomla.org/images/a/a0/Joomla_welcome2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Joomla Bitnami lampstack setup" />

Klik op "Volgende".

<img src="https://docs.joomla.org/images/5/5f/Joomla_components2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Joomla Bitnami lampstack components" />

Selecteer de componenten die je wilt installeren. Als je niet zeker bent, laat dan de standaardcomponenten geselecteerd. Klik op "Volgende" wanneer je klaar bent.

<img src="https://docs.joomla.org/images/0/0a/Joomla_directory2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Joomla Bitnami lampstack installation directory" />

Nu zal er gevraagd worden waar je het programma wilt installeren. Geef de
locatie op waar je de BitNami Joomla! stack wilt installeren en klik op
"Volgende" wanneer je klaar bent.

<img src="https://docs.joomla.org/images/3/3c/Joomla_userdata2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Joomla Bitnami lampstack admin account" />

De gebruikersnaam en het wachtwoord die je hier opgeeft, zullen worden gebruikt om het admin-account in Joomla! aan te maken. Klik op "Volgende" wanneer je klaar bent.

<img src="https://docs.joomla.org/images/8/8b/Joomla_sitename2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Joomla Bitnami lampstack sitenaam" />

Typ de naam die je voor je Joomla site wilt gebruiken en klik op "Volgende".

<img src="https://docs.joomla.org/images/d/dd/JoomlaReadytoinstall2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Joomla Bitnami lampstack Klaar om te installeren" />

De installer biedt je de mogelijkheid om een e-mailaccount te configureren, zodat Joomla! meldingen via e-mail kan versturen. Klik op "Volgende".

<img src="https://docs.joomla.org/images/9/9d/JoomlaCopyingfiles2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Joomla Bitnami lampstack Bestanden kopiëren" />

Wacht even terwijl de installer de bestanden kopieert en je
Joomla! installatie configureert.

<img src="https://docs.joomla.org/images/e/ea/Joomlafinalscreen2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Joomla Bitnami lampstack eindscherm" />

Joomla! is nu geïnstalleerd en klaar voor gebruik. Klik op "Voltooien" om de
applicatie te starten.

<img src="https://docs.joomla.org/images/8/8d/JoomlaManager.png"
decoding="async" data-file-width="784" data-file-height="586"
width="784" height="586" alt="Joomla Bitnami lampstack Beheer servers" />

Met het beheergereedschap is het eenvoudig om de Apache en MySQL
servers te starten/stoppen.

<img
src="https://docs.joomla.org/images/7/73/Joomlaapplicationscreen2.png"
decoding="async" data-file-width="982" data-file-height="729"
width="982" height="729" alt="Joomla applicatiescherm" />

Het is gemakkelijk om de Joomla! database te beheren met phpMyAdmin.

<img src="https://docs.joomla.org/images/f/f3/JoomlaphpMyAdmin.png"
decoding="async" data-file-width="982" data-file-height="751"
width="982" height="751" alt="phpMyAdmin scherm" />

## Optie 2: BitNami LAMPStack en Joomla!

### Wat is BitNami LAMPStack?

BitNami LAMPStack is een gratis, gemakkelijk te installeren pakket dat elk stuk software (afhankelijkheid) bundelt dat nodig is om een LAMP (Apache, MySQL en PHP voor Linux) omgeving op te zetten en draaiende te houden voor ontwikkelings- of productiedoeleinden. Het is een zelfstandige eenheid, maakt geen aanpassingen aan uw systeem en kan gemakkelijk worden verwijderd. U kunt de nieuwste versie van BitNami LAMPStack voor Linux downloaden op <a href="http://bitnami.org/stack/lampstack" rel="nofollow noreferrer noopener">http://bitnami.org/stack/lampstack</a>. Een <a href="http://bitnami.org/stack/wampstack" rel="nofollow noreferrer noopener">Windows-versie</a> en een <a href="http://bitnami.org/stack/mampstack" rel="nofollow noreferrer noopener">OS X-versie</a> zijn ook beschikbaar.

Ongeacht welk besturingssysteem u gebruikt (Windows / Linux / Mac), het installatieproces is hetzelfde.

### BitNami LAMPStack installeren

Zoek de installatietool die u zojuist van de BitNami-website heeft gedownload (de bestandsnaam zal vergelijkbaar zijn met bitnami-lampstack-VERSIE-linux-installer.run). Dubbelklik op het pictogram om de installatie te starten.

<img src="https://docs.joomla.org/images/1/14/Lampstack_welcome.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Bitnami lampstack welkom" />

Klik op "Volgende".

<img src="https://docs.joomla.org/images/7/78/Lampstack_directory.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Bitnami lampstack map" />

Nu vraagt het waar u het programma wilt installeren. Selecteer de locatie op uw apparaat en klik op "Volgende" wanneer u klaar bent.

<img src="https://docs.joomla.org/images/2/22/Lampstack_passwd.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Bitnami lampstack wachtwoord" />

Voer uw MySQL root-wachtwoord in. Dit zal het wachtwoord zijn voor de "root" gebruiker van de database.

<img src="https://docs.joomla.org/images/7/72/LampstackReadytoinstall.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Bitnami lampstack klaar om te installeren" />

De installatietool is nu klaar om het installatieproces te starten. Klik op "Volgende".

<img src="https://docs.joomla.org/images/1/19/LampstackCopyingfiles.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Bitnami lampstack bestanden kopiëren" />

Wacht een moment terwijl de installatietool de bestanden kopieert en uw LAMPStack-installatie configureert.

<img src="https://docs.joomla.org/images/b/bc/Lampstackfinalscreen.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Bitnami lampstack laatste scherm" />

BitNami LAMPStack is nu ingesteld en klaar voor gebruik. Klik op "Voltooien" om de applicatie te starten.

### Joomla! handmatig installeren

Volg de instructies zoals beschreven in het artikel Joomla installeren.

*Vertaald door openai.com*

