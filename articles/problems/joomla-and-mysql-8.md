<!-- Filename: Joomla_and_MySQL_8 / Display title: Joomla and MySQL 8 -->

## MySQL default authentication plugin issue

It is possible to connect to a MySQL 8 Database using Joomla
<img src="https://docs.joomla.org/images/4/4d/Compat_icon_3_x.png"
decoding="async" data-file-width="40" data-file-height="17" width="40"
height="17" alt="Joomla 3.x" />, however it requires a customisation on
the MySQL 8 installation configuration. The reason is that MySQL 8 has a
lot of low-level changes including the default authentication plugin
changing to `sha256_password` from `mysql_native_password`. The native
PHP MySQL-Driver doesn't currently support MySQL 8 with this plugin. <a
href="https://github.com/php/php-src/commit/d6e81f0bfd0cb90586dd83d4fd47a4302605261a"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">PHP 7.3 (alpha)</a> is supporting
MySQL 8 though.

## MySQL configuration change to get Joomla working with MySQL 8

If you edit the configuration file for MySQL 8, you can change the
default authentication plugin for MySQL to use the older
mysql_native_password. Open your configuration file
`sudo nano /etc/my.cnf` (Please note that your file may be under a
different directory) and add the following configuration:

    [mysqld]
    default-authentication-plugin=mysql_native_password

If you don't have access to your config file then you can update your
user as follows:

    ALTER USER 'username'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

Vervang gebruikersnaam door de naam van het gebruikersaccount en
wachtwoord door het wachtwoord dat bij het account hoort. Start MySQL
opnieuw op en je bent klaar ... nou ja, alleen als Joomla 3.8 of 3.9 is
geïnstalleerd.

## How MySQL default authentication plugin works

Het voordeel van`mysql_native_password`is dat het het
challenge-response-mechanisme ondersteunt dat erg snel is en geen
gecodeerde verbinding vereist. ` mysql_native_password ` is echter
afhankelijk van het SHA1-algoritme en NIST heeft aanbevolen het gebruik
te stoppen.

Verder, als twee gebruikers hetzelfde wachtwoord
gebruiken,`mysql_native_password`transformatie is hetzelfde in de
mysql.user table. Hoewel de hash geen informatie laat zien van het
huidige wachtwoord, het zegt wel welke twee gebruikers hetzelfde
wachtwoord gebruiken. Om dat te voorkomen moet een salt gebruikt worden.
Een salt is in feite een willekeurig getal dat wordt gebruikt als een
van de parameters voor cryptografische hashfuncties die worden gebruikt
om gebruikerswachtwoorden te transformeren. Aangezien een salt
willekeurig en verschillend is voor elke uitvoering, zelfs als twee
gebruikers dezelfde wachtwoorden gebruiken, zou het eindresultaat van de
transformatie er heel anders uitzien. Since MySQL 5.6, sha256_password
authentication plugin is supported. It uses multiple rounds of SHA256
hash on a salted password to make sure that the hash transformation is
more secure. However, it requires either encrypted connections or
support for an RSA key pair. So, while password security is stronger,
secure connections and multiple rounds of hash transformations require
more time in the authentication process.

caching_sha2_password tries to combine the best of both worlds.
<sup>[\[1\]](#cite_note-1)</sup>

1.  <span id="cite_note-1">[↑](#cite_ref-1) <a
    href="https://mysqlserverteam.com/mysql-8-0-4-new-default-authentication-plugin-caching_sha2_password/"
    class="external free" target="_blank"
    rel="nofollow noreferrer noopener">https://mysqlserverteam.com/mysql-8-0-4-new-default-authentication-plugin-caching_sha2_password/</a></span>
