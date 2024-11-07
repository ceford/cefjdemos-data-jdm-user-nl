<!-- Filename: J4.x:Adding_a_New_Article / Display title: Artikel: Bewerken - Inhoud -->

## Introductie

*Een artikel toevoegen* werd behandeld in een *Aan de slag* artikel. Dit is de eerste in een reeks artikelen die meer details bieden over het *Artikel: Bewerken* formulier. Het behandelt de *Inhoud* tab en enkele aspecten van de TinyMCE-editor, de standaardeditor die met Joomla wordt geleverd.

De volgende screenshot toont het bewerkingsformulier met een artikel dat al is opgeslagen.

![Het inhoudsbewerkingsformulier](../../../en/images/articles/articles-edit-content.png)

## Gegevensinvoer

Het artikelbewerkingsformulier heeft tabbladen. Een nieuw artikel heeft standaard het tabblad **Inhoud** geselecteerd. Anders is het laatst geopende tabblad geselecteerd.

### Het Titelveld

Het **Titel**-veld is *Vereist* en wordt gebruikt waar de titel van het artikel wordt weergegeven. Dit is het enige veld dat tekst moet bevatten om een bewerkingsformulier op te kunnen slaan.

Titels moeten kort maar beschrijvend zijn van de inhoud van het artikel, aangezien ze verschijnen in lijsten en menu-items waar ruimte beperkt is.

Titels hoeven niet uniek te zijn, hoewel het het beste is als ze dat wel zijn. Als u bijvoorbeeld *Opslaan als kopie* selecteert in de *Opslaan & Sluiten* vervolgkeuzelijst, wordt het huidige artikel opgeslagen en een nieuw artikel gegenereerd met een nummer toegevoegd aan de Titel en Alias. U kunt het nummer uit de Titel verwijderen, maar niet uit de Alias en de kopie *Opslaan*. Hierdoor ontstaan twee artikelen met dezelfde weergavetitel.

### Het Aliasveld

Het *Alias*-veld wordt meestal leeg gelaten. Wanneer het artikel wordt opgeslagen, wordt de Alias gegenereerd op basis van de titel door deze volledig in kleine letters te maken en niet-alfanumerieke tekens te vervangen door streepjes.

Als je de titel van het artikel wijzigt, kun je de Alias verwijderen en wordt er een nieuwe gegenereerd. Als de Alias is gebruikt om naar het artikel te verwijzen in interne en externe links, verbreek je hiermee de links. Het is dus het beste om de Alias van een oud artikel niet te wijzigen.

### Het Inhoud Tabblad - Artikeltekst

De bovenstaande schermafbeelding toont de artikeltekst in een WYSIWYG-editor die lijkt op een tekstverwerker. U moet echter opletten dat de artikeltekst wordt opgeslagen als HTML en dat het invoerveld voor gegevens in werkelijkheid een tekstgebied is dat deze HTML bevat. U kunt dit zelf zien door de knop *Editor wisselen* onder het bewerkgebied te selecteren. De Editor is in feite een JavaScript-toepassing die de HTML opnieuw weergeeft om het gemakkelijk te maken om deze te lezen en aan te passen.

#### Niet-toegestane HTML-tags en -attributen

Zowel Joomla als de TinyMCE-editor hebben instellingen die bepaalde HTML-tags en attributen niet toestaan. Bijvoorbeeld, de standaardverbodenlijst van Joomla bevat *iframe*, dus als je probeert die tag in een artikel op te nemen, wordt hij stilletjes verwijderd bij het opslaan. Tekstfilters worden ingesteld in de *Globale Configuratie*. De TinyMCE-plugin heeft een optie om de *Joomla Tekstfilter* te gebruiken. Als dit is ingesteld op *Uit*, worden *script, applet, iframe* weergegeven als *Verboden Elementen*.

#### Editor Werkbalken

Boven het tekstgebied bevinden zich rijen werkbalken. Twee worden standaard weergegeven. De andere kunnen worden weergegeven door het ellips-symbool (...) aan het einde van de tweede werkbalk te selecteren. De werkbalken kunnen worden geconfigureerd om verschillende balken en inhoud te tonen aan verschillende gebruikersgroepen.

