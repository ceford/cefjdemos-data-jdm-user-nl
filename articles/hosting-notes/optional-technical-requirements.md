<!-- Filename: J4.x:Optional_Technical_Requirements / Display title: Optionele Technische Vereisten -->

Deze pagina somt *optionele* technische vereisten op die niet nodig zijn
om Joomla! te installeren en draaien, maar die vereist zijn voor sommige interne API's. De lijst
werd gemaakt voor Joomla 4.

| Item                     | Beschrijving                                                                                                                                    |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| **Applicatie**           |                                                                                                                                                 |
| JApplicationDaemon       | Vereist PHP's `ext/pcntl` en `ext/posix`                                                                                                        |
| **Archief**              |                                                                                                                                                 |
| BZ2                      | Vereist PHP's `ext/bz2`                                                                                                                         |
| GZip                     | Vereist PHP's `ext/zlib`                                                                                                                        |
| Zip                      | Vereist PHP's `ext/zip` of `ext/zlib`                                                                                                           |
| **Cache**                |                                                                                                                                                 |
| APC                      | Vereist PHP's `ext/apc` op PHP 5.3 of 5.4, `ext/apcu` op PHP 5.5 of 5.6, niet ondersteund op PHP 7.x (Opmerking: DIT MOET WORDEN GECONTROLEERD) |
| APCu                     | Vereist PHP's `ext/apcu` op PHP 5.3+                                                                                                            |
| CacheLite                | Vereist de PEAR Cache_Lite-pakket (getest op 1.7.16, zal werken met 1.8)                                                                        |
| Memcache                 | Vereist PHP's `ext/memcache` en een Memcache-server (Opmerking: De Memcache-extensie is niet compatibel met PHP 7.x)                            |
| Memcached                | Vereist PHP's `ext/memcached` en een Memcached-server                                                                                          |
| Redis                    | Vereist PHP's `ext/redis` en een Redis-server                                                                                                  |
| Wincache                 | Vereist PHP's `ext/wincache` (alleen Windows)                                                                                                  |
| XCache                   | Vereist PHP's `ext/xcache`                                                                                                                     |
| **Client-adapters**      |                                                                                                                                                 |
| LDAP                     | Vereist PHP's `ext/ldap`                                                                                                                        |
| HTTP/Curl                | Vereist PHP's `ext/curl`                                                                                                                        |
| HTTP/Socket              | Vereist dat PHP's `fsockopen()`-functie is ingeschakeld                                                                                         |
| HTTP/Stream              | Vereist dat PHP's `fopen()`-functie en `allow_url_fopen` zijn ingeschakeld                                                                      |
| **Cryptografie**         |                                                                                                                                                 |
| JCrypt                   | Vereist PHP's `ext/mcrypt` voor alle ciphers behalve de SodiumCipher die `ext/sodium` vereist                                                   |
| JKeychain                | Vereist PHP's `ext/openssl`                                                                                                                     |
| **Database**             |                                                                                                                                                 |
| Microsoft SQL Azure      | Vereist PHP's `ext/sqlsrv` (de PHP 5.x extensie ondersteunt alleen Windows, een Linux-compatibele versie van de extensie is beschikbaar voor PHP 7.x) |
| Microsoft SQL Server     | Vereist PHP's `ext/sqlsrv` (de PHP 5.x extensie ondersteunt alleen Windows, een Linux-compatibele versie van de extensie is beschikbaar voor PHP 7.x) |
| MySQL                    | Vereist PHP's `ext/mysql` (niet ondersteund op PHP 7.x)                                                                                         |
| MySQLi                   | Vereist PHP's `ext/mysqli`                                                                                                                      |
| Oracle                   | Vereist PHP's `ext/pdo` met Oracle-ondersteuning (alleen beschikbaar voor 3PD; de CMS zal hier niet mee draaien)                                |
| PDO MySQL                | Vereist PHP's `ext/pdo` met MySQL-ondersteuning                                                                                                |
| PostgreSQL               | Vereist PHP's `ext/pgsql`                                                                                                                       |
| SQLite                   | Vereist PHP's `ext/pdo` met SQLite-ondersteuning (alleen beschikbaar voor 3PD; de CMS zal hier niet mee draaien)                               |
| **Afbeelding**           |                                                                                                                                                 |
|                          | Vereist PHP's `ext/gd`                                                                                                                          |
|                          | Vereist PHP's `ext/fileinfo`                                                                                                                    |
| **Sessie**               |                                                                                                                                                 |
| APC                      | Vereist PHP's `ext/apc` op PHP 5.3 of 5.4, `ext/apcu` op PHP 5.5 of 5.6, niet ondersteund op PHP 7.x (Opmerking: DIT MOET WORDEN GECONTROLEERD)  |
| Memcache                 | Vereist PHP's `ext/memcache` en een Memcache-server (Opmerking: De Memcache-extensie is niet compatibel met PHP 7.x)                            |
| Memcached                | Vereist PHP's `ext/memcached` en een Memcached-server                                                                                          |
| Wincache                 | Vereist PHP's `ext/wincache` (alleen Windows)                                                                                                   |
| XCache                   | Vereist PHP's `ext/xcache`                                                                                                                      |
| **OPTIONELE VERBETERINGEN** |                                                                                                                                             |
| **String**               |                                                                                                                                                 |
| mbstring                 | Schakel PHP's `ext/mbstring` in voor de phputf8-bibliotheek om native functies te gebruiken                                                     |

*Vertaald door openai.com*

