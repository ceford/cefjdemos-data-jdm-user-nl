<!-- Filename: J3.x:Adding_custom_fields/Parameters_for_all_Custom_Fields / Display title: Veldparameters -->

## Formulier voor Gegevensinvoer

Er zijn 16 of meer veldtypen beschikbaar in de keuzelijst voor typen in het formulier voor gegevensinvoer. De meeste formulier velden zijn hetzelfde voor alle veldtypen, maar andere veranderen afhankelijk van het geselecteerde type. Dit artikel beschrijft de gemeenschappelijke parameters voor alle velden. Het gegevensinvoerformulier is ook hetzelfde voor **Artikel**, **Contact** en **Gebruiker** velden en hun Categorie velden.

Een veldenlijst zal aanvankelijk leeg zijn. Om te beginnen, bijvoorbeeld met Artikel velden:
* Selecteer **Nieuw** vanaf de werkbalk in de Artikelen: Velden lijst.

Het formulier bestaat uit een Titelveld en vier tabbladen.

![Algemene tab van veldparameters](../../../en/images/fields/fields-parameters-general-tab.png)

## Titel

De titel wordt weergegeven op de *Artikelen: Velden* lijstpagina, waar het geselecteerd kan worden om het veld voor bewerking te openen. De titel wordt niet weergegeven wanneer je een artikel maakt of in de frontend. Echter, het label kan worden gemaakt vanuit de titel en het wordt weergegeven in het invoerformulier van artikelgegevens en kan worden weergegeven in de artikelweergave.

### Algemeen tabblad

#### In het linker paneel:

- **Type** Selecteer een van de 16 veldtypes uit de vervolgkeuzelijst. Wanneer je het veld opslaat, is dit type permanent. Je kunt het later niet meer wijzigen.
- **Naam** De naam zal worden gebruikt om het veld te identificeren. Laat dit leeg en Joomla zal een standaardwaarde invullen vanuit de titel.
- **Label** Gebruik een beschrijvend label voor het veld. Deze tekst is niet vertaalbaar. Als je geen tekst voor een label invoert, wordt de tekst van de titel gebruikt als labeltekst.
- **Beschrijving** Tekst die getoond zal worden als een tooltip om het doel van het veld te beschrijven tijdens het invoeren van gegevens. Deze tekst is niet vertaalbaar en zal niet in de frontend worden getoond.
- **Verplicht** Stel in op *Ja* als dit een verplicht veld is dat moet worden ingevuld voordat een artikel ingediend kan worden.
- **Alleen gebruiken in Subformulier** Verklaring vereist [ToDo]
- **Standaardwaarde** Stel een standaardwaarde in indien toepasselijk. Deze tekst is niet vertaalbaar.
- **Filter** Kies een van de beschikbare opties uit de vervolgkeuzelijst. Het veld zal worden gevalideerd op overeenstemming met het geselecteerde gegevenstype.
- **Maximale Lengte** Stel dit in om de lengte van tekstgegevens die kunnen worden ingevoerd te beperken.

### In het rechter paneel:

- **Status** Stel een publicatiestatus in gekozen uit *Gepubliceerd*, *Gedepubliceerd*, *Gearchiveerd* of *Verwijderd*.
  - Gepubliceerd: Het veld is zichtbaar tijdens het bewerken van een artikel of een contact. En het is zichtbaar in de frontend.
  - Gedepubliceerd: Het veld zal niet zichtbaar zijn voor gebruikers tijdens het bewerken van een artikel of een contact.
  - Gearchiveerd: Het veld zal niet langer verschijnen bij het bewerken van een artikel of een contact. Je kunt het openen in de veldmanager wanneer je de filter instelt op gearchiveerd.
  - Verwijderd: Het veld is verwijderd maar nog steeds in de database. Het kan permanent worden verwijderd uit de database met de Prullenbak legen functie in Veldbeheer.
- **Veldgroep** Selecteer geen of een groep gekozen uit een vooraf ingestelde lijst. Groepen verschijnen als aparte tabbladen in het invoerformulier van artikelgegevens.
- **Categorie** Je kunt een veld toewijzen aan een of meer veldcategorieën. Let op dat de standaard *Alle* geen *ongecategoriseerde* artikelen omvat.
- **Toegang** Het bekeken toegangslevel voor dit veld.
- **Taal** Selecteer de taal voor dit aangepaste veld. Als je de meertalige functie van Joomla niet gebruikt, houd dan de standaard op *Alle*.
- **Notitie** Een optioneel veld om je persoonlijke notities voor het veld te maken.

### Opties tabblad

