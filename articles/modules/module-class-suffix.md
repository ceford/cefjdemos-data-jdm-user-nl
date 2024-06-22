<!-- Filename: Module_Class_Suffix / Display title: Module class achtervoegsel -->

Module class achtervoegsel is een parameter in Joomla! modules. Het
wordt geconfigureerd in het module: \[Bewerken\] venster bij
"Geavanceerde instellingen". Het instellen van deze parameter laat
Joomla! ofwel een nieuwe CSS class toevoegen of de bestaande CSS class
wijzigen van het `div` element voor deze specifieke module.

Wanneer Joomla! een module genereert , maakt het automatisch een CSS
class genaamd "moduletable" aan om het stylen van de module toe te staan
-- bijvoorbeeld:

Om een nieuwe class aan te maken, voer de parameter in voorafgaand door
een spatie. Bijvoorbeeld het ingeven van een spatie plus
"mijnNieuweClass" zal leiden tot een nieuwe CSS class met de naam
"mijnNieuweClass". De HTML wordt veranderd in

Om de naam te wijzigen van een bestaande class, voer de parameter in
zonder een spatie. Bijvoorbeeld, het invoeren van "\_mySuffix" (zonder
spatie) zorgt ervoor dat de HTML wordt veranderd naar

Over het algemeen is het aan te bevelen om een nieuw te maken class
vooraf te laten gaan door een spatie. Op deze manier zal de CSS-styling
voor deze module met de standaard class blijven werken. Een nieuwe class
kan worden gebruikt om iedere gewenste styling toe te voegen aan de
module, zonder dat de al bestaande CSS-code aangepast hoeft te worden.
Let op: iedere nieuwe class-naam moet uniek zijn om niet in conflict te
komen met al bestaande class-namen.

Zie:  Gebruik van class
achtervoegsels.

## Gebruik

Als u een module class achtervoegsel met een voorafgaande spatie
opneemt, wordt er een nieuwe CSS class aangemaakt. Als de parameter niet
is voorzien van een voorafgaande spatie, dan wordt de CSS class
"moduletable" gewijzigd. De eerste methode heeft vaak de voorkeur, omdat
dan niet de bestaande styling van de module wordt gewijzigd, en men
hoeft alleen maar nieuwe CSS code toe te voegen voor de nieuwe styling.

Als er niet gebruik wordt gemaakt van een voorafgaande spatie, dan moet
een kopie van alle styling-code van de "moduletable" class worden
gemaakt in de nieuwe CSS class voor het maken van CSS wijzigingen.

Zie  de handleiding voor het gebruik van class
achtervoegsels
voor een gedetailleerd voorbeeld van het gebruik van pagina- en module
class achtervoegsels.
