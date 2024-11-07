<!-- Filename: J4.x:FatalError / Display title: FataleFout  -->

## Introductie

Van tijd tot tijd kan Joomla een foutenpagina weergeven in plaats van de pagina die je verwachtte. Er zijn twee soorten foutenpagina's:

- De systeemfoutenpagina heeft een rode achtergrond. Deze wordt geactiveerd als er een ernstige fout optreedt voordat de site- of beheerderssjabloon wordt geladen.
- De sjabloonfoutenpagina lijkt op de normale site- of beheerderssjabloon, maar het inhoudsgebied wordt vervangen door een foutmelding. Dit wordt geactiveerd wanneer de fout optreedt in de inhoudscode.

### Systeemfoutenpagina

![Systeem fatale foutenpagina](../../../en/images/problems/fatal-error.png)

### Sjabloonfoutenpagina

![Sjabloonfoutenpagina](../../../en/images/problems/template-error.png)

## Hoe te Oplossen

Er zijn een aantal mogelijke redenen waarom fatale fouten kunnen optreden. Hier zijn er slechts een paar:

- Een verandering bij je host, bijvoorbeeld een geüpdatete PHP-versie die niet compatibel is met Joomla of een van je Extensies.
- Een probleem met schijfruimte, geheugengebruik of script time-out.
- Een nieuw geïnstalleerde of ingeschakelde Extensie die niet compatibel is met Joomla. Een slechte plugin kan de Administrator-login uitschakelen!

### Debug Inschakelen

Als je Administrator-interface **wel** werkt:
- Ga naar **Home Dashboard → Systeem paneel → Globale Configuratie**.
- Stel op het tabblad Systeem *Debug Systeem* in op *Ja*.
- Stel op het tabblad Server *Foutmeldingen* in op *Maximaal*.
- Klik daarna op *Opslaan & Sluiten*.

Als je Administrator-interface **niet** werkt, bewerk dan het
*configuration.php* bestand in de hoofdmap van je Joomla-website.

1. Verander de permissies van *444* of *-r--r--r--* (niemand heeft
   toestemming om het bestand te schrijven) naar *644* of *-rw-r--r--* (alleen de
   Eigenaar heeft toestemming om te schrijven).
2. Bewerk het bestand met een teksteditor en stel `$debug` in op `true` en 
   `$error_reporting` op `'maximum'`.
3. *Sla* het bestand op.

Na het aanbrengen van de wijzigingen, herlaad je de pagina die de fout veroorzaakte. Nu zou je een stack trace moeten zien. Voorbeeld:

![Template fout pagina](../../../en/images/problems/template-error-stack-trace.png)

Het eerste item in de stack trace geeft aan waar de fout is getriggerd. Soms is dat genoeg om de defecte Extensie te identificeren. Soms staat de defecte Extensie verder naar beneden in de stack trace. Het betekent mogelijk niet veel voor jou, maar de stack trace is van onschatbare waarde voor de experts die vragen beantwoorden in de Joomla Forums.

Als je de defecte Extensie kunt identificeren, schakel deze dan uit. Dat kun je doen met de Administrator-interface als die werkt. Anders gebruik je phpMyAdmin om de Extensie te vinden in de `#__extensions` databasetabel en zet je de `enabled` waarde op `0`. Je zou geen enkele core Joomla Extensies hoeven uit te schakelen.  

## Forum Post Assistent

Om problemen op te lossen, moet je de
[Forum Post Assistant (FPA)](https://forumpostassistant.github.io/docs/) downloaden en
het in de hoofdmap van je Joomla-website laden. De link om het te vinden is ook
dichtbij de bovenkant van elke Joomla Forum-pagina te vinden. De FPA is een zelfstandige PHP
script dat je Joomla-installatie analyseert en je vertelt wat er mis zou kunnen zijn. Nogmaals, het kan misschien niet veel voor jou betekenen, maar de experts die
vragen beantwoorden in de Forums kunnen vragen om het te bekijken.

## Opruimen

Wanneer je probleem is opgelost:

1. Ga naar **Startdashboard → Systeempaneel → Globale Configuratie**
2. Selecteer de tab Systeem en stel *Debug Systeem* in op *Nee*.
3. Selecteer de tab Server en stel *Foutmelding* in op *Systeemstandaard*.
4. *Opslaan & Sluiten*.
5. Verwijder de Forum Post Assistant.

De machtigingen van `configuration.php` worden ingesteld op alleen-lezen (444 of *r--r--r--*)
wanneer het formulier van de Globale Configuratie wordt opgeslagen. Het is niet nodig om dit
handmatig te doen.

*Vertaald door openai.com*

