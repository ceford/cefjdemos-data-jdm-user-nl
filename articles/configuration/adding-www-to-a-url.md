<!-- Filename: Adding_www_to_a_url / Display title: www toevoegen aan een URL  -->

## Apache .htaccess Reguliere Expressies

Voor een eenvoudige oplossing, voeg het volgende toe aan je `.htaccess`-bestand:

```bash
    RewriteEngine On
    RewriteCond %{HTTP_HOST} !^(www\.example\.com)?$ [NC]
    RewriteRule (.*) https://www.example.com/$1 [R=301,L]
```

In dit geval zal een URL van de vorm `https://example.com/index.php?item=1`
worden omgeleid naar `https://www.example.com/index.php?item=1`.

In het bovenstaande voorbeeld:

* `RewriteCond` definieert een testconditie.
* `%{HTTP_HOST}` gebruikt de hostvariabele van het verzoek (example.com).
* `!` betekent NIET en `^` betekent BEGIN - dus, start niet met www.example.com
* `(` en `)` vangen op wat zich tussen de haakjes bevindt voor het gebruik in een terugverwijzing.
* `\` verandert het volgende teken van een controlekarakter in een werkelijk teken.
* `.` betekent meestal elk teken, maar voorafgegaan door \ betekent het een punt.
* `?` maakt de match optioneel.
* `$` betekent EIND (van de optionele match).
* `[NC]` staat voor No Case, wat hoofdletterongevoelig betekent.
* `RewriteRule` is geldig als de url niet begint met www.
* `(.*)` is een patroon, in dit geval een enkel teken herhaald 0 of meer
    keren, wat het padgedeelte van de URL betekent. Het wordt opgevangen als $1.
* `https://www.example.com/` is de vervanging voor het hostgedeelte van de URL.
* `$1` is het opgevangen pad.
* `[]` bevat vlaggen - instructies over wat te doen.
* `R=301` is een instructie om een Moved Permanently-header te verzenden.
* `L` betekent Laatst in set - aangezien een match is gevonden, negeer alle daaropvolgende regels.

Een meer complete oplossing die verschillende andere canonisatieproblemen tegelijkertijd oplost:

    RewriteEngine On
    #
    RewriteCond %{THE_REQUEST} ^[A-Z]{3,9}\ /([^/]+/)*index\.html?\ HTTP/
    RewriteRule ^(([^/]+/)*)index\.html?$ http://www.example.com/$1 [R=301,L]
    #
    RewriteCond %{THE_REQUEST} !^POST
    RewriteCond %{THE_REQUEST} ^[A-Z]{3,9}\ /([^/]+/)*index\.php\ HTTP/
    RewriteCond %{SERVER_PORT}>s ^(443>(s)|[0-9]+>s)$
    RewriteRule ^(([^/]+/)*)index\.php$ http%2://www.example.com/$1 [R=301,L]
    #
    RewriteCond %{HTTP_HOST} !^(www\.example\.com)?$
    RewriteRule (.*) http://www.example.com/$1 [R=301,L]

Als je zou willen begrijpen wat dit allemaal betekent, kun je deze artikelen lezen:

* [Apache mod_rewrite Introductie](https://httpd.apache.org/docs/2.4/rewrite/intro.html)
* [Introductie tot .htaccess Redirects](https://www.danielmorell.com/guides/htaccess-seo/redirects/introduction-to-redirects)

*Vertaald door openai.com*

