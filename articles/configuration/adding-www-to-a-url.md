<!-- Filename: Adding_www_to_a_url / Display title: Het toevoegen van www aan een url -->

## Hoe krijg ik www als voorvoegsel in al mijn Joomla! sites?

Voeg het volgende toe aan je `.htaccess`-bestand:

    RewriteEngine On
    RewriteCond %{HTTP_HOST} !^(www\.example\.com)?$
    RewriteRule (.*) http://www.example.com/$1 [R=301,L]

Een meer complete oplossing die tegelijkertijd een aantal andere
problemen rond canonicalisatie behandelt:

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

  
<a
href="https://docs.joomla.org/index.php?title=Categorie:FAQ&amp;action=edit&amp;redlink=1"
class="new"
title="Categorie:FAQ (page does not exist)">Categorie:FAQ</a> <a
href="https://docs.joomla.org/index.php?title=Categorie:Installation&amp;action=edit&amp;redlink=1"
class="new"
title="Categorie:Installation (page does not exist)">Categorie:Installatie</a>
<a
href="https://docs.joomla.org/index.php?title=Categorie:Server_configurations&amp;action=edit&amp;redlink=1"
class="new"
title="Categorie:Server configurations (page does not exist)">Categorie:Server
configuraties</a>
