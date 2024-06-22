<!-- Filename: J4.x:Optional_Technical_Requirements / Display title: Optionele technische vereisten -->

## Optionele eisen voor Joomla! 4.x

Deze pagina geeft een lijst met *optionele* technische vereisten, welke
niet verplicht zijn om te installeren en Joomla te gebruiken maar zijn
vereist voor sommige interne API's.

|                             |                                                                                                                                                       |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Toepassing**              |                                                                                                                                                       |
| JApplicationDaemon          | Vereist PHP's `ext/pcntl` en `ext/posix`                                                                                                              |
| **Archief**                 |                                                                                                                                                       |
| BZ2                         | Vereist PHP's `ext/bz2`                                                                                                                               |
| GZip                        | Vereist PHP's `ext/zlib`                                                                                                                              |
| Zip                         | Vereist PHP's `ext/zip` of `ext/zlib`                                                                                                                 |
| **Cache**                   |                                                                                                                                                       |
| APC                         | Vereist PHP's `ext/apc` op PHP 5.3 of 5.4, `ext/apcu` op PHP 5.5 of 5.6, niet ondersteund op PHP 7.x (Let op: DIT MOET GECONTROLEERD WORDEN)          |
| APCu                        | Vereist PHP's ext/apcu op PHP 5.3+                                                                                                                    |
| CacheLite                   | Vereist het PEAR Cache_Lite pakket (getest op 1.7.16, werkt met 1.8)                                                                                  |
| Memcache                    | Vereist PHP's `ext/memcache` en een Memcache-server (Let op: De Memcache extensie is niet compatible met PHP 7.x)                                     |
| Memcached                   | Vereist PHP's `ext/memcached` en een Memcached server                                                                                                 |
| Redis                       | Vereist PHP's `ext/redis` en een Redis server                                                                                                         |
| Wincache                    | Vereist PHP `ext/wincache` (alleen voor Windows)                                                                                                      |
| XCache                      | Vereist PHP `ext/xcache`                                                                                                                              |
| **Client adapters**         |                                                                                                                                                       |
| LDAP                        | Vereist PHP's `ext/ldap`                                                                                                                              |
| HTTP/Curl                   | Vereist PHP's `ext/curl`                                                                                                                              |
| HTTP/Socket                 | Vereist dat PHP's `fsockopen()` functie geactiveerd is                                                                                                |
| HTTP/Stream                 | Vereist PHP's `fopen()` functie en `allow_url_fopen` geactiveerd                                                                                      |
| **Cryptography**            |                                                                                                                                                       |
| JCrypt                      | Vereist PHP's `ext/mcrypt` voor alle ciphers uitgezonderd de SodiumCipher die `ext/sodium` vereist                                                    |
| JKeychain                   | Vereist PHP's `ext/openssl`                                                                                                                           |
| **Database**                |                                                                                                                                                       |
| Microsoft SQL Azure         | Vereist PHP's `ext/sqlsrv` (de PHP 5.x extensie ondersteund alleen Windows, een Linux compatibele versie van de extensie is beschikbaar voor PHP 7.x) |
| Microsoft SQL Server        | Vereist PHP's `ext/sqlsrv` (de PHP 5.x extensie ondersteund alleen Windows, een Linux compatibele versie van de extensie is beschikbaar voor PHP 7.x) |
| MySQL                       | Vereist PHP's `ext/mysql` (niet ondersteund op PHP 7.x)                                                                                               |
| MySQLi                      | Vereist PHP's `ext/mysqli`                                                                                                                            |
| Oracle                      | Vereist PHP's `ext/pdo` met Oracle ondersteuning (alleen beschikbaar voor 3PD; het CMS draait er niet mee)                                            |
| PDO MySQL                   | Vereist PHP's `ext/pdo` met MySQL ondersteuning                                                                                                       |
| PostgreSQL                  | Vereist PHP's `ext/xcache`                                                                                                                            |
| SQLite                      | Vereist PHP's `ext/pdo` met SQLite ondersteuning (alleen beschikbaar voor 3PD; het CMS draait er niet mee)                                            |
| **Afbeelding**              |                                                                                                                                                       |
|                             | Vereist PHP's `ext/gd`                                                                                                                                |
|                             | Vereist PHP's `ext/fileinfo`                                                                                                                          |
| **Sessie**                  |                                                                                                                                                       |
| APC                         | Vereist PHP's `ext/apc` op PHP 5.3 of 5.4, `ext/apcu` op PHP 5.5 of 5.6, niet ondersteund op PHP 7.x (Let op: DIT MOET GECONTROLEERD WORDEN)          |
| Memcache                    | Vereist PHP's `ext/memcache` en een Memcache-server (Let op: De Memcache extensie is niet compatible met PHP 7.x)                                     |
| Memcached                   | Vereist PHP's `ext/memcached` en een Memcached server                                                                                                 |
| Wincache                    | Vereist PHP `ext/wincache` (alleen voor Windows)                                                                                                      |
| XCache                      | Vereist PHP `ext/xcache`                                                                                                                              |
| **OPTIONELE VERBETERINGEN** |                                                                                                                                                       |
| **String**                  |                                                                                                                                                       |
| mbstring                    | Activeer PHP's `ext/mbstring` voor de phputf8 library om de native functies te gebruiken                                                              |
