<!-- Filename: J4.x:Administrator_Modules / Display title: Beheerdersmodules   -->

## Inleiding

De Atum Beheerder-sjabloon wordt geleverd met een volledige set van beheerdermodules die zijn geïnstalleerd en geconfigureerd voor dagelijks gebruik. De onderstaande illustratie toont de posities van het Home Dashboard om aan te geven waar modules zich bevinden.

![atum home dashboard posities](../../../en/images/modules/atum-template-positions.png)

In de bovenstaande illustratie zijn de panelen instanties van de Quick Icon-module die zijn gekoppeld aan quickicon-plugins.

### Opmerkingen over enkele Moduleposities

- **Custom Top** bevindt zich boven de banner en is nuttig als je een aangepast menu of een aangepaste module met een belangrijke boodschap wilt publiceren. Bijvoorbeeld om beheerders te waarschuwen dat de site binnenkort wordt gesloten voor systeemonderhoud.
- **Status** is voor de pictogrammen die rechts uitgelijnd in de Banner worden weergegeven.
- **Menu** bevindt zich in de linkerzijbalk van het Atum-scherm.
- **Toolbar** bevindt zich boven het hoofdinhoudsgebied in lijst- en bewerkschermen, maar is niet aanwezig in dashboardschermen.
- **Top** bevindt zich onder de Toolbar, maar boven een systeembericht en componentinhoud.
- **Bottom** bevindt zich onder de componentinhoud.
- **Debug** bevindt zich onder alles.

Atum sjabloonposities op naam

```xml
  <positions>
    <!-- direct gebruikt in de template -->
    <position>bottom</position>
    <position>cpanel</position>
    <position>customtop</position>
    <position>debug</position>
    <position>icon</position>
    <position>login</position>
    <position>menu</position>
    <position>sidebar</position>
    <position>status</position>
    <position>title</position>
    <position>toolbar</position>
    <position>top</position>
  </positions>
```

## Een Aangepaste Module Toevoegen

U wilt misschien een Aangepaste module toevoegen om beheerders te informeren over een systeemprobleem. Selecteer **Inhoud → Beheerdersmodules** in het beheerdersmenu. De lijst met geïnstalleerde modules is tamelijk lang:

![atum admin modules lijst](../../../en/images/modules/atum-admin-modules-list.png)

Selecteer de knop Nieuw en vervolgens de Aangepaste module. Voer in het bewerkingsformulier Modules: Aangepast een Titel in, een Aangepaste boodschap en selecteer een Positie voor de module. In het onderstaande voorbeeld is de Top-positie geselecteerd. Bovendien zijn in het tabblad Geavanceerd, in het veld Moduleklasse enkele stijlen ingevoerd om de tekst te centreren en wat ruimte toe te voegen: **alert alert-warning text-center**. Sla op om het resultaat te zien. Sluit om het resultaat op de Modules-lijstpagina te zien.

![atum aangepaste module bewerkings systeemboodschap](../../../en/images/modules/atum-admin-module-system-message.png)

Wanneer u klaar bent met het bericht, kunt u gewoon de Status-knop in de modulelijst selecteren om de module te depubliceren.

## Lijst van Beheerdersmodules

- **Actielogboeken - Laatste** Deze module toont een lijst van de meest recente acties.
- **Beheerdersdashboardmenu** Deze module toont een submenu voor beheerders.
- **Beheerdersmenu** Deze module toont een module voor het beheerdersmenu.
- **Artikelen - Laatste** Deze module toont een lijst van de meest recent aangemaakte artikelen.
- **Aangepast** Deze module stelt je in staat om je eigen module te creëren met een WYSIWYG-editor.
- **Feedweergave** Deze module stelt je in staat om een gesyndiceerde feed weer te geven.
- **Frontend-link** Deze module toont een link naar de frontend en is bedoeld om in de 'status'-positie te worden weergegeven.
- **Joomla! Versie-informatie** Deze module toont de Joomla!-versie en is bedoeld om in de 'status'-positie te worden weergegeven.
- **Ingelogde gebruikers** Deze module toont een lijst van de ingelogde gebruikers.
- **Inlogformulier** Deze module toont een inlogformulier met gebruikersnaam en wachtwoord. Het mag niet worden gedepubliceerd.
- **Inlogondersteuningsinformatie** Deze module toont enkele nuttige links naar Joomla-ondersteuningssites op het inlogscherm.
- **Berichten** Deze module toont het aantal privéberichten en is bedoeld om in de 'status'-positie te worden weergegeven. Het wordt alleen weergegeven wanneer er berichten zijn om te lezen.
- **Meertalige status** Deze module toont de status van de meertalige parameters en is bedoeld om in de 'status'-positie te worden weergegeven.
- **Populaire artikelen** Deze module toont een lijst van de meest populaire gepubliceerde artikelen die nog actueel zijn. Sommige die worden getoond, kunnen zijn verlopen, ook al zijn ze de meest recente.
- **Berichten na installatie** Deze module toont een teller en een link naar de laatste berichten na installatie. Het wordt alleen weergegeven wanneer er berichten zijn om te lezen.
- **Privacydashboard** De Privacydashboardmodule toont informatie over privacyverzoeken.
- **Privacystatuscontrole** De Privacystatuscontrolemodule toont informatie over de privacystatus van je site.
- **Snelle pictogrammen** Deze module toont snelle pictogrammen die zichtbaar zijn op het thuisdashboard (startpagina van het beheerdersgebied).
- **Voorbeeldgegevens** Deze module laat je voorbeeldgegevens installeren.
- **Statistieken** De Statistiekenmodule toont informatie over je serverinstallatie samen met statistieken over de websitegebruikers en het aantal artikelen in je database.
- **Titel** Deze module toont de titel van de toolbarcomponent.
- **Werkbalk** Deze module toont de werkbalkpictogrammen die worden gebruikt om acties in het hele beheerdersgebied te beheren.
- **Gebruikersmenu** Deze module toont het gebruikersmenu en is bedoeld om in de 'status'-positie te worden weergegeven.

