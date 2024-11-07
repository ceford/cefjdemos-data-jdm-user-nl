<!-- Filename: Auto_redirect_guests_to_login / Display title: Leid gasten automatisch om naar inloggen  -->

## Gewenste Functionaliteit

Stel dat je enkele menu-opties hebt die vereisen dat een gebruiker is ingelogd,
zoals *Een Artikel Indienen*. Je wilt dat alle gebruikers het beperkte menu-item kunnen zien, ongeacht of ze zijn ingelogd of niet. Het gewenste gedrag is als volgt:

* Als de gebruiker is ingelogd, gaat de gebruiker direct naar het beperkte menu-item.
* Als de gebruiker niet is ingelogd, krijgt de gebruiker het inlogformulier te zien en gaat na 
succesvolle inlog door naar de beperkte pagina.
* Als de gebruiker niet geregistreerd is, heeft de gebruiker de optie om zich te registreren of naar een andere pagina te navigeren.

## Oplossing

Hier is hoe je dit doet in Joomla!.

1.  Creëer een nieuw menu uit de **Menu's** lijst, noem het bijvoorbeeld **Verborgen Menu**.
2.  Voeg enkele menu-items toe die alleen toegankelijk zijn voor geregistreerde gebruikers
    (bijvoorbeeld, *Dien een Artikel in*). Stel de vereiste toegangs­niveaus
    van deze menu-items in op **Geregistreerd**.
3.  Maak GEEN module voor het *Verborgen Menu*. Het zal niet worden
    weergegeven op enige pagina, dus het heeft geen module nodig.
4.  Creëer je *echte* menu, noem het bijvoorbeeld **Site Menu**, en het menu-item
    dat zal worden weergegeven voor alle gebruikers, bijvoorbeeld *Dien een Artikel in*.
    - Het menu-item zal een menu-itemtype hebben van **Menu Item Alias**, te vinden
      in de **Systeemkoppelingen** Menu Item Type.
    - De parameter *Menu Item* zal het *Dien een Artikel in* menu-item
      in het *Verborgen Menu* zijn.
    - Het Toegangs­niveau voor dit menu-item zal **Openbaar** zijn, aangezien iedereen
      het moet kunnen zien en gebruiken.
5.  Maak een module voor het *Site Menu* net zoals je dat doet voor elk menu.
6.  Als je sub-menu's wilt, zorg ervoor dat je de sub-menu items hebt toegevoegd in
    het **Site Menu** en niet in het **Verborgen Menu**.

Wanneer een gast (niet-ingelogde gebruiker) toegang krijgt tot de *Dien een Artikel in*
menu-optie, wordt deze doorgestuurd naar de inlogpagina. Als het inloggen succesvol is, wordt de gebruiker
doorgestuurd naar de beperkte **Dien een Artikel in** pagina. Als de gebruiker al is ingelogd,
is de doorverwijzing onmiddellijk.

## Voorbeeld

Voor de volgende menu-items:

1.  Home
2.  Blog
3.  Wiki
4.  Directory
5.  Advertenties
6.  FAQ's
7.  Winkel
8.  Contacteer Ons

Alle menu-items moeten voor iedereen zichtbaar zijn aan de voorkant, maar items 3, 4, 5, 6 en 7 moeten alleen toegankelijk zijn voor **Geregistreerde** gebruikers.

In dit geval bevinden menu-items 3 tot 7 zich in het *verborgen* menu met hun **Toegang**-parameter ingesteld op **Geregistreerd**. Items 3 tot 7 hebben *Alias* menu-items in het *echte* menu met hun **Toegang**-parameters ingesteld op **Publiek**.

*Vertaald door openai.com*

