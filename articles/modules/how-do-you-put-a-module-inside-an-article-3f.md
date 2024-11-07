<!-- Filename: How_do_you_put_a_module_inside_an_article%3F / Display title: Modules binnen Artikelen  -->

## Introductie

Je wilt meestal modules op een bepaalde manier aan artikelen koppelen. Modules worden meestal toegewezen aan moduleposities en de moduleposities verschijnen ergens op de webpagina, zoals bepaald door het sjabloon. Soms is het echter nuttig om een module daadwerkelijk binnen een artikel in te sluiten. Joomla heeft hiervoor een plugin genaamd *Content - Load Modules*. Wanneer deze is ingeschakeld, kan een module op drie verschillende manieren in een artikel worden ingesloten:

```
    {loadposition positie,[stijl]}
    {loadmodule mod_type,de titel,[stijl]}
    {loadmoduleid moduleId}
```

Waarbij `stijl` een van de Module Stijl-waarden is uit het tabblad Geavanceerd van het modulegegevensinvoerformulier, bijvoorbeeld html, outline, table, card of noCard.

## loadposition

Om een module in een artikel in te voegen, publiceer je de module op een positie en laad je die positie in het artikel als volgt:

1. Maak een module en stel de positie in op ***mijnpositie***. ***mijnpositie*** kan elke waarde zijn die niet in conflict is met een bestaande sjabloonpositie. Typ in het modulebewerkingsformulier de positie ***mijnpositie*** in en druk op enter in plaats van deze uit de vervolgkeuzelijst te selecteren.
2. Wijs de module toe aan **Alle** menu-items. Dit zorgt ervoor dat deze altijd verschijnt, ongeacht hoe de bezoeker bij het artikel is gekomen. De module wordt niet weergegeven tenzij je de opdracht gebruikt om de module in een artikel te laden.
3. Bewerk het artikel en voeg de tekst ***{loadposition mijnpositie}*** in op de plaats waar je de module wilt laten verschijnen.

**Opmerking:** Als de plugin *Content - Modules Laden* is uitgeschakeld, wordt de tekst *{loadposition mijnpositie}* ongewijzigd in het artikel weergegeven. Ook moet de naam van de positie volledig in kleine letters zijn. CamelCapitalisation zal falen.

## loadmodule

De *{loadmodule yyy}*-syntaxis zoekt naar de eerste module waarvan het **type** overeenkomt met de string 'yyy'. Dus je zou een *mod_login* module kunnen laden door {loadmodule login} in je tekst te plaatsen. Het type is niet zo voor de hand liggend! Bijvoorbeeld, de Taalwisselaar heeft het type **languages**. Om het type te vinden, moet je de lijst van modulemappen doorlopen met een bestandsbeheerder/verkenner en het *mod_*-gedeelte van de mapnaam weglaten.

Als je een specifieke instantie van een module wilt laden, omdat je meer dan één loginmodule hebt, bijv. met de titels Login 1, Login 2, enz., moet je {loadmodule mod_modType, modTitle} gebruiken, waarbij **mod_modType** mod_login zou zijn en **modTitle** de naam/titel is die aan je module-instantie is gegeven. In het bovenstaande voorbeeld eindig je dus met **{loadmodule mod_login Login 2}**.

Je kunt ook de stijl toevoegen die wordt gebruikt voor het renderen van de module. Om dit te doen, voeg je de stijl als derde parameter toe zoals {loadmodule login,Login 2,xhtml}. Als je geen stijl toevoegt, wordt er geen gebruikt.

## loadmoduleid

De syntaxis *{loadmoduleid z}* zoekt naar de module waarvan de `id` overeenkomt met het nummer `z`. Je kunt de module met id 200 laden door *{loadmoduleid 200}* in je tekst te plaatsen. Deze variant gebruikt geen extra parameters zoals de `style`-parameter.

## Editor Knop

Als de editor-xtd plugin *Knop - Module* is geactiveerd, kun je de editor knop *Module* gebruiken om de hierboven beschreven tags gemakkelijker in de editor tekst in te voegen. De Modullijst heeft een knop in de titelkolom om in te voegen op id en een knop in de Positie kolom om in te voegen op positie.

## Modules binnen Modules

Het is mogelijk om een module op te nemen binnen een *Aangepaste HTML* module. Ze worden op dezelfde manier verwerkt door inhoudsplug-ins als artikelen.

Er kunnen opmaakproblemen optreden omdat de stijl van de *Aangepaste HTML* module de stijl van de opgenomen module zal omgeven. Dat is de reden waarom de *Module* editor knop niet beschikbaar is in modules van het type *Aangepast*.

*Vertaald door openai.com*

