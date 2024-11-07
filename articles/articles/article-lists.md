<!-- Filename: J4.x:Article_Lists / Display title: Artikel: Bewerken - Lijsten -->

## Lijsttypen

HTML heeft drie soorten lijsten:

- Ongeordende lijsten worden vaak gestyled met een inspringing en een punt,
  zoals deze lijst.
- Geordende lijsten zijn vergelijkbaar maar worden gemarkeerd met nummers.
- Definitielijsten bestaan uit titels en definities.

De opsommingstekens en nummers worden door de browser toegepast uit een
selectie van stijlen. De gebruiker mag geen opsommingsteken of nummertekst
invoeren, omdat dat als onderdeel van de lijst wordt behandeld. De TinyMCE-editor heeft
pictogrammen om veelvoorkomende opsommingstekens en nummerstijlen toe te passen. Definitielijsten
zijn ingewikkelder en moeten met de hand worden vervaardigd.

Lijsten kunnen andere lijsten bevatten tot elk niveau, hoewel diep inspringende
lijsten moeilijk leesbaar worden, dus het is het beste om bij één of twee niveaus te blijven.

## Screenshot

De volgende screenshot toont een ongeordende lijst met twee niveaus van inspringing. Het toont ook de volledige gereedschapsset die wordt geopend door op de ellipsknop (…) aan het einde van de eerste rij gereedschapsiconen te klikken.

![Geneste ongeordende lijsten](../../../en/images/articles/articles-edit-lists.png)

Deze screenshot zal worden gebruikt om uit te leggen hoe de opsommingstekens zijn gemaakt met behulp van de tools *Opsommingstekens*, *Inspringing vergroten* of *Inspringing verkleinen*:

## Lijststijlen

### Opsommingslijsten

Drie stijlen zijn beschikbaar:

- Een gevulde cirkel is de standaard.
- Een open cirkel.
- Een gevulde vierkant.

De naar beneden wijzende chevron rechts van het opsommingstekenpictogram opent een klein paneel waarmee de voorkeursstijl kan worden gekozen voor een geselecteerd lijstitem:

![Hulpmiddelen voor manipulatie van opsommingslijsten](../../../en/images/articles/articles-edit-list-bullets.png)

Het lijstpictogram werkt als een schakelaar. Als de cursor in een alinea staat en een opsommingsteken is geselecteerd, wordt de alinea een lijstitem. Als het opsommingsteken opnieuw wordt geselecteerd, verandert het lijstitem weer in een alinea.

Als twee of meer alinea's zijn geselecteerd en een lijstpictogram is geselecteerd, wordt elke alinea een lijstitem. Om een ingesprongen lijst te maken, selecteer je het *Inspringing vergroten* hulpmiddel rechts van de Lijst-hulpmiddelen. Standaard neemt het ingesprongen lijstitem de volgende lijststijl aan.

Zo maak je de ingesprongen lijsten in de schermafbeelding:

- Typ elk van de termen als eenparige woordalinea's.
- Selecteer alle alinea's die in een opsomming moeten komen.
- Selecteer het *Opsommingslijst* pictogram.
- Selecteer de eerste groep termen die ingesprongen moeten worden.
- Selecteer het *Inspringing vergroten* pictogram.
- Selecteer de tweede groep termen die ingesprongen moeten worden.
- Selecteer het *Inspringing vergroten* pictogram.

### Genummerde lijsten

Zes stijlen zijn beschikbaar:

- Nummers: 1, 2, 3 ...
- Letters: a, b, c ...
- Griekse tekens: &alpha;, &beta;, &gamma; ...
- Kleine Romeinse cijfers: i, ii, iii ...
- Hoofdletters: A, B, C ...
- Hoofdletters Romeinse cijfers: I, II, III ...

![Hulpmiddelen voor manipulatie van genummerde lijsten](../../../en/images/articles/articles-edit-list-numbers.png)

Genummerde lijsten werken iets anders. Wanneer een lijstitem wordt ingesprongen, neemt het de eerste numerieke waarde aan en schuiven de nummers van de rest van de lijst op zodat de lijst altijd in de juiste numerieke volgorde staat.

### Gemengde lijsten

Het nummersysteem kan op elk niveau worden gewijzigd. Je zou bijvoorbeeld het eerste niveau kunnen instellen om numerieke waarden te gebruiken en het tweede niveau om opsommingspunten, of Griekse tekens, of iets anders te gebruiken.

Het is waarschijnlijk het beste om te experimenteren met lijsten om te zien hoe ze gemanipuleerd kunnen worden.

## Definitielijsten

Definitielijsten bestaan uit een *Definitietitel* en een of meer *Definitieomschrijvingen*, gevolgd door de volgende *Definitietitel* en de bijbehorende *Omschrijving*. Ze zouden goed zijn voor een *Woordenlijst* of een set van sleutel/waarde-paren. Om een definitielijst te maken:

- Selecteer de knop *Toggle Editor* om de HTML-artikelopmaak te bekijken.
- Typ de opmaak voor de Definitielijst in. Hier is een voorbeeld:
```html
<dl>
<dt>Amfibie</dt>
<dd>Koudbloedige gewervelde die eieren in water legt en een aquatische larvaal stadium heeft.</dd>
<dt>Reptiel</dt>
<dd>Koudbloedige gewervelde die eieren op land legt.</dd>
</dl>
```
Sla op en bekijk het resultaat in de Voorvertoning.

*Vertaald door openai.com*

