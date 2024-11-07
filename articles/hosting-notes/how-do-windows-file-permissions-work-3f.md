<!-- Filename: How_do_Windows_file_permissions_work%3F / Display title: Windows-bestandsmachtigingen  -->

## Introductie

Voor degenen onder jullie die Joomla!-websites ontwikkelen of leveren vanuit een Windows-omgeving, is het soms moeilijk om relevante informatie over machtigingen te verkrijgen. Helaas is het een feit dat de meeste webdiensten onder Unix worden aangeboden en dat Unix binnen deze omgeving vrij goed is gedocumenteerd. Hopelijk helpt de volgende informatie enige verwarring op te helderen en biedt het een beetje begeleiding.

### Overzicht van Windows-webserver

Laten we eerst de verschillen tussen servers bespreken. Over het algemeen lijkt het erop dat de meeste Windows-gebruikers ofwel Apache(Win32) of Microsoft IIS gebruiken. Deze twee webservers werken erg verschillend en gebruiken iets verschillende leveringsmodellen. Apache(Win32) draait meestal op de hostcomputer als de gebruiker waaronder het is geïnstalleerd, terwijl IIS wordt geïnstalleerd onder een specifieke gebruiker, maar zal draaien onder een nieuw geïnstalleerde gebruiker *IUSR_*.

### Standaard machtigingen

Standaard geeft Unix meestal alleen de *eigenaar* volledige toegang tot bestanden en mappen. In tegenstelling tot deze benadering zal Windows standaard ook de groep *Iedereen*, volledige machtigingen toekennen. Het eerste wat een goede Windows-beheerder zal doen, is de rechten van de groep *Iedereen* verwijderen om de beveiliging te verbeteren. Voor lokaal pc-testen is dit waarschijnlijk niet nodig, maar het verklaart waarom, indien *Iedereen* niet wordt verwijderd en je een of andere vorm van machtigingscontrolescript of de Joomla! Pre-Installation check uitvoert, je over het algemeen volledige *Lezen, Schrijven en Uitvoeren* machtigingen hebt, omdat je de rechten van de groep *Iedereen* verkrijgt.

### Microsoft Internet Information Server (IIS)

IIS is in twee hoofdvarianten beschikbaar, PWS (Personal WebServer) en IIS (Internet Information Server). In wezen zijn dit dezelfde applicatie. PWS is slechts een afgeslankte versie van IIS, ontworpen voor desktopomgevingen, terwijl IIS is ontworpen voor serveromgevingen. PWS limiteert je tot een enkele hoofdwebsite, dus je applicatie-installaties bevinden zich over het algemeen in submappen van de hoofdwebsite. IIS daarentegen biedt de functionaliteit voor virtuele hosts vanuit deze mappen, waardoor de mogelijkheid voor meerdere sites wordt geboden.

Vanwege de verschillende functionele beperkingen heeft PWS niet de *Permissions Wizard*, omdat wordt geacht dat deze niet nodig is. Slechts één gebruiker zal de PWS-server gebruiken. In IIS zullen veel gebruikers de server gebruiken, waardoor verschillende machtigingstoewijzingen nodig zijn.

Zodra de *Iedereen* account is verwijderd, heeft Windows IIS nu de *IUSR_* account met top-level rechten tot de webserverdirectories. Een machtigingscontrole moet nu andere resultaten opleveren. Alleen de *IUSR_* account heeft volledige machtigingen en andere gebruikers moeten ofwel *alleen-lezen* of helemaal geen rechten hebben. Rechten worden bepaald door welke andere gebruikers handmatig welke rechten hebben toegewezen gekregen aan de IIS-directories.

### Machtigingen toewijzen

Het toewijzen van machtigingen in Windows is redelijk eenvoudig, maar kan soms een beetje verwarrend zijn. Klik met de rechtermuisknop op de juiste map of het bestand. Het selecteren van *Eigenschappen* of *Delen en beveiliging* opent het Windows Security Management-paneel. Door op een vermelde gebruikersnaam te klikken, worden de rechten van die gebruiker in de onderste helft van het paneel weergegeven. Sommige rechten kunnen zijn *uitgegrijsd*. Deze zijn niet beschikbaar, ofwel omdat de huidige gebruiker (jij bent ingelogd als) niet over voldoende hoge machtigingen beschikt om ze te wijzigen, of omdat ze zijn overgenomen van de bovenliggende map en zijn ingesteld om de machtigingen van die hogere map te gebruiken (dit is over het algemeen het standaardmechanisme).

Zoals je kunt zien, gebruikt Windows het volgende Machtigingen/Rechten-systeem:

