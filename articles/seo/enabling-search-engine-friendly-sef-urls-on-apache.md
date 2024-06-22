<!-- Filename: Enabling_Search_Engine_Friendly_(SEF)_URLs_on_Apache / Display title: Het inschakelen van Search Engine Friendly (SEF) Url ' s in Apache -->


"'Zoekmachine vriendelijk (SEF)"', "'voor mensen leesbaar"' of
<a href="https://en.wikipedia.org/wiki/Clean_URL" class="extiw"
title="wikipedia:Clean URL">schone URL's</a> zijn URL's die zinvol zijn
voor zowel mensen als zoekmachines, omdat ze het pad naar de specifieke
pagina waar ze naar verwijzen beschrijven. Sinds versie 1.5, is Joomla!
in staat URL's in alle formaten te creëren, inclusief SEF URL's. Dit is
onafhankelijk van de URL-rewriting uitgevoerd door de web-server, zodat
het zelfs werkt als Joomla! draait op een andere server dan met de
Apache mod_rewrite module. De SEF URL's volgen een bepaald patroon, maar
de gebruiker kan een  korte beschrijvende tekst
(alias)
definiëren voor elk deel van de URL.

Intern heet het lokale gedeelte van een SEF URL (het gedeelte achter de
domeinnaam) de "route"'. Het maken en verwerken van SEF URL's wordt
daarom aangeduid als "'routeren', en de relevante code wordt ook wel een
'router' genoemd.

In dit artikel wordt ingegaan op SEF URL's voor de populaire,
open-source Apache webserver. Het is ook mogelijk SEF URL's te gebruiken
op Microsoft's IIS webserver. Zie hiervoor [Inschakelen van Zoekmachine
vriendelijke (SEF) URL's op
IIS](https://docs.joomla.org/Enabling_Search_Engine_Friendly_(SEF)_URLs_on_IIS "Special:MyLanguage/Enabling Search Engine Friendly (SEF) URLs on IIS").

Sinds Joomla!
<img src="https://docs.joomla.org/images/d/da/Compat_icon_1_6.png"
decoding="async" data-file-width="40" data-file-height="17" width="40"
height="17" alt="Joomla 1.6" />, zijn basis SEF URL's standaard
ingesteld. In eerdere versies moet u ze via de Algemene Instellingen
actieveren. De instructies hieronder zijn nog steeds van toepassing als
u Apaches's mod_rewrite/URL rewriting wil toepassen.

## Controleer of .htaccess ingeschakeld is

Controleer of uw Apache configuratie bestand .htaccess overrides
toestaat. U moet zeker weten dat dit is ingesteld, anders zal het
.htaccess bestand in de root van uw Joomla! installatie worden genegeerd
of kunnen er fouten optreden. In het gedeelte van uw host configuratie
bestand, of in het hoofd (`htpd.conf`) configuratie bestand moet iets
vergelijkbaars staan als het voorbeeld hieronder om overrides te
activeren.

      AllowOverride All



      AllowOverride All Options=[an option],[an option],...

Er zijn andere manier om te testen of `.htaccess` geactiveerd is als u
geen toegang heeft tot de configuratiebestanden van uw site. Kijk naar
de <a href="http://httpd.apache.org/docs/current/howto/htaccess.html"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">.htaccess handleiding</a> op
<a href="http://www.apache.org/" class="external text" target="_blank"
rel="nofollow noreferrer noopener">The Apache Software Foundation</a>
voor meer informatie.

## Stap-voor-stap

Dit zijn stap-voor-stap instructies. Volg ze in de aangegeven volgorde.
Als een stap niet lukt, ga dan **niet** verder tot u het probleem heeft
opgelost.

1.  Hernoem het bestand `"htaccess.txt"` in de root van uw Joomla!
    website naar `".htaccess"`.

2.  *Mogelijk is deze stap niet noodzakelijk.* Open het `.htaccess`
    bestand in een tekst editor. Verwijder het commentaar teken (#) voor
    `RewriteBase /`. Als Joomla! in een eigen map is geïnstalleerd (en
    niet in de root map van uw domein) voeg dan de naam van de map toe
    voor de schuine streep naar voren b.v. `RewriteBase /uwjoomlamap`.

3.  Log in in de Back-end en open de Algemene Instellingen

4.  Schakel **Gebruik Apache mod_rewrite/Gebruik URL herschrijven**
    optie in en klik op *Opslaan*. Deze optie gebruikt Apache's
    *mod_rewrite* functie om het "index.php" deel uit de URL te
    verwijderen.

    Controleer of uw website nog goed werkt. Uw URL's zouden er zo uit
    moeten zien:

        http://www.voorbeeld.nl/het-nieuws/1­-laatste-­nieuws/1-­welkom-bij­-joomla

    Als deze optie fouten veroorzaakt kijk dan hier: [Hoe controleert u
    of mod rewrite is geactiveerd op uw
    server](https://docs.joomla.org/How_to_check_if_mod_rewrite_is_enabled_on_your_server "Special:MyLanguage/How to check if mod rewrite is enabled on your server").

    - Als dit niet geactiveerd is en u heeft toegang tot
      `apache/conf/httpd.conf`, open dan dat bestand en controleer of de
      regel `LoadModule rewrite_module modules/mod_rewrite.so` geen
      commentaar is. Indien nodig, verwijder de \# vooraan de regel en
      herstart de Apache web server.
    - Als *mod_rewrite* niet geactiveerd kan worden, laat deze optie dan
      uit staan. Het is niet erg om het `.htaccess` bestand niet terug
      te wijzigen in `htaccess.txt`.

5.  *Als u denkt dat het nodig is*, activeer **Voeg een achtervoegsel
    (suffix) aan URL's toe** en klik op *Opslaan*. Deze optie voegt
    `.html` toe aan het eind van de URL's. Er zijn verschillende
    meningen over de vraag of dit nodig of zelfs nuttig is. Het lijkt
    zoekmachines niet uit te maken of uw URL al dan niet eindigt op
    `.html`.

6.  Open de Plugin Manager en activeer de **Systeem - SEF plugin**. Deze
    plugin voegt SEF ondersteuning toe voor de links in uw Joomla!
    artikelen. Het werkt direct in de HTML en heeft geen speciale tag
    nodig.