![Veldparameters algemeen tabblad](../../../en/images/fields/fields-parameters-options-tab.png)

#### Formulier Opties

- **Plaatshouder** Een plaatshoudertekst die in het aangepaste veld zal verschijnen als een hint voor de invoer. De plaatshouder is actief in de backend tijdens het maken van een artikel. Je ziet het niet in de frontend.
- **Veldklasse** De klasse-attributen van het veld wanneer het veld wordt weergegeven. Als verschillende klassen nodig zijn, vermeld ze dan met spaties.
- **Labelklasse (Formulier)** De klasse-attributen van het veld in het bewerkingsformulier. Als verschillende klassen nodig zijn, vermeld ze dan met spaties.
- **Bewerkbaar in** Op welk deel van de site het veld moet worden getoond: Site, Beheerder of Beide.
- **Showon Attribuut** Laat het veld voorwaardelijk zien of verberg het afhankelijk van de waarde van andere velden. De syntaxis die hier moet worden gebruikt, is bijvoorbeeld:
  - `lijst-van-items:waarde1[OF]lijst-van-items:waarde2` waarbij
  - lijst-van-items: De naam van een al aangemaakt veld waarop dit veld afhankelijk is.
  - waarde1: De waarde die nodig is in het veld lijst-van-items om dit veld te laten zien.
  - [OF] Om een keuze te maken tussen meerdere velden. In het voorbeeld, zal dit veld worden getoond wanneer het veld lijst-van-items een waarde heeft van waarde1 OF waarde2.
  - [EN] Om meerdere velden te combineren. Dit veld zal alleen worden getoond wanneer de velden lijst-van-items de waarde waarde1 EN waarde2 hebben.
  - Je kunt ook gebruik maken van de waarde 'is niet gelijk aan' zoals in lijst-van-items!:waarde1. De syntaxis zal dit veld alleen laten zien wanneer lijst-van-items niet gelijk is aan waarde1.
  - Om dit veld te laten zien wanneer het veld lijst-van-items is geselecteerd en geen lege waarde heeft, gebruik de syntaxis lijst-van-items!: (zonder een gespecificeerde waarde).
  - Opmerking: Subformulier velden behandelen de naam van lijst-van-items anders.
Als je een Subformulier veld maakt en je voegt dit voorwaardelijke veld toe voor een veld dat je daar maakt, moet je veld[ID] gebruiken in plaats van lijst-van-items, waarbij ID het id is van het veld lijst-van-items. Daarom moet het showon attribuut voor dit voorwaardelijke veld dat je maakt worden ingesteld op: veld36:waarde1[OF]veld36:waarde2 waarbij 36 het ID is van het veld 'Lijst van items'. Dit heeft verduidelijking nodig!

#### Weergave Opties

- **Weergave Klasse** De klasse van de veldcontainer in de output.
- **Waarde Klasse** De klasse van de veldwaarde in de output.
- **Label** Toon of verberg het label.
- **Labelklasse (Output)** De klasse van de labeloutput indien het label wordt weergegeven.
- **Automatische Weergave** Joomla biedt enkele inhoudsevenementen die worden geactiveerd tijdens het inhoudscreatieproces. Dit is de plek om te bepalen hoe de aangepaste velden geïntegreerd moeten worden in de inhoud. Je kunt kiezen voor *Na Titel*, *Voor Weergeef Inhoud*, *Na Weergeef Inhoud* of *Toon niet automatisch*.
- **Prefix** Vaste tekst die wordt weergegeven voor een veld, bijvoorbeeld £.
- **Suffix** Vaste tekst die wordt weergegeven na een veld, bijvoorbeeld EUR.
- **Layout** Selecteer een lay-out uit beschikbare sjablonen en overrides.
- **Weergave Als Alleen-Lezen** Selecteer uit *Overerven*, *Ja* of *Nee*. Als het veld alleen-lezen is (misschien heeft de gebruiker niet het toegangslevel), moet het veld dan worden weergegeven of worden verborgen.

#### Slim Zoeken

- **Zoekindex** Selecteer uit de lijst met opties. Waarschuwing: Wanneer *Zoekbaar maken* is geselecteerd, wordt de inhoud van het veld geïndexeerd met de kijkrechten van het inhoudsitem. Dit kan leiden tot onverwachte informatiedoorbreking.

### Publicatie tabblad

![Veldparameters algemeen tabblad](../../../en/images/fields/fields-parameters-publishing-tab.png)

### Rechten tabblad

![Veldparameters algemeen tabblad](../../../en/images/fields/fields-parameters-permissions-tab.png)

