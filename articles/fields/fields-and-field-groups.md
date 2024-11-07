<!-- Filename: J4.x:Fields_and_Field_Groups / Display title: Velden en veldgroepen  -->

## Introductie

Velden worden gebruikt om extra attributen van Artikelen, Contacten of Gebruikers weer te geven. De gegevens worden ingevoerd in een Administrator Bewerken-formulier en weergegeven op de Site. Een voorbeeld:

Stel dat je artikelen schrijft over aspecten van de natuur, soms Bloemen, soms Dieren. Een veld dat je mogelijk wilt vastleggen en weergeven voor beide is de Latijnse Naam, waarvoor een tekstveld nodig is. Een ander kan Habitat zijn: Bos, Vijver, Weide, enzovoort, waarvoor een vervolgkeuzelijst nodig is. Voor bloemen wil je misschien de Bloeitijd vastleggen met behulp van 4 selectievakjes, één voor elk seizoen, of 12 selectievakjes, één voor elke maand.

Lege velden in het invoerformulier worden niet weergegeven in de Site-uitvoer, dus je zou alle velden in één lange lijst kunnen bewaren. Maar meestal is het beter om categorieën voor je Artikelen te gebruiken, bijvoorbeeld Bloemen en Dieren. Velden kunnen aan meer dan één Categorie worden toegewezen. Dus de velden Latijnse Naam en Habitat zouden aan beide worden toegewezen, maar Bloeitijd zou alleen aan de categorie Bloemen worden toegewezen.

Als een veld niet aan een groep is toegewezen, verschijnt het in het Bewerken-formulier in een tabblad Velden. Als een veld aan een groep is toegewezen, verschijnt het in een tabblad met die naam. Dus voor de groep Bloemen lijkt het gepast om een veldgroep aan te maken genaamd Bloemgegevens (of gewoon Bloemen, hoewel het gebruik van dezelfde naam voor verschillende dingen verwarrend kan worden). En voor de andere algemene velden zou je een groep Natuur kunnen gebruiken.

## Een Uitgewerkt Voorbeeld - Natuur Aantekeningen

Voor artikelen over Natuur kunnen de artikelcategorieën en subcategorieën voor elke tak van de levende wereld eruitzien zoals in het volgende voorbeeld:

![Artikelcategorieën voor natuur](../../../en/images/fields/fields-articles-categories-list.png)

Enkele opvallende kenmerken van Natuur om op te merken:

- De categorie Natuur is voor artikelen die over de natuur in het algemeen gaan in plaats van over specifieke soorten planten of dieren.
- De subcategorieën zijn voor artikelen die specifieker zijn en zij kunnen hun eigen subcategorieën nodig hebben.
- Alle levensvormen hebben Algemene namen en Latijnse Namen.
- Bloemen en Bomen hebben een Bloeiseizoen, Hoogte en Spreiding, maar Vogels en Zoogdieren niet.
- Vogels hebben Spanwijdte en Lengte, terwijl Zoogdieren Hoogte en Lengte hebben.
- Kleur kan constant of gevarieerd zijn.

Het punt hier is dat het nodig kan zijn om Veld- of Veldgroepen op te zetten voor gemeenschappelijke kenmerken, zoals Latijnse Naam, en aparte Veldgroepen voor elke natuurcategorie.

## Veldgroepen

Het maken van veldgroepen voor artikelen is heel eenvoudig:

- Selecteer **Inhoud → Veldgroepen** in het beheerdersmenu.
- Selecteer de **Nieuw**-knop in de werkbalk.
- Voer een geschikte **Titel** in.
- Voer een **Beschrijving** in. Deze verschijnt onder het veld in het artikelbewerkingsformulier wanneer *Inline Help Inschakelen* is geselecteerd.
- Selecteer **Opslaan & Sluiten** in de werkbalk.

![Lijst met inhoud veldgroepen](../../../en/images/fields/fields-field-groups-list.png)

### Volgorde

Invoervelden uit veldgroepen verschijnen in de volgorde die zichtbaar is in deze lijst. Sleep items om de volgorde te wijzigen.

## Velden

Om een nieuw artikelveld aan te maken, selecteer **Content → Velden** in het 
Administrator-menu en vul het formulier in. Enkele voorbeelden worden hieronder 
geïllustreerd.

### Tekst - Latijnse Naam

Let op dat in de onderstaande schermafbeelding dit veld is toegewezen aan de 
Nature Veldgroep en aan de Nature categorie. Dit zorgt ervoor dat het altijd verschijnt 
in artikelen in de Nature categorie en alle subcategorieën.

![Tekstveld - latijnse naam in natuur groep](../../../en/images/fields/fields-latin-name.png)

### Selectievakjes - Bloeiseizoen

Selectievakjes verschijnen in het Artikel Bewerkingsformulier zodat u deze kunt aanvinken 
om het bloeiseizoen te selecteren. In de artikelweergave worden alleen de aangevinkte 
seizoenen vermeld. Bijvoorbeeld, als u Lente en Zomer aanvinkt, zal de uitvoer laten zien: 
Bloeiseizoen: Lente, Zomer.

