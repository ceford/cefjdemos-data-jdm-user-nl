<!-- Filename: How_do_you_recover_or_reset_your_admin_password%3F / Display title: Hoe kun je je administrator wachtwoord herstellen of opnieuw instellen? -->

Joomla! 1.5 wachtwoord herstel

Deze pagina is alleen voor Joomla! 2.5 of hogere versies. Voor Joomla!
1.5 website's  zijn hier instructies te
vinden.

Normaal gesproken kunnen in het gebruikersbeheer de wachtwoorden van
gebruikers worden gewijzigd. Om dit te doen, moet je ingelogd zijn met
een Super Administrator account.

In sommige situaties is dit echter niet mogelijk. Bijvoorbeeld als de
website is gehacked en het wachtwoord is veranderd. Of als je het
wachtwoord van de Super Administrator vergeten bent.

In zulke situaties is het nog steeds mogelijk om de Joomla! database aan
te passen, zodat je als een Super Administrator kunt inloggen. Dit zijn
de beschikbare mogelijkheden voor Joomla! administrators.

## Methode 1: configuration.php bestand

Als er toegang is tot de `configuratie.php` van de Joomla! installatie
kan het wachtwoorden op de volgende manier achterhaald worden:

1\. Gebruik een FTP programma om verbinding maken te maken met de
website. Zoek het bestand configuration.php en kijk naar de
bestandsrechten. Als de bestandsrechten 444 of iets anders zijn,
verander deze dan naar 644. Dit zal problemen voorkomen tijdens het
uploaden van het aangepaste configuration.php bestand later in dit
proces.

2\. Download het configuration.php bestand.

3\. Open het configuration.php bestand dat je hebt gedownload in een
tekstverwerker, bijvoorbeeld notepad++ en voeg de volgende regel toe

    public $root_user='myname';

onderaan de lijst, waarbij 'myname' een gebruikersnaam is met
administrator rechten, waarvan het wachtwoord bekend is. Een
gebruikersnaam met rechten in de auteur gebruikersgroep of hoger kan ook
gebruikt worden in plaats van een gebruikersnaam met administrator
rechten.

4\. Sla het configuration.php bestand op en upload het terug naar je
website. Je mag de gebruikersrechten van het configuration.php bestand
op 644 laten staan.

Deze gebruiker wordt nu een tijdelijke super administrator.

5\. Login in het beheergedeelte en wijzig het wachtwoord van de
administrator gebruiker waar u het wachtwoord van hebt of maak een
nieuwe super gebruiker aan. Als u een nieuwe gebruiker aanmaakt wilt u
misschien de oude blokkeren of verwijderen, afhankelijk van uw
omstandigheden.

6\. Gebruik, als u klaar bent, de link "Klik hier om te proberen het
automatisch te doen" die verschijnt in de waarschuwing, om de regel te
verwijderen die toegevoegd is aan het configuration.php bestand. Ga, als
het gebruik van de link niet succesvol was, terug en verwijder de
toegevoegde regel uit het configuration.php bestand met een teksteditor.
Upload het configuration.php bestand terug naar de site.

7\. Controleer, met behulp van uw FTP programma, de bestandsrechten van
het configuration.php bestand, ze zouden op 444 moeten staan. Wijzig,
als u de toegevoegde regel handmatig heeft verwijderd, de
bestandsrechten van het configuration.php bestand in 444.

Als u geen gebruikers weet die hun wachtwoord kennen en u geen gebruik
kunt maken van registreren vanaf de website, dan moet u misschien een
wijziging in de database aanbrengen, zoals hieronder in dit document
beschreven.

## Methode 2: Direct aanpassen in de database

Als bovenstaande methode niet werkt, heeft u twee andere opties, die
beide het werken direct in de MySQL database vereisen.

### Wijzig het wachtwoord in de database

Als de admin-gebruiker nog gedefinieerd is, is de eenvoudigste optie het
wachtwoord te wijzigen in de database naar een bekende waarde. Dit
vereist dat u toegang heeft tot de MySQL database met behulp van
phpMyAdmin of een andere client.

<img
src="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/25px-Stop_hand_nuvola.svg.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/38px-Stop_hand_nuvola.svg.png 1.5x, https://docs.joomla.org/images/4/41/Stop_hand_nuvola.svg.png 2x"
data-file-width="40" data-file-height="40" width="25" height="25"
alt="Stop hand nuvola.svg.png" />Zorg ervoor dat u uw wachtwoord wijzigt
wanneer u weer toegang heeft

Deze instructies tonen hoe u handmatig een wachtwoord kunt wijzigen naar
het woord - "secret"

1.  Navigeer naar phpMyAdmin en selecteer de database van de Joomla!
    site in de keuzelijst links. Dit toont de database tabellen aan de
    linkerkant van het scherm.

2.  Zoek en klik op de tabel met "\_users" in de lijst met tabellen (let
    op: u heeft misschien een voorvoegsel dat niet jos\_ is, ga naar de
    \_users tabel met uw voorvoegsel).

3.  Klik op de "Browse" knop in de bovenste werkbalk. Dit toont alle
    gebruikers die op deze site bestaan.

4.  Zoek de gebruiker waarvan u het wachtwoord wilt wijzigen en druk op
    het Wijzigen icoon voor deze rij.