Er zijn te veel tools om ze hier allemaal te beschrijven. Dat zou een speld in een hooiberg voor je creëren. Verken het gewoon!

Er zijn echter enkele functies die extra uitleg verdienen.

#### CMS Inhoud

Deze knop toont een vervolgkeuzelijst waarmee items in een artikel kunnen worden opgenomen die elders in het CMS zijn verkregen.

- **Artikel** Deze link toont een pop-uplijst met artikelen. Selecteer een artikel om een link naar dat artikel op te nemen in het huidige artikel.
- **Contact** Neem een link op naar een contact in het huidige artikel.
- **Veld** Neem een veld op in het artikel. Het wordt weergegeven als `{field 1}`.
- **Media** Neem een afbeelding of bestand op uit een Media-component pop-up.
- **Menu** Neem een link op naar een menu-item uit een menu-lijst pop-up.
- **Pagina-einde** Er verschijnt een prompt voor een *Paginatitel* en *Inhoudsopgave Alias*. Deze functie wordt gebruikt om lange documenten in verschillende pagina's op te splitsen.
- **Lees Meer** Er wordt een *Lees Meer...*-scheidingsteken ingevoegd op de positie van de cursor. Kies een onderbreking tussen alinea's voordat je selecteert.

#### Externe links

Het **Invoegen** item in de eerste werkbalk heeft opties om een *Link...*, *Afbeelding...* of *Media...* in te voegen. Deze zijn voor externe items, dus zorg ervoor dat je de URL van het te gebruiken item bij de hand hebt.

### Het Inhoud Tabblad - Instellingen

Het **Inhoud**-tabblad wordt grotendeels bezet door de TinyMCE-editor.

Naast de inhoud zijn er velden om het publiceren, hoe en waar het artikel wordt weergegeven, en wie het kan zien wanneer het is gepubliceerd, te beheren. In de meeste gevallen kunnen deze instellingen op hun standaardwaarden worden gelaten.

1. **Status** *Gepubliceerd*, *Niet gepubliceerd*, *Gearchiveerd* of *In de prullenbak* - de standaardwaarde is *Gepubliceerd*.
2. **Categorie** Dit is een *Vereist* veld, maar standaard wordt het ingesteld op *Niet-gecategoriseerd*. U kunt een categorie selecteren uit de lijst of enkele tekens van een categorienaam typen om de lijst met te kiezen categorieën in te korten.
3. **In het Oog** Schakel tussen *Nee* en *Ja* om het artikel op de startpagina weer te geven als dat een *In het Oog Artikel* indeling gebruikt.
4. **Toegang** Het toegangsniveau kan worden gewijzigd om het artikel te beperken tot Gebruikersgroepen die zijn toegewezen aan specifieke *Toegangsniveaus*: *Openbaar*, *Gast*, *Geregistreerd*, *Speciaal* of *Supergebruikers*.
5. **Tags** Begin te typen om vooraf gedefinieerde tags te zoeken en selecteren of voeg er een nieuwe toe door deze in te typen en vervolgens **enter in te drukken**.
6. **Opmerking** Elke opmerking over dit artikel die zichtbaar zal zijn onder de Titel op de Pagina met Artikellijst.
7. **Versieopmerking** Voeg opmerkingen toe om aan te geven wat er in deze versie is veranderd. Dit wordt weergegeven in de *Versies* modale dialoog en het veld wordt na het opslaan weer leeg.

### Andere Tabbladen

**Je ziet mogelijk niet alle volgende tabbladen** omdat een sitebeheerder sommige tabbladen kan verbergen om de consistentie van de artikelindeling op de website te behouden. U kunt ook extra tabbladen voor *Aangepaste Velden* zien als deze zijn ingesteld.

