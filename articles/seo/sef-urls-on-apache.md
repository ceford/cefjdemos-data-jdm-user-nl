<!-- Filename: Enabling_Search_Engine_Friendly_(SEF)_URLs_on_Apache / Display title: SEF-URL's op Apache   -->

## Verifiëren of .htaccess is ingeschakeld

Controleer of je Apache-configuratiebestand .htaccess-overrides toestaat. Je moet ervoor zorgen dat overrides zijn ingeschakeld, anders wordt het .htaccess-bestand in je Joomla!-rootdirectory genegeerd of veroorzaakt een fout. In het gedeelte van je virtuele hostconfiguratiebestand of in het hoofdconfiguratiebestand (`httpd.conf`) moet je iets vergelijkbaars hebben als het onderstaande voorbeeld om overrides in te schakelen:

```bash
<Directory "/home/user/public_html">
  AllowOverride All
</Directory>

<Directory "/path/to/htdocs">
  AllowOverride All Options=[een optie],[een optie],...
</Directory>
```

Er zijn andere manieren om te testen of `.htaccess` is ingeschakeld als je geen toegang hebt tot de configuratiebestanden van je site. Raadpleeg de [.htaccess handleiding](http://httpd.apache.org/docs/current/howto/htaccess.html) op de website van *The Apache Software Foundation* voor aanvullende informatie.

## Stap voor Stap

Dit zijn stapsgewijze instructies. Volg ze in de volgorde waarin ze hier worden gepresenteerd. Als een stap mislukt, **ga dan niet** verder totdat je het probleem hebt opgelost.

1. Hernoem het bestand `htaccess.txt` in de basisfolder van je Joomla! naar `.htaccess`.
2. *Deze stap is mogelijk niet noodzakelijk.* Open `.htaccess` in een teksteditor. Haal het commentaar weg bij `RewriteBase /` (verwijder het eerste teken, \#). Als Joomla is geïnstalleerd in zijn eigen folder, voer dan de Joomla-foldernaam in na de schuine streep. Bijvoorbeeld `RewriteBase /joujoomlafolder`.
3. Log in op je Backend en open de Globale Configuratie.
4. Schakel de optie **Gebruik Apache mod_rewrite/URL herschrijven** in en klik op *Opslaan*. Deze optie gebruikt de Apache *mod_rewrite* functie om het "index.php" gedeelte van de URL te elimineren.

    Controleer of je site correct werkt. Je URLs zouden er nu als volgt uit moeten zien:

        `http://www.example.com/het-nieuws/1-laatste-nieuws/1-welkom-bij-joomla`

    Als deze optie fouten veroorzaakt, raadpleeg dan 
    [Hoe te controleren of mod_rewrite op je server is ingeschakeld](https://docs.joomla.org/How_to_check_if_mod_rewrite_is_enabled_on_your_server).

    - Als het niet is ingeschakeld en je toegang hebt tot het bestand
      `apache/conf/httpd.conf`, open dat bestand en controleer of de regel
      `LoadModule rewrite_module modules/mod_rewrite.so` niet is
      uitgeschakeld. Indien nodig, verwijder het commentaar op de regel en
      herstart de Apache-webserver.
    - Als *mod_rewrite* niet kan worden ingeschakeld, laat deze optie dan uit. Het maakt niet uit als je het `.htaccess` bestand hernoemd laat.
5. *Als je denkt dat dit nodig is*, schakel dan **Voeg suffix toe aan URLs** in en klik op *Opslaan*. Deze optie voegt `.html` toe aan het einde van URLs. Er zijn verschillende meningen over of dit nodig of zelfs nuttig is. Zoekmachines lijken het niet uit te maken of je URLs eindigen op `.html` of niet.
6. Open de Plugin Manager en schakel de **Systeem - SEF plugin** in. Deze plugin voegt SEF-ondersteuning toe aan links in je Joomla-artikelen. Het werkt direct op de HTML en vereist geen speciale tag.

*Vertaald door openai.com*