Let op dat in deze schermafbeelding het veld is toegewezen aan de Bloemen 
groep en aan de Bloemen categorie. Dit zou ervoor moeten zorgen dat het veld 
alleen voorkomt in artikelen over bloemen.

![Selectievakje veld - bloeiseizoen](../../../en/images/fields/fields-flowering-season.png)

### Kleur - Kleur

Om verwarring te zaaien, is de naam van het veldtype Color (Amerikaanse spelling) 
maar het label in de documentatie is Colour (Britse spelling).

![Kleur veld](../../../en/images/fields/fields-colour.png)

Het Kleur veld is toegewezen aan de Nature veldgroep en de Nature categorie 
aangezien het niet uniek is voor bloemen.

### Integer - Winterhardheid

De winterhardheid van een plant kan worden weergegeven als een geheel getal van 1 tot 7. Er is 
geen veld voor een reëel getal, dus lengte en breedte zouden gehele getallen kunnen zijn met een schaal 
(cm of m of ft) opgenomen in het label. Er zijn *Prefix* en *Suffix* instellingen 
in het *Opties* tabblad. Als er geen duidelijke bovengrens is, laat dan het *Laatste:* 
veld leeg.

![Winterhardheid veld](../../../en/images/fields/fields-hardiness.png)

RHS Winterhardheid is een eigenschap die gewoonlijk wordt toegepast op bloemen!

Er is een probleem met het integer veld. Het heeft altijd een waarde en verschijnt 
dus altijd in de uitvoer. U kunt dat probleem omzeilen met een sjabloonoverride 
voor *Plugins / Integer*. Bijvoorbeeld, u zou een waarde boven of onder de verwachte limieten kunnen gebruiken om het veld uit de uitvoer weg te laten.

## Formulier voor het Bewerken van Artikelen

Wanneer een nieuw formulier voor artikelen wordt geopend, is de standaardcategorie
Ongecategoriseerd en bevatten de formulier tabbladen niet de tabs Velden en Bloemen.
Selecteer de categorie Bloemen en het formulier wordt opnieuw geladen met die
tabs aanwezig.

### Natuur Tab

![Bluebell artikel natuur tab](../../../en/images/fields/field-article-bluebell-nature-tab.png)

- **Latijnse Naam** Dit is een tekstinvoerveld, dus het is enkel een kwestie van
  het intypen van de Latijnse naam van welke levensvorm het artikel behandelt.
  De categorie Natuur behandelt echter het leven in het algemeen, evenals
  specifieke dieren of planten. Daarom is dit geen *verplicht* veld.
- **Kleur** Het kleurselectieveld kan zowel invoer van een hexadecimale kleurwaarde
  via het toetsenbord als een keuze uit de kleurkiezertool accepteren. Het hexgetal
  is xrrggbb waarbij rr roodwaarden zijn, gg groenwaarden en bb blauwwaarden zijn.
  Bij de uitvoer geeft de site de hexwaarde weer, wat niet erg nuttig is!

### Bloemen Tab

![Bluebell artikel natuur tab](../../../en/images/fields/field-article-bluebell-flowers-tab.png)

- **Bloeitijd** Het selectievakveld – blauwe druifjes zijn bekende lentebloemen
  dus de selectie van één selectievakje is passend.
- **Winterhardheid** Het geheel getal veld. Er is hier een probleem - er is
  geen methode beschikbaar om dit veld leeg te laten. Dus het is altijd aanwezig
  in de uitvoer, zelfs voor meer algemene artikelen over bloemen waar het niet
  passend is. Er is een oplossing die een sjabloonoverschrijving inhoudt.

## Resultaat van de Site

Bekijk het resultaat dat op uw site te zien is. In dit voorbeeld is een menu-item voor een enkel artikel gemaakt:

![Bluebell artikel siteweergave](../../../en/images/fields/field-article-bluebell-site.png)

### De hex Kleur

De standaardgegevensweergave is de hex kleurwaarde, wat niet erg nuttig is. De eenvoudige oplossing is om een sjabloonoverride te maken voor de velden / kleur plugin, zoals getoond in de bovenstaande screenshot.

Vervang gewoon deze regel:
```
echo htmlentities($value);
```
door deze regels:
```
if (is_array($value)) {
  $list = [];
  foreach ($value as $v) {
    $x = htmlentities($v);
    $list[] = '<span class="ps-5 pe-5" style="background-color: ' . $x . ';">&nbsp</span> ' . $x;
    echo implode(', ', $list);
  }
} else {
    $x = htmlentities($value);
    echo '<span class="ps-5 pe-5" style="background-color: ' . $x . ';">&nbsp</span> ' . $x;
}
```
En de hex waarde zal voorafgegaan worden door een staaltje met de achtergrondkleur van de waarde.

*Vertaald door openai.com*

