<!-- Filename: contacts.md / Display title: Contacten  -->

## Inleiding

Een contactpersoon is een verzameling persoonlijke informatie over een individu. U wilt misschien dergelijke informatie beschikbaar maken op uw website voor openbare of privéweergave. U wilt bijvoorbeeld belangrijke leden van uw organisatie of gemeenschap vermelden. De Joomla! Contactcomponent is voor dit doel ontworpen. Hiermee kunt u mensen en hun persoonlijke informatie op uw website vermelden, niet noodzakelijkerwijs geregistreerde gebruikers. U kunt ook iedereen of alleen geregistreerde gebruikers toestaan om e-mails naar deze personen te sturen.

Als een voorbeeld van het gebruik van persoonlijke gegevens kunt u kijken naar de Wikipedia-pagina over de parlementaire commissies van het Verenigd Koninkrijk. Daar ziet u lijsten van commissies met pop-upinformatie over individuele voorzitters. Als u een link naar een commissie volgt, ziet u een lijst van leden met geselecteerde informatie over elke individu. Om iets dergelijks in Joomla te doen, zou u categorieën en subcategorieën voor elke commissie instellen. Zo:

```
House of Commons
- Business
- Cultuur
- ...
House of Lords
- Communicatie
- Grondwet
- ...
```

Elk commissielid heeft extra informatie die niet aanwezig is in de standaardgegevens - politieke affiliatie, zoals Conservatief, Labour of SNP, en kiesdistrict, het gebied van het land dat ze vertegenwoordigen. Die items kunnen worden verzameld met behulp van Aangepaste Velden.

Er moet voorzichtig worden omgegaan met het verzamelen en tonen van persoonlijke informatie. Individuen kunnen erg gevoelig zijn voor het beschikbaar maken van welke informatie dan ook online.

## Contactgegevens

Contacten worden aangemaakt via de pagina met de lijst van contacten. Selecteer de knop `Nieuw` in de werkbalk om een nieuwe vermelding toe te voegen. Er is ook een **Gebruiker - Contactmaker**-plugin die automatisch een contact aanmaakt wanneer een nieuwe gebruiker wordt geregistreerd.

In het formulier **Contacten: Bewerken**, voer de gegevens in die je beschikbaar hebt over het contact.

![screenshot gegevensinvoer](../../../en/images/contacts/contact-data-entry.png)

**Opmerkingen:**

In de screenshot werd de **Positie** ingevoerd als *Voorzitter*, wat logisch was in de context van een categorielijst van commissieleden, maar het heeft geen zin in de context van een lijst van Uitgelichte contacten die bestaat uit alle Voorzitters van alle commissies. Dit moet specifieker zijn: *Voorzitter van de Commissie voor Cultuur, Media en Sport*.

De velden **Eerste…**, **Tweede…** en **Derde Sorteerveld** hebben woorden nodig die voor elke invoer zijn toegevoegd om sortering mogelijk te maken door een door de gebruiker gedefinieerde volgorde, zoals een conventionele achternaam-voornaam-volgorde. Dit wordt later in dit artikel behandeld.

De tab **Diversen** bevat een tekstbewerkingsveld met een korte persoonlijke verklaring.

De tab **Extra** bevat de aangepaste velden *Partij* en *Kiesdistrict*.

De tab **Formulier** bevat instellingen voor het e-mailcontactformulier. Als er geen e-mailadres is ingevoerd, wordt dit veld niet weergegeven.

## Contactweergave

De Contact-component biedt vier menu-items om contactgegevens weer te geven:

* Enkel Contact
* Uitgelichte Contacten
* Lijst van Contacten in een Categorie
* Lijst van Alle Contacten in een Categorieboom

Het is een goed idee om elk menutype uit te proberen om te zien hoe de output eruitziet.
Enkele voorbeelden:

### Lijst Alle Categorieën in een Contacten Categorieboom

In dit geval bestaat de categorieboom uit een hoofdcategorie en twee subcategorieën:
```
House of Commons
- Business Commissie
- Cultuur Commissie
```
![alle categorieën in een categorieboom](../../../en/images/contacts/contact-all-committees.png)

De tweede regel van elke inzending komt uit de Categorie Beschrijving.

Als je een van de Commissie-links selecteert, kan de Commissiepagina er als volgt uitzien:

![contacten in een categorie](../../../en/images/contacts/contact-culture-committee.png)

De lay-out is niet helemaal naar wens. Het zou goed zijn geweest om een
miniatuurafbeelding van elk individu en een betere lay-out van de details op te nemen. Dat
kan worden gedaan met een sjabloonoverride (later).

### Lijst Contacten in een Categorie

Voor de Business Commissie is er een Lijst Contacten in een Categorie-menu-item.
Dat zorgt ervoor dat een andere lay-out wordt gebruikt:

![contact categorie lijst](../../../en/images/contacts/contact-category-list.png)

Beter maar nog steeds niet helemaal goed! Een stijl-override was nodig om de
afbeelding stijl te verminderen. Opnieuw lijkt het dat een sjabloonoverride nuttig kon zijn.

### Uitgelichte Contacten

Voor dit voorbeeld werden de Voorzitters van alle commissies als uitgelicht gemarkeerd.

![uitgelichte contacten](../../../en/images/contacts/contact-featured.png)

## Sorteervolgorde

De volgorde waarin contacten verschijnen kan worden ingesteld in de opties van de Contact-component of in een menu-item. Het laatste overschrijft het eerste indien ingesteld. De beschikbare instellingen zijn als volgt:
* **Naam** De naam van het contact. Dit is mogelijk niet geschikt voor alfabetische volgorde.
* **Sorteernaam** Dit zijn de drie *Sorteerveld* velden in het Contact-dataformulier die eerder zijn genoemd.
* **Volgorde** Dit is de volgorde waarin contacten verschijnen in de Contactenlijst.
* **Uitgelichte Contacten Volgorde** Uitgelichte contacten verschijnen vóór andere contacten, maar verder worden contacten in volgorde van de lijst weergegeven.

*Vertaald door openai.com*

