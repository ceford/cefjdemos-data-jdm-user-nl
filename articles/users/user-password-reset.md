<!-- Filename: J4.x:User_Password_Reset / Display title: Wachtwoord Herstellen voor Gebruiker  -->

## Gebruiker Resetten

Als uw gebruikers toegang hebben tot inloggen op de site en een gebruiker kan zich ofwel de gebruikersnaam of het wachtwoord niet herinneren, is het het beste om te vereisen dat de persoon zelf de inloggegevens reset via de links in het inlogformulier:

![site gebruiker loginmodule](../../../en/images/users/user-site-login-module.png)

In elk geval leidt het selecteren van een link naar een formulier waarin het e-mailadres moet worden ingevoerd dat aan het account is gekoppeld:

![site wachtwoord vergeten reset formulier](../../../en/images/users/user-forgot-password-reset.png)

Het hele proces wordt uitgevoerd door de gebruiker zonder dat er tussenkomst van een beheerder nodig is. Dit is het formulier voor wachtwoordverificatie:

![site wachtwoord vergeten bevestigingsformulier](../../../en/images/users/user-forgot-password-confirm.png)

En ten slotte moet de gebruiker een nieuw wachtwoord invoeren:

![site wachtwoord vergeten reset voltooi formulier](../../../en/images/users/user-forgot-password-complete.png)

## Administrator Reset

Als er slechts één Administrator-login is, moet een wachtwoordreset door een Super User of Administrator worden uitgevoerd. Als de enige Super User de inloggegevens niet kent, bekijk dan het aparte artikel over Administrator Wachtwoordherstel. Anders:

- Selecteer **Gebruikers → Beheren** in het Administrator-menu of selecteer
  *Gebruikers* van het Hoofd Dashboard Site-paneel.
- Vind de gebruiker die een wachtwoordreset nodig heeft.
- Selecteer de gekoppelde **Naam** om het *Gebruiker: Bewerken* formulier te openen.
- Voer een nieuw wachtwoord in de velden Wachtwoord en Herhaal Wachtwoord in.
- Stel het veld **Wachtwoord Reset Vereisen** in op *Ja*.
- **Opslaan & Sluiten**

![administrators gebruikerediteer formulier](../../../en/images/users/users-edit-user-john-doe.png)

U moet vervolgens een e-mail sturen naar de gebruiker met het nieuwe tijdelijke
wachtwoord in platte tekst. Na inloggen kan de gebruiker de startpagina van de site zien, maar elke poging om naar een andere pagina te navigeren zal de gebruiker naar het nieuwe wachtwoordformulier brengen.

*Vertaald door openai.com*

