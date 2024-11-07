<!-- Filename: J4.x:User_Registration / Display title: Gebruikersregistratie   -->

## Registratiebeleid

Op een Joomla-site mogen geregistreerde gebruikers inloggen om inhoud te bekijken of te handelen op inhoud die niet-geregistreerde gebruikers niet kunnen zien. Site-login en beheerderslogin worden afzonderlijk behandeld, hoewel er een globale configuratie-instelling is die toestaat dat ze worden gecombineerd. Sommige sites hebben een klein aantal gebruikers dat door een beheerder is aangemaakt. Andere sites hebben zoveel gebruikers dat ze zichzelf moeten registreren en hun accounts zelf moeten activeren. Hoe gebruikers zich registreren voor je site is geconfigureerd in het formulier *Gebruikers: Opties*.  

## Zelfregistratie Toestaan

Gebruiker zelfregistratie is standaard niet toegestaan. Elke nieuwe gebruiker moet worden aangemaakt door een Manager of Beheerder. Zelfregistratie kan worden toegestaan met enkele eenvoudige wijzigingen in het *Gebruikers: Opties* formulier.

- Selecteer **Gebruikers → Beheer** in het Beheerdersmenu.
- Selecteer de knop *Opties* in de Werkbalk.
- Stel **Gebruikersregistratie Toestaan** in op **Ja**.
- De **Nieuwe Gebruikers Registratiegroep** moet **- Geregistreerd -** zijn, tenzij er een goede reden is om iets anders te kiezen.
- De **Activering van Nieuw Gebruikersaccount** moet **Zelf** of **Beheerder** zijn.
  - Zelf: Gebruiker ontvangt een e-mail met een activatielink. Het account wordt geactiveerd wanneer de gebruiker op de activatielink klikt.
  - Beheerder: Gebruiker ontvangt een e-mail met een activatielink. Wanneer de gebruiker op deze link klikt, wordt de Sitebeheerder via e-mail op de hoogte gesteld. De Sitebeheerder moet dan het account van de gebruiker activeren.

![Gebruikersconfiguratie gebruikers opties tabblad](../../../en/images/users/users-configuration-user-options.png)

- **Opslaan & Sluiten**
- Voeg een *Login* module toe. Of
- Voeg een *Gebruikers: Inlogformulier* menu-item en een *Gebruikers: Uitloggen* menu-item toe.

## Zelfregistratie Uitschakelen

- Zet **Registratie van gebruikers toestaan** op **Nee**.

## Een Nieuwe Gebruiker Toevoegen

Als zelfregistratie niet is toegestaan, moet elke nieuwe gebruiker door een Administrator worden aangemaakt. Ga als volgt te werk:

- Selecteer het **Gebruikers +** pictogram in het Home Dashboard Site paneel. Of
- Selecteer **Gebruikers** → **Beheer +** uit het Administrator-menu.
- Vul het formulier **Nieuwe Gebruikersgegevens** in. De meeste velden hebben geschikte standaardwaarden.

![Pagina voor invoer van nieuwe gebruikersgegevens](../../../en/images/users/users-new-user.png)

- Selecteer het tabblad **Toegekende Gebruikersgroepen** en vink het vakje aan bij de gewenste gebruikersgroep. Standaard is 'Geregistreerd' aangevinkt.
- **Opslaan & Sluiten**.
- Controleer in de Gebruikerslijst of het nieuwe gebruikersaccount is Ingeschakeld (groen vinkje in de kolommen Ingeschakeld).

## Een Gebruiker Blokkeren

De beste manier om met een lastige gebruiker om te gaan, is door het gebruikersaccount te blokkeren in plaats van het te verwijderen. Deze maatregel kan worden gebruikt om de gebruiker te schorsen en kan worden teruggedraaid als de gebruiker belooft zich goed te gedragen. Het verwijderen van een account zou elke link naar door gebruikers bijgedragen content, zoals auteurschap van artikelen, verbreken en de gebruiker de mogelijkheid bieden om zich opnieuw te registreren met hetzelfde e-mailadres.

Om een gebruiker te blokkeren:

- Selecteer **Gebruikers → Beheren** in het Beheerdersmenu.
- Zoek de gebruiker in de *Gebruikers*-lijst. Gebruik indien nodig de tekstfilter.
- Selecteer het ingeschakelde pictogram dat verschijnt als een groen vinkje naast de gebruikersnaam. Een **Blokkeren**-label verschijnt bij zweven.

![Nieuwe invoerpagina gebruiker](../../../en/images/users/users-hover-block.png)

- Selecteer het *Ingeschakeld*-pictogram. De pagina wordt opnieuw geladen met het ingeschakelde pictogram dat verschijnt als een grijze kruis.

## Een gebruiker deblokkeren

Eenvoudig:

- Zet het *Ingeschakeld* pictogram terug naar een groene vink.

*Vertaald door openai.com*

