<!--
{
    "source": "https://docs.joomla.org/J4.x:Setting_Up_Your_Local_Environment",
    "title": "Lokale ontwikkelomgeving instellen",
    "description": " ",
    "author": ""
}
-->

Sinds Joomla! 4 hebben we het ontwikkelproces gewijzigd. Het is niet langer
mogelijk om de repository te klonen en een bruikbare Joomla-installatie te
hebben.
We volgen best practices en implementeren een buildproces voor het CMS.

## Snelstartgids

De stappen voor het instellen van uw ontwikkelomgeving zijn afhankelijk van uw
besturingssysteem. We kunnen geen documentatie voor elk besturingssysteem (OS)
schrijven. Gebruik daarom uw favoriete zoekmachine om een handleiding te
vinden.

### Benodigde tools

1.  PHP - in principe hetzelfde als wat u nodig hebt om een Joomla-site te draaien, maar
    u hebt de PHP CLI-versie (command-line-interface) nodig. (Zie
    de pagina [Een LAMPP-server configureren voor PHP-ontwikkeling](https://docs.joomla.org/Special:MyLanguage/Configuring_a_LAMPP_server_for_PHP_development "Special:MyLanguage/Configuring a LAMPP server for PHP development").)
2.  Composer - voor het beheren van Joomla's PHP-afhankelijkheden. Raadpleeg voor hulp
    bij het installeren van Composer de documentatie
    op <a href="https://getcomposer.org/doc/00-intro.md" class="external free"
    target="_blank"
    rel="nofollow noreferrer noopener">https://getcomposer.org/doc/00-intro.md</a>.
3.  Node.js - voor het compileren van Joomla's JavaScript- en SASS-bestanden. Volg voor hulp bij
    het installeren van Node.js de instructies op
    <a href="https://nodejs.org/en/" class="external free" target="_blank"
    rel="nofollow noreferrer noopener">https://nodejs.org/en/</a>. Let op,
    u hebt NodeJS 12 of hoger nodig om Joomla te installeren.
4.  Git - voor versiebeheer.

### Stappen voor het instellen van de lokale omgeving

1.  Kloon de repository
2.  Check de branch van de nieuwste release uit.
3.  Voer `composer install` uit (composer = pakketbeheerder voor PHP) vanuit de
    hoofdmap van de git-repository. (Je kunt *--ignore-platform-reqs* toevoegen als je
    PHP-LDAP lokaal niet hebt geïnstalleerd en je dit niet nodig hebt.)
4.  Voer `npm ci` uit (npm = pakketbeheerder voor JavaScript, de parameter "ci"
    betekent "schone installatie") vanuit de hoofdmap van de git-repository.
    (Let op: hiervoor heb je npm 10.1.0 of hoger nodig.
    Voer `npm install -g npm@lts` uit om je versie van npm bij te werken naar de
    LTS-versie.)

Gebruikers van Linux en OSX kunnen de volgende bash-alias instellen door het volgende in het *~/.bashrc-bestand* te plaatsen:

```
    alias jclean="rm -rf administrator/templates/atum/css; \
    rm -rf templates/cassiopeia/css; \
    rm -rf administrator/templates/system/css; \
    rm -rf templates/system/css; \
    rm -rf media/; \
    rm -rf node_modules/; \
    rm -rf libraries/vendor/; \
    rm -f administrator/cache/autoload_psr4.php; \
    rm -rf installation/template/css"
    alias jinstall="jclean; composer install; npm ci"
```

Hiermee worden alle gecompileerde bestanden op je systeem verwijderd en wordt een
schone installatie uitgevoerd met één opdracht door `jinstall` binnen je Joomla-installatie aan te roepen.

## Iets uitgebreidere startgids

Joomla lijkt tegenwoordig op veel andere webtools. Het bevat een groot PHP-
gedeelte en steeds meer JavaScript-code. Hoewel PHP-programmeren niet veel
voorbereiding vereist, heeft JavaScript veel tooling eromheen nodig. De
belangrijkste reden is dat niemand code schrijft op een manier die elke
browser begrijpt. Daarom moet de code bijvoorbeeld van ES6 worden
getranspileerd naar een compatibele versie van JavaScript. Hetzelfde geldt
voor CSS. Voor Joomla gebruiken we SASS, dat wordt omgezet naar native CSS
zodat elke browser het begrijpt. Het nadeel is dat het instellen van een
ontwikkelomgeving iets ingewikkelder is, maar de tooling maakt het coderen
gemakkelijker. Dankzij watchers en het automatisch herladen van de browser
kun je je wijzigingen in realtime zien.

### PHP

Het zou voldoende moeten zijn om `composer install` uit te voeren, omdat hiermee de PHP-afhankelijkheden worden geïnstalleerd die zijn opgeslagen in het bestand *composer.lock*. U kunt dit zo vaak uitvoeren als u wilt. Er worden alleen nieuwe pakketten geïnstalleerd wanneer het bestand *composer.lock* is gewijzigd. Voer `composer update` niet uit, omdat hiermee alle pakketten naar nieuwere versies worden bijgewerkt en het bestand *composer.lock* wordt bijgewerkt.

**Opmerking:** Mogelijk moet u `composer install` uitvoeren met de optie `--ignore-platform-reqs` om de in Composer opgegeven platformvereisten te negeren. Dat is bijvoorbeeld het geval als de LDAP-extensie van PHP niet is geïnstalleerd.

### Node/npm-scripts

Node.js wordt geleverd met een pakketbeheerder genaamd NPM (in sommige opzichten hetzelfde als Composer). NPM heeft een opdracht `run` en we hebben enkele scripts voorbereid om uw leven gemakkelijker te maken. U moet de opdrachten uitvoeren vanuit de hoofdmap van de repository wanneer u JS- of SASS-bestanden hebt gewijzigd. Voorheen moest u eenmaal `npm ci` uitvoeren om de afhankelijkheden te installeren.

#### npm run build:css (tot en met Joomla 6.1)

Hiermee worden SASS-bestanden naar CSS gecompileerd en worden ook de geminificeerde bestanden gemaakt.

#### npm run build:js (tot en met Joomla 6.1)

Hiermee worden de JavaScript-bestanden gecompileerd en getranspileerd naar de juiste indeling
en worden geminificeerde bestanden gemaakt.

#### Gebruik vanaf Joomla 6.2 de volgende opdrachten:

- npm run build -- -n <extension> om een specifieke extensie opnieuw te bouwen 
- voer npm run builders-list uit om de naam van de extensie te vinden
- npm run build -- --all om alles opnieuw te bouwen

## Mogelijke problemen

Bij het uitvoeren van `composer install` kunt u deze fouten tegenkomen

```
    Problem 1
        - Installation request for joomla/ldap 2.0.0-beta -> satisfiable by joomla/ldap[2.0.0-beta].
        - joomla/ldap 2.0.0-beta requires ext-ldap * -> the requested PHP extension ldap is missing from your system.
    Problem 2
        - Installation request for symfony/ldap v5.1.5 -> satisfiable by symfony/ldap[v5.1.5].
        - symfony/ldap v5.1.5 requires ext-ldap * -> the requested PHP extension ldap is missing from your system.
```

De oplossing is om `composer install` uit te voeren met de
optie `--ignore-platform-reqs` om de platformvereisten
die in Composer zijn opgegeven te negeren. Dat wil zeggen, als u de PHP-extensie
LDAP niet hebt geïnstalleerd.

```
    composer install --ignore-platform-reqs
```

Als u een aanmeldingsfout ontvangt zoals hieronder wordt weergegeven, verwijdert u
het bestand `administrator/cache/autoload_psr4.php`.

![aanmeldingsfoutscherm van Joomla 4](../../../en/images/hosting-local/local-environment-setup/01-joomla-4-login-error-screen.png)

*Vertaald door openai.com*