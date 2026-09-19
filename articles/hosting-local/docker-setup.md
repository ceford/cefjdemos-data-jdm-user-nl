<!--
{
    "source": "https://docs.joomla.org/https:",
    "title": "Docker instellen",
    "description": " ",
    "author": ""
}
-->

## Een lokale Joomla-omgeving instellen met Docker

Om Joomla op je computer te laten werken, zijn er vier dingen nodig: 
- een webserver **Apache** of **nginx** downloaden en configureren, 
- een databaseservice zoals **MySQL of** **MariaDB**, 
- en natuurlijk hebben we **PHP** nodig 
- en **Joomla.** 

Om al deze verschillende onderdelen daadwerkelijk met elkaar te laten communiceren, vertrouwen de meesten van ons op gebundelde software zoals **XAMPP**, **Laragon** of **FlyEnv**.

Traditionele configuraties kunnen echter gemakkelijk leiden tot poortconflicten of databaseservers die om onverklaarbare redenen weigeren te starten. Wanneer een lokale server crasht, kan het zijn dat je Joomla-sites steeds opnieuw handmatig moet downloaden en installeren, alleen maar om één PR te testen, waarbij je mogelijk je werk verliest tijdens het oplossen van een bug. Het kost waardevolle tijd en de oplossingen zijn meestal slechts tijdelijke lapmiddelen.

