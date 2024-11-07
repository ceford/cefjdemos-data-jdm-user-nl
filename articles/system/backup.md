<!-- Filename: jdocmanual?manual=user&heading=system&filename=backup.md / Display title: Back-up  -->

## Ongelukken Gebeuren!

Er gaat veel tijd, moeite en geld zitten in het maken en onderhouden van een website. Zonde om alles te verliezen door een bizar ongeluk. Back-up is eenvoudig voor doorsnee sites. Grote of gespecialiseerde sites hebben waarschijnlijk gespecialiseerd advies nodig.

## Back-up Strategie

Joomla! websites bestaan uit twee delen:

* De **bestanden** die zich in de Joomla hoofdmap bevinden. Tussen updates door veranderen de bestanden mogelijk niet veel, aangezien ze voornamelijk gerelateerd zijn aan code. Nieuwe afbeeldingen en documenten kunnen worden toegevoegd en misschien ook sjabloonoverschrijvingen.
* De **database** die zich ergens anders op de hostserver bevindt. De database bevat het grootste deel van de inhoud van de site en kan veel veranderen, aangezien gebruikers inhoud toevoegen of bewerken.

Elke site-eigenaar heeft een strategie nodig voor het herstellen van de site in geval van een ramp. Een veelvuldig gegeven advies op de forums is om de **laatste back-up te herstellen**. Dus bepaal wat je wilt back-uppen en hoe vaak je dat wilt doen.

Hostingservices maken vaak **snapshots** van klantensites en kunnen mogelijk een site herstellen naar de staat van gisteren, vorige week of vorige maand. Maar dat kan alles in het account omvatten, zoals mail en andere softwarepakketten. Vertrouw daar niet op voor Joomla site-herstel.

Dit artikel beschrijft enkele veel voorkomende **gratis** methoden om Joomla websites te back-uppen. Je zou ervoor kunnen kiezen om te betalen voor backup-tools en/of -services, maar dat wordt hier niet behandeld.

## Akeeba Backup

Als je het beheerdersmenu gebruikt om naar **Systeem / Extensies Installeren / Installeren Vanaf het Web** te navigeren, is het eerste item in de lijst *Akeeba Backup*. Het staat bovenaan de lijst omdat het de meeste positieve recensies heeft. Het behoeft geen betoog dat het een zeer lange geschiedenis en een onberispelijke reputatie heeft. Er is een gratis versie en een betaalde versie met enkele extra functies. Dat is een veelvoorkomend bedrijfsmodel voor Extensie-ontwikkelaars. Wees niet huiverig! De gratis versie is gemakkelijk te gebruiken, heeft geen afleidingen en is voldoende voor de meeste sites. Wat het doet:

* Akeeba Backup analyseert je installatie om de optimale instellingen te bepalen voor het creëren van een back-upbestand.
* Het maakt een samengesteld back-upbestand dat alle websitebestanden en de inhoud van de database bevat.
* Het slaat back-ups met tijdstempels op om deze te beheren, te downloaden of indien nodig te verwijderen.
* De download is een .jpa-bestand. Het beveelt aan om FTP te gebruiken voor de download.
* Er is een aparte Akeeba Kickstart-applicatie om het .jpa-bestand uit te pakken. Dit wordt allemaal beschreven op de Akeeba Beheer Back-ups-pagina.
* Na het uitpakken wordt de site geïnstalleerd met een Akeeba-installeerder via een proces dat lijkt op een Joomla-installatie.
* De installeerder wijzigt de configuratie om te herstellen naar een andere locatie en vraagt om de nieuwe databasegegevens.

Het enige probleem dat waarschijnlijk kan optreden is dat het back-upbestand erg groot kan zijn en dat je je bestandsruimtequota kunt overschrijden als je back-ups laat opstapelen.

Probeer het! Het kost niets en duurt minuten in plaats van uren.

## Hosttools

De meeste hostingdiensten bieden back-uptools. Voorbeeld:

### cPanel

Op de pagina **Tools** heeft het item *Bestanden* een *Backup* link. De **Backup** pagina heeft drie opties:

