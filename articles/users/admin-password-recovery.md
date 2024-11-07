<!-- Filename: How_do_you_recover_or_reset_your_admin_password%3F / Display title: Herstel administratiewachtwoord -->

## Inleiding

Normaal gesproken kan een Supergebruiker gebruikers en wachtwoorden toevoegen, bewerken en verwijderen uit de gebruikerslijst. In sommige situaties is dit misschien niet mogelijk. Bijvoorbeeld, de persoon die het Supergebruikerswachtwoord kende is niet langer beschikbaar. Of misschien is de Supergebruiker het wachtwoord vergeten dat werd gebruikt.

In dergelijke gevallen zijn er twee methoden beschikbaar waarmee een sitebeheerder kan inloggen als een Supergebruiker.

## Methode 1: Het configuration.php-bestand bewerken

Als je toegang hebt tot het `configuration.php`-bestand van de Joomla-installatie op je server, kun je een Super User-wachtwoord resetten of een nieuwe Super User aanmaken als je kunt inloggen als Manager of Administrator.

Je moet het `configuration.php`-bestand openen in een teksteditor. Verander eerst de bestandsrechten naar 644. Je sitebeheerhulpmiddelen, zoals cPanel of Plesk (er zijn ook andere), bieden je meestal de mogelijkheid dit online te doen. Zo niet, dan moet je mogelijk FTP gebruiken om het bestand te downloaden, het lokaal te wijzigen en het opnieuw te uploaden.

Voeg deze regel onderaan het bestand toe, maar vóór de afsluitende accolades:
```
    public $root_user='mijnnaam';
```
waarbij **mijnnaam** een gebruikersnaam is met toegang tot de *Manager*- of *Administrator*-groep waarvan je het wachtwoord kent. Een gebruikersnaam die tot de *Author*-, *Editor*- of *Publisher*-groepen behoort, zal niet werken omdat deze groepen geen backendtoegang hebben.

Deze gebruiker zal nu tijdelijk een Super User zijn.

Log in op de backend en wijzig het wachtwoord van de Super User waarvoor je het wachtwoord niet hebt, of maak een nieuw Super User-account aan. Als je een nieuwe gebruiker aanmaakt, wil je wellicht de oude gebruiker blokkeren of verwijderen, afhankelijk van je omstandigheden.

Wanneer je klaar bent, gebruik dan de link *Selecteer hier om het automatisch te proberen* die verschijnt in het waarschuwingsvak om de regel te verwijderen die aan het configuration.php-bestand is toegevoegd. Als het gebruik van de link niet succesvol was, ga dan terug en verwijder de toegevoegde regel uit je configuration.php-bestand met behulp van een teksteditor.

Als je geen gebruikers hebt die hun wachtwoord kennen, moet je mogelijk een wijziging in je database aanbrengen.

## Methode 2: Wijzig de Database

Als de bovenstaande methoden niet hebben gewerkt, heb je twee andere opties, die beide vereisen dat je direct met de MySQL-database werkt.

### Wijzig een Wachtwoord in de Database

De eenvoudigste optie is om het Super User-wachtwoord in de database te wijzigen naar een bekende waarde. Dit vereist dat je toegang hebt tot de MySQL-database via phpMyAdmin of een andere client. Deze instructies laten zien hoe je een wachtwoord wijzigt naar het woord **geheim**.

Deze methode werkt alleen als de geselecteerde gebruiker deel uitmaakt van de *Manager*- of *Administrator*-groepen.

**Zorg ervoor dat je het Super User-wachtwoord wijzigt zodra je weer toegang hebt!**

1.  Open phpMyAdmin en selecteer de database voor de Joomla!-site. Dit toont de database tabellen aan de linkerkant van het scherm.
2.  Zoek en selecteer de *#__users* tabel waarbij *#_* het tabelvoorvoegsel voor jouw site is.
3.  In de *Bladeren* weergave, zoek de gebruiker wiens wachtwoord je wilt wijzigen en selecteer het Bewerk-pictogram voor deze rij.
    - als de lijst lang is, selecteer de SQL-knop bovenaan en gebruik deze query:<br>
    `SELECT * FROM `xxxxx_users` WHERE `username` = 'gebruikersnaam'`<br>
    waarbij je jouw databasevoorvoegsel gebruikt om `xxxxx` te vervangen en de gebruikersnaam die je moet vinden in plaats van `gebruikersnaam`.
4.  Verander in het bewerkformulier het wachtwoord naar<br>
    `d2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199`<br>
    en selecteer de *Go*-knop onderaan het formulier. phpMyAdmin zou het bericht *Getroffen rijen: 1* moeten tonen. Op dit punt zou het wachtwoord **geheim** moeten zijn.
5.  Log in met deze gebruiker en het wachtwoord en wijzig het wachtwoord van deze gebruiker naar een veilige waarde. Controleer alle gebruikers om er zeker van te zijn dat ze legitiem zijn. Als je gehackt bent, wil je misschien alle wachtwoorden op de site wijzigen.

### Voeg een nieuwe Supergebruiker toe

Als het wijzigen van het wachtwoord niet werkt of als je niet zeker weet welke gebruiker lid is van de Super User-groep, kun je deze methode gebruiken om een nieuwe Super User te maken.
1.  Open phpMyAdmin en selecteer de database voor de Joomla!-site.
2.  Selecteer de *SQL*-knop in de werkbalk om een SQL-query uit te voeren op de geselecteerde database. Dit toont een veld genaamd "Voer SQL-query/queries uit op database xxxxx".
3.  Verwijder eventuele tekst in dit veld en kopieer en plak de volgende query. Vergeet niet `xxxxx` te vervangen door je eigen databasevoorvoegsel.
    ```
    INSERT INTO `xxxxx_users`
       (`name`, `username`, `password`, `params`, `registerDate`, `lastvisitDate`, `lastResetTime`)
    VALUES ('Administrator2', 'admin2',
        'd2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199', '', NOW(), NOW(), NOW());
    INSERT INTO `xxxxx_user_usergroup_map` (`user_id`,`group_id`)
    VALUES (LAST_INSERT_ID(),'8');
    ```
    Selecteer de *Go*-knop om de query uit te voeren en de nieuwe Super User aan de tabel toe te voegen.

Op dit punt zou je moeten kunnen inloggen in de backend van Joomla!
met de gebruikersnaam *admin2* en het wachtwoord *geheim*.

Na het inloggen, ga naar de Gebruikerslijst en verander het wachtwoord naar een nieuwe veilige waarde en voeg een geldig e-mailadres toe aan het account.

Als er een kans is dat je *gehackt* bent, controleer dan of alle gebruikers legitiem zijn, vooral eventuele leden van de Super User-groep.

## Alternatieve Tijdelijke Wachtwoorden

**Waarschuwing:** De wachtwoordwaarden die op deze pagina worden getoond zijn
algemeen bekend en zijn alleen voor hersteldoeleinden. Om te voorkomen dat je
gehackt wordt, zorg ervoor dat je een tijdelijk wachtwoord wijzigt naar een
veilige waarde na het inloggen.

    wachtwoord = "dit is het MD5 en gezouten gehashte wachtwoord"
    ------------------------------------------------------------
    admin  = 433903e0a9d6a712e00251e44d29bf87:UJ0b9J5fufL3FKfCc0TLsYJBh2PFULvT
    geheim = d2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199
    OU812  = 5e3128b27a2c1f8eb53689f511c4ca9e:J584KAEv9d8VKwRGhb8ve7GdKoG7isMm

*Vertaald door openai.com*

