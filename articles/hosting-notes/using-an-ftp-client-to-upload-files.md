<!-- Filename: Using_an_FTP_client_to_upload_files / Display title: Een FTP-client gebruiken om bestanden te uploaden. -->

Omdat vele hostingbedrijven het niet toestaan dat hun gebruikers
shell/lokale toegang tot hun bestanden hebben zullen gebruikers die
nieuwe bestanden naar hun hostingruimte willen uploaden gebruik moeten
maken van een "File Transfer Program"
<a href="https://en.wikipedia.org/wiki/FTP_client" class="extiw"
title="wikipedia:FTP client">FTP</a> programma's staat gebruikers toe om
bestanden naar de server te uploaden die lokaal bewerkt zijn. Er is een
verscheidenheid aan
<a href="https://en.wikipedia.org/wiki/FTP_client" class="extiw"
title="wikipedia:FTP client">FTP</a> programma's beschikbaar en
<a href="https://en.wikipedia.org/wiki/Comparison_of_FTP_clients"
class="extiw" title="wikipedia:Comparison of FTP clients">dit
overzicht</a> laat de sterke punten van tal van deze populaire
programma's zien, waarvan er vele open source zijn of gratis te
downloaden zijn.

Als u Firefox gebruikt kunnen we
<a href="http://fireftp.mozdev.org/" class="external text"
target="_blank" rel="nofollow noreferrer noopener">FireFTP</a>
suggereren als een handige add-on. FireFTP zal voor deze handleiding
worden gebruikt.

U wilt de weergave van verborgen bestanden uitschakelen zodat u niet uw
.htaccess bestand (op een linux server) verliest wanneer u upload.

## Met behulp van Windows verkenner

Als u een Windows besturingssysteem geïnstalleerd heeft kunt u Windows
verkenner gebruiken om met FTP verbinding te maken.

### Windows Verkenner openen

De afbeeldingen die volgen zijn afkomstig van Windows Vista maar het
proces blijft het zelfde.

Eer zijn vele manieren om Windows verkenner te starten. U kan een folder
of Mijn computer openen, of u kan de **Windowstoets** ingedrukt houden
en op **R** drukken. Type dan **explorer.exe** in en klik op **OK**.

<img src="https://docs.joomla.org/images/f/f2/Runexplorer-en.png"
decoding="async" data-file-width="427" data-file-height="233"
width="427" height="233" alt="Runexplorer-en.png" />

### Verbinding maken met FTP

OOm verbinding te maken met uw FTP-server heeft u de login-gegevens
nodig die door uw hosting of administrator zijn aangeleverd. In de
adresbalk typt u:**`ftp://USERNAME:PASSWORD@example.com`** waarbij u de
gebruikersnaam, wachtwoord en example.com vervangt met uw eigen
gegevens. Als u Windows Vista gebruikt, moet u misschien op de adresbalk
dubbelklikken om de tekst toe te voegen. Druk op **enter** op uw
toetsenbord wanneer u de gegevens correct hebt ingevoerd en Windows
explorer zal verbinding maken met uw FTP server.

Als u de aanmeldgegevens onjuist ingevoerd hebt ontvangt u een
foutbericht vergelijkbaar met dit:

<img src="https://docs.joomla.org/images/2/2a/Errorwindowsftp-en.png"
decoding="async" data-file-width="496" data-file-height="345"
width="496" height="345" alt="Errorwindowsftp-en.png" />

Als dit het geval is, voer dan opnieuw uw gebruikersgegevens in de
tekstvakken en probeer het opnieuw.

U ziet nu een lijst van mappen en bestanden van uw server vergelijkbaar
met de volgende afbeelding:

<img
src="https://docs.joomla.org/images/a/ab/Connectedwindowsftp-en.png"
decoding="async" data-file-width="680" data-file-height="411"
width="680" height="411" alt="Connectedwindowsftp-en.png" />

*Uit veiligheidsoverwegingen zijn de `bestanden/folders` in dit
voorbeeld verwijderd*

### Overdracht van bestanden

Het voordeel van het gebruiken van Windows explorer als uw
FTP-applicatie is dat u waarschijnlijk bekend bent met hoe het
overbrengen van bestanden werkt. De interface is identiek als u zou
kopiëren/verplaatsen naar een andere map op uw computer.

De truc is om te bepalen naar welke map u de bestanden wilt uploaden. In
de meeste gevallen zal u moeten uploaden naar een map met de naam
**"public_html"**, **"htdocs"** or **"www"**. U kan dit opnemen met uw
hosting of administrator.

Om een bestand te uploaden kunt u het bestand slepen van de
oorspronkelijke map naar het venster dat met uw FTP-server verbonden is.
Hier is een voorbeeld:

<img src="https://docs.joomla.org/images/0/07/Transferftpwin-en.png"
decoding="async" data-file-width="1069" data-file-height="566"
width="1069" height="566" alt="Transferftpwin-en.png" />

### Het sluiten van uw FTP-verbinding

Om uw FTP-verbinding te sluiten, sluit simpelweg het Windows Explorer
venster. Om dit te doen, drukt u op de rode "X"' in de rechterbovenhoek
van het venster, zoals aangegeven in de volgende screenshot.

<img src="https://docs.joomla.org/images/8/86/Closewin-en.png"
decoding="async" data-file-width="380" data-file-height="201"
width="380" height="201" alt="Closewin-en.png" />

## FireFTP gebruiken

<a href="http://fireftp.mozdev.org/" class="external text"
target="_blank" rel="nofollow noreferrer noopener">FireFTP</a> is een
goed programma voor FTP-overdracht indien u Mozilla Firefox gebruikt.

### FireFTP opstarten

Om met een bestand versturen te beginnen kunt u FireFox openen en op ''
*Extra \>\> FireFTP* klikken . FireFTP zal geopend worden in een nieuw
tabblad.

<img src="https://docs.joomla.org/images/8/8d/Fireftpmenu-en.png"
decoding="async" data-file-width="226" data-file-height="280"
width="226" height="280" alt="Fireftpmenu-en.png" />

### Configuratie van uw FTP-Gegevens

Als dit de eerste keer dat u verbinding maakt naar een FTP-server, dient
u de configuratie van FireFTP in te stellen om te kunnen verbinden naar
de juiste server. U kan de gegevens hiervan van uw host of beheerder
krijgen.
