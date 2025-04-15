<!-- Filename: J4.x:Global_Configuration / Display title: Globale Configuratie -->

## Overzicht

Tijdens de installatie creëert een Joomla-site een bestand genaamd **configuration.php** in de root van de site. Dit bestand bevat de waarden van configuratievariabelen die van toepassing zijn op de gehele site. Voorbeelden hiervan zijn de sitenaam en database-gegevens die tijdens het installatieproces zijn ingevoerd. Er zijn nog veel meer variabelen die geschikte initiële waarden krijgen.

Het formulier voor de Globale Configuratie stelt een Supergebruiker in staat om de configuratievariabelen aan te passen aan de behoeften van de site. Naast de variabelen die zijn opgeslagen in configuration.php, houdt het formulier ook informatie bij over Logging, Filtering en Toegangscontrole, waarvan een deel in de database is opgeslagen.

## Screenshot

Het formulier voor de globale configuratie heeft zes tabbladen, waarvan sommige lange lijsten met parameters hebben. Gebruik de *Inline Help Wisselen* knop in de werkbalk om meer of minder informatie over elke parameter te zien.

![Globale configuratie site-tabblad](../../../en/images/configuration/global-configuration-site-tab.png)

Sommige parameters tonen of verbergen andere parameters wanneer ze geselecteerd worden. Bijvoorbeeld, de **Site Offline** knop toont meer velden wanneer deze op *Ja* is ingesteld dan wanneer deze op *Nee* staat. Met uitgebreide inline help zijn de meeste velden voldoende gedocumenteerd om hier geen verdere uitleg te behoeven, afgezien van enkele aanvullende gebruikersopmerkingen op elk tabblad.

## Site-tabblad

### Sitepaneel

- **Sitenaam** Dit is de naam van de site die verschijnt in het inlogformulier voor beheerders en in de link naar de site in de titelbalk. Pas het aan indien nodig.
- **Site offline** Er is een aparte [handleiding](jdocmanual?article=user/configuration/site-offline) voor dit item.
- **Standaard lijstlimiet** stelt het standaard maximumaantal items per pagina in in lijstweergaven. Standaard is deze parameter ingesteld op 20, maar lijstweergaven bevatten meestal een keuzelijst om andere waarden te selecteren, variërend van 5 tot 100. Minder waarden zijn sneller te verwerken en vereisen minder scrollen door de gebruiker.

### Metadatapaneel

- **Metadata beschrijving van de site** Dit is de standaard metadatabeschrijving die wordt gebruikt als een dergelijke beschrijving niet is gespecificeerd in een artikelvelden voor metadescriptie of een menu metadescriptieveld. Als alle drie leeg zijn, wordt de metadatabeschrijving weggelaten uit de pagina-uitvoer. Zoekmachines gebruiken dit vaak om descriptive text voor een pagina te geven. Indien afwezig, kunnen zoekmachines tekst uit de inhoud van de pagina gebruiken, wat ongepast kan zijn. Een beschrijving van het doel van de site van ongeveer 20 woorden wordt aanbevolen.
- **Inhoudsrechten** stelt de *rechten* metadatainvoer in. Beschrijf hier indien van toepassing welke rechten anderen hebben om deze inhoud te gebruiken. Deze metadatainvoer wordt weggelaten van webpagina’s als dit veld leeg is. Voorbeeld: Creative Commons Naamsvermelding 4.0 Internationale Licentie (zie de [Creative Commons Licentie Kiezer](https://creativecommons.org/choose/)).

### SEO-paneel

SEO is een acroniem voor *Search Engine Optimization*. Instellingen in deze groep wijzigen het formaat van URL’s voor pagina’s op de website en dit kan een aanzienlijk effect hebben op de zoekresultaten van individuele pagina’s en de site als geheel. SEO-URL’s zijn beter leesbaar voor mensen.

**Tip** Na het aanbrengen van wijzigingen in de instellingen in deze groep, vernieuw je de al geopende pagina's van de website in je webbrowser (meestal doe je dat met Ctrl+R of Cmd+R). Als je de pagina's niet vernieuwt, kan het betekenen dat het formaat van interne links op de site niet meer overeenkomt met wat Joomla verwacht, met als gevolg dat de links niet meer werken.

**Tip** Vermijd, indien enigszins mogelijk, het wijzigen van de SEO-instellingen zodra een website is gevestigd. Het doen van dergelijke wijzigingen kan leiden tot verbroken links van andere sites en mogelijk tot een tijdelijke daling in zoekmachinerangschikking.

- **Unicode aliassen** Het wijzigen van deze parameter wijzigt niet met terugwerkende kracht aliassen, het verandert alleen het gedrag van automatische aliastoewijzing voor toekomstige inhoudsbewerking en -creatie. *Transliteratie* (Nee) is de standaardinstelling.

### Cookiepaneel

- **Cookie-domein** Overschrijft het standaard cookie-domein van de site met het hier toegevoegde domein. De meest waarschijnlijke situatie waarin dit nodig is, is wanneer de Joomla-site wordt “overbrugd“ met andere sites (bijv. forum of e-commerce) in subdomeinen van de Joomla-site. Het standaard cookie-domein kan `www.example.com` zijn, maar door `.example.com` (let op de leidende punt) hier te gebruiken, worden cookies geleverd die geldig zijn voor elk subdomein van example.com.
- **Cookiepad** Overschrijft het standaardpad van de site waarvoor de cookie geldig is met het hier toegevoegde pad. Dit kan nodig zijn als je meerdere Joomla-installaties hebt in gelijkwaardige mappen.

## Systeem tabblad

![Globale configuratie systeem tabblad](../../../en/images/configuration/global-configuration-system-tab.png)

### Debug paneel

De items in dit paneel worden goed uitgelegd door de inline hulp. Als je echter een probleem tegenkomt dat normale toegang tot de Beheerder-interface uitschakelt, moet je mogelijk Debug Systeem instellen door met een teksteditor configuration.php te bewerken. Op de meeste Linux-gebaseerde hostingsystemen zijn de bestandsrechten ingesteld op 444, wat opslaan vanuit een teksteditor verhindert. Verander het recht naar 644 vóór het bewerken. Stel vervolgens \$debug = `true`; en stel \$error_reporting = `'maximum'`; in en sla op. Je zou dan een stack trace moeten krijgen die precies aangeeft waar het probleem zich voordoet. Daarmee kun je hulp zoeken op de Forums. De meeste problemen ontstaan door incompatibele extensies van derden of door problemen met de hostingomgeving.

## Server-tabblad

![Globale configuratie server-tabblad](../../../en/images/configuration/global-configuration-server-tab.png)

### E-mailpaneel

Een Joomla-site moet in staat zijn om uitgaande e-mails te versturen. Onder andere worden er automatische berichten gestuurd naar de eigenaar van de site wanneer er updates beschikbaar zijn. Sommige hostingdiensten beperken echter de methoden waarmee uitgaande e-mail verzonden mag worden.

#### Testmail verzenden

Voor Joomla 5.3 stuurde de knop **Verstuur testmail** een bericht naar het adres dat was ingesteld in het veld **Van e-mailadres**. Sinds versie 5.3 wordt de testmail rechtstreeks verzonden naar het e-mailadres van de ingelogde beheerder.

- Probeer eerst PHP Mail en selecteer de knop *Stuur Testmail*. Als de
  e-mail aankomt, ben je klaar om te gaan. Zo niet:
- Probeer de Sendmail-optie. Als ook dat niet werkt:
- Probeer de SMTP-optie. Dit moet worden ingesteld voor een specifieke mailserver. Het kan er een zijn die door je hostingdienst wordt aangeboden. Het kan een GMail-account zijn.
- **SMTP-host** De hostnaam van de SMTP-server (bijv.
  *smtp.example.com*).
  - **SMTP-poort** De poort die gebruikt moet worden bij het verbinden met de SMTP-server.
    Dit is meestal *25* wanneer SMTP-beveiliging is ingesteld op *Geen*, of
    *465* of *587* wanneer SMTP-beveiliging is ingesteld op `SSL/TLS` of `STARTTLS`.
    Vraag je SMTP-dienstverlener welke poort te gebruiken.
  - **SMTP-beveiliging** De vorm van beveiliging die vereist is door de SMTP-server:
    *Geen*, *SSL/TLS* of *STARTTLS*. De standaardinstelling is *Geen*.
  - **SMTP-authenticatie** Of de externe SMTP-server authenticatie vereist voordat uitgaande e-mails worden geaccepteerd. De standaardinstelling is *Nee*.
  - **SMTP-gebruikersnaam** De gebruikersnaam die moet worden gebruikt bij het verbinden met de SMTP-server in SSL- of TLS-modus. Dit kan leeg worden gelaten als er geen SMTP-authenticatie is.
  - **SMTP-wachtwoord** Het wachtwoord dat moet worden gebruikt bij het verbinden met de SMTP-server in SSL- of TLS-modus. Dit kan leeg worden gelaten als er geen SMTP-authenticatie is.

### Gmail gebruiken als Mailserver

Als je een werkend Gmail-account hebt, kun je Gmail gebruiken als je mailserver door dit in de globale configuratie in te stellen. Stel het volgende in op het server-tabblad:

- Mailer: SMTP
- SMTP-host: smtp.gmail.com
- SMTP-poort: 465
- SMTP-beveiliging: SSL/TLS
- SMTP-authenticatie: Ja
- Vul de volgende twee regels in met jouw informatie. Je moet een app-specifiek wachtwoord (ASP) gebruiken, zoals hieronder beschreven.
- SMTP-gebruikersnaam: je Gmail-gebruikersnaam
- SMTP-wachtwoord: het app-specifieke wachtwoord (ASP) dat je hebt gegenereerd, zoals hieronder beschreven.

De volgende combinaties werken ook:

- SMTP-poort: 587
- SMTP-beveiliging: STARTTLS
- SMTP-poort: 25
- SMTP-beveiliging: STARTTLS

#### Opmerkingen

- De SSL-module hoeft niet te worden ingeschakeld in Apache.
- De OpenSSL-extensie moet worden ingeschakeld in PHP. De details kunnen worden
  gevonden op de [php.net Installatiepagina](https://www.php.net/manual/en/openssl.installation.php).
- Als je WAMP op Windows gebruikt, is de openssl-module standaard niet ingeschakeld en moet je deze inschakelen. Om dit te doen:
  - Open het php.ini-bestand en haal het puntkomma-; aan het begin van de regel `extension=php_openssl.dll` weg.
  - Sla het php.ini-bestand op en herstart de Apache-service.
- Als je 2-stapsverificatie in Gmail gebruikt, moet je een nieuw wachtwoord toevoegen in Instellingen - Accounts - Accountinstellingen wijzigen - Andere Google-accountinstellingen - Beveiliging - 2-stapsverificatie - Beheer je toepassingsspecifieke wachtwoorden.
- Wanneer het nieuwe Toepassingsspecifieke Wachtwoord (ASP) wordt weergegeven in groepen van vier tekens gescheiden door spaties, zorg ervoor dat je de **spaties NIET invoert** in het SMTP-wachtwoord in de mailserverinstellingen in Joomla.
- Toepassingsspecifieke Wachtwoorden (ASPs): Kijk op de Google Support pagina over hoe je [Inloggen met App Wachtwoorden](https://support.google.com/accounts/answer/185833) kunt gebruiken.
- 2-stapsverificatie: Kijk op de Google Support pagina over hoe je [2-stapsverificatie kunt inschakelen](https://support.google.com/accounts/answer/185839).

## Logboek tabblad

![Tabblad Globale configuratie site](../../../en/images/configuration/global-configuration-logging-tab.png)

Bij normaal gebruik zou een Joomla-site de logboekfunctie uitgeschakeld moeten hebben. Als er problemen zijn, kun je het logboek inschakelen door het veld **Log Almost Everything** op `Ja` te zetten. De optie **Log Deprecated API** is echt alleen voor ontwikkelaars. Het veld **Pad naar Logmap** laat je zien waar je de logbestanden kunt vinden als je logging hebt ingesteld om te helpen bij foutopsporing. De foutrapporten die je daar vindt, zijn alleen diegene die door Joomla worden opgevangen. Er kunnen andere fouten zijn die alleen in de foutlogboeken van je server verschijnen.

## Het Tabblad Tekstfilters

![Tabblad globale configuratiesite](../../../en/images/configuration/global-configuration-filters-tab.png)

De instellingen voor tekstfilters worden toegepast op alle teksteditorvelden die door gebruikers in de geselecteerde groepen worden ingediend. Deze filteropties geven meer controle over de HTML die uw contentproviders indienen. U kunt zo strikt of soepel zijn als nodig is om aan de behoeften van uw site te voldoen. De filtering is opt-in en de standaardinstellingen bieden goede bescherming tegen opmaak die vaak verband houdt met aanvallen op websites.

## Tabblad Machtigingen

![Tabblad globale configuratie site](../../../en/images/configuration/global-configuration-permissions-tab.png)

Machtigingen bepalen wat gebruikers in elke Gebruikersgroep kunnen zien en doen. De
inzendingen in het tabblad Machtigingen stellen de standaardmachtigingen voor de site in.

Er zijn uitgebreide beschrijvingen van het gebruik van de instellingen onder
dit tabblad en de algemene principes van werking en instelling van
machtigingen in een [Toegangscontrollijst Handleiding](jdocmanual?article=user/users/access-control).

*Vertaald door openai.com*

