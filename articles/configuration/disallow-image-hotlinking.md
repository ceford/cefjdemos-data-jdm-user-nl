<!-- Filename: How_do_you_block_direct_hot_linking_to_image_files_using_htaccess%3F / Display title: Afbeeldingen Hotlinken Verbieden  -->

## Definitie

Hotlinken is de praktijk waarbij een afbeelding van de ene website wordt gelinkt vanuit een artikel op een andere website. Het kan een zeer nuttige praktijk zijn. Deze website gebruikt veel afbeeldingen die feitelijk op de docs.joomla.org-website staan. Het bespaart tijd en moeite die nodig zijn om screenshots te maken en op de bandbreedte van deze site. Er kunnen echter auteursrechtelijke problemen zijn en u wilt misschien voorkomen dat uw afbeeldingen op deze manier worden gebruikt.

De hier beschreven methode maakt gebruik van een *.htaccess*-bestand, wat een functie van de Apache-server is. Andere webservers kunnen andere methoden bieden om hotlinken te voorkomen.

## Instructies

Plaats de volgende code in het *.htaccess*-bestand van uw hoofdmap.
```
<IfModule mod_rewrite.c>
    RewriteEngine on
    RewriteCond %{HTTP_REFERER} !^$
    RewriteCond %{HTTP_REFERER} !^http(s)?://(www\.)?yourdomain.com [NC]
    RewriteCond %{HTTP_REFERER} !^http(s)?://(www\.)?google.com [NC]
    RewriteRule \.(jpg|jpeg|png|gif|webp|svg)$ - [NC,F,L]
</IfModule>
```

### Uitleg

* De eerste RewriteCond staat directe aanvragen via een URL toe - geen referer.
* De tweede RewriteCond staat aanvragen van uw eigen domein toe. De *\[NC\]*
    vlag betekent *No Case*, dat wil zeggen, match zowel hoofd- als kleine letters.
* De derde RewriteCond staat aanvragen van Google toe, zodat uw afbeeldingen
    nog steeds in zoekresultaten kunnen verschijnen. U kunt soortgelijke regels toevoegen voor andere
    sites die u wilt toestaan.
* De RewriteRule blokkeert aanvragen voor afbeeldingsbestanden van alle domeinen die niet
    eerder waren toegestaan. De F-vlag vertelt de browser om een Forbidden-header (403) terug te sturen. L staat voor Laatste regel.

### Blokkeer Hotlinking van Specifieke Domeinen

Om hotlinking alleen van specifieke domeinen te stoppen, zoals *myspace.com*,
*blogspot.com* en *livejournal.com*, terwijl u andere websites toestaat
om naar uw afbeeldingen te hotlinken, gebruikt u de volgende code:

```
<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteCond %{HTTP_REFERER} ^http(s)?://(.+\.)?myspace\.com/ [NC,OR]
    RewriteCond %{HTTP_REFERER} ^http(s)?://(.+\.)?blogspot\.com/ [NC,OR]
    RewriteCond %{HTTP_REFERER} ^http(s)?://(.+\.)?livejournal\.com/ [NC]
    RewriteRule \.(jpg|jpeg|png|gif|webp|svg)$ - [NC,F,L]
</IfModule>
```
U kunt zoveel verschillende domeinen toevoegen als u wilt. Elke *RewriteCond*
regel behalve de laatste moet eindigen met de *\[NC,OR\]* vlaggen. *NC*
betekent dat er geen rekening wordt gehouden met hoofdletters of kleine letters. *OR* betekent "Of Volgende", zoals in, match deze regel
**of** de volgende regel. De laatste *RewriteCond* laat de *OR* vlag weg om te stoppen
na de laatste *RewriteCond*.

*Vertaald door openai.com*

