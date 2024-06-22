<!-- Filename: How_do_you_choose_secure_extensions%3F / Display title: Hoe kiest u veilige extensies? -->

Het belangrijkste dat u kunt doen is de juiste beslissingen nemen bij
het kiezen van de extensies die u op uw website wilt gebruiken. Zodra
een onveilige of schadelijke extensie geïnstalleerd is, moet u uw hele
website als aangetast beschouwen. Er is geen mogelijkheid om te
voorkomen dat een component databasetabellen opent die niet geopend
moeten worden, of om dat proces te stoppen. Er is ook geen manier om een
component te laten stoppen met het verzenden van alle informatie die het
heeft gevonden op een geïnfecteerde website. Zodra een onveilige of
schadelijke component is geïnstalleerd, is uw hele website onveilig.

## Eenvoudige tips om de juiste keuze te maken bij het installeren van extensies

- Wanneer is de laatste versie uitgebracht?

Is het meer dan een jaar gelelden, beschouw het project dan als verlopen
en zoek iets anders. Installeer geen oude componenten.

- Wat voor soort release is het? (Stabiel, Release Candidate (RC), Beta,
  Alpha)

Voor live websites zou u zo veel mogelijk gebruik moeten maken van
stabiele releases. Als u niet kunt wachten tot er een stabiele release
beschikbaar is, zijn Release Candidates de enige andere optie die u kunt
overwegen. Er wordt niet aangeraden om Beta of Alpha extensies op een
live website te installeren. Het betekent dat er nog steeds fouten in
zitten, ze zijn onvoldoende getest en kunnen hinderlijke bugs of
onopgeloste veiligheidsproblemen bevatten.

- Heeft de extensie een aantoonbaar goed veiligheidsbeleid?

Dit is natuurlijk iets subjectiever, maar desalniettemin een bruikbare
indicatie voor de toekomstige betrouwbaarheid. Het vereist enig
onderzoek en research. Kijk rond op de ontwikkelaars downloadpagina's en
in het archief. Zijn er veel veiligheids-releases of patches? Zijn er
veel melding van 'hacking'-activiteiten bij deze extensie? Is de
ontwikkelaar ervaren en zich bewust van veiligheid? Wat vinden andere
leden van de community van de extensie?

- Is er een support community voor deze extensie?

Dit is heel belangrijk voor gebruiksgemak en veiligheid. Als een
extensie een support community heeft, is er meer kans dat
veiligheidsproblemen bekend zijn en opgelost worden. Een support
community betekent dat er mensen zijn die de extensie willen blijven
gebruiken en dat ze de extensie de moeite waard vinden. Dit bevordert de
kans dat veiligheidsproblemen worden gevonden, bekendgemaakt, en
onmiddellijk afgehandeld.

- Is er een versie compatible met de meeste recente Joomla 3?

Op zichzelf maakt dit een extensie niet onveilig, het is belangrijk te
weten of de extensie compatible is met Joomla 3. Joomla 2.5 heeft zijn
EOL (einde leven) bereikt. Het updaten van Joomla versies is veel
eenvoudiger als een extensie compatible is met de meest recente versie
die van Joomla beschikbaar is.

- Is de extensie over het algemeen bug-vrij?

Het is vrijwel onmogelijk dat een extensie geheel bug-vrij is, maar hoe
kleiner het aantal bugs, hoe beter. Bugs in de software betekenen fouten
in de software. Hoe meer fouten, hoe hoger het risico op gebruiks- en
veiligheidsproblemen. Veiligheidsproblemen zijn meestal het resultaat
van niet één, maar meerder bugs of een verkeerde aanpak. De recente
kwetsbaarheden in extensies van derden die het mogelijk maken om
bestanden te uploaden zijn bijvoorbeeld het gevolg van:

## Slechte praktijken

- PHP's Register Globals ingeschakeld hebben.
- Het gebruiken van gedateerde of verlaten extensies.
- Geen andere veiligheidscontroles ingeschakeld voor PHP. (url_fopen
  off, open_basedir restrictions, disabled PHP functies)
- Slecht ingestelde bestand-permissies.
- Geen aanroep filteren of software "firewall". (zoals mod_rewrite rules
  of mod_security Apache modules)

## Bugs

- Geen defined('\_VALID_MOS') or die... statements opgenomen
- Slecht opgebouwde include() statements.

## Belangrijk om te onthouden

**Hoewel de Joomla! core veilig is wanneer hij goed is geconfigureerd,
zijn extensies van derden er in alle smaken, leeftijden en
kwaliteiten.** Bekijk altijd de code voor je gaat installeren, tenzij je
de extensieontwikkelaar volledig vertrouwt. Hier volgt een lijst van
aandachtsgebieden.

1\. Hoe complex is de extensie?

Hoe groter de extensie, hoe waarschijnlijker dat er problemen kunnen
zijn, en hoe zorgvuldiger u hem moet beoordelen. Wanneer u niet kunt
zien wat het doet, moet u het niet vertrouwen.

2\. Leest de extensie bestanden van uw server, of schrijft de extensie
er bestanden naartoe?

Programma's die bestanden lezen kunnen onbedoeld de beperkingen die u
hebt ingesteld overtreden, of gevoelige informatie over het systeem
doorgeven aan crackers. Programma's die bestanden schrijven kunnen
bestaande bestanden wijzigen of beschadigen, of Trojans toevoegen.

3\. Communiceert de extensie met andere programma's op uw systeem?

Een voorbeeld: veel extensies versturen email als respons op een
formulier, door het openen van een verbinding met het sendmail
programma. Gebeurt dat op een veilige manier?

4\. Wordt de extensie uitgevoerd met suid (set-user-id) rechten?

Dit is over het algemeen zeer gevaarlijk; een extensie moet wel een heel
goede reden hebben om dit te doen.

5\. Valideert de extensie door gebruikers ingevulde gegevens, zoals
bijvoorbeeld in formuliervelden en in de URL?

6\. Controleer hier, of de extensie staat bij de  kwetsbare
extensies

7\. Gebruikt de extensie expliciete pad-namen bij het aanroepen van
externe programma's?

Vertrouwen op de PATH environment variabele om gedeeltelijke path namen
te bepalen is een slechte praktijk.

8\. Is de extensie beveiligd tegen directe toegang via de URL?

Bijvoorbeeld:
`www.yoursite.com/components/com_bad_extension.php?lots_of_bad_code_here`

9\. Is de extensie beveiligd tegen het op afstand toevoegen van
bestanden?

10\. Is de extensie beveiligd tegen SQL injecties?

11\. Is de extensie beveiligd tegen Cross Site Scripting (XSS)?

12\. Is het voor de extensie nodig om PHP register_globals of Joomla! RG
Emulation op ON te zetten?

Zo ja, dan wordt nummer 7 (hierboven) waarschijnlijk geschonden.

13\. Geeft de extensie hogere database toegang aan gebruikers met minder
rechten?

Bijvoorbeeld: laat het gasten of geregistreerde gebruikers gegevens zien
die alleen publishers of administrator zouden moeten kunnen zien?

### Meer informatie

- Zie: <a
  href="http://extensions.joomla.org/support/knowledgebase/item/choosing-secure-extensions"
  class="external text" target="_blank" rel="noreferrer noopener">het
  Kiezen van Veilige Extensies op de JED website</a>
- Zie:
  <a href="http://vel.joomla.org/" class="external text" target="_blank"
  rel="noreferrer noopener">Kwetsbare extensies lijst</a>
