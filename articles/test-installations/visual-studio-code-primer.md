<!-- Filename: Visual_Studio_Code_Primer / Display title: Visual Studio Code Inleiding  -->

## VS Code - Een Populaire Gratis IDE

Van Wikipedia:

> Visual Studio Code, vaak aangeduid als VS Code, is een
> broncode-editor gemaakt door Microsoft voor Windows, Linux en macOS.
> Functies omvatten ondersteuning voor debuggen, syntaxiskleuring,
> intelligente codevoltooiing, snippets, coderefactoring en ingebouwde
> Git. Gebruikers kunnen het thema, de sneltoetsen, voorkeuren wijzigen en
> extensies installeren die extra functionaliteit toevoegen.

## Installatie

De standaardpagina van de VS Code-site heeft een keuzelijst voor elk ondersteund platform. De kans is groot dat jouw platform al is geselecteerd. Dus download en installeer en je bent klaar om te beginnen.

### Aan de Slag

De *Aan de Slag* pagina van VS Code bevat enkele *Start* items, een lijst met *Recente* items en een korte lijst met *Rondleidingen*. Als je helemaal nieuw bent met VS Code, worden deze aanbevolen om te bekijken. Ze kosten slechts een paar minuten.

De VS Code Documentatie is beschikbaar via het menu *Help / Documentatie*. De [Introductievideo's](https://code.visualstudio.com/docs/getstarted/introvideos) zijn zeer de moeite waard om te bekijken. Elk duurt 2 tot 6 minuten en geven een uitstekende introductie tot de functies van VS Code.

De officiële documentatie is de plek om naartoe te gaan als je specifieke informatie wilt opzoeken.

### VS Code Extensies

VS Code kan worden gebruikt voor elk type tekst, inclusief een breed scala aan programmeertalen. Het werkt zonder toevoegingen met JavaScript. Andere talen worden gedetecteerd op basis van context, dus als je begint met het maken en opslaan van PHP-code, krijg je waarschijnlijk de melding om een PHP-ondersteuningspakket te installeren.

Klik op het *Extensies*-icoon in de linker *Activiteitenbalk* om te zien wat je hebt geïnstalleerd en wat wordt aanbevolen. Je hebt de PHP Debug-extensie nodig!

### De VS Code Schermindeling

Enkele termen die in de daaropvolgende instructies worden gebruikt:

- **Activiteitenbalk** de smalle balk aan de linkerkant van het scherm. Selecteer een pictogram om de Primaire Zijbalk te openen of te sluiten.
- **Primaire Zijbalk** toont bij openen details over de geselecteerde activiteit.
- **Statusbalk** onderaan het scherm. Het laat zien wat er gaande is.
- **Paneel** een gebied onder de teksteditors om andere informatie weer te geven.

Selecteer een indelingsicoon rechtsboven om een van deze elementen te openen of te sluiten.

## Coderen van een Joomla-extensie

Om een extensie te maken, is het uw doel om een zip-bestand aan te maken dat u kunt installeren op een werkende Joomla-site. U heeft dus een map nodig om uw code in op te slaan. Deze map moet binnen uw persoonlijke bestandsruimte op uw laptop of desktop computer voor lokale ontwikkeling staan. Het moet niet in uw website-structuur staan. U zou bijvoorbeeld *~/jextensions* kunnen gebruiken om submappen voor verschillende extensies in op te slaan. Ik gebruik *~/git* omdat het kort en gemakkelijk te spellen is, hoewel potentieel verwarrend omdat elke submap een apart git-repository gebruikt.

### Voorbeeldcode

Als u wat voorbeeldcode wilt om aan te werken, is er een extensie beschikbaar op GitHub genaamd *mod_debugme*. Zoals de naam al doet vermoeden, is het een module met enkele bugs. Naast de modulecode is er een *build.xml* bestand om één manier te illustreren om het bouwen voor testen en het maken van een zip-bestand te automatiseren.

De module is ontworpen om de volgende paar (standaard 3) evenementen (verjaardagen) uit een lijst die in een databasetabel is opgeslagen, weer te geven. U zou zich kunnen voorstellen dat dit in een kantoor- of familiewebsite wordt gebruikt met de verwachting van taart.

Het is waarschijnlijk het beste om te beginnen met het gebruik van git-commando's vanaf de opdrachtregel. Maak eerst een map voor uw code en kloon dan de externe repository:
```sh
    mkdir ~/git
    cd ~/git
    git clone https://github.com/ceford/j4xdemos-mod-debugme
```
De reactie zou slechts een paar seconden moeten duren:
```sh
    Cloning into 'j4xdemos-mod-debugme'...
    remote: Enumerating objects: 23, done.
    remote: Counting objects: 100% (23/23), done.
    remote: Compressing objects: 100% (16/16), done.
    remote: Total 23 (delta 3), reused 23 (delta 3), pack-reused 0
    Unpacking objects: 100% (23/23), done.
```
Neem even de tijd om naar de inhoud van de map te kijken:
```sh
    cd j4xdemos-mod-debugme
    ls -al
    total 16
    drwxr-xr-x   6 ceford  staff   192  2 Sep 17:48 .
    drwxr-xr-x   3 ceford  staff    96  2 Sep 17:48 ..
    drwxr-xr-x  12 ceford  staff   384  2 Sep 17:48 .git
    -rw-r--r--   1 ceford  staff  1402  2 Sep 17:48 README.md
    -rw-r--r--   1 ceford  staff   927  2 Sep 17:48 build.xml
    drwxr-xr-x   8 ceford  staff   256  2 Sep 17:48 mod_debugme
```
De *.git* map bevat informatie over de repo. Het *README.md* bestand is een markdown-document dat deze repo beschrijft. Het *build.xml* bestand is een bestand dat wordt gebruikt om de extensie te bouwen met een extern hulpmiddel, Phing - later beschreven. De *mod_debugme* map bevat de code van de extensie.

### Installatie in Joomla

Comprimeer de extensiemap om een installeerbaar zip-bestand te maken:
```sh
    zip -r mod_debugme.zip mod_debugme
```
U kunt nu het zip-bestand installeren op de Joomla-site die u gebruikt voor testen. Na installatie moet u een Sitemodule maken en deze toewijzen aan een modulepositie. Omdat het een defecte module is, kunt u het toewijzen aan een positie op *Alle pagina's* terwijl u eraan werkt; of u kunt het toewijzen aan een positie op een enkele pagina; of u kunt het positioneren in een artikel dat zijn eigen menu-item heeft.

Verwijder na installatie het zip-bestand.

### Debugmodus inschakelen

Stel in de Globale Configuratie van Joomla *Systeemdebug* in op *Ja* en *Foutrapportage* op *Maximum*.

Wanneer u een pagina opent die de defecte module bevat, ziet u een stack-trace die u vertelt waar een fout werd gegenereerd.

![vscode stack trace](../../../en/images/test-installations/vscode-primer-stack-trace.png)

Soms bevindt de codeerfout zich op de eerste regel van de stack-trace. Als de fout echter in bibliotheekcode wordt gegenereerd, bijvoorbeeld door het doorgeven van ongeldige gegevens aan een databasefunctie, kan de codeerfout verderop in de lijst met functieaanroepen staan.

## Open Extensiemap in VS Code

In VS Code, gebruik het menu-item Bestand / Map openen om de map te vinden en te openen die je lokale kopie van de *mod_debugme* extensiecode bevat. Je zou iets vergelijkbaars met het volgende moeten zien:

![vscode folder view](../../../en/images/test-installations/vscode-primer-screen.png)

Je kunt mogelijk het probleem diagnosticeren door gewoon de code te lezen. In het geval van de fout *Class "DebugHelper" not found* zul je zien dat een *use* instructie een paar regels eerder is uitgecommentarieerd. Het vergeten om een *use* instructie in te voegen is een veelgemaakte fout tijdens de eerste ontwikkeling!

Los dat probleem op en comprimeer en installeer de module opnieuw. Die stap wordt een beetje saai wanneer je meerdere problemen hebt. Dat is waar bouwtools van pas komen.

## Phing

Phing is een opdrachtregeltool, beschikbaar voor alle platforms, die wordt gebruikt om softwarepakketten te bouwen met behulp van instructies opgeslagen in een xml-bestand, standaard genoemd build.xml. Voor het werken met extensiecode kan het worden gebruikt voor twee dingen:

- veranderde bestanden kopiëren van je extensiebronmap naar de juiste locaties in je webmap.
- een nieuw zipbestand genereren voor nieuwe installaties.

Download en installeer Phing. Andere buildtools
zijn beschikbaar! Je kunt Phing installeren in je eigen bin-map of in een systeem-bitmap. Je moet het pad naar je Phing-code noteren. In dit voorbeeld is het *~/bin/phing-latest.phar*. Je kunt het uitproberen vanaf de opdrachtregel nadat je bent overgeschakeld naar de map die je extensiecode bevat:
```sh
    cd ~/git/j4xdemos-mod-debugme
    php ~/bin/phing-latest.phar
```
Antwoord:
```sh
    Buildfile: /Users/ceford/git/j4xdemos-mod-debugme/build.xml

    mod_debugme > main:
          ... Eventuele gekopieerde bestanden worden hier vermeld
          [zip] Bouwen zip: /Users/ceford/zips/mod_debugme.zip

    BUILD VOLTOOID

    Totale tijd: 0.0863 seconden
```

## VS Code Taken

Om Phing vanuit VS Code uit te voeren, moet je een *tasks.json*-bestand aanmaken
in de *.vscode*-map in de hoofdmap van de *j4xdemos-mod-debugme*-map.
Als deze map nog niet bestaat, maak deze dan eerst aan. Maak vervolgens het
*tasks.json*-bestand aan en voer de volgende code in:
```json
    {
        // Zie https://go.microsoft.com/fwlink/?LinkId=733558
        // voor de documentatie over het tasks.json-formaat
        "version": "2.0.0",
        "tasks": [
          {
            "label": "Build mod_debugme",
            "type": "shell",
            "command": "php ~/bin/phing-latest.phar",
            "windows": {
              "command": "php ~/bin/phing-latest.phar"
            },
            "group": "build",
            "presentation": {
              "reveal": "always",
              "panel": "shared"
            }
          }
        ]
    }
```
Windows-gebruikers moeten het Windows-specifieke commando aanpassen. Je kunt nu
de extensie bouwen met behulp van het menu *Terminal / Run Build Task*. Het
resultaat van de opdracht zou moeten verschijnen in het Terminalpaneel onder het
bewerkingsgebied.
```sh
      *  Uitvoeren van taak: php ~/bin/phing-latest.phar

    Buildfile: /Users/ceford/git/gitdemo/j4xdemos-mod-debugme/build.xml

    mod_debugme > hoofd:

          [zip] Niets te doen: /Users/ceford/zips/mod_debugme.zip is up-to-date.

    BOUW VOLTOOID

    Totale tijd: 0.1031 seconden

     *  Terminal wordt hergebruikt door taken, druk op een toets om deze te sluiten.
```
Er kunnen onbegrijpelijke foutmeldingen optreden. De meest waarschijnlijke oorzaak is
het hebben van ongeldige paden naar mappen in het *build.xml*-bestand of een map
is niet aangemaakt. Weer een ander soort probleem om te debuggen!

## Debuggen

Je zou de eerste bug moeten kunnen oplossen door code-inspectie. Meer gecompliceerde problemen vereisen stap voor stap door de code te gaan met de debugger. Dat stelt je in staat om variabelen te inspecteren om te zien of ze de verwachte waarden bevatten, bijvoorbeeld bij het doorgeven van argumenten aan bibliotheekfuncties.

### *php.ini*-instellingen

Om debuggen op te zetten met Xdebug moet je enkele regels toevoegen aan het begin van je *php.ini*-bestand.
```ini
    zend_extension="xdebug.so"
    xdebug.mode="debug"
    xdebug.client_port=9003
    xdebug.start_with_request = yes
```
Sla na het opslaan van eventuele wijzigingen je Apache-server opnieuw.

### Voeg Website Venster Toe

Je extensiemap bevat slechts een paar bestanden, de ***sources*** van de bestanden die op je website zijn geïnstalleerd. Runtime debuggen omvat het instellen van breakpoints in je ***site***-bestanden, dus je hebt toegang nodig tot die bestanden. Je zou het menu *Bestand / Map aan Werkruimte Toevoegen...* kunnen gebruiken om de sitemap aan je werkruimte toe te voegen. Er is echter een zeer grote kans dat je eindigt met het maken van veranderingen aan sitebestanden in plaats van bronbestanden. Het is dus waarschijnlijk het beste om een apart VS Code-venster te openen voor debuggen.

- **Open nieuw venster:** Selecteer vanuit het VS Code-menu *Bestand / Nieuw Venster* en selecteer de map met de Joomla-website.
- **Open map:** In het nieuw geopende venster, selecteer *Bestand / Map Openen...* vanuit het VS Code-menu. Vind je websitemap en selecteer deze. Je zou een lijst van alle bestanden in je Joomla-website moeten zien in de primaire zijbalk.

### Launch-configuratie

Om debuggen daadwerkelijk te laten werken in VS Code heb je een launch-configuratie nodig. Maak in de root van je website een map genaamd *.vscode* (let op de leidende punt) met daarin een bestand genaamd *launch.json* met de volgende inhoud:
```json
    {
        "configurations": [
            {
                "name": "Listen for XDebug",
                "type": "php",
                "request": "launch",
                "hostname": "0.0.0.0",
                "port": 9003,
                "stopOnEntry": true,
                "pathMappings": {
                    "/Users/ceford/Sites/j421rc2": "${workspaceFolder}"
                }
            }
        ]
    }
```
Vergeet niet om het pathMappings-item in dit voorbeeld te vervangen door de daadwerkelijke pathMappings van je eigen site. Het stopOnEntry-item zal de uitvoering stoppen op de allereerste regel PHP-code die wordt uitgevoerd.

### Debug *mod_debugme*

Nu ben je klaar om de bugs in de geïnstalleerde module te vinden en op te lossen.

- **Vind module-code:** Vind de eerste bug op regel 16 van JROOT/modules/mod_debugme/mod_debugme.php.
- **Stel breakpoint in:** Klik in de ruimte links van nummer 16. Een lichtrode stip zal verschijnen als je zweeft en volledig rood worden nadat je klikt om aan te geven dat een breakpoint is ingesteld.
- **Start debuggen:** Selecteer *Run / Start Debugging* vanuit het VS Code-menu. Herlaad je site in je browser. Je VS Code-venster zou opnieuw moeten verschijnen met de code gestopt op de eerste regel van het *index.php*-bestand van de site. Bovenaan het scherm staan enkele pictogrammen om het debugproces te beheren. Ze zouden voor zichzelf moeten spreken. Zo niet, kijk ze dan na in de VS Code Help / Documentatie.
- **Doorgaan:** Selecteer de knop doorgaan - de code zal verder gaan naar je eerste breakpoint. Onderzoek de code om te zien wat het probleem is.
- **Zweven:** Als je zweeft over een variabele die een waarde toegewezen heeft gekregen, verschijnt er een kleine Tooltip die de attributen van die variabele samenvat. Er is geen Tooltip voor variabelen die geen waarden toegewezen hebben gekregen.
- **Variabelen:** De linker kolom bevat meer informatie over de toestand van de code op het breakpoint. Er zijn er te veel om hier te behandelen. Verken ze indien nodig!
- **Stop met Debuggen:** Het is waarschijnlijk het beste om het Doorgaan-pictogram te selecteren, anders wordt de webpagina blanco geleverd. Anders zou je de Stop-knop of het menu Run / Stop Debuggen kunnen gebruiken.

### Los een Bug op

**Onthoud:** Los de bug niet op in de website-code! Los deze op in de broncode!

Los de broncode op en gebruik vervolgens *Terminal / Run Build Task...*.

Herstart debug.

### Tips

Een paar minder voor de hand liggende problemen:

- Je lost de eerste bug op maar het crasht nog steeds op die regel. Kijk in mod_debugme.xml om te zien waar de src van namespaced classes is gedefinieerd. Wanneer opgelost in de bron moet je het zip-bestand opnieuw installeren of *administrator/cache/autoload_psr4.php* verwijderen. Wanneer afwezig, herbouwt Joomla dat bestand vanuit de manifestbestanden. Maar als het een incorrect of ontbrekend item heeft, wordt het niet opgelost totdat de extensie opnieuw is geïnstalleerd.
- Soms moet je een paar regels voor de regel waar de fout optreedt een breakpoint instellen, vooral als je de waarden wilt controleren die aan functieaanroepen worden doorgegeven.
- Tabel *xxx.yyy\\debugme* bestaat niet. Ah ja, de code om een tabel te maken bij installatie en te verwijderen bij deïnstallatie werd nooit gecreëerd. Je zult een SQL-query moeten uitvoeren in phpMyAdmin met de inhoud van het *mod\\debugme.sql*-bestand. Vergeet niet om *\#\\* te wijzigen in de tabelnamen voor je databaseprefix. En als het nog steeds mislukt, controleer de tabelnaam in de code.

## Screenshot

Wanneer alles is opgelost, is dit wat je mogelijk ziet:

![vscode debugged module site view](../../../en/images/test-installations/vscode-primer-debugme-fixed.png)

Cake dagen?

## Referenties

Uit de Joomla! Documentatie: [Visual Studio Code](https://docs.joomla.org/Visual_Studio_Code) behandelt ook de configuratie van andere tools, zoals CodeSniffer en PHPUnit.

*Vertaald door openai.com*

