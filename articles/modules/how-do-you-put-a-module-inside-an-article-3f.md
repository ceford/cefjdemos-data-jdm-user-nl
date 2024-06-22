<!-- Filename: How_do_you_put_a_module_inside_an_article%3F / Display title: Hoe zet u een module in een artikel? -->

Joomla!  <span class="small">≥ </span>2.5 serie

U wilt meestal op de een of andere manier modules aan artikelen
koppelen. De modules worden toegewezen aan module posities en de module
posities verschijnen ergens op de webpagina, bepaald door het template.
Het is echter soms handig om een module binnen het artikel op te nemen.
De Joomla core voorziet op drie manieren om dit te doen: loadposition,
loadmodule en loadmoduleid. De plugin "Inhoud - Laad modules" moet
actief zijn.

Syntaxis:

- {loadposition position,\[style\]}
- {loadmodule mod_type,the title,\[style\]}
- {loadmoduleid moduleId}

## loadposition

Om een module binnen een artikel in te voegen, publiceert u de module op
een positie en laadt u die positie als volgt in het artikel:

1.  Maak een module en zet zijn positie op ***Mijnpositie***.
    ***mijnpositie*** kan elke waarde hebben die niet conflicteert met
    een bestaande template positie. Type bij 'Positie' ***mijnpositie***
    en druk op enter in plaats van het selecteren uit de drop-down
    lijst.
2.  Wijs de module toe aan **Alle** menu-items. Dit zorgt ervoor dat hij
    altijd verschijnt, ongeacht hoe de bezoeker bij het artikel gekomen
    is. De module zal niet getoond worden behalve als u het commando om
    de module te laden in een
    artikel
    zet.
3.  Bewerk de artikelen waarin u wilt dat de module verschijnt en voeg
    de tekst ***{loadposition mijnpositie}*** toe in het artikel op de
    plaats waar u de module wilt hebben.

\*Let op dat dit alleen werkt als de [*Inhoud - Laad module* plugin
geactiveerd
is](https://docs.joomla.org/Help25:Extensions_Plugin_Manager_Edit#Content_-_Load_Modules "Special:MyLanguage/Help25:Extensions Plugin Manager Edit").
Als deze plugin gedeactiveerd is, verschijnt de tekst *{loadposition
mijnpositie}* onveranderd in het artikel. De naam van de positie moet
daarnaast volledig in kleine letters zijn. Een mix van hoofdletters en
kleine letters werkt niet.

## loadmodule

Een alternatief voor "{loadposition xx}" is de "{loadmodule yyy}"
variatie die wordt afgehandeld door dezelfde plugin.

In dit geval zoekt de plugin naar de eerste module waarvan het **type**
overeenkomt met de tekenreeks 'yyy'. U zou dus een "mod_login" module
kunnen tonen door {loadmodule login} in de tekst te zetten. Als u een
speciale versie van een module wilt laten zien, omdat u bijvoorbeeld
meerdere login modules heeft met de titels login 1, login 2 etc,
gebruikt u {loadmodule mod_modType, modTitle} waarbij mod\_**modType**
wordt mod_login en **modTitle** is de naam/titel gegeven aan uw
instantie van die module. In bovenstaande voorbeeld wordt dat dus
**{loadmodule mod_login Login 2}**. . U kunt ook de stijl toevoegen die
wordt gebruikt voor het weergeven van de module. Voeg daarvoor de stijl
toe als derde parameter: {loadmodule login,login2,xhtml}. Als u geen
stijl toevoegt, wordt "none" gebruikt.

## loadmoduleid

Sinds Joomla! versie 3.9.0 is een alternatief van `{loadposition xx}` en
`{loadmodule yyy}` `{loadmoduleid z}` wat door dezelfde plugin wordt
uitgevoerd.

In dit geval kijkt de plugin naar de module waarvan het `id` overeenkomt
met net nummer `z`. zo kun je de module laden met id 200 door
`{loadmoduleid 200}` in je tekst te zetten. Deze variant "begrijpt" geen
extra parameters zoals de `style` parameter.

## Bewerk knop (sinds Joomla! versie 3.5)

Als de editor-xtd plugin "Knop - Module" geactiveerd is kun je de
bewerk-knop "Module" gebruiken om de hierboven beschreven tags
makkelijker in te voegen in het tekstvak. Sinds Joomla! 3.9 kan dat ook
met de variant `loadmouleid`.

## Modules binnen modules

In Joomla! 2.5+ en Joomla! 3.x+ is het mogelijk een module op te nemen
in een "Aangepaste HTML" module, aangezien de content plugins ze op
dezelfde manier verwerken als artikelen.

Om dit te laten werken moet de optie "Bewerk inhoud" ingeschakeld zijn,
zoals in dit screenshot.

<img
src="https://docs.joomla.org/images/4/48/J3x_custom_html_prepare_content_option-nl.png"
decoding="async" data-file-width="691" data-file-height="396"
width="691" height="396"
alt="De &quot;Bewerk inhoud&quot; optie in een Aangepaste HTML module." />

Denk er aan dat, als u dit doet, dat er opmaak problemen kunnen ontstaan
aangezien de "chrome" van de "Aangepaste HTML" module de "chrome" van de
opgenomen module waardoor ongewenste effecten kunnen ontstaan bij de
opmaak of lay-out. Dit is de reden waarom de "Module" bewerkknop niet
beschibaar is in modules van het type "Aangepast".