| # | Machtigingen | Rechten |
|:-----:|:----------|:---------|
| 1 | Volledige controle | Toestaan: 1, 2, 3, 4, 5, 6, 7 |
| 2 | Wijzigen | Toestaan: 2, 3, 4, 5, 6 |
| 3 | Lezen & Uitvoeren | Toestaan: 3, 4 |
| 4 | Mapinhoud weergeven | Toestaan: 4 (maar kan geen programma's uitvoeren) |
| 5 | Lezen | Toestaan: 5 (Implicatie: 4) |
| 6 | Schrijven | Toestaan: 6 (Implicatie: 4) |
| 7 | Speciale machtigingen | Toestaan: Combinaties |

### Eigenschappen van Windows bestandmachtigingen

Windows bestandmachtigingen kunnen worden gezien als het hebben van **vergelijkbare** eigenschappen als UNIX of Linux bestand (modi) machtigingen, ze worden alleen anders weergegeven. Bijvoorbeeld, als je voornamelijk een Unix/Linux-gebruiker bent, ben je waarschijnlijk gewend om machtigingen te zien als 644/666 755/777, in plaats van in de hierboven beschreven termen. Dus, als het aanbevolen wordt om 644 te gebruiken, komt dit overeen met:

* De eigenaar van dit bestand kan het lezen en schrijven.
* De groep van de eigenaar kan het bestand lezen.
* Iedereen kan het bestand lezen.

**Opmerking:** Windows en Unix machtigingen (Access Control Lists) komen niet exact overeen, omdat Windows het *Groepen* mechanisme niet op dezelfde manier gebruikt. Echter, voor deze discussie en met betrekking tot de webhostingomgeving kunnen ze samenvattend worden gelijkgesteld. Ah, maar in Windows worden ***Groepen*** niet gebruikt en ***Iedereen*** zou verwijderd moeten zijn. Dit is waar Windows en Unix niet helemaal overeenkomen, maar wat gedaan kan worden, is om overeenkomstige betekenissen te *matchen* of te *correleren*.

Deze korte uitleg gaat je geen specifieke handleiding geven voor Windows of NTFS-machtigingen, maar meer een begrip van hoe de vaak geciteerde genummerde UNIX/Linux-stijl machtigingen correleren op een machine met een NTFS-bestandssysteem. De bestanden die in de www- of public_html basisfolder worden geplaatst, of welke map je site (www.domain.com.au of localhost) ook maar naar verwijst op je harde schijf, zouden eigendom moeten zijn van je gebruikersaccount, maar alleen als die gebruiker niet wordt beschouwd als een bevoorrechte gebruiker zoals *Administrator* op Windows of *root* op UNIX/Linux. Deze accounts geven veel te veel toegang en moeten nooit worden gebruikt voor dagelijks gebruik.

### Best practices

Veelgebruikte beveiligingspraktijken suggereren dat alle **bestanden** de volgende machtigingen zouden moeten hebben:

* **Eigenaar:** Lezen & Schrijven
* **Groep:** Alleen lezen
* **Overige:** Alleen lezen

Alle **mappen** zouden de volgende machtigingen moeten hebben:

* **Eigenaar:** Lezen, Schrijven & Uitvoeren
* **Groep:** Lezen & Uitvoeren
* **Overige:** Lezen & Uitvoeren

Dit is wellicht niet per se de *optimum* beveiliging, maar er moet een balans worden gevonden tussen beveiliging, functionaliteit en onderhoudbaarheid. Windows, in tegenstelling tot Unix, onderhoudt geen enkele ACL voor *Uitvoeren*, maar biedt eenvoudigweg *Lezen & Uitvoeren* gecombineerd aan, wat niet *Schrijven* impliceert. De *Lezen & Uitvoeren* ACL impliceert weliswaar *Mapinhoud weergeven*. Daarom, als je alleen *Lezen & Schrijven* machtigingen hebt op een map maar geen *Uitvoeren*, zul je de inhoud van de map niet kunnen zien en mogelijk problemen ondervinden bij het proberen het bestand via een webbrowser uit te voeren. Een beetje begrip van UNIX/Linux-machtigingen is vereist om ze volledig te kunnen equateren/correleren aan Windows-machtigingen. De volgende tabel zou moeten helpen:

| Unix Mode | Windows ACL | Opmerkingen |
|:-----:|:----------|:---------|
| 7 | Wijzigen | Lezen, Schrijven & Uitvoeren, je zou de eigenaar van dit bestand moeten zijn |
| 6 | Lezen & Schrijven |  |
| 5 | Lezen & Uitvoeren | gebruikt voor de meeste applicaties |
| 4 | Alleen lezen | beveiliging door obscuriteit is geen goede praktijk |
| 3 | Schrijven & Uitvoeren | niet beschikbaar via windows, tenzij "Speciale" Machtigingen worden gebruikt, niet veel gebruikt |
| 2 | Alleen schrijven | niet beschikbaar via windows, tenzij "Speciale" Machtigingen worden gebruikt, niet veel gebruikt |
| 1 | Alleen uitvoeren | niet beschikbaar via windows, tenzij "Speciale" Machtigingen worden gebruikt, niet veel gebruikt |

In vergelijking met Unix-modi, wanneer je zoiets als 644 ziet, zou je dat opdelen in drie elementen:

**6**  :  **4**  : **4**

Het eerste getal vertegenwoordigt de *Eigenaar* rechten, het tweede vertegenwoordigt de *Groep* rechten en het derde, de *Overige* rechten. Het Windows-equivalent zou zijn:

* **Eigenaar** (6) : **Lezen & Schrijven**
* **Groep** (4) : **Alleen lezen**
* **Overige** (4) : **Alleen lezen**

Hopelijk biedt dit voorbeeld enig inzicht in hoe Unix-modi/machtigingen kunnen worden gecorreleerd aan Windows Machtigingen/ACL's. Dit document behandelt niet de meer complexe onderwerpen zoals *Effectieve*, *Geërfde* of *Speciale* machtigingen. Ondanks het gebruikersgemak van Windows, zijn de machtigings- en ACL-mechanismen van Microsoft eigenlijk redelijk complex en zeer uitgebreid, maar dit kan je wellicht een snelle referentie geven om te proberen enige verwarring rond de vertaling van Unix- en Windows-machtigingen te verlichten.

*Vertaald door openai.com*

