<!-- Filename: Unable_to_connect_to_the_database / Display title: Databaseverbinding -->

## Fout bij Verbinding Maken

Als u tijdens de **installatie** een foutmelding "**Kan geen verbinding maken met de database**" ontvangt, controleer dan of u uw MySQL/MariaDB-databasegegevens correct hebt ingevoerd. Het **installatie**script staat u niet toe verder te gaan tenzij de gegevens correct zijn.

Houd er rekening mee dat u tijdens de installatie geen databasegebruiker en wachtwoord hoeft aan te maken. Deze moeten van tevoren zijn aangemaakt.

Als de fout optreedt nadat u uw site naar een andere host heeft verplaatst, controleer dan de volgende items van uw *configuration.php*-bestand. De normale databasesettings zijn als volgt:

    public $dbtype = 'mysqli';
    public $host = 'localhost';
    public $user = 'yourdbuser';
    public $password = 'yourdbpassword';
    public $db = 'yourdbname';
    public $dbprefix = 't6q6i_';

Als de fout optreedt op een site die eerder heeft gewerkt, zijn er een aantal mogelijke redenen, soms tijdelijk en soms per ongeluk.

## De Meest Voorkomende Fouten

1. Soms zie je dit bericht als MySQL/MariaDB is gestopt met draaien op je server. Je serverbeheerder kan MySQL/MariaDB tijdelijk uitschakelen voor onderhoud. In dergelijke gevallen zal je site waarschijnlijk spoedig terugkeren.
2. Je databasegebruiker is verwijderd. Als dit het geval is, moet je je databasegebruiker opnieuw aanmaken met dezelfde gebruikersnaam en wachtwoord die bestonden toen je Joomla voor het eerst installeerde. Gebruik je domeinconfiguratiescherm om dit te beheren of neem contact op met je serverbeheerder.
3. Je databasegebruikersnaam of wachtwoord is gewijzigd.

*Vertaald door openai.com*
