<!-- Filename: How_to_check_if_mod_rewrite_is_enabled_on_your_server / Display title: Hoe controleert u of mod rewrite is ingeschakeld op uw sever -->

Veel problemen met SEO ontstaan doordat de host mod_rewrite (Apache
instelling) niet heeft ingeschakeld. Hoewel vaak gezegd wordt dat dit is
ingeschakeld, is dit niet altijd het geval. U kunt zelf controleren of
dit correct is of niet en of dit ervoor zorgt dat uw server een HTTP
Error 500 geeft.

Zo kunt u controleren of mod_rewrite echt is ingeschakeld!

**1. Schakel SEO in in het administratie gedeelte:**

Ga naar Site -\> Algemene instellingen -\> SEO instellingen: Zoekmachine
vriendelijke URL's en zet dit op Ja. Zet ook URL herschrijven op Ja. (De
instelling Voeg suffix toe aan URL's is optioneel).

  
**2. Hernoem het bestand htaccess.txt naar .htaccess:**

Plaats vervolgens ALLEEN de volgende regels in uw .htaccess bestand:

    RewriteEngine On
    Options +FollowSymLinks
    RewriteRule ^joomla\.html http://www.joomla.org/? [R=303,L]

  
**3. Ga nu in uw browser naar:**
<a href="http://www.uwdomeinnaam.nl/joomla.html" class="external free"
target="_blank"
rel="nofollow noreferrer noopener">http://www.uwdomeinnaam.nl/joomla.html</a>

(Vervang www.uwdomeinnaam.nl door uw eigen domeinnaam in de URL
hierboven.)

Als u wordt doorgestuurd naar joomla.org dan werkt mod_rewrite. Als u
een foutmelding krijgt dan werkt mod_rewrite niet.

Notitie: als uw site in een map staat zoals */test/* dan moet u de
volgende code in de het .htaccess bestand plaatsen:

    RewriteEngine On
    Options +FollowSymLinks
    RewriteRule ^test/joomla\.html http://www.joomla.org/? [R=303,L]
