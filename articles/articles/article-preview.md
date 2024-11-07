<!-- Filename: J4.x:Article_Preview / Display title: Artikel: Voorvertoning -->

## Introductie

Het kan nuttig zijn om een artikel te bekijken voordat het gepubliceerd wordt. Er is een *Voorvertoning* knop in de werkbalk van het backend *Artikel: Bewerken* formulier voor dit doel. Echter, deze functie gebruikt het opgeslagen artikel en niet de inhoud van het bewerkingsformulier. De Voorvertoning-functie is niet beschikbaar in het frontend artikel bewerkingsformulier.

Mogelijk wil je een artikel niet zichtbaar maken tot het klaar is. Voor dit doel zijn verschillende strategieën nodig voor frontend en backend editors.

## Frontend Voorbeeld

De enige manier om een artikel semi-privé te houden vanaf de frontend is door de Toegang in te stellen op *Geregistreerd*, zodat alleen ingelogde gebruikers het kunnen zien.

- Log in op de frontend van de website.
- Selecteer de *Bewerken* link voor een artikel dat moet worden bijgewerkt. Of...
- Selecteer de knop *Nieuw Artikel* onder blogindelingen.
  - Stel het toegankelijkheidsniveau van het artikel in op *Geregistreerd* totdat het klaar is voor publicatie.
  - Je zou een *Waarschuwing* kunnen toevoegen met de mededeling dat het artikel in aanbouw is: `<div class="alert alert-warning">In Aanbouw</div>`.
- *Opslaan & Sluiten* om het artikel te zien.

## Backend Voorbeeld

Na in te loggen op de Beheerdersinterface:

- Selecteer een artikel om te bewerken of maak en sla een nieuw artikel op.
- Om een nieuw artikel voorlopig privé te houden, stel de Status in op *Niet gepubliceerd* of laat het op *Gepubliceerd* staan en pas de datum *Start Publiceren* aan.
- Breng wijzigingen aan en *Bewaar* het artikel.
- Selecteer de knop *Voorbeeld* in de Werkbalk. Er zou een pop-upvoorbeeldvenster moeten verschijnen.
- Als je een bericht krijgt dat *De gevraagde pagina niet kan worden gevonden*, log dan in op de Frontend en probeer het opnieuw.
- Om het Voorbeeldvenster te sluiten, selecteer de *X* knop in de rechterbovenhoek.

![Het voorbeeldvenster](../../../en/images/getting-started/article-edit-preview.png)

*Vertaald door openai.com*

