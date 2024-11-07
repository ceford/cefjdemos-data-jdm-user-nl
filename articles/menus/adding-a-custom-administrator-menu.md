<!-- Filename: J4.x:Adding_a_Custom_Administrator_Menu / Display title: Aangepast Beheerdersmenu  -->

## Introductie

Stel dat je een gebruiker hebt die je slechts één taak wilt laten uitvoeren op je website. Neem het geval van een organisatie die vestigingen over de hele wereld heeft en de enige taak die elke vestiging mag uitvoeren is om locaties op een kaart te plaatsen voor weergave op de site. De component voor deze taak is Ffmap, maar dat zal hier niet worden behandeld, anders dan de betrokken Administrator-menu-items.

Om deze taak te volbrengen, moet je een aangepaste gebruikersgroep creëren, een gebruiker aan die groep toewijzen en een aangepast menu maken voor gebruik door die gebruiker.

## Een Gebruikersgroep Maken

- Selecteer **Gebruiker → Gebruikers → Groepen** in het Beheerdersmenu.
- Selecteer de **Nieuw** knop in de Werkbalk.
  - Voer een **Titel voor de Groep** in, **'Afdeling'** in dit geval.
  - Selecteer **Publiek** als de bovenliggende groep. Dit is belangrijk - je wilt geen permissies erven van een andere groep.
- Selecteer **Opslaan en Sluiten** in de Werkbalk.

## Stel Wereldwijde Machtigingen Voor De Groep In

- Selecteer **Globale Configuratie** vanuit het Home Dashboard.
- Selecteer het tabblad **Machtigingen**.
- Selecteer het item **Branch**.
- Stel **Administrator Login** in op **Toegestaan**.
- Selecteer **Opslaan en Sluiten** in de Werkbalk.

Op dit punt kan elke gebruiker die is toegewezen aan de Branch Gebruikersgroep inloggen op de Administrator-interface en het Home Dashboard zien. Er kunnen dashboardmodules zichtbaar zijn omdat hun toegangsniveau is ingesteld op Openbaar, bijvoorbeeld: Ingelogde Gebruikers, Populaire Artikelen en Recent Toegevoegde artikelen. Het is het beste om de toegang tot deze modules in te stellen op Speciaal. Er zullen geen menu-items zijn die de gebruiker kan zien.

## Stel Componentmachtigingen voor de Groep in

Of:

- Selecteer de **Ffmap**-component in het Beheerdersmenu.
- Selecteer de **Opties**-knop van FFmap in de werkbalk om het configuratiescherm te openen.

Of:

- Selecteer **Globale Configuratie** op het Startdashboard.
- Selecteer Ffmap uit de lijst van componenten.

Vervolgens:

- Selecteer het tabblad **Machtigingen** en daarna het item **Branch**.
- Stel Toegang tot Beheerdersinterface, Maken, Verwijderen, Bewerken, Bewerkingstoestand,
  Eigen Bewerken en Bewerken Aangepaste Veldwaarde in op **Toegestaan**.
- Selecteer **Opslaan en Sluiten** in de werkbalk.

## Een nieuw Administrator-menu maken

- Selecteer **Menu → Beheren** in het Administrator-menu.
- Selecteer **Administrator** in de Site/Administrator keuzelijst.
- Selecteer de knop **Nieuw** in de werkbalk.
- Voer een titel in voor het menu, bijvoorbeeld **Vestigingsmenu** en een unieke id, bijvoorbeeld **vestigingsmenu**.
- Selecteer **Opslaan en sluiten** in de werkbalk.

## Module maken voor het menu

Selecteer in de lijst met menu's de knop **Gelinkte Modules** in het Branch Menu-record.

- Voer een titel in voor de module, bijvoorbeeld **Branch Menu**.
- Selecteer Menu om te tonen: **Branch Menu**.
- Zet Controleer Menu op **Nee**, anders zijn er waarschuwingsberichten over ontbrekende beheerdersfuncties.
- Selecteer de positie: **menu**.

## Maak een Container voor het Componentenmenu

- Selecteer in de lijst Menus het pictogram Menu-items voor het Branch Menu. Dit opent de lijst met items, die op dit moment leeg is.
- Selecteer de knop **Nieuw** in de werkbalk.
- Voer een titel in voor het menu-item: **Branch Componenten**.
- Selecteer het menu-itemtype **Selecteerknop**.
  - Scrol in het modale dialoogvenster naar het item **Systeemlinks** en vouw het paneel uit.
  - Selecteer het itemtype **Container voor Componentenmenu**.
- Terug in het menuconfiguratieformulier, selecteer **Toon Geen** om alle items in het Componentenmenu te verbergen (rood).
- Scrol naar de Ffmap-items en klik op de verbergknoppen om ze op Weergeven te zetten (groen).
- Selecteer **Opslaan en sluiten** in de werkbalk.

## Screenshot

![aangepaste beheerder menu component selectie](../../../en/images/menus/menus-custom-administrator-menu.png)

## Resultaat

Maak een gebruiker aan in de Branch Group om zelf mee te testen. Log in op de beheerdersinterface als die gebruiker om het resultaat te zien:

![resultaat aangepast beheerdersmenu](../../../en/images/menus/menus-custom-administrator-menu-result.png)

## Notities

Als je later een ander component toevoegt, wordt deze toegevoegd aan de Componentenmenucontainer en is deze standaard zichtbaar. Je zult terug moeten gaan naar het Administrator-menu-item en de nieuwe inhoud op Verbergen instellen.

Als het component is ingesteld om menu-items op te nemen in elk van de Administrator-lijstvoorkeuren, door middel van default.xml-bestanden, kun je menu-items direct toevoegen aan het aangepaste menu en het gebruik van de Componentenmenucontainer vermijden.

Het Branch Components-menu blijft onderdeel van het Administrator-menu - onvermijdelijke duplicatie!

*Vertaald door openai.com*

