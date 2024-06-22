<!-- Filename: How_do_you_block_directory_scans_using_htaccess%3F / Display title: Hoe blokkeert u map-scans met behulp van htaccess? -->

**Instructies**

Add Apache rewrite rules to your `.htaccess` file. For example, the
following will redirect all attempts to access files with names starting
with, "phpMyAdmin" to `index.php`.

  
**Voorbeeld Apache Rewrite Rule**

    RewriteRule ^/phpMyAdmin.*$ /index.php

  
**Enkele reguliere expressie tips**

    ^ Betekent begin van de bestandsnaam
    . Betekent elk ander teken als nieuwe regel
    * Betekent één of meer van de voorafgaande tekens
    $ Betekent einde regel
