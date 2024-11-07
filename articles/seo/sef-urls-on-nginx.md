<!-- Filename: Enabling_Search_Engine_Friendly_(SEF)_URLs_on_Nginx / Display title: SEF URL's op Nginx  -->

## Inleiding

Zoekmachinevriendelijke (SEF), voor mensen leesbare of schone URL's zijn URL's die zowel voor mensen als zoekmachines logisch zijn, omdat ze het pad naar de specifieke pagina die ze aanwijzen, uitleggen. Joomla! is in staat om URL's in elk formaat te maken en te verwerken, inclusief SEF URL's. Dit is niet afhankelijk van URL-herschrijving door de webserver, dus het werkt zelfs als Joomla! een andere server dan Apache met de mod_rewrite-module draait. De SEF URL's volgen een bepaald vast patroon, maar de gebruiker kan een korte beschrijvende tekst (alias) definiëren voor elk segment van de URL.

Intern verwijst het lokale deel van een SEF URL (het deel na de domeinnaam) naar een route. Het maken en verwerken van SEF URL's wordt daarom routing genoemd, en de relevante code wordt een router genoemd.

Dit artikel behandelt SEF URL's onder de populaire, open-source Nginx-webserver.

## Stappen voor NginX Servers¶

- Voeg de volgende code toe aan je server (vhost) configuratie in het nginx.conf bestand:

```
    # Ondersteuning voor schone (aka zoekmachinevriendelijke) URL's
    location / {
       try_files $uri $uri/ /index.php?$args;
    }
```
- Als het bovenstaande niet werkt, voeg dan de volgende code toe aan je serverconfiguratie in het nginx.conf bestand: (Dit werkte met nginx 1.4.6 op Ubuntu.)
```
    server {
      ....
      location / {
      expires 1d;

      # Schakel joomla SEF URL's in binnen Nginx
      try_files $uri $uri/ /index.php?$args;
      }
      ....
    }
```
- Log in op je Backend en open de Globale Configuratie
- Schakel de optie **Zoekmachinevriendelijke URL's** in en Save. Deze optie zet de URL's om van het native Joomla! formaat naar het SEF-formaat. Controleer of je site correct werkt. Je URL's zouden er nu zo uit moeten zien: `http://www.example.com/index.php/the-­news/1-­latest­-news/1­-welcome­-to­-joomla`. Als je site niet correct werkt, zie dan [Waarom raakt je site in de war wanneer je SEF (Zoekmachinevriendelijke URL's) inschakelt?](https://docs.joomla.org/Why_does_your_site_get_messed_up_when_you_turn_on_SEF_(Search_Engine_Friendly_URLs)%3F)
- Schakel de optie **Gebruik Apache mod_rewrite/URL herschrijven** in en Save. Deze optie gebruikt de Apache mod_rewrite functie om het *index.php* gedeelte van de URL te elimineren. Controleer of je site correct werkt. Je URL's zouden er nu zo uit moeten zien: `http://www.example.com/the-­news/1­-latest-­news/1-­welcome-­to­-joomla`. Als deze optie fouten veroorzaakt, zie dan [Hoe controleer je of mod rewrite is ingeschakeld op je server](https://docs.joomla.org/How_to_check_if_mod_rewrite_is_enabled_on_your_server). Als het niet is ingeschakeld en je hebt toegang tot het bestand `apache/conf/httpd.conf`, open dat bestand en controleer of de regel `LoadModule rewrite_module modules/mod_rewrite.so` niet is uitgecommentarieerd. Zo nodig, verwijder het commentaar van de regel en start de Apache webserver opnieuw op. Als *mod_rewrite* niet kan worden ingeschakeld, laat deze optie dan uitgeschakeld. Het maakt niet uit als je het `.htaccess` bestand niet hernoemd laat.
- *Als je denkt dat dit nodig is*, schakel **Voeg achtervoegsel toe aan URL's** in en *Save*. Deze optie voegt `.html` toe aan het einde van URL's. Er zijn verschillende meningen over of dit nodig of zelfs nuttig is. Zoekmachines lijken zich niet te bekommeren of je URL's eindigen op `.html` of niet.
- Open de Plugin Manager en schakel de **Systeem - SEF** plugin in. Deze plugin voegt SEF-ondersteuning toe aan links in je Joomla-artikelen. Het werkt direct op de HTML en vereist geen speciaal label.

*Vertaald door openai.com*

