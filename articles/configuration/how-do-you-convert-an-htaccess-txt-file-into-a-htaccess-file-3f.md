<!-- Filename: How_do_you_convert_an_htaccess.txt_file_into_a_.htaccess_file%3F / Display title: Hoe verandert u een een htaccess.txt bestand in een .htaccess bestand? -->

### Inleiding

Bij gebruik van PHP als Apache module, kunnen de
configuratie-instellingen gewijzigd worden via opdrachten in de Apache
configuratiebestanden (bijvoorbeeld httpd.conf en .htaccess bestanden).
U heeft "AllowOverride Options" of "AllowOverride All" rechten nodig om
dit te doen. Indien u uw eigen Apache configuratie beheert, moet u
httpd.conf gebruiken. Indien u niet uw eigen Apache configuratie beheert
(zoals op een gedeelde server), moet u .htaccess bestanden gebruiken.

### Richtlijnen

1.  Zoek eerst, met behulp van FTP om op uw server te komen, naar het
    bestand htaccess.txt in in uw root-map. Het bestand moet
    geïnstalleerd zijn tijdens de Joomla! installatie. (Let op dat de
    bestandsnaam niet met een punt begint) Open en lees htaccess.txt
    zorgvuldig. Het bevat belangrijke aanwijzingen over het beschermen
    van uw site.
2.  Pas dit bestand aan voor uw site, en sla hem dan op in de "home map"
    als .htaccess (inclusief de punt). Zorg dat het "Verberg
    bestandsnamen die beginnen met een punt"-vakje in uw FTP programma
    uit staat.
3.  Test de website en het beheergedeelte. Hernoem, als er fouten
    optreden, het bestand terug in htaccess.txt, en los de fouten van uw
    wijzigingen op. Als het niet lukt het werkend te krijgen, moet u
    misschien het bestand htaccess.txt laten.
4.  Gebruik phpinfo() om ervoor te zorgen dat de configuratie als
    bedoeld is. Let op: Vanuit het web toegankelijke bestanden die
    phpinfo() bevatten zijn potentiële veiligheidsrisico's . Ze geven
    aanvallers veel nuttige informatie over uw server. Verwijder zulke
    bestanden altijd na gebruik.

### Meer informatie

- <a href="http://us2.php.net/configuration.changes" class="external text"
  target="_blank" rel="nofollow noreferrer noopener">Officiële PHP
  handleiding: Hoe configuratie-instellingen te wijzigen</a>
- <a href="http://us2.php.net/manual/en/ini.php#ini.list"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">Officiële PHP handleiding: Lijst met
  PHP INI richtlijnen</a>
