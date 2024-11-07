<!-- Filename: Enabling_the_Login_Form_module / Display title: Inlogformulier  -->

## Inlogmethoden voor de site

Er zijn twee manieren om geregistreerde gebruikers in te laten loggen op de frontend van een website. Er is een **Inlogformulier** menu-item te vinden in de Gebruikersgroep van menu-items. De *Toegang* permissies hiervan moeten ingesteld zijn op *Gast*. Een tweede *Uitloggen* menu-item is nodig met de *Toegang* permissies ingesteld op *Geregistreerd*.

Het alternatief is de **Inlogformulier** module. Deze is standaard geïnstalleerd in de *sidebar-right* positie bij een nieuwe Joomla-installatie. Deze module kan verplaatst worden naar een andere positie, gepubliceerd, in de prullenbak geplaatst of verwijderd worden. Deze acties zijn van toepassing op een instantie van de module en niet op de modulecode. Zo kun je een nieuw *Inlogformulier* module maken of een duplicaat, bijvoorbeeld voor gebruik in verschillende sjablonen. De Inlogformulier module verandert na inloggen de weergave om een *Uitloggen* knop te tonen.

## Het Inlogformulier Module

Om een ongepubliceerd inlogformulier te publiceren:

* Selecteer **Content → Site Modules** vanuit het Administrator menu.
* Zoek de **Inlogformulier** module.
* Als het **Status**-icoon een groene vink in een cirkel is, is het al ingeschakeld. Als het Status-icoon een grijs kruis is, is het momenteel uitgeschakeld. Selecteer het icoon om de module in te schakelen.
* Als de *Inlogformulier* module niet in de lijst staat, stel dan de Filteropties in, selecteer het veld *- Selecteer Status - op *Alle* of *Verwijderd* om te zien of het in de prullenbak is geplaatst. Zo ja, dan kan het worden gepubliceerd door het selecteren van het prullenbak-icoon.
* Als de Inlogformulier module ontbreekt, maak dan een nieuwe aan.

Om een nieuw inlogformulier of een tweede inlogformulier te maken:

* Selecteer **Content → Site Modules** vanuit het Administrator menu.
* Selecteer de **Nieuw**-knop uit de Toolbar.
* Selecteer uit de Modules-lijst het item **Inloggen**.
* Vul het *Modules: Inloggen* gegevensinvoerformulier in.
  - Voer een unieke Titel in.
  - Selecteer een sjabloonpositie of creëer een benoemde positie voor gebruik in een artikel.
  - Vul andere velden in zoals van toepassing.
* **Opslaan & Sluiten**
* Test of de module correct verschijnt op de frontend van de site.

## De Login Form-module toewijzen aan geselecteerde webpagina's

U kunt ervoor zorgen dat de Login Form-module op één of meer pagina's verschijnt door deze toe te wijzen aan geselecteerde Menu-items. Dit doet u met behulp van de velden in de groep Menu-toewijzing op het Module-bewerkingsscherm:

- Selecteer de tabblad **Menu-toewijzing**.
- De lijst **Module-toewijzing** heeft vier opties:
  - **Op alle pagina's**: De Login Form-module verschijnt op alle pagina's.
  - **Geen pagina's**: De Login Form-module verschijnt op geen enkele pagina.
  - **Alleen op de geselecteerde pagina's**: Een lijst van alle menu's en menu-items op uw
  site zal verschijnen. De Login Form-module verschijnt op de pagina's die in deze lijst zijn geselecteerd.
  - **Op alle pagina's behalve de geselecteerde pagina's:** De Login Form verschijnt op alle
  niet-geselecteerde pagina's.
- **Menu-selectie**: Toont een lijst van alle Menu's en Menu-items waarvan er één of meer kunnen worden geselecteerd. Dit veld wordt alleen gebruikt als het
  **Menu's**-veld is ingesteld op **Selecteer Menu-item(s) uit de lijst**.

  ![module menu toewijzing](../../../en/images/modules/modules-login-menu-assignment.png)

## De module Aanmeldformulier aanpassen

Als je het uiterlijk van de Aanmeldmodule wilt wijzigen, kun je stijlen toevoegen, zowel Bootstrap-stijlen als je eigen stijlen die gedefinieerd zijn in je sjabloonbestand user.css. Voeg de stijlen toe in het tabblad **Geavanceerd** van het bewerkingsformulier van de Modules: Aanmelden.

Als je de informatie wilt wijzigen die in het Aanmeldformulier wordt weergegeven, kun je een sjabloonoverschrijving maken. Zie de sectie over [Sjabloonoverschrijvingen](jdocmanual?article=user/templates/template-overrides) voor meer details.

*Vertaald door openai.com*