* **Volledige Backup:** Een volledige backup maakt een archief van alle bestanden en configuratie van je website. Je kunt dit bestand gebruiken om je account naar een andere server te verplaatsen of om een lokale kopie van je bestanden te bewaren.
* **Gedeeltelijke Backup**
  - Download een Backup van de Homedirectory
  - Download een Database Backup (met een lijst van databases)

Er zijn ook opties om elk van deze backuptypen te **Herstellen**. Er kunnen ook opties beschikbaar zijn om automatisch backups te maken.

Individuele mappen kunnen in verschillende formaten worden gecomprimeerd die geschikt zijn voor download met behulp van de cPanel Bestandsbeheer. Een database kan worden geëxporteerd met phpMyAdmin. Geen van deze methoden wordt hier behandeld.

## Lokale Hulpmiddelen

Er zijn gelegenheden waarbij je een site lokaal op een laptop of
kantoor desktopcomputer moet back-uppen. Bijvoorbeeld, je wil misschien een site kopiëren van/naar een
hostingdienst naar/van jouw lokale computer. Als je een lokale Joomla
installatie hebt, kun je Akeeba Backup gebruiken zoals hierboven beschreven. Anders kun je
de database en Joomla-bestanden afzonderlijk back-uppen.

### mysqldump

Als je MySQL gebruikt, heb je waarschijnlijk de *mysqldump* commandoregel
tool beschikbaar. Probeer deze opdracht:

```bash
/usr/local/mysql/bin/mysqldump -u root -p dbname > ~/tmp/dbname-dump.sql
```
waarbij `root` een gebruiker is die toegang heeft tot de database en `dbname` de naam
van de database is die je wilt exporteren. Het kan zijn dat je wordt gevraagd om het wachtwoord in te voeren.

Je kunt de uitvoer ook naar een zip- of gzip-opdracht leiden:
```bash
/usr/local/mysql/bin/mysqldump -u root -p dbname | gzip > ~/tmp/dbname-dump.sql.gz
```

### phpMySQL

Om dezelfde taak uit te voeren met je lokale installatie van phpMyAdmin, open je het en
selecteer je de database die je wilt exporteren. Selecteer de knop **Exporteren** bovenaan het scherm. Standaard gebruikt de *Snelle* export SQL als uitvoerformaat. Selecteer de knop **Exporteren** om dat te proberen. Je wordt gevraagd een uitvoerbestand te benoemen.

Als je de optie *Aangepast* selecteert, kun je een Uitvoercompressie-optie kiezen, ofwel geen, gezipt of gegzipt. Probeer een gecomprimeerde export en selecteer de knop **Exporteren**.

Je moet de geëxporteerde database **controleren**. Maak een nieuwe database aan, misschien `animporttest`, zodat deze bovenaan je lijst met databases staat. Met de nieuwe lege database geselecteerd gebruik je de knop **Importeren** bovenaan het scherm. In het importformulier **Bladeren** om het bestand dat je geëxporteerd hebt te vinden en selecteer vervolgens de knop **Importeren**.

Het was de **controle** waard. De gzip-export exporteerde slechts drie tabellen. De zip-export werkte prima. Dat was duidelijk te zien in de grootte van de geëxporteerde bestanden. Het zipbestand was 4Mb, maar het gzip-bestand was slechts 75Kb. Er moet ergens een bug zijn!

### Zip en Gzip

Deze commandoregel tools zijn vrij alomtegenwoordig en worden vaak gebruikt binnen grafische interfaces. Bijvoorbeeld, in de Finder op een Mac kan ik een directory selecteren die een Joomla-site bevat, met de rechtermuisknop klikken en **Comprimeer** selecteren. Het duurt een paar seconden om een zip-archief te maken en heeft geen invloed op het origineel.

## Een Backup Herstellen

Veelvoorkomende adviezen van de Joomla-forums:

* Herstel geen backup bovenop een defecte site.
* Maak je database leeg door alle tabellen te verwijderen of maak een nieuwe database aan en wijs hier een databasegebruiker aan toe.
* Verwijder alle mappen en bestanden binnen je Joomla-hoofddirectory.

