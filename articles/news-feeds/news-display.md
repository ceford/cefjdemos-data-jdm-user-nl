<!-- Filename: jdocmanual?manual=user&heading=news&filename=news-display.md / Display title: Nieuwsweergave  -->

## De Feedweergavemodule

Er is een kernmodule voor *Feedweergave* beschikbaar om nieuws van andere sites weer te geven. De volgende schermafbeelding toont het gegevensinvoerformulier met de URL van de Joomla Aankondigingen-nieuwsfeed. Let op dat het Aantal Woorden is ingesteld op 100. Anders kan de lengte van een aankondiging buitensporig zijn voor een zijbalkmodule.

![Gegevensinvoer feedweergavemodule](../../../en/images/news-feeds/news-joomla-news-form.png)

Het resultaat kan er onaantrekkelijk uitzien, maar kan worden verbeterd met enkele aangepaste stijlen in user.css:

![Gegevensinvoer feedweergavemodule](../../../en/images/news-feeds/news-joomla-news-display.png)

## Pagina's voor Feedweergave

Als alternatief voor het tonen van nieuws in een module kunt u een menu-item maken om een nieuwsfeed op een webpagina weer te geven. Vanuit het Administratormenu:

* Selecteer **Componenten / Nieuwsfeeds / Feeds**. U kunt eerst een categorie voor nieuws maken.
* Selecteer de **Nieuw** knop in de *Werkbalk*.
* Vul het formulier **Nieuwsfeeds: Bewerken** in:
    - De **Link** is de RSS-link die is gekopieerd van een externe bron.
    - De **Beschrijving** is optioneel.
    - Het **Opties** tabblad bevat items om de feed*weergave* te regelen.
* **Opslaan & Sluiten**

![Invoer van gegevens in de Nieuwsfeedcomponent](../../../en/images/news-feeds/news-feed-data-entry.png)

Maak een menu-item beginnend vanuit het Administratormenu:

* Selecteer **Menu's / Hoofdmenu** of een ander menu voor dit item.
* Selecteer **Nieuw** in de *Menu's: Items* Werkbalk.
* Gebruik in het **Menu-itemtype** de **Selecteer** knop om *Nieuwsfeeds / Enkele nieuwsfeed* te vinden en te selecteren.
* Vul de rest van het formulier passend in.
* **Opslaan & Sluiten**

![Invoer van gegevens in het Nieuwsfeedmenu-item](../../../en/images/news-feeds/news-feed-data-entry.png)

Probeer het uit: ga naar het Sitemenu en selecteer het Feedmenu-item.

![Weergave van de Nieuwsfeed](../../../en/images/news-feeds/news-feed-display.png)

Elk item in de feed is een `<li>` binnen een `<ul>` tag, dus standaard wordt het gemarkeerd met een bullet. Dit is minder duidelijk als de items lang zijn. U kunt uw eigen stijlen toepassen in *user.css*. Het volgende plaatst elk item in een aparte doos:

```css
ul.com-newsfeeds-newsfeed__items {
  list-style-type: none;
  padding-left: 0;
}

ul.com-newsfeeds-newsfeed__items > li {
  padding: 1rem;
  margin-bottom: 1rem;
  border: 2px solid navy;
}
```
Dit ziet er als volgt uit:

![Aangepaste weergave van de Nieuwsfeed](../../../en/images/news-feeds/news-feed-custom-display.png)

## Lijst Nieuwsfeeds in een Categorie

De pagina *Joomla! RSS Nieuwsfeeds* toont acht aparte nieuwsfeeds. Je zou een feed kunnen maken voor een aantal of allemaal en deze aan een categorie, bijvoorbeeld *Joomla Nieuws*, kunnen toewijzen. Vervolgens kun je een menu-item creëren waarbij de *Menu-itemtype* is ingesteld op *Lijst Nieuwsfeeds in een Categorie* en de Categorie op *Joomla Nieuws*.

![Nieuwsfeed per categorievorm van menu](../../../en/images/news-feeds/news-feed-menu-category-form.png)

Probeer het eens en bekijk het resultaat!
*Vertaald door openai.com*  

