<!-- Filename: Nginx / Display title: Nginx -->

<a href="http://nginx.org/" rel="nofollow noreferrer noopener">Nginx</a> is een lichte webserver die
<a href="https://en.wikipedia.org/wiki/Nginx" rel="nofollow noreferrer noopener">ongeveer 33%</a> van de webservers over alle domeinen aandrijft. Tenzij je specifieke eisen hebt die een zware webserver zoals Apache vereisen, ben je veel beter af met het gebruik van Nginx.

Hieronder staan instructies om Joomla! aan de praat te krijgen met de <a href="https://www.nginx.com/resources/wiki/start/topics/examples/phpfcgi/" rel="nofollow noreferrer noopener">PHP FastCGI Voorbeeld</a>.
## Installeer Nginx

Voor Ubuntu, voer *aptitude install Nginx* uit. Voor andere distributies, voer de overeenkomstige pakketbeheerder uit of zie de <a href="https://www.nginx.com/resources/wiki/start/topics/tutorials/install/" rel="nofollow noreferrer noopener">Nginx Installatie pagina</a>.

## Installeer PHP FastCGI

Voor Ubuntu, lees <a
href="https://www.nginx.com/resources/wiki/start/topics/examples/phpfcgi/"
rel="nofollow noreferrer noopener">PHP FastCGI Voorbeeld</a>.

Voor Gentoo zal PHP draaien als een FastCGI-service (FPM), dus de Nginx-server
zal PHP als een apart proces uitvoeren:

    # echo "dev-lang/php gd gd2 curl simplexml tokenizer dom tidy sqlite xml fpm cgi" >> /etc/portage/package.use
    # emerge php

De standaardinstellingen van PHP-FPM zijn geschikt voor de meeste servers. Voor speciale
configuraties, bezoek de
<a href="http://php.net/manual/en/install.fpm.php"
rel="nofollow noreferrer noopener">PHP FPM site</a>.

## Nginx configureren

Nginx configuratiebestanden bevinden zich in:

- `/etc/nginx/sites-available/` op Ubuntu (voor sites die op die Nginx-instantie draaien)
- `/etc/nginx/nginx.conf` op Gentoo en Raspbian (Debian geoptimaliseerd voor Raspberry Pi)

Hier is een voorbeeld van een Nginx-configuratiebestand, *joomla.conf*, dat je kunt hergebruiken op al je Nginx-ingeschakelde sites.

    server {
      listen 80;
        server_name YOUR_DOMAIN;
        server_name_in_redirect off;

        access_log /var/log/nginx/localhost.access_log;
        error_log /var/log/nginx/localhost.error_log info;

        root PATH_ON_SERVER;
        index index.php index.html index.htm default.html default.htm;
        # Ondersteuning voor schone (ook bekend als zoekmachinevriendelijke) URL's
        location / {
            try_files $uri $uri/ /index.php?$args;
        }

        # voeg globale x-content-type-options header toe
        add_header X-Content-Type-Options nosniff;

        # scripts binnen schrijfbare directories weigeren uit te voeren
        location ~* /(images|cache|media|logs|tmp)/.*\.(php|pl|py|jsp|asp|sh|cgi)$ {
            return 403;
            error_page 403 /403_error.html;
        }

        location ~ \.php$ {
          fastcgi_pass  127.0.0.1:9000;
          fastcgi_index index.php;
          include fastcgi_params;
          fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
          include /etc/nginx/fastcgi.conf;
        }

        # caching van bestanden
        location ~* \.(ico|pdf|flv)$ {
            expires 1y;
        }

        location ~* \.(js|css|png|jpg|jpeg|gif|swf|xml|txt)$ {
            expires 14d;
        }

    }

Let op een paar dingen:

1.  De parameter *fastcgi_pass* is ingesteld op *127.0.0.1:9000*, overeenkomend met de poort waarop FPM is geconfigureerd om te luisteren. Dit betekent dat je de PHP-processen op afzonderlijke servers kunt draaien. Op Gentoo kun je deze configuratie vinden in het bestand */etc/php/fpm-php5.3/php-fpm.conf/*.
2.  Vergeet niet YOUR_DOMAIN & PATH_ON_SERVER hierboven te vervangen, afhankelijk van je domein en het pad van Joomla op je server.

## GZip Ondersteuning

Als je GZip-compressieondersteuning nodig hebt, voeg dan het volgende gedeelte toe aan de *http* sectie van het hoofdconfiguratiebestand van Nginx:

```nginx
    gzip on;
    gzip_http_version 1.1;
    gzip_comp_level 6;
    gzip_min_length 1100;
    gzip_buffers 4 8k;
    gzip_types text/plain application/xhtml+xml text/css application/xml application/xml+rss text/javascript application/javascript application/x-javascript;
    gzip_proxied any;
    gzip_disable "MSIE [1-6]\.";
```

## Bronnen

- <a href="https://wiki.gentoo.org/wiki/Nginx" rel="nofollow noreferrer noopener">Nginx in Gentoo</a>
- <a href="https://kevinworthington.com/nginx-for-windows/" rel="nofollow noreferrer noopener">Nginx voor Windows</a>
- <a href="https://ubuntu.com/tutorials/install-and-configure-nginx#1-overview" rel="nofollow noreferrer noopener">Nginx in Ubuntu</a>
- <a href="https://www.debianadmin.com/howto-install-nginx-webserver-in-debian.html" rel="nofollow noreferrer noopener">Nginx in Debian</a>
- <a href="https://www.php.net/manual/en/install.fpm.php" rel="nofollow noreferrer noopener">PHP-FPM installatie en configuratie</a>
- <a href="https://docs.nginx.com/nginx/admin-guide/web-server/compression/" rel="nofollow noreferrer noopener">Compressie en decompressie</a>
- <a href="https://www.nginx.com/blog/creating-nginx-rewrite-rules/" rel="nofollow noreferrer noopener">Het maken van NGINX Rewrite Rules</a>
- <a href="http://nginx.org/en/docs/http/request_processing.html" rel="nofollow noreferrer noopener">Hoe Nginx een verzoek verwerkt</a>

*Vertaald door openai.com*