## Akeeba Quickstart

Als je Akeeba Backup hebt gebruikt, gebruik dan Akeeba Quickstart om je backup te herstellen.
* Raadpleeg de [Videotutorial](http://akee.ba/abrestoreanywhere "").
* Download Akeeba Quickstart (PDF 94Kb) gratis.
* Controleer of de herstelde site correct werkt!

Akeeba Quickstart herstelt zowel de database als de Joomla-bestanden. Andere methoden herstellen de database en Joomla-bestanden apart.

## Herstel de Database

Als je een databaseback-up hebt, is het het beste om systeemtools te gebruiken om deze te herstellen. *phpMyAdmin* kan middelgrote databases installeren, maar het kan problemen krijgen met de tijd of het geheugen bij grote databases.

Als je cPanel gebruikt bij een hostingservice, kun je een database importeren vanaf de *Backup / Restore* pagina. Dat wordt hier niet beschreven.

Als je commandoregeltoegang hebt, ofwel bij een hostingservice of op je lokale laptop of desktopcomputer, kun je de `mysql` commandoregel gebruiken om de import uit te voeren. Upload het databasearchief naar een tijdelijke locatie buiten je webdirectory en pak het uit zodat je een bestandsnaam hebt die eindigt op `.sql`. Gebruik dan het volgende commando:
```
mysql -u dbgebruikersnaam -p -D dbnaam < db_dump_naam.sql
```
Vervang `dbgebruikersnaam`, `dbnaam` en `db_dump_naam.sql` met de werkelijke waarden voor je site. Mogelijk word je gevraagd om een databasegebruikersnaamwachtwoord. Het kan even duren, maar het zou tot voltooiing moeten komen.

## Herstel de Bestanden

Dit is een eenvoudige kwestie van het uitpakken van het gecomprimeerde bestand van je laatste back-up. Behalve dat het soms niet zo eenvoudig is. Afhankelijk van je besturingssysteem en gekozen methode, kunnen de gearchiveerde mappen en bestanden allemaal verschijnen in de huidige map, een nieuwe map, of je kunt gevraagd worden om een doelmap aan te geven. Totdat je weet wat jouw systeem doet, is het wellicht het beste om het archief in een lege map te plaatsen, het daar uit te pakken en vervolgens de inhoud naar de juiste plek te verplaatsen.

Sommige gebruikers geven er de voorkeur aan om SFTP te gebruiken om bestanden naar een hostingservice te uploaden vanuit de lokaal uitgepakte archiefbestanden. Er zijn duizenden bestanden, dus dit kost behoorlijk wat tijd.

In de root van je site bevindt zich een bestand genaamd `configuration.php`. Dit bestand bevat de databasenaam en toegangsinformatie. Zorg ervoor dat deze correct zijn voor je herstelde site. Het bestand heeft toegangsrechten ingesteld op 444. Dit moet worden gewijzigd naar 644 zodat je eventuele benodigde wijzigingen kunt opslaan.

Als alles goed gaat, zou je herstelde site moeten werken en in de toestand moeten zijn waarin deze verkeerde toen de back-up werd gemaakt.

## Een Site Kopiëren

Er zijn verschillende goede redenen om een volledige website van de ene server naar de andere te kopiëren. Forumexperts raden bijvoorbeeld vaak aan dat gebruikers een lokale versie van een site maken op een laptop of desktop voor testdoeleinden, zoals het uitproberen van nieuwe extensies of ontwerpen. Soms besluit een individu over te stappen naar een nieuwe hostingservice om redenen van kosten of prestaties.

Wat de reden ook is, het proces is relatief eenvoudig: maak een back-up van de originele site en herstel deze op de bestemmingssite. Er zijn enkele zaken waar je op moet letten:

* Zorg ervoor dat de bestemmingshost voldoet aan de minimale Joomla Technische Vereisten. Dat betekent meestal Server-, PHP- en Database-versies.
* Na installatie kan het zijn dat sommige essentiële modules niet zijn ingeschakeld. De meeste hostingservices zullen dergelijke problemen op verzoek oplossen.

*Vertaald door openai.com*

