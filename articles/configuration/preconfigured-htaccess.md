<!-- Filename: Preconfigured_htaccess / Display title: Vooraf geconfigureerde htaccess -->

Een Apache-webserver gebruikt een htaccess-bestand in de hoofddirectory
van een site voor specifieke site configuratie. Een vooraf
geconfigureerd htaccess-bestand (`htaccess`) wordt bij Joomla!
meegeleverd. Deze bevat instructies om een veelgebruikte exploits te
voorkomen en implementeert SEF URL's. Ook voegt deze sommige
instellingen toe die voor uw omgeving gecontroleerd moeten worden.

- IndexIgnore \*
- Options +FollowSymLinks
- Options -Indexes
- RewriteBase /
- 

Het activeren van `htaccess.txt` betekent het samenvoegen van een
bestaand .htaccess bestand met htaccess.txt en beslissingen te nemen
over de hiervoor genoemde instellingen.

**Opmerking:**

Het actieve bestand bevindt zich in één van de
`httpd.conf bestanden met: `

    AccessFileName .htaccess

Deze hoort als .htaccess te staan (wat het een verborgen bestand maakt
op Linux-omgevingen). Dit hoeft niet aangepast te worden.

Op het Windows platform zou dat aangepast kunnen worden naar:

    AccessFileName htaccess.ini

zodat je het makkelijker kan bewerken.

Gebruik `htaccess.txt` niet hier want bij het updaten van Joomla zal
deze worden overschreven en zullen aanpassingen verloren gaan.

Inhoud van `htaccess.txt`:

    ##
    # @package    Joomla
    # @copyright  Copyright (C) 2005 - 2018 Open Source Matters. All rights reserved.
    # @license    GNU General Public License version 2 or later; see LICENSE.txt
    ##

    ##
    # READ THIS COMPLETELY IF YOU CHOOSE TO USE THIS FILE!
    #
    # The line 'Options +FollowSymLinks' may cause problems with some server configurations.
    # It is required for the use of mod_rewrite, but it may have already been set by your 
    # server administrator in a way that disallows changing it in this .htaccess file.
    # If using it causes your site to produce an error, comment it out (add # to the 
    # beginning of the line), reload your site in your browser and test your sef urls. If 
    # they work, then it has been set by your server administrator and you do not need to 
    # set it here.
    ##

    ## No directory listings

      IndexIgnore *


    ## Can be commented out if causes errors, see notes above.
    Options +FollowSymlinks
    Options -Indexes

    ## Mod_rewrite in use.

    RewriteEngine On

    ## Begin - Rewrite rules to block out some common exploits.
    # If you experience problems on your site then comment out the operations listed 
    # below by adding a # to the beginning of the line.
    # This attempts to block the most common type of exploit `attempts` on Joomla!
    #
    # Block any script trying to base64_encode data within the URL.
    RewriteCond %{QUERY_STRING} base64_encode[^(]*\([^)]*\) [OR]
    # Block any script that includes a  tag in URL.
    RewriteCond %{QUERY_STRING} (<|%3C)([^s]*s)+cript.*(>|%3E) [NC,OR]
    # Block any script trying to set a PHP GLOBALS variable via URL.
    RewriteCond %{QUERY_STRING} GLOBALS(=|\[|\%[0-9A-Z]{0,2}) [OR]
    # Block any script trying to modify a _REQUEST variable via URL.
    RewriteCond %{QUERY_STRING} _REQUEST(=|\[|\%[0-9A-Z]{0,2})
    # Return 403 Forbidden header and show the content of the root home page
    RewriteRule .* index.php [F]
    #
    ## End - Rewrite rules to block out some common exploits.

    ## Begin - Custom redirects
    #
    # If you need to redirect some pages, or set a canonical non-www to
    # www redirect (or vice versa), place that code here. Ensure those
    # redirects use the correct RewriteRule syntax and the [R=301,L] flags.
    #
    ## End - Custom redirects

    ##
    # Uncomment the following line if your webserver's URL
    # is not directly related to physical file paths.
    # Update Your Joomla! Directory (just / for root).
    ##

    # RewriteBase /

    ## Begin - Joomla! core SEF Section.
    #
    RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]
    #
    # If the requested path and file is not /index.php and the request
    # has not already been internally rewritten to the index.php script
    RewriteCond %{REQUEST_URI} !^/index\.php
    # and the requested path and file doesn't directly match a physical file
    RewriteCond %{REQUEST_FILENAME} !-f
    # and the requested path and file doesn't directly match a physical folder
    RewriteCond %{REQUEST_FILENAME} !-d
    # internally rewrite the request to the index.php script
    RewriteRule .* index.php [L]
    #
    ## End - Joomla! core SEF Section.
    </pre></tt><p><tt>
    </tt></p>
    <!-- 
    NewPP limit report
    Cached time: 20230210211957
    Cache expiry: 86400
    Dynamic content: false
    Complications: []
    CPU time usage: 0.021 seconds
    Real time usage: 0.032 seconds
    Preprocessor visited node count: 15/1000000
    Post‐expand include size: 6/2097152 bytes
    Template argument size: 0/2097152 bytes
    Highest expansion depth: 2/40
    Expensive parser function count: 0/100
    Unstrip recursion depth: 0/20
    Unstrip post‐expand size: 4261/5000000 bytes
    -->
    <!--
    Transclusion expansion time report (%,ms,calls,template)
    100.00%    0.000      1 -total
    -->

    <!-- Saved in parser cache with key docsj_mediawiki:pcache:idhash:99688-0!canonical and timestamp 20230210211957 and revision id 583119
     -->
