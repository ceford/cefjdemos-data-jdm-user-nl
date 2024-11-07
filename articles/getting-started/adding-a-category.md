<!-- Filename: J4.x:Getting_Started:_Adding_a_Category / Display title: Een categorie toevoegen  -->

## Inleiding

Website-eigenaren met meer dan een handvol artikelen zouden moeten nadenken over hoe ze content het beste kunnen presenteren voor eenvoudige navigatie. Als je bijvoorbeeld een dierentuin, een museum, een minerale collectie of gewoon een grote tuin hebt, moet je misschien wel 1000 exemplaren beschrijven. Eén artikel voor elk exemplaar, met foto's, heeft een bepaalde organisatorische structuur nodig. Als de artikelen bestanden waren, zou je ze waarschijnlijk in een bestandsstructuur plaatsen. In een CMS zijn artikelen geen bestanden, maar categorieën zorgen voor een vergelijkbare boomachtige structuur. Voorbeeld:

| Categorie   | Subcategorieën                         |
|-------------|----------------------------------------|
| Zoogdieren  | Apen, Bavianen, Ongulaten, Honden, Katten   |
| Reptielen   | Slangen, Hagedissen, Krokodillen, Schildpadden   |
| Amfibieën   | Kikkers, Padden                           |
| Vogels      | Roofvogels, Eenden, Meeuwen, Vinken, Mezen   |
| Geleedpotigen | Spinnen, Vlinders, Bijen, Sprinkhanen    |
| Vissen      | Haaien, Zalm, Kabeljauw, Haring, Makreel |

Subcategorieën kunnen ook nog verdere subcategorieën hebben. Een maximale beheersbare diepte lijkt ongeveer zeven te zijn. Voor de bovenstaande tabel zou een museum meer hoofdcategorieën kunnen toevoegen:

```text
natuur -> leven -> dieren -> zoogdieren...
natuur -> leven -> planten -> bomen...
natuur -> mineralen...
geschiedenis -> Egypte...
wetenschap -> astronomie...
wetenschap -> scheikunde...
```

Stel je voor hoeveel exemplaren een nationaal of klein stadsmuseum bezit!  

## Typen Menu-items

Er zijn verschillende soorten menu-items ontworpen om te werken met categorieën:

- **Categorie Blog** Dit is een paginalayout met één of twee leidende
  artikelvoorbeelden, vaak over de volle breedte van de pagina, gevolgd door 
  meerdere artikelvoorbeelden in twee of drie kolommen en ten slotte een 
  pagineringsmechanisme om naar meer artikelen in dezelfde categorie te linken. 
  Het voorbeeld is de inhoud vóór een pagina-einde, vaak de eerste of tweede 
  alinea. Een *Startpagina* van een site is vaak een categorieblog die *Alle 
  Categorieën* omvat. Een *Uitgelichte Artikelen* layout lijkt op een categorieblog 
  en wordt ook vaak als startpagina gebruikt.
- **Categorielijst** Dit is een lijstlayout die een lijst van artikelen in 
  een categorie weergeeft. Het kan worden weergegeven met een zoekfilter om 
  het zoeken naar artikelen op titel, auteur, hits, tags of maand van 
  publicatie mogelijk te maken.
- **Lijst Alle Categorieën in een Artikelcategoriestamboom** Deze layout 
  lijst een categoriestamboom vanaf een gekozen oudercategorie. Elke tak is 
  inklapbaar en is het meest nuttig voor grote, complexe categoriestroomstructuren.

Menu-items worden in een later artikel behandeld.

## Een Categorie Maken

Het volgende voorbeeld gebruikt een zoogdieren-categorie, geïnspireerd door de bovenstaande lijst, om te demonstreren hoe je een nieuwe categorie aanmaakt:

![Categorie bewerk formulier](../../../en/images/getting-started/article-category-edit.png)

- Selecteer het **Inhoud** item in het Beheerdersmenu om het uit te vouwen.
- Selecteer het **+** icoon naast het *Categorieën* menu-item om het 
  Categorie-bewerkingsformulier te openen.
- Het formulier **Artikelen: Nieuwe Categorie** heeft slechts één verplicht veld: 
  de *Titel*, in dit geval *Zoogdieren*.
- Het veld **Beschrijving** is optioneel, maar het is het beste om het in te vullen aangezien het in sommige lijsten wordt gebruikt. Suggestie:<br>
  *Zoogdieren zijn warmbloedige dieren die levende jongen ter wereld brengen.*
- Het veld **Ouder** specificeert of dit een primaire categorie 
  (-Geen Ouder-) of een subcategorie is, die geselecteerd wordt uit de lijst met categorieën.
- **Opslaan en Sluiten** om terug te keren naar de **Artikelen: Categorieën** lijstpagina.

Deze categorie is nu beschikbaar voor gebruik bij artikelen.

*Vertaald door openai.com*  

