<!-- Filename: How_do_you_add_a_PayPal_button%3F / Display title: Hoe voeg je een PayPal-knop toe? -->

Joomla!  3.x Joomla!  2.5

PayPal, Google Checkout en andere e-commerce sites bieden vaak een
HTML-code die je kunt gebruiken om links in te voegen zoals "Voeg toe
aan winkelwagen" en "Koop" knoppen in je website.

Het heeft de algemene voorkeur om een custom HTML module te maken in
plaats van de code in een artikel te plakken. Op deze manier kun je de
link in een module postitie op zoveel pagina's als je wilt. Je kunt ook
de module in een artikel plaatsen met gebruik van de  {loadposition
myposition}
opdracht.

## PayPal Technische Documentatie

Specificaties en voorbeelden van de HTML code wordt getoond in de
<a href="https://www.paypal.com/uk/webapps/mpp/standard"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">PayPal Website Payments Standard
Integration Guide</a>.

## HTML Editor Valkuilen

Je kunt dit type HTML code invoegen, inclusief formulieren, ofwel in een
artikel of in een aangepaste HTML module. De TinyMCE editor zal normaal
de HTML code weglaten. Als je probeert te plakken in sommige types van
HTML code met behulp van deze editor, zal het niet werken, de editor zal
de code verwijderen als je het artikel of de module opslaat.

### TinyMCE Editor Oplossing

Om dit probleem te vermijden tijdens het gebruik van de TinyMCE editor:

1.  Ga naar de gebruiker Manager en verander de gebruiker Editor in
    *Geen editor*.
2.  Ga naar het artikel of custom HTML module en plak in de gewenste
    HTML code.
3.  Ga terug naar de gebruiker manager en wijzig de gebruiker editor
    naar TinyMCE.

Let op dat je dit telkens moet herhalen als je de code wilt bewerken
(tenzij je de alternatieve oplossing hieronder gebruikt).

### JCE Editor Oplossing

1.  Installeer de JCE editor van:
    <a href="https://extensions.joomla.org/extension/jce/"
    class="external text" target="_blank" rel="noreferrer noopener">de
    Joomla Extensions Directory</a>
2.  Wijzig de standaard editor (Global Configuration \> Site \> Default
    WYSIWYG Editor) naar JCE vanuit TinyMCE. Je moet mogelijk ook de
    standaard editor voor andere gebruikers wijzigen.
3.  Ga naar het artikel of Custom HTML module en klik op de
    *toon/verberg* knop, die het edit vak verandert zodat het wordt
    toegestaan om HTML code in te voeren in plaats van WYSIWYG tekst.
4.  Plak de HTML code in de editor.

Wanneer je terug navigeert naar het artikel of module in de back-end,
zal het al ingesteld zijn op HTML input; de code wordt dan niet
onleesbaar. Dit is makkelijker dan iedere keer de gebruikersinstellingen
te wijzigen telkens als je de code wilt bewerken voor het testen van
verschillende knopinstellingen.

## Email verhullen Valkuilen

De PayPal code omvat een emailadres voor je website. Joomla! heeft een
plugin *Content - Email verhullen* dat probeert emails te verhullen in
artikelen. Als je PayPal code direct in een artikel wilt plakken, moet
je deze plugin misschien uitschakelen. Ga naar Extensies / Plugins, zoek
de plugin *Content - Email verhullen* en klik op het groene vakje in de
actieve kolom om deze uit te schakelen.

Plugins zijn niet verwerkt in modules, dus moet u gebruik maken van een
custom HTML module, je zult nog steeds in staat zijn om email verhulling
in te schakelen.

### Artikel Specifieke Email Verhulling Schakelaar

Je kan de email verhulling uitschakelen in een artikel door het invoeren
van *{emailcloak=off}* overal in het artikel voor het emailadres. Met
deze controle, hoef je niet de wereldwijde email te verhullen.

### Beveiligde Verkoper Account ID in plaats van het emailadres

PayPal biedt een veilige verkoper ID (een alfanumerieke reeks wordt
gebruikt in plaats van de verkoper emailadres) zonder kosten. Het is
beschikbaar voor web betalingen standaard voor klanten als ook de
extra-kosten plannen. Email verhullen is niet van invloed op het
beveiligde verkopers account ID.

## PayPal Knop Functie aangeroepen door een Joomla Menu Item

U kunt gebruik maken van een menu-item die functioneert als een
PayPal-knop. Bijvoorbeeld, de PayPal Winkelwagen knop stuurt gewoon een
zoekopdracht als onderdeel van een Uniform Resource Locator (URL) met
een HTML-formulier. U kunt een Joomla menu-item maken dat dezelfde
functie vervult.

In het Menu-Item Manager maak een nieuwe externe link menu-item. In het
Menu-Item sectie details, ga naar het Link veld en voer bij URL van het
formulier in:

    https://www.paypal.com/us/cgi-bin/webscr&business=myusername@mysite.com&cmd=_cart&display=1

Vervang "myusername@mysite.com" in het URL voorbeeld hierboven met de
unieke gebruikersnaam ""uw"' PayPal account.

Om de werking te testen in de PayPal Sandbox, pas de URL een beetje aan,
zodat *www.paypal.com* omgezet wordt naar *www.sandbox.paypal.com*.

    https://www.sandbox.paypal.com/us/cgi-bin/webscr&business=myusername@mysite.com&cmd=_cart&display=1
