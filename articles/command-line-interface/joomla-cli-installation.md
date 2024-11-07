<!-- Filename: J4.x:Joomla_CLI_Installation / Display title: Joomla CLI-installatie  -->

## Introductie

Het Joomla CMS wordt meestal geïnstalleerd via een webbrowserinterface. Ervaren gebruikers kunnen echter de voorkeur geven aan het installeren van Joomla met behulp van opdrachten in een terminalinterface. Dit maakt snelle implementatie van meerdere Joomla-instanties mogelijk.

## Systeemvereisten

Joomla vereist PHP, een database en een webserver. Voor de meest recente informatie over de ondersteunde software en de minimale en aanbevolen versies, bezoek de <a href="https://manual.joomla.org/docs/next/get-started/technical-requirements/" rel="noreferrer noopener">Technische Vereisten</a> pagina.

De installatie kan op twee verschillende manieren worden uitgevoerd:

1.  Handmatige installatie
2.  Scriptgestuurde automatische installatie

## Handmatige installatie

Handmatige installatie biedt goede controle tijdens het installatieproces. Elke stap is zichtbaar in de terminal en kan worden afgebroken met `Ctrl+C` in geval van een onjuiste invoer.

### Stappen die moeten worden uitgevoerd

1. Upload het installatiepakket als zip- of tar-bestand naar de webserver.
2. Pak het zip- of tar-bestand uit.
3. Hernoem de uitgepakte map en verplaats deze naar een geschikte plaats in de documentroot van de webserver.
4. Ga naar de map met de Joomla-code en voer de volgende opdracht uit:<br>
   `php installation/joomla.php install`
5. U wordt gevraagd om de parameters die nodig zijn voor de installatie, zoals in het volgende voorbeeld:

```bash
php installation/joomla.php install

Installeer Joomla
=================

Systeemvereisten controleren...OK
Configuratie verzamelen...

 Voer de naam van uw Joomla-site in:
 > J51
 Voer de echte naam van uw Super User in:
 > John Doe
 Stel de gebruikersnaam in voor uw Super User-account:
 > johndoe
 Stel het wachtwoord in voor uw Super User-account:
 >
 Voer het e-mailadres van de website Super User in:
 > johndoe@example.com
 Databasetype. Ondersteund: mysql, mysqli, pgsql [mysqli]:
 >
 Databasehost [localhost]:
 >
 Databasegebruikersnaam:
 > j4
 Databasewachtwoord:
 >
 Databasenaam [joomla_db]:
 > j51
 Voorvoegsel voor de databasetabellen [u5dke_]:
 >
 Versleuteling voor de databaseverbinding. Waarden: 0=Geen, 1=Eenweg, 2=Tweeweg [0]:
 >
 Relatief of absoluut pad naar de publieke map []:
 >
OK
DB-verbinding valideren...OK
Database maken en vullen...OK
Configuratie.php en aanvullende setup schrijven ...OK
Map /installation verwijderen...OK
 [OK] Joomla is geïnstalleerd
```

Zodra het script met succes is voltooid, kan de nieuwe website worden geopend via uw webbrowser.

### Opmerkingen

* Let goed op uw invoer. Het is niet mogelijk om terug te gaan in het script. Als de invoer onjuist is, moet het script worden afgebroken.
* De naam van uw Joomla-site verschijnt in de Administrator Titelbalk, houd het dus kort en onderscheidend. Dit kan later worden gewijzigd.
* De echte naam van uw Super User kan later worden gewijzigd.
* De gebruikersnaam voor uw Super User-account moet een naam vermijden die lijkt op *admin*. Dit is mogelijk onveilig omdat het gemakkelijk door een hacker kan worden geraden.
* Het wachtwoord voor de gebruiker moet 12 tekens bevatten.
* Het standaard databasetype is *mysqli*. Ondersteunde databasetypes zijn MySQL (mysql) en PostgreSQL (pgsql) databases en compatibele types zoals MariaDB.
* De databasehost is bijna altijd `localhost`. Een IP-adres of een hostnaam moet hier alleen worden ingevoerd als de verantwoordelijke databaseserver op een andere host is geïnstalleerd. De terminalgebruiker moet echter schrijfrechten hebben op de geselecteerde host. U krijgt deze informatie van uw internetprovider (ISP).
* De gebruikersnaam van de database is meestal anders dan de naam van de Super User.
* Het databasewachtwoord voor de Joomla-database is bijna altijd anders dan het wachtwoord van de Super User.
* De databasenaam heeft standaard `joomla_db`, maar andere namen worden vaak gebruikt.
* Het voorvoegsel voor de databasetabellen wordt ingesteld op een willekeurige selectie van vijf tekens. De waarde wordt gebruikt om Joomlatabellen te scheiden van andere tabellen in de database als deze ook door andere applicaties wordt gebruikt.
* De versleutelingsinstelling voor de databaseverbinding wordt zelden gebruikt. Tenzij anders geadviseerd door uw ISP, laat deze waarde op de standaard [0].

## Scriptgestuurde automatische installatie

De installatie van Joomla wordt aangestuurd door een *joomla.php*-bestand dat zich bevindt in de *installatie* submap na het uitpakken van het Joomla-pakketbestand. Elke programmeertaal die het aanroepen en uitvoeren van PHP-bestanden mogelijk maakt, stelt je in staat om een script te maken dat de benodigde voorbereidingen en de daadwerkelijke installatie automatiseert met behulp van aangepaste variabelen. Een lijst met parameters kan worden verkregen met het volgende commando:
```bash
php installation/joomla.php help install
```
Hier is een voorbeeld van een shell-script genaamd jinstall.sh, geplaatst in de Joomla hoofdmap, gemaakt voor een eenvoudige Joomla-installatie:
```
#!/bin/bash

php installation/joomla.php install \
--site-name=SITE-NAAM \
--admin-user=ADMIN-GEBRUIKER \
--admin-username=ADMIN-GEBRUIKERSNAAM \
--admin-password=ADMIN-WACHTWOORD \
--admin-email=johndoe@example.com \
--db-type=mysqli \
--db-host=localhost \
--db-user=j51 \
--db-pass=Garbage1n0ut \
--db-name=j51 \
--db-prefix=xyz12_ \
--db-encryption=0 \
--public-folder=j51
```
Met zijn permissies ingesteld op 700 is het een eenvoudige kwestie om het script aan te roepen vanaf de commandoregel met `./jinstall.sh` en Joomla is letterlijk in een oogwenk geïnstalleerd. Het script had kunnen worden bewerkt om plaatsaanduidingswaarden te wijzigen, of deze kunnen later worden gewijzigd na het inloggen als beheerder.

Als je deze aanpak gebruikt, vergeet dan niet om je jinstall.sh-script te verwijderen of het uit je webstructuur te verplaatsen voor later gebruik elders. De installatiemap wordt aan het einde van het installatieproces verwijderd. Het jinstall.sh-script een tweede keer uitvoeren zal dus niet werken.

