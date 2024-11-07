<!-- Filename: Moving_the_site_among_directories/sub-directories / Display title: Installatiemap Verplaatsen -->

Vaak installeer je Joomla in een submap en wil je deze vervolgens naar een hoger gelegen map verplaatsen. Hier is een korte handleiding over hoe dit te doen.

Stel dat je Joomla in de volgende map hebt geïnstalleerd: public_html/tryjoomla. Nu je tevreden bent met de site, wil je deze verplaatsen naar public_html.

1. Verplaats alle bestanden van de submap (d.w.z., public_html/tryjoomla) naar de bovenliggende map (d.w.z., public_html).
    Je kunt hiervoor je favoriete FTP-client of het controlepaneel van je hostingservice gebruiken.
2. Download en open het bestand configuration.php in een teksteditor.
3. Verwijder eenvoudig de mapnaam tryjoomla uit het pad. Zoek naar de volgende regels:
    ```
    var $live_site = '';
    var $log_path = '/home/gebruikersnaam/public_html/tryjoomla/administrator/logs';
    var $tmp_path = '/home/gebruikersnaam/public_html/tryjoomla/tmp';
    var $ftp_root = 'public_html/tryjoomla';
    ```
    Verander naar:
    ```
    var $live_site = '';
    var $log_path = '/home/gebruikersnaam/public_html/administrator/logs';
    var $tmp_path = '/home/gebruikersnaam/public_html/tmp';
    var $ftp_root = 'public_html';
    ```
    N.B. De $live_site-variabele hoeft zelden een waarde te hebben. Maar als het tijdens de installatie een waarde heeft gekregen, pas dat pad dan ook aan.
    ```
    var $live_site = 'http://www.voorbeeld.com/tryjoomla';
    ```
    Verander naar:
    ```
    var $live_site = 'http://www.voorbeeld.com';
    ```
4. Controleer het .htaccess-bestand van je site. De submap moet daar ook verwijderd worden. De RewriteBase-directive moet worden uitgeschakeld. Controleer op een RewriteRule die de oude subdirectory bevat.
5. Verifieer dat er geen omleidingsopdrachten naar de oude subdirectory actief zijn in je hostingcontrolepaneel.
6. Als je caching hebt ingeschakeld, log dan in op de beheerders backend (wat nu `http://www.voorbeeld.com/administrator` zal zijn en niet `http://www.voorbeeld.com/tryjoomla/administrator`). Ga naar Systeem / Cache en verwijder alle cachebestanden.

*Vertaald door openai.com*

