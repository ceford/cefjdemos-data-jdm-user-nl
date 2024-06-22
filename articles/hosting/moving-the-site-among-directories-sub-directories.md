<!-- Filename: Moving_the_site_among_directories/sub-directories / Display title: Verplaatsen van een website naar een andere map of submap -->

Vaak wordt Joomla! in een sub-map geïnstalleerd en wilt u het later naar
een hoger gelegen map verplaatsten. Hier is een korte handleiding over
hoe u dit kunt doen.

Stel u heeft Joomla geinstalleerd in de map public_html/tryjoomla Nu u
tevreden bent met de website wilt u de website verplaatsen naar de map
public_html.

1\. Verplaats alle bestanden van de sub-map (b.v. public_html/tryjoomla)
naar de bovenliggende map (b.v. public_html). Dit kunt u doen met uw
favoriete FTP programma of het controlepaneel dat uw host aanbiedt.

2\. Download en open het configuration.php bestand in een tekst editor.

3\. Verwijder de probeerjoomla map uit de naam van het pad. Zoek naar de
volgende regels

    var $live_site = '';
    var $log_path = '/home/username/public_html/tryjoomla/administrator/logs';
    var $tmp_path = '/home/username/public_html/tryjoomla/tmp';
    var $ftp_root = 'public_html/tryjoomla';

Wijzig deze in:

    var $live_site = '';
    var $log_path = '/home/username/public_html/administrator/logs';
    var $tmp_path = '/home/username/public_html/tmp';
    var $ftp_root = 'public_html';

N.B. De \$live_site variable heeft zelde een waarde nodig. Heeft het een
waarde gekregen tijdens de installatie, pas dit pad dan ook aan.

    var $live_site = 'http://www.example.com/tryjoomla';

Wijzig in:

    var $live_site = 'http://www.example.com';

4\. Controleer het .htaccess bestand van uw website. De sub-mail moet
hier ook verwijderd worden. De RewriteBase moet uitgecommentarieerd
worden. Zoek naar een RewriteRule die de oude sub-map bevat.

5\. Controleer of er geen verwijzingen naar de oude sub-map zijn
ingesteld in het controle paneel van uw host.

Als u de cache ingeschakeld heeft, log dan in de administrator backend
(nu <a href="http://www.example.com/administrator" class="external free"
target="_blank"
rel="nofollow noreferrer noopener">http://www.example.com/administrator</a>
in plaats van <a href="http://www.example.com/tryjoomla/administrator"
class="external free" target="_blank"
rel="nofollow noreferrer noopener">http://www.example.com/tryjoomla/administrator</a>).
Ga naar Syteem -\> Wis Cache en verwijder alle bestanden in de cache.
