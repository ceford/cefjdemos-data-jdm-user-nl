<!-- Filename: How_do_Windows_file_permissions_work? / Display title: Bestandstoestemmingen: Windows  -->

## Inleiding

Voor degenen onder jullie die Joomla!-websites ontwikkelen of leveren vanuit een Windows-omgeving, kan het soms moeilijk zijn om relevante informatie over permissies te verkrijgen. Helaas is het een feit dat de meeste webhosting wordt aangeboden onder Unix en dat Unix vrij goed gedocumenteerd is binnen deze omgeving. Hopelijk zal de volgende informatie enige verwarring ophelderen en ook wat begeleiding bieden.

## Overzicht van Windows Webservers

Laten we eerst de verschillen tussen servers bespreken. Over het algemeen lijken de meeste Windows-gebruikers ofwel Apache (Win32) of Microsoft IIS te gebruiken. Deze twee webservers werken heel verschillend en maken gebruik van iets verschillende leveringsmodellen. Apache (Win32) draait meestal op de hostcomputer als de gebruiker waaronder het is geïnstalleerd, terwijl IIS wordt geïnstalleerd onder een specifieke gebruiker, maar zal draaien onder een nieuw aangemaakte gebruiker *IUSR_*. 

## Standaardmachtigingen

Standaard geeft Unix meestal alleen volledige toegang aan de *bezittende* gebruiker tot bestanden en directories. Daarentegen kent Windows standaard ook de groep *Iedereen* volledige machtigingen toe. Het eerste wat een goede Windows-beheerder zal doen, is de rechten van de groep *Iedereen* verwijderen om de beveiliging te verbeteren. Voor lokaal pc-testen is dit waarschijnlijk niet nodig, maar het verklaart waarom, als de groep *Iedereen* niet wordt verwijderd en je een of andere vorm van machtigingscontrolescript of de Joomla! Pre-Installatiecontrole uitvoert, je volledige *Lees-, Schrijf- en Uitvoermachtigingen* hebt. Je verkrijgt de rechten van de groep *Iedereen*. 

## Microsoft Internet Information Server (IIS)

IIS is beschikbaar in twee hoofdvarianten, PWS (Personal WebServer), en IIS (Internet Information Server). In wezen zijn dit dezelfde applicatie. PWS is gewoon een afgeslankte versie van IIS ontworpen voor desktopomgevingen, terwijl IIS is ontworpen voor serveromgevingen. PWS beperkt je tot een enkele hoofdwebsite, dus je applicatie-installaties zullen over het algemeen in submappen van de hoofdwebsite staan. IIS daarentegen biedt de functionaliteit voor Virtual Hosts die vanuit deze directories kunnen worden uitgevoerd, wat een multi-site capaciteit biedt.

Vanwege de verschillende functionele beperkingen heeft PWS de *Permissions Wizard* niet, omdat deze als onnodig wordt beschouwd. Slechts één gebruiker zal de PWS-server gebruiken. In IIS zullen veel gebruikers de server gebruiken, en daarom zijn er verschillende toewijzingen van rechten nodig.

Zodra het *Iedereen* account is verwijderd, blijft Windows IIS over met het *IUSR_** account dat de hoogste rechten heeft op de Web-server directories. Een controle van de rechten zou nu andere resultaten moeten opleveren. Alleen het *IUSR_** account heeft volledige rechten en andere gebruikers zouden alleen *Read Only*-rechten of geen rechten moeten hebben. Rechten worden bepaald door welke andere gebruikers handmatig rechten zijn toegewezen in de IIS directories.

### Rechten Toewijzen

Het toewijzen van rechten in Windows is redelijk eenvoudig, maar kan soms verwarrend zijn. Klik met de rechtermuisknop op de juiste map of bestand. Door *Voorkeuren* of *Delen en Beveiliging* te selecteren, kom je in het Windows Beveiligingsbeheer paneel. Door (eenmaal) op een gebruikersnaam uit de lijst te klikken, worden de rechten van die gebruiker in de onderste helft van het paneel weergegeven. Sommige rechten kunnen *grijs* worden weergegeven. Deze zijn niet beschikbaar, omdat de huidige gebruiker (je bent ingelogd als) niet voldoende rechten heeft om ze te veranderen, of omdat ze zijn geërfd van de bovenliggende directory en zijn ingesteld om de hogere rechten van die directory te gebruiken. (Dit is meestal het standaard mechanisme.)

Zoals je kunt zien, gebruikt Windows het volgende Rechten/Toegangsrechten-schema:

