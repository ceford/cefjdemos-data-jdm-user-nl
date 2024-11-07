<!-- Filename: jdocmanual?manual=user&heading=news&filename=news-feeds.md / Display title: Nieuwsfeeds -->

## Inleiding tot Nieuwsfeeds

Er was eens een tijd dat het gebruikelijk was voor een website om nieuwsitems van externe websites weer te geven op een pagina of in een paneel. Browsers hadden zelfs ingebouwde Nieuwslezers om precies dat te doen. De tijden veranderen en de grote browsers bieden die optie niet langer aan. En er zijn nieuwe methoden om site-inhoud te delen, vooral met social media-sites.

De methode om nieuws te delen is *Really Simple Syndication*, meestal afgekort tot **RSS**, en dit heeft nog steeds een plaats in websitepromotie. De volgende schermafbeelding toont *NetNewsWire*, een gratis en open source RSS-lezer voor Mac. Andere RSS-lezers zijn beschikbaar voor andere platforms. De illustratie toont de **Joomla! Aankondigingen** RSS-feed geselecteerd. Tien aankondigingen worden vermeld met titel en korte beschrijving. De geselecteerde aankondiging wordt volledig weergegeven in de rechterkolom.

![RSS-feed van Joomla Aankondigingen](../../../en/images/news-feeds/news-netnewswire-display.png "Joomla Aankondigingen")

Stel je eens voor wat een of meer RSS-feeds voor jouw website zouden kunnen doen!

## Een Nieuwsfeed Inrichten

Je website heeft standaard Nieuwsfeeds ingericht. Een pas geïnstalleerde Joomla 5-website heeft deze twee regels nabij de bovenkant van de broncode van de Homepage:

```
<link href="/j51/index.php?format=feed&amp;type=rss" rel="alternate" type="application/rss+xml" title="Home">
<link href="/j51/index.php?format=feed&amp;type=atom" rel="alternate" type="application/atom+xml" title="Home">
```
Deze regels maken het mogelijk voor geautomatiseerde systemen om zowel RSS als Atom Feeds te gebruiken. Atom is een latere en iets andere nieuws-syndicatie specificatie. De regels zullen aanwezig zijn op alle **Featured** pagina's en **Category Blog** pagina's, maar niet op de meeste andere paginatypen. Je kunt de opname van deze RSS-feeds uitschakelen als je dat wilt.

## RSS-feedlink In-/Uitschakelen

De globale instelling van de RSS-feedlink bevindt zich op het tabblad **Integratie** op de pagina Artikelen: Opties. Stel deze in op *Weergeven* of *Verbergen* naar eigen inzicht. De standaardinstelling is **Weergeven**.

De globale instelling kan worden overschreven in een categorieblogmenu-item. Selecteer opnieuw het tabblad *Integratie* en stel de *RSS-feedlink* in op *Weergeven* of *Verbergen*.

De RSS-feed kan niet verborgen worden op een homepage met uitgelichte artikelen (bug?)!

## De Module voor Syndicatief feeds

Er is een kernmodule die je kunt plaatsen op Uitgelichte of Categorie Blogpagina's om een sindicatie-link te bieden. Vul de velden in het Module-tabblad in. De meeste hebben geschikte standaardinstellingen. Als het Label-veld leeg wordt gelaten, is het standaard Engelstalige label *Feed Entries*. Selecteer in het tabblad *Menu Toewijzing* **Op alle pagina's**. De module zal alleen verschijnen op Uitgelichte en Categorie Blogpagina's.

![Gegevensinvoer syndicatief feeds](../../../en/images/news-feeds/news-syndication-feeds-form.png "Gegevensinvoer syndicatief feeds")

Vergeet niet de module aan een *Positie* toe te wijzen en deze *Gepubliceerd* te maken.

In de weergave van de sitepagina toont de module een link. Deze is niet bedoeld om op te klikken, tenzij je een lokale Nieuwslezer hebt geconfigureerd. De link moet worden gekopieerd voor gebruik in een Nieuwslezer op een andere site of Nieuwslezer-applicatie.

![Weergave syndicatief feeds](../../../en/images/news-feeds/news-syndication-feeds-display.png "Weergave syndicatief feeds")

Merk op dat de link betrekking heeft op de items op die pagina. Dus als je site meerdere categorie blogpagina's heeft, zal je verschillende RSS-feeds hebben.
*Vertaald door openai.com*

