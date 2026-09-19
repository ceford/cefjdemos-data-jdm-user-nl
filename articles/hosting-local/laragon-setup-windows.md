<!--
{
    "source": "https://docs.joomla.org/https:",
    "title": "Laragon voor Windows",
    "description": " ",
    "author": ""
}
-->

## Een lokale Joomla-omgeving instellen met Laragon

Laragon is een lichtgewicht Windows-hulpprogramma dat Apache, MySQL en
PHP in één eenvoudige installatie beheert. Geen configuratiebestanden,
geen handmatige installatie: gewoon downloaden, uitvoeren en beginnen
met het bouwen en testen van Joomla. Lees dit artikel in het Joomla
Community Magazine: [Laragon: The Effortless, High-Performance
AMP Server for Windows](https://magazine.joomla.org/all-issues/october-2025/laragon-the-effortless,-high-performance-amp-server-for-windows).

Deze handleiding brengt je van nul naar een werkende lokale Joomlasite en
behandelt ook een kleine eigenaardigheid in de gebruikersinterface van de
nieuwste versie die eenvoudig is op te lossen zodra je weet wat er
gebeurt.

### Laragon downloaden en installeren

Ga om te beginnen naar de officiële [downloadpagina van
Laragon](https://laragon.org/download). Download de volledige versie van Laragon
(momenteel v8.6.1), omdat deze alles bevat wat je nodig hebt (zoals Apache,
MySQL en de nieuwste PHP-versies) en direct klaar voor gebruik is.
Je kunt ook rechtstreeks het [installatieprogramma](https://github.com/leokhoa/laragon/releases/download/8.6.1/laragon-wamp.exe) downloaden.

Zodra het `.exe`-bestand is gedownload, dubbelklik je erop om de
installatie te starten.

**Opmerking over Windows Defender:** Omdat Laragon een krachtig
ontwikkelprogramma is, kan Windows Defender SmartScreen het starten ervan blokkeren en
een blauw waarschuwingsscherm tonen. Dit is normaal - klik gewoon op **Meer informatie**
en klik vervolgens op de knop **Toch uitvoeren** die onderaan verschijnt.

![laragon setup windows protected warning](../../../en/images/hosting-local/laragon-setup-windows/01-laragon-setup-windows-protected-warning.png)

Doorloop de installatiewizard. De standaardinstellingen zijn prima,
maar houd deze twee belangrijke details in de gaten:

1.  **Installatielocatie:** Laat de installatiemap staan op
    `C:\laragon`. Installeren diep in `Program Files` of `Documents` kan later soms
    problemen met machtigingen veroorzaken.
2.  **Installatieopties:** Zorg ervoor dat het selectievakje **Auto virtual hosts** is
    aangevinkt. Deze functie geeft je lokale Joomla-site een nette
    URL (zoals `http://myjoomla.test`) in plaats van een onbewerkt IP-adres.

![installatieopties van Laragon](../../../en/images/hosting-local/laragon-setup-windows/02-laragon-setup-options.jpg)

Start je computer opnieuw op zodra de installatie is voltooid. (de installatiewizard
zal je vragen hetzelfde te doen)

### Je server starten en firewallmachtigingen

Open Laragon vanuit het menu Start en klik op de knop **Alles starten**.

Omdat dit de eerste keer is dat je een lokale server uitvoert, moet Windows
controleren of deze veilig is. Je ziet pop-ups van Windows Defender Firewall
waarin om netwerktoegang wordt gevraagd voor services zoals **Apache HTTP
Server**, **MySQL** en **Mailpit**.

- Klik bij elk van deze meldingen eenvoudig op **Toegang toestaan**.

Zodra je toestemming hebt gegeven, start Laragon je lokale omgeving. Je weet
dat deze werkt wanneer je de Apache- en MySQL-poortnummers in het
Laragon-venster ziet verschijnen.

### De eigenaardigheid "Al actief" (en hoe u dit oplost)

Wanneer u klaar bent met werken, klikt u mogelijk op "Alles stoppen" om Apache
en MySQL uit te schakelen en klikt u vervolgens op de "X" in de
rechterbovenhoek om het Laragon-venster te sluiten.

Dit is de eigenaardigheid: door op de "X" te klikken, wordt Laragon niet
volledig afgesloten. Het blijft stil op de achtergrond actief. Als u de
Laragon-app opnieuw probeert te openen vanuit het Startmenu of vanaf uw
bureaublad, ziet u rechtsonder op uw scherm een gele waarschuwing met de tekst:
**"Laragon is al actief!"**

![melding dat de Laragon-installatie al actief is](../../../en/images/hosting-local/laragon-setup-windows/03-laragon-setup-already-running-notice.png)

**De valkuil:** Als u op de "X" van die kleine gele waarschuwing klikt om deze te sluiten,
verdwijnt ook het hoofdvenster van Laragon, waardoor u geen toegang meer hebt
tot het configuratiescherm. (Opmerking: soms verschijnt er ook een licentiepop-up
waardoor de interface op vergelijkbare wijze vastloopt.)

**De oplossing:** Als uw interface verdwijnt of vastloopt, hoeft u alleen maar te
forceer het afsluiten van het achtergrondproces en begin opnieuw. Het is heel eenvoudig:

1.  Druk op `Ctrl + Shift + Esc` op je toetsenbord om **Windows
    Taakbeheer** te openen.
2.  Zoek naar **Laragon** in de lijst met actieve processen.
3.  Klik er met de rechtermuisknop op en selecteer **Taak beëindigen**.

Dat is alles! Je hebt het vastgelopen achtergrondproces veilig beëindigd. Je kunt
Laragon nu openen vanuit je Startmenu. Het programma wordt dan probleemloos
geladen, zodat je zonder fouten op "Start All" kunt klikken.

### Omgaan met de licentiepop-ups (de ‘zeurschermen’)

Laragon is gratis te gebruiken voor niet-commerciële ontwikkeling en tests
zonder een licentie aan te schaffen. Nadat je de app echter enige tijd
hebt gebruikt, krijg je waarschijnlijk een prompt voor een "Licentiesleutel"
waarin je wordt aangemoedigd het project te ondersteunen.

Omdat je de gratis versie gebruikt, kun je deze schermen eenvoudig sluiten,
maar er is een specifieke volgorde waar je rekening mee moet houden:

1.  Het hoofdvenster **Licentiesleutel** verschijnt boven je Laragon-
    interface. Klik op de tekst **Sluiten** of op de 'X'.<br>
    ![laragon setup license key window](../../../en/images/hosting-local/laragon-setup-windows/04-laragon-setup-license-key-window.png)
2.  Direct nadat je het hebt gesloten, verschijnt er een tweede pop-up met
    een **Waarschuwing**, waarin je eraan wordt herinnerd dat Laragon zonder
    licentie wordt uitgevoerd. Klik op **OK** of op de 'X'.<br>
    ![laragon setup no license warning](../../../en/images/hosting-local/laragon-setup-windows/05-laragon-setup-no-license-warning.png)
3.  Nadat je die tweede waarschuwing hebt gesloten, opent Laragon mogelijk automatisch
    je webbrowser openen en je doorsturen naar `https://laragon.org/key`. Je
    kunt dat browsertabblad gewoon sluiten.
4.  Wanneer je teruggaat naar de Laragon-interface en op **Start All** klikt
    om je server weer te starten, moet je mogelijk nog een keer door precies
    dezelfde twee pop-ups klikken.

Nadat je ze deze tweede keer hebt gesloten, verdwijnen de pop-ups en kun je
Laragon volledig vrij gebruiken!

*(Opmerking: Als je Laragon-interface op enig moment tijdens deze pop-ups
vastloopt en je nergens meer op kunt klikken, denk dan aan de
`Ctrl + Shift + Esc`-truc uit de vorige stap om het achtergrondproces te
beëindigen en opnieuw te beginnen)*

### Een database voor Joomla maken

Voordat u Joomla installeert, hebt u een lege database nodig om de gegevens ervan op te slaan.
Laragon bevat een ingebouwde databasemanager genaamd HeidiSQL, dus
alles wat u nodig hebt, is al aanwezig.

1.  Zorg ervoor dat uw Laragon-services actief zijn (klik op **Start All**).
2.  Klik op de knop **Database** in de hoofdinterface van Laragon.
3.  Er wordt een venster van Session Manager geopend. Laragon vult automatisch
    de standaard lokale inloggegevens voor u in (Gebruiker: `root`, Wachtwoord:
    *\[leeg laten\]*).
4.  Klik onderaan op de knop **Open**.<br>    
    **Probleemoplossing: fout 'Access denied for user 'root'@'localhost'"
    : ** Als u op de knop **Open** klikt en onmiddellijk een foutmelding over een
    mislukte verbinding krijgt, hoeft u zich geen zorgen te maken! Dit betekent meestal dat u
    een ander MySQL-programma (zoals XAMPP of MySQL Workbench) op de
    achtergrond hebt draaien, waardoor de toegang van Laragon tot de databasepoort
    (poort 3306) wordt geblokkeerd.<br>
    ![problemen met toegang bij de Laragon-installatie](../../../en/images/hosting-local/laragon-setup-windows/06-laragon-setup-troubleshooting.jpg)
    **De oplossing:**
    1.  Druk op de Windows-toets, typ **Services** en druk op Enter.
    2.  Blader omlaag door de lijst om **MySQL**, **MySQL80** of **MariaDB** te vinden.
    3.  Klik met de rechtermuisknop op de actieve service en selecteer **Stoppen**.
    4.  Ga terug naar Laragon, klik op **Alles stoppen**, vervolgens op **Alles starten** en
        probeer opnieuw op **Openen** te klikken in de sessiebeheerder. Er zou nu
        zonder fout verbinding moeten worden gemaakt.
5.  Zodra u succesvol bent verbonden en zich in de HeidiSQL-databasebeheerder bevindt, kijkt u naar de linkerkolom. Klik met de rechtermuisknop op de servernaam (meestal aangeduid als `Laragon.MySQL` of `127.0.0.1`).
6.  Beweeg de muisaanwijzer over **Nieuwe maken** en selecteer **Database**.
7.  Er verschijnt een klein venster. Typ een eenvoudige naam voor uw database in het veld "Naam" (bijvoorbeeld: `joomla_dev`). U kunt de vervolgkeuzelijst "Sortering" op de standaardinstelling laten staan.
8.  Klik op **OK**.
Je nieuwe database verschijnt in de lijst aan de linkerkant. Dat is
alles! Je kunt het databasebeheervenster nu volledig sluiten.

### Uw Joomla-bestanden ophalen

Nu uw server en database gereed zijn, is het tijd om de Joomla-
bestanden op hun plaats te zetten. Hoe u dit doet, hangt volledig af van wat u
met deze lokale installatie wilt bereiken:

**Methode 1: Voor het bouwen van een standaardwebsite** Als u alleen een
website wilt bouwen of extensies wilt testen, hebt u de standaard stabiele release nodig.

- Ga naar de officiële [Joomla-downloadpagina](https://downloads.joomla.org) 
  en download het nieuwste `.zip`-bestand van het **volledige pakket**.

**Methode 2: Voor het testen van PR's van de community (patches testen)** Als uw doel is
de community te helpen door patches en pullrequests te testen, hebt u een
vooraf samengesteld pakket nodig dat de absoluut nieuwste code bevat.

- **De nightly build:** Download de nieuwste `.zip` van de nightly build via
  [Nightly Builds](https://developer.joomla.org/nightly-builds.html).
  Deze worden elke nacht gegenereerd en zijn perfect voor gebruik met de
  Joomla Patch Tester-component.
- **Het vooraf gebouwde PR-pakket:** Als je een specifieke PR op GitHub test, scrol je naar de onderkant van de PR-pagina, klik je op **Show all checks** en zoek je naar de link **Download Prebuilt packages**.
  ![link naar vooraf gebouwd pakket voor Laragon](../../../en/images/hosting-local/laragon-setup-windows/07-laragon-setup-prebuilt-package-link.png)

**Methode 3: Voor het bijdragen van kerncode** Als je van plan bent code te schrijven en je eigen pull requests in te dienen, heb je de onbewerkte, niet-gecompileerde broncode nodig.

- Kloon de [Joomla CMS GitHub-repository](https://github.com/joomla/joomla-cms) rechtstreeks met Git naar je Laragon-omgeving.
- *Belangrijk:* Een onbewerkte GitHub-kloon werkt niet direct — je moet de terminal van Laragon openen en `composer install` en `npm ci` uitvoeren in je map om de PHP-afhankelijkheden en CSS/JS-assets te bouwen. (Omdat je de volledige versie van Laragon hebt geïnstalleerd, zijn Composer en NPM al op je systeem geïnstalleerd.)

### **De bestanden in Laragon plaatsen:**

Welke methode je ook hebt gekozen, de bestanden laten werken in Laragon
verloopt precies hetzelfde:

1.  Open de interface van Laragon en klik op de knop **Root**. Hierdoor wordt
    automatisch de map `C:\laragon\www` op je computer geopend.
2.  Maak in deze map `www` een nieuwe map voor je project. Houd de mapnaam
    eenvoudig, in kleine letters en zonder spaties (bijvoorbeeld:
    `joomla_dev` of `joomla_pr_test`).
3.  Plaats je Joomla-bestanden in deze nieuwe map. (Als je in methode 1 of 2
    een `.zip` hebt gedownload, pak dan alle inhoud rechtstreeks uit in deze
    map. Als je Git gebruikt in methode 3, kloon de repository dan naar deze
    map.)
4.  Omdat je tijdens de installatie "Auto virtual hosts" hebt ingeschakeld,
    gebruikt Laragon automatisch je mapnaam om je lokale webadres aan te maken. Een
    map met de naam `joomla_dev` is daardoor in je browser toegankelijk via
    `http://joomla_dev.test`.
    <br>
    **Tip: Houd je omgevingen schoon:** Het is een goed idee om
    verschillende mappen te maken voor verschillende Joomla-versies of specifieke PR-tests
    (bijvoorbeeld een map met de naam `joomla5_stable` en een andere met de naam
    `joomla4_dev`). Laragon voert ze allemaal probleemloos naast elkaar uit met
    hun eigen schone `.test`-URL's, zodat je code en databases
    niet door elkaar raken!
    <br>
    ![projectmappen instellen in Laragon](../../../en/images/hosting-local/laragon-setup-windows/08-laragon-setup-project-folders.png)

## De Joomla-installatie uitvoeren

Je hebt je database en je Joomla-bestanden staan in hun nieuwe
map (bijvoorbeeld `C:\laragon\www\joomla_dev`). Nu is het tijd om Joomla
daadwerkelijk te installeren!

**Cruciale stap: Apache opnieuw laden!** Als Laragon al actief was toen
je je nieuwe projectmap aanmaakte, weet Laragon nog niet dat de map
bestaat.

- Open de interface van Laragon.

- Klik rechtsboven op **"Reload"**. *(Hierdoor scant Laragon de map
  `www` opnieuw en genereert het nieuwe adres `http://joomla_dev.test`.)*

**De installatie voltooien:**

1. Open je webbrowser en typ de automatisch gegenereerde URL van je project
   in (bijv. `http://joomla_dev.test`).
2. Je zou onmiddellijk de Joomla-webinstallatiepagina moeten zien.
3. Kies je taal en voer een naam voor je Joomla-site in.
4. Stel je Super User-account in (onthoud deze inloggegevens, je hebt ze
   nodig om toegang te krijgen tot het Joomla-beheerdersdashboard!).
5.  Voer op het scherm **Databaseconfiguratie** de inloggegevens in voor
    de Laragon-database die je eerder hebt gemaakt:
    - **Databasetype:** `MySQLi` (standaard)
    - **Hostnaam:** `localhost`
    - **Gebruikersnaam:** `root`
    - **Wachtwoord:** *\[Laat dit volledig leeg\]*
    - **Databasenaam:** De exacte naam die je eerder in HeidiSQL hebt ingevoerd
      (bijvoorbeeld `joomla_dev`).
    ![laragon setup joomla installer database settings](../../../en/images/hosting-local/laragon-setup-windows/09-laragon-setup-joomla-installer-database.png)

6.  Klik op **Joomla installeren.**

Zodra de voortgangsbalk is voltooid, zie je een succesbericht. Je kunt nu op
**Site openen** klikken om je live lokale website te bekijken, of op
**Beheerder openen** om in te loggen op de Joomla-backend.

Dat is alles: je lokale Joomla-site is live en klaar voor gebruik.

*Vertaald door openai.com*