1. **Afbeeldingen en Links** stelt u in staat om een inleidende en uitgelichte afbeelding en/of links in te stellen die op vooraf gedefinieerde posities verschijnen. Dit kan worden gebruikt als uw artikel binnen een categorieblog wordt weergegeven.
2. **Opties** stelt u in staat om de indeling van het artikel en bijbehorende informatie zoals titel, categorie, tags, publicatiegegevens, enz. te specificeren. Dit wordt normaal gesproken globaal ingesteld, maar kan artikel specifiek zijn via deze opties.
3. **Schema** is een methode om metadata aan een artikel toe te voegen. Het wordt gebruikt door robots, maar niet gezien door mensen.
4. **Publiceren** stelt u in staat om publicatiedata en -tijden in te stellen om het publiceren van een artikel in te plannen. Standaard wordt een artikel direct gepubliceerd wanneer het wordt opgeslagen. U kunt ook de Metadata voor het artikel instellen.
5. **Configureer Bewerk Scherm** stelt u in staat om parameters voor het artikel te tonen of verbergen.
6. **Machtigingen** toont de machtigingen voor elke gebruikersgroep die bepalen wat wel of niet kan worden gedaan.

Er zijn afzonderlijke artikelen over elk van deze tabbladen.

## Het Artikel Opslaan

Zodra je de vereiste informatie en inhoud hebt toegevoegd, kun je het artikel opslaan. Er zijn verschillende manieren om dit te doen, afhankelijk van wat je daarna wilt doen in Joomla.

Om het artikel op te slaan, kun je kiezen voor *Opslaan* of *Opslaan & Sluiten*. Laatstgenoemde heeft dropdown-opties zoals *Opslaan & Nieuw*, *Opslaan naar Menu* en *Opslaan als Kopie*.

- **Opslaan** Sla het artikel op en houd het open voor verdere bewerking. 
  Het is een goede gewoonte om regelmatig je werk op te slaan bij langere artikelen.
- **Opslaan & Sluiten** Sla het artikel op en ga naar de Artikel-lijst. De Opslaan & Sluiten-knop heeft verdere
  dropdown-opties:
  - **Opslaan & Nieuw** Sla het artikel op en open dan een **Artikelen: Nieuw** pagina. 
    Deze optie bespaart tijd bij het toevoegen van meerdere artikelen.
  - **Opslaan naar Menu** Sla het artikel op en open een **Menu's: Nieuw Item** pagina.
  - **Opslaan als Kopie** Sla het artikel op en open dan een **Artikelen: Bewerken** pagina 
    met een getal tussen haakjes toegevoegd aan de titel en hetzelfde nummer 
    volgend op een koppelteken, -2 bijvoorbeeld, in het aliasveld. Je kunt 
    de titel wijzigen en het alias van het nieuwe artikel, dat al is aangemaakt, 
    wijzigen of verwijderen.

Een systeemmelding geeft aan dat het artikel succesvol is opgeslagen.

### Fouten bij het proberen op te slaan:

- Als je de vereiste velden niet hebt ingevuld, zal er een rode foutmelding 
  verschijnen die de ontbrekende informatie aangeeft die je moet toevoegen.
- Je zult een foutmelding zien als het artikel een alias heeft die al 
  bestaat. Je kunt dit oplossen door het aliasveld aan te passen.

## Tips

- Als je niet de Super User of Administrator bent, neem dan de tijd om te begrijpen hoe de website is opgezet. Alleen omdat je een artikel hebt opgeslagen, betekent dit niet dat het zichtbaar is op de website. Als er gebruik wordt gemaakt van Categorie Blog pagina's, zal het toewijzen van de juiste categorie het artikel weergeven. Anders moet een artikel worden toegewezen aan een menu-item. Dit kun je doen in het artikel of via het Administrator **Menu's** menu.
- Probeer titels van artikelen kort en specifiek te houden.
- Hoewel het mogelijk is, vermijd het maken van nieuwe categorieën en tags in artikelen als er meerdere gebruikers zijn die artikelen toevoegen aan de website. Spellingsfouten en verschillen kunnen gemakkelijk voorkomen dat artikelen worden weergegeven waar ze bedoeld waren. Het aanmaken van categorieën en tags op hun respectieve lijstpagina zorgt voor consistentie op de website.
- Maak gebruik van opmerkingen bij artikelen indien nodig. Ze kunnen erg nuttig zijn, vooral als meerdere mensen artikelen toevoegen.
- Waar je ook bent in Joomla, je kunt een artikel toevoegen zonder naar het Start Dashboard te gaan - gebruik het Joomla Administrator Menu.

*Vertaald door openai.com*