**De overstap naar Docker ([Meer informatie over Docker](https://docs.docker.com/get-started/))** 
Met Docker kun je
sla de handmatige configuratie volledig over. In plaats van webservers rechtstreeks op je computer te installeren, schrijf je gewoon één enkel ‘receptbestand’. Docker downloadt, isoleert en verbindt alles automatisch op de achtergrond. Als er iets misgaat, hoef je je hele installatie niet opnieuw te installeren; je start de container gewoon opnieuw.

In deze handleiding leer je de eenvoudigste manier om een lokale Joomla-omgeving met Docker op te zetten, zodat je minder tijd kwijt bent aan het repareren van servers en meer tijd kunt besteden aan bijdragen.

### Vereisten

Je hoeft maar één ding te installeren voordat we beginnen: **Docker Desktop**.

- Download het via [**docker.com**](https://www.docker.com/) en voer het
  installatieprogramma uit
- Laat op Windows de optie "Use WSL 2 instead of Hyper-V" ingeschakeld -
  dit maakt alles sneller
- Open Docker Desktop en wacht totdat linksonder de groene status
  **Engine running** wordt weergegeven.

![Docker Desktop](../../../en/images/hosting-local/docker-setup/01-docker-setup-desktop.png)

Dat is alles.

### Het bestand docker-compose.yml

Wanneer u meerdere services met elkaar moet laten communiceren, zoals een webserver
(Apache/Nginx), PHP en een database (MySQL/MariaDB), gebruikt u een speciaal
orkestratiebestand met de naam `docker-compose.yml`. Dit bestand fungeert als
blauwdruk voor uw project en definieert alle benodigde services en hoe deze
samenwerken. (De officiële Docker Joomla-image is in feite boven op een PHP- en
Apache-image gebouwd. Dit betekent dat u door alleen deze ene Joomla-image te
gebruiken, PHP, Apache en Joomla allemaal gebundeld krijgt).

Maak eerst een nieuwe map op uw computer voor uw project (maak bijvoorbeeld op
uw bureaublad een map met de naam `joomla-docker`).

Maak in die map een nieuw tekstbestand en geef het exact deze naam:

    docker-compose.yml

Open dat bestand in een teksteditor naar keuze (zoals VS Code of Kladblok),
plak de volgende code er exact in zoals deze is en sla het bestand op:

```
    services:
      joomla:
        image: joomla:latest
        ports:
          - "8080:80"
        environment:
          - JOOMLA_DB_HOST=db
          - JOOMLA_DB_USER=joomla
          - JOOMLA_DB_PASSWORD=joomlapass
          - JOOMLA_DB_NAME=joomladb
        depends_on:
          - db
      db:
        image: mariadb:10.11
        environment:
          - MYSQL_ROOT_PASSWORD=rootpass
          - MYSQL_DATABASE=joomladb
          - MYSQL_USER=joomla
          - MYSQL_PASSWORD=joomlapass
        volumes:
          - db_data:/var/lib/mysql
    volumes:
      db_data:
```

### De omgeving starten

Open je terminal (of PowerShell op Windows), ga naar je map `joomla-docker`
en voer het volgende uit:

```
    docker compose up -d
```

De eerste keer dat je dit uitvoert, downloadt Docker de Joomla- en MariaDB-
images. Dit kan, afhankelijk van je internetsnelheid, een minuut of twee duren.
Daarna duurt elke volgende start vrijwel direct, zoals je hieronder kunt zien.

![Uitvoer van docker start in de terminal](../../../en/images/hosting-local/docker-setup/02-docker-setup-terminal-transcript.png)

### Het Joomla-installatieprogramma

Open je browser en ga naar `http://localhost:8080`. Je zou het
Joomla-installatiescherm moeten zien.

![Joomla-installatie: sitenaam instellen](../../../en/images/hosting-local/docker-setup/03-docker-setup-joomla-installer-sitename.png)

Vul op het eerste scherm de naam van je site en de beheerdersgegevens in.

![Joomla-installatie: inloggegevens](../../../en/images/hosting-local/docker-setup/04-docker-setup-joomla-installer-login-data.png)

Wanneer je het scherm **Databaseconfiguratie** bereikt, lopen de meeste
mensen hier vast:

**Typ niet `localhost` als hostnaam.**

Omdat de database in een eigen container draait, heeft Joomla de servicenaam
van de container nodig — niet localhost. Gebruik deze exacte waarden:

- **Databasetype:** MySQLi
- **Hostnaam:** `db`
- **Gebruikersnaam:** `joomla`
- **Wachtwoord:** `joomlapass`
- **Databasenaam:** `joomladb`

![Joomla-installatie: database instellen](../../../en/images/hosting-local/docker-setup/05-docker-setup-joomla-installer-database-config.png)

Klik door, voltooi de installatie en je bent klaar.

Wanneer je klaar bent met werken voor vandaag, voer je `docker compose stop` uit om te
pauzeer de containers en maak geheugen vrij. Je site zal de volgende keer
precies zijn waar je hem hebt achtergelaten.

------------------------------------------------------------------------

### Veelvoorkomende problemen

- **De pagina op localhost:8080 wordt direct na het starten niet geladen:** De
  databasecontainer heeft enkele seconden nodig om de initialisatie te voltooien. Wacht 30
  seconden en vernieuw de pagina.
- **Poort 8080 is al in gebruik:** Wijzig `"8080:80"` in `"8081:80"` in
  het composebestand en open de site via `localhost:8081`.
- **De containers zijn gestart, maar Joomla geeft een databasefout weer:** Controleer nogmaals
  of de Host Name in het installatieprogramma `db` is en niet `localhost`.

### Pro-tip: Toegang tot de Joomla-bestanden voor ontwikkeling

Op dit moment draait je Joomla-site, maar de daadwerkelijke PHP-bestanden
zijn verborgen in de Docker-container. Als je wilt bijdragen aan Joomla,
PR's wilt testen of je eigen plug-ins wilt schrijven, heb je die bestanden
op je computer nodig, zodat je ze kunt openen in VS Code of je favoriete editor.

Om de bestanden van de container naar je lokale harde schijf te synchroniseren, hoef je alleen
twee regels (`volumes: `) en (`- ./site_joomla:/var/www/html`)
toe te voegen aan het gedeelte `joomla` van je bestand `docker-compose.yml`, zoals hieronder weergegeven:

```yml
services:
  joomla:
    image: joomla:latest
    ports:
      - "8080:80"
    volumes:
      - ./site_joomla:/var/www/html
    # ... (rest of your settings)
```

**Wat dit doet:** 

De volgende keer dat je `docker compose up -d` uitvoert, maakt Docker automatisch
een map met de naam `site_joomla` aan naast je compose-bestand. De map
bevat de volledige Joomla-core (inclusief het beheerdersdashboard,
componenten en templates).

![IDE-verkenner van Joomla-installatie in Docker](../../../en/images/hosting-local/docker-setup/06-docker-setup-ide-explorer.png)

Elke codewijziging die je in die map op je computer aanbrengt, wordt onmiddellijk bijgewerkt in de actieve container! Je bent nu volledig ingesteld voor lokale ontwikkeling.

### Bonustip 1: Specifieke Joomla- en PHP-versies testen

Bij het testen van PR's zullen maintainers je vaak vragen om te testen met
specifieke PHP-versies. Met XAMPP is het downgraden of upgraden van PHP een
nachtmerrie. Met Docker duurt het twee seconden.

In plaats van `image: `**`joomla:latest`** in je
**`docker-compose.yml`** te gebruiken, kun je exacte versies opgeven met tags. Als
je bijvoorbeeld **Joomla 5.2** op **PHP 8.3** moet testen, wijzig je die ene
regel in: **`image: joomla:5.2-php8.3-apache`**

Voer **`docker compose up -d`** opnieuw uit en Docker vervangt je
serveromgeving onmiddellijk. Je vindt alle beschikbare versietags op de
<a href="https://hub.docker.com/_/joomla" class="ng-star-inserted"
target="_blank" rel="noopener" data-hveid="0"
data-ved="0CAAQ_4QMahgKEwjl8vi347CTAxUAAAAAHQAAAAAQkgI">officiële Joomla
Docker Hub-pagina</a>.

### Bonustip 2: phpMyAdmin toevoegen

Als u van **XAMPP** komt, mist u misschien een visuele interface om uw
database te bekijken. U kunt eenvoudig **phpMyAdmin** aan uw configuratie
toevoegen door een nieuw **serviceblok** onderaan uw
**`docker-compose.yml`**-bestand toe te voegen:

```yml
    phpmyadmin:
        image: phpmyadmin/phpmyadmin:latest
        ports:
          - "8081:80"
        environment:
          - PMA_HOST=db
        depends_on:
          - db
```

Start uw containers opnieuw op en u kunt phpMyAdmin nu openen door in uw
browser naar **http://localhost:8081** te gaan. Log gewoon in met **`joomla`**
als gebruikersnaam en **`joomlapass`** als wachtwoord.

*Vertaald door openai.com*