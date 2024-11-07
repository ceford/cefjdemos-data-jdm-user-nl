<!-- Filename: How_do_you_password_protect_directories_using_htaccess%3F / Display title: Wachtwoord Beveiligen van Mappen -->

## Inleiding

U kunt ervoor kiezen om een directory of een hele site te beschermen tegen openbare toegang. Een reden hiervoor is om openbare toegang tot een ontwikkelingssite te weigeren. Alleen degenen die de gebruikersnaam en het wachtwoord kennen, krijgen toegang. Een andere reden is paranoia - bijvoorbeeld de bescherming van de beheerdersmap zodat gebruikers een gebruikersnaam en wachtwoord moeten invoeren om toegang te krijgen tot het inlogformulier van de Joomla-beheerder.

De hier beschreven methode is voor Apache-servers met behulp van een *.htaccess*-bestand.

### Waarschuwing van Apache.org

Basisverificatie moet niet worden beschouwd als veilig volgens een bijzonder strenge definitie van veiligheid. Hoewel het wachtwoord op de server versleuteld wordt opgeslagen, kan het in platte tekst van de client naar de server via het netwerk worden verzonden. Iedereen die meeluistert met een pakket sniffer van welke aard dan ook, zal de gebruikersnaam en het wachtwoord kunnen lezen zodra ze worden verzonden.

De gebruikersnaam en het wachtwoord worden bij elk verzoek verzonden, niet alleen wanneer de gebruiker ze voor het eerst invoert. Dus de pakket sniffer hoeft niet op een bijzonder strategisch moment te luisteren, maar gewoon lang genoeg om één enkel verzoek over de lijn te zien komen.

Bovendien worden de inhoud zelf ook zonder encryptie over het netwerk verzonden, dus als de website gevoelige informatie bevat, zou dezelfde pakket sniffer toegang tot die informatie hebben, zelfs als de gebruikersnaam en het wachtwoord niet werden gebruikt om directe toegang tot de website te verkrijgen.

Gebruik geen basisverificatie voor iets dat echte beveiliging vereist. Het is een nadeel voor de meeste gebruikers, aangezien zeer weinig mensen de moeite zullen nemen, of de benodigde software of apparatuur hebben, om wachtwoorden te achterhalen. Echter, als iemand de wens had om binnen te komen, zou het voor hen heel weinig moeite kosten.

Basisverificatie via een SSL-verbinding zal echter wel veilig zijn, omdat alles, inclusief de gebruikersnaam en het wachtwoord, versleuteld zal worden verzonden.

## Gebruik van cPanel

Als je een hostingservice gebruikt, dien je de daar geboden methode voor directorybescherming te gebruiken. cPanel heeft bijvoorbeeld een optie genaamd Directory Privacy. Bij selectie kun je naar een directory navigeren en er een naam voor instellen. Vervolgens krijg je de mogelijkheid om een gebruikersnaam en wachtwoord voor de genoemde directory aan te maken. Eenvoudig?

Als je nu in de door jou beschermde directory kijkt, zul je een nieuw .htaccess-bestand vinden dat iets dergelijks bevat om de Joomla api-map te beschermen:

```
#----------------------------------------------------------------cp:ppd
# Sectie beheerd door cPanel: Directorybescherming            -cp:ppd
# - Bewerk dit deel van het htaccess-bestand niet!            -cp:ppd
#----------------------------------------------------------------cp:ppd
AuthType Basic
AuthName "API"
AuthUserFile "/home/gebruikersnaam/.htpasswds/public_html/[jroot]/api/passwd"
Require valid-user
#----------------------------------------------------------------cp:ppd
# Einde sectie beheerd door cPanel: Directorybescherming      -cp:ppd
#----------------------------------------------------------------cp:ppd
```
Het is belangrijk om je ervan bewust te zijn dat cPanel-directorybescherming mogelijk hetzelfde .htaccess-bestand gebruikt dat door Joomla voor andere doeleinden wordt gebruikt.

Als je in het genoemde passwd-bestand kijkt, zul je de door jou opgegeven gebruikersnaam en de versleutelde versie van het wachtwoord zien.

De bescherming kan worden verwijderd door het proces te herhalen en het selectievakje `Directory met wachtwoord beveiligen.` uit te schakelen. Dat verwijdert de authenticatiesectie uit het .htaccess-bestand. Het verwijdert het .htaccess-bestand zelf niet!

## .htaccess Regels

Je kunt alle vereiste stappen handmatig uitvoeren. Deze tool kan helpen:

<a href="https://www.htaccessredirect.net/"
 rel="nofollow noreferrer noopener"><em>.htaccess</em>
generator</a>

Het maakt de benodigde bestanden voor je aan. Je moet de gebruikersnaam,
het wachtwoord en het pad opgeven.

Vul de twee secties in: **Wachtwoordbeveiliging Bestand** en **htpasswd Generator**
en selecteer vervolgens de knop `Genereer Code`. Je ontvangt de tekst voor het .htaccess-bestand en de tekst voor het .htpasswd-bestand in aparte vakken.
Voorbeelden:
```
//Wachtwoordbeveiliging bestand
<Files /admin>
AuthName "Prompt"
AuthType Basic
AuthUserFile /home/user/.htpasswd
Require valid-user
</Files>
```

```
John:$apr1$a3dbt6j7$KJQr137CY9QuN6tYl6M4Z1
```

*Vertaald door openai.com*

