<!-- Filename: J4.x:Fix_%22Database_Table_Structure_NOT_Up_to_Date%22_before_Update / Display title: Fix "Database Table Structure NOT Up to Date" before Update -->

## Gerapporteerde fouten

Bij het updaten van Joomla! moet de database tabelstructuur up-to-date
zijn voordat het proces kan beginnen.

De "Voor-Update controle voor Joomla" klaagt als dit niet het geval is.

<img
src="https://docs.joomla.org/images/6/66/J4-database-table-structure-up-to-date-no.jpg"
decoding="async" data-file-width="1716" data-file-height="135"
width="1716" height="135"
alt="Joomla! 4 - Voor-Update controle - database tabelstructuur niet up-to-date" />

Maar als je gaat naar 'Systeem - Onderhoud - Database' is er niets aan
de hand.

## Getroffen versies

Algemene informatie

Dit wordt vermeld in iedere Joomla! 4.x versie.

## Wat is de oorzaak

Dit wordt veroorzaakt door een lege \#\_\_schemas tabel in de database.
Dit ontstaat waarschijnlijk als Joomla! niet geïnstalleerd is door de
officiële Joomla! installer maar bijvoorbeeld door een aangepast script
dat niet alle verplichte gegevens invult.

## Hoe repareren

Dit kan gerepareerd worden door de ontbrekende waarde toe te voegen aan
de tabel. Allereerst heb je de ID nodig uit Joomla!. Ga naar de
\#\_\_extensions tabel via bijvoorbeeld phpMyAdmin (of een ander
database tool). Zoek naar de naam="files_joomla" en schrijf het ID op
(in ons geval 211).

Daarnaast moet je het nieuwste SQL script dat geïnstalleerd is weten. Ga
naar "administrator/components/com_admin/sql/updates/mysql" en bepaal de
bestandsnaam met het hoogste versie. In dit voorbeeld, gaan we ervan uit
dat "4.0.3-2021-09-05.sql" de bestandsnaam met de hoogste versie is. Je
moet dit nu toevoegen aan de insert query als tweede waarde:

    INSERT INTO `#__schemas` (`extension_id`, `version_id`) VALUES
    (211, '4.0.3-2021-09-05');

of voor PostgreSQL:

    INSERT INTO "#__schemas" ("extension_id", "version_id") VALUES
    (211, '4.0.3-2021-09-05');

Vervang "#\_\_" door het database prefix (zie Algemene instellingen)
voor het uitvoeren.

Ga dan naar "Systeem - Onderhoud - Database" en repareer de tabellen.

Nu zou de update als verwacht moeten werken.