| # | Controle  | Toestemming #       |
| :---:        |:----   | :--- |
| 1.|  Volledige controle | Toestemming: 1, 2, 3, 4, 5, 6, 7 |
| 2.| Wijzigen  | Toestemming: 2, 3, 4, 5, 6 |
| 3.| Lezen & Uitvoeren | Toestemming: 3, 4 |
| 4.| Mapinhoud Lijst | Toestemming: 4 (maar kan geen programma's uitvoeren)|
| 5.| Lezen | Toestemming: 5 (Implicatie: 4)|
| 6.| Schrijven | Toestemming: 6 (Implicatie: 4)|
| 7.| Speciale Rechten | Toestemming: Combinaties |

### Eigenschappen van Windows-bestandsrechten

Windows-bestandsrechten kunnen worden gezien als gelijkaardige eigenschappen als UNIX- of Linux-bestandsrechten (Modes). Ze worden alleen anders weergegeven. Als u bijvoorbeeld voornamelijk een Unix/Linux-gebruiker bent, bent u waarschijnlijk gewend om rechten weer te geven als 644/666 755/777, in plaats van te worden beschreven in de bovenstaande termen. Dus, wanneer je 644 gebruikt, betekent dit:

- De eigenaar van dit bestand kan het lezen en schrijven.
- De groep van de eigenaar kan het bestand lezen.
- Iedereen anders kan het bestand lezen.

**Opmerking:** Windows en Unix-rechten (Access Control Lists) komen niet exact overeen; Windows gebruikt het *Groepen* mechanisme niet op dezelfde manier. Voor deze bespreking en in verband met de webhostingomgeving kunnen ze worden gelijkgesteld. Ah, maar in Windows worden *Groepen* niet gebruikt en zou *Iedereen* verwijderd moeten zijn. Dit is waar Windows en Unix niet helemaal overeenkomen, maar wat kan gedaan worden is om de equivalente betekenissen te *matchen* of te *correleren*.

Dit overzicht zal je niet echt voorzien van een specifieke handleiding voor Windows of NTFS-rechten, maar meer van een begrip van hoe de vaak geciteerde UNIX/Linux-stijl nummers overeenkomen op een machine met een NTFS-bestandssysteem. De bestanden die in de `www` of `public_html` root map worden geplaatst, of welke map je website (`www.domein.com` of `localhost`) verwijst naar op je harde schijf zouden door je gebruikersaccount in eigendom moeten zijn, maar alleen als die gebruiker niet wordt beschouwd als een bevoorrechte gebruiker zoals *Administrator* op Windows of *root* op UNIX/Linux. Deze accounts bieden veel te veel toegang en zouden nooit voor dagelijks gebruik gebruikt moeten worden.

### Beste Praktijken

Veelgebruikte beveiligingspraktijken suggereren dat alle **bestanden** de volgende rechten zouden moeten hebben:

- **Eigenaar:** Lezen & Schrijven
- **Groep:** Alleen lezen
- **Anderen:** Alleen lezen

Alle **directories/mappen** zouden de volgende rechten moeten hebben:

- **Eigenaar:** Lezen, Schrijven & Uitvoeren
- **Groep:** Lezen & Uitvoeren
- **Anderen:** Lezen & Uitvoeren

Dit is misschien niet noodzakelijk *optimaal* qua beveiliging, maar er moet een balans worden gevonden tussen beveiliging, functionaliteit en onderhoudbaarheid.

Windows, in tegenstelling tot Unix, behoudt niet een enkele ACL voor *Uitvoeren*, maar voorziet simpelweg in *Lezen & Uitvoeren* gecombineerd, hetgeen niet *Schrijven* impliceert. De *Lezen & Uitvoeren* ACL impliceert echter *Lijst Directory Inhoud*. Daarom, als je alleen *Lezen & Schrijven* rechten hebt op een map maar geen *Uitvoeren* zul je de inhoud van de map niet kunnen zien en kun je ook problemen ervaren wanneer je probeert het bestand via een webbrowser uit te voeren. Enige kennis van UNIX/Linux-rechten is vereist om ze volledig op Windows-rechten te kunnen gelijkstellen/correleren. De volgende tabel zou moeten helpen:

| Unix Modus | Windows ACL | Opmerkingen|
|:-----------:| :----  | :--- |
| 7 | Wijzigen | Lezen, Schrijven & Uitvoeren, je zou de eigenaar van dit bestand moeten zijn | 
| 6 | Lezen & Schrijven | | 
| 5 | Lezen & Uitvoeren | gebruikt voor de meeste applicaties | 
| 4 | Alleen lezen | beveiliging door onzichtbaarheid is geen goede praktijk | 
| 3 | Schrijven & Uitvoeren | niet beschikbaar in Windows, tenzij *Speciale* Rechten wordt gebruikt, niet vaak gebruikt | 
| 2 | Alleen schrijven | niet beschikbaar in Windows, tenzij *Speciale* Rechten wordt gebruikt, niet vaak gebruikt | 
| 1 | Alleen uitvoeren | (niet beschikbaar in Windows, tenzij *Speciale* Rechten wordt gebruikt, niet vaak gebruikt) |

In vergelijking met Unix-modus, wanneer je iets als 644 ziet, splits dat in drie elementen:

Het eerste nummer vertegenwoordigt de Eigenaar rechten, de tweede vertegenwoordigt de Groep rechten en de derde, de Andere rechten. Het Windows-equivalent zou zijn:

- **Eigenaar** (6) Lezen & Schrijven
- **Groep** (4) Alleen lezen
- **Anderen** (4) Alleen lezen

Hopelijk biedt dit voorbeeld enig inzicht in hoe de Unix Modus/Rechten naar Windows Rechten/ACL's te correleren zijn. Dit document bevat niet complexere onderwerpen zoals *Effectief*, *Geërfd*, of *Speciale* rechten. Ondanks het gebruiksgemak van Windows, zijn de Mechanismen voor Microsoft-rechten en ACL's eigenlijk redelijk complex en zeer uitgebreid, maar dit zou je een snelle referentie kunnen geven om enkele van de verwarring rond Unix en Windows-rechten vertalingen te verlichten.

*Vertaald door openai.com*