5.  Een formulier wordt zichtbaar dat u de mogelijkheid geeft het
    wachtwoord-veld te bewerken. Kopieer de waarde

        d2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199

    naar het wachtwoord-veld en druk op *Start* knop. phpMyAdmin zou de
    boodschap "1 rij bijgewerkt". Op dit moment is het wachtwoord
    gewijzigd in **"secret"**.

6.  Login met deze gebruiker en wachtwoord en wijzig het wachtwoord van
    de gebruiker in een veilige waarde. Controleer of alle gebruikers
    die toegang hebben tot het beheergedeelte dat mogen. Als u gehackt
    bent, wilt u misschien alle wachtwoorden op de site veranderen.

### Voeg een nieuwe Super gebruiker toe

Als het wijzigen van het wachtwoord niet werkt, of als u niet weet welke
gebruikers lid zijn van de Super gebruikers-groep, dan kunt u deze
methode gebruiken om een nieuwe gebruiker aan te maken.

1.  Navigeer naar phpMyAdmin en selecteer de database van de Joomla!
    site in de keuzelijst links. Dit toont links op het scherm de
    database tabellen.
2.  Druk op de "SQL" knop in de werkbalk om een SQL query te draaien op
    de gekozen database. Dit toont een veld genaamd "Voer
    SQL-query/queries uit op databank ".
3.  Verwijder alle tekst in dit veld en kopieer en plak onderstaande
    query en druk op de *Start* knop om de query uit te voeren en voeg
    de nieuwe beheerders-gebruiker toe aan de tabel.
4.  Gebruik de SQL query hieronder om nog een beheerders-account toe te
    voegen.

<img
src="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/25px-Stop_hand_nuvola.svg.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/38px-Stop_hand_nuvola.svg.png 1.5x, https://docs.joomla.org/images/4/41/Stop_hand_nuvola.svg.png 2x"
data-file-width="40" data-file-height="40" width="25" height="25"
alt="Stop hand nuvola.svg.png" />Zorg ervoor dat uw database
tabel-voorvoegsel gebruikt wordt!

De volgende code gebruikt jos31\_ als tabelnaam voorvoegsel, wat alleen
maar een voorbeeld tabel-voorvoegsel is. Het voorvoegsel toen u voor het
eerst Joomal installeerde is **WILLEKEURIG** of datgene waar u het
specifiek naar heeft gewijzigd. U moet alle waarden van **jos31\_**(uw
installatie voorvoegsel) uit onderstaande code veranderen in het
voorvoegsel die bij uw installatie gebruikt wordt.

**SQL code die gebruikt moet worden voor Joomla
 <img src="https://docs.joomla.org/images/5/53/Compat_icon_2_5.png"
decoding="async" data-file-width="40" data-file-height="17" width="40"
height="17" alt="Joomla 2.5" /> <img src="https://docs.joomla.org/images/4/4d/Compat_icon_3_x.png"
decoding="async" data-file-width="40" data-file-height="17" width="40"
height="17" alt="Joomla 3.x" /> <img src="https://docs.joomla.org/images/b/bd/Compat_icon_4_x.png"
decoding="async" data-file-width="40" data-file-height="17" width="40"
height="17" alt="Joomla 4.x" />**

    INSERT INTO `jos31_users`
       (`name`, `username`, `password`, `params`, `registerDate`, `lastvisitDate`, `lastResetTime`)
    VALUES ('Administrator2', 'admin2',
        'd2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199', '', NOW(), NOW(), NOW());
    INSERT INTO `jos31_user_usergroup_map` (`user_id`,`group_id`)
    VALUES (LAST_INSERT_ID(),'8');

Op dit punt zou u in staat moeten zijn in te loggen in het
beheergedeelte van Joomla! met de gebruikersnaam "admin2" en het
wachtwoord "secret". Ga, na het inloggen, naar gebruikersbeheer en
wijzig het wachtwoord in een nieuwe veilige waarde en geef het een juist
e-mailadres. Zorg, als er kans is dat u "gehackt" bent, dat alle
gebruikers legitiem zijn, met name leden van de groep Super gebruikers.

<img
src="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/25px-Stop_hand_nuvola.svg.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/38px-Stop_hand_nuvola.svg.png 1.5x, https://docs.joomla.org/images/4/41/Stop_hand_nuvola.svg.png 2x"
data-file-width="40" data-file-height="40" width="25" height="25"
alt="Stop hand nuvola.svg.png" />Warning!

Waarschuwing: De wachtwoorden die op deze pagina getoond worden zijn
publiek bekend en zijn alleen bestemd voor het herstellen. Uw site kan
gehackt worden als u deze wachtwoorden niet wijzigt in een veilige
waarde na het inloggen. Zorg ervoor dat u het wachtwoord wijzigt in een
veilige waarde na het inloggen!


Bovenstaande voorbeelden wijzigen het wachtwoord in "secret". Twee
andere mogelijke waarden worden hieronder getoond:

    - password = "this is the MD5 and salted hashed password"
    ------------------------------------------------------
    - admin  = 433903e0a9d6a712e00251e44d29bf87:UJ0b9J5fufL3FKfCc0TLsYJBh2PFULvT
    - secret = d2064d358136996bd22421584a7cb33e:trd7TvKHx6dMeoMmBVxYmg0vuXEA4199
    - OU812  = 5e3128b27a2c1f8eb53689f511c4ca9e:J584KAEv9d8VKwRGhb8ve7GdKoG7isMm
