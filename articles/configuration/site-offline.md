<!-- Filename: J4.x:Site_Offline / Display title: Site Offline  -->

## Alleen voor sitegebruikers

Er kunnen momenten zijn waarop je jouw Joomla!-website tijdelijk niet beschikbaar wilt maken voor bezoekers. Er is een eenvoudige **Site Offline**-configuratieschakelaar voor dit doel die je van **Nee** naar **Ja** kunt wijzigen indien nodig. Als deze op *Ja* staat, zien alle sitebezoekers een offline berichtpagina met een inlogformulier. Het standaard offline formulier kan aangepast worden met een afbeelding:

![Site offline scherm](../../../en/images/configuration/site-offline.png)

De Site Offline-schakelaar is niet van toepassing op de beheerdersinterface, en gebruikers die kunnen inloggen op de backend kunnen blijven inloggen op de frontend. Frontend login wordt alleen geweigerd voor gebruikers in de groepen Geregistreerd, Auteur, Redacteur en Uitgever.

## Offline inschakelen

- Selecteer **Home Dashboard → Globale Configuratie** in het beheerdersmenu.
- Zet in het tabblad **Site** de schakelaar **Site Offline** op **Ja**.
- Vervolgens kunt u kiezen om
  - **Gebruik aangepaste boodschap** te gebruiken, wat de tekst is in het veld voor Aangepaste Boodschap. Of...
  - **De standaardboodschap van de sitetaal** die in het Engels **Deze site is gesloten voor onderhoud. Probeer het later opnieuw.** luidt of het equivalent in de geselecteerde sitetaal. Dit biedt ook de mogelijkheid om een afbeelding te selecteren. Of...
  - **Verbergen** zodat er helemaal geen boodschap wordt getoond.
- Selecteer **Opslaan & Sluiten** in de werkbalk.
- Voer het benodigde onderhoud uit.
- Keer terug naar het formulier Globale Configuratie.
- Zet de schakelaar Site Offline op **Nee**.
- Selecteer **Opslaan & Sluiten** in de werkbalk.

## Alle Gebruikers

U kunt de toegang tot uw website beperken door de Joomla-directory met een wachtwoord te beschermen. Alleen gebruikers die de gebruikersnaam en het wachtwoord voor toegang tot de directory kennen, kunnen de site openen. U kunt meer dan één dergelijke gebruiker instellen. Met het cPanel Hosting Configuratiescherm:

- Log in op uw cPanel-account.
- Selecteer in het gedeelte Bestanden **Directoriebescherming**.
- Als de root van uw site in een subdirectory van public_html staat:
  - Selecteer de public_html-directory
- Selecteer de Bewerken-knop voor de directory die uw site bevat (public_html als uw site in de web root staat).
- Vink het selectievakje **Beveilig deze directory met een wachtwoord.** aan.
- Voer een naam in voor de beveiligde directory: de standaard is mogelijk voldoende.
- Selecteer de knop **Opslaan**.
- Er verschijnt een succesbericht met een link om terug te gaan, selecteer deze.
- Maak een gebruiker aan voor toegang tot de beveiligde directory.
- Voer een gebruikersnaam in.
- Voer een wachtwoord in en herhaal dit (onthoud het of schrijf het op).
- Selecteer **Opslaan**.

Controleer nu of de directory een wachtwoord vereist om toegang te krijgen via het web. Wanneer u uw site bezoekt, wordt u gevraagd om uw gebruikersnaam en wachtwoord voor toegang tot de directory. Deze kunnen volledig verschillend zijn van uw Joomla-gebruikersnaam en -wachtwoord.

Om wachtwoordbescherming van de directory te verwijderen:

- Log in op uw cPanel-account.
- Selecteer in het gedeelte Bestanden **Directoriebescherming**.
- Als de root van uw site in een subdirectory van public_html staat:
  - Selecteer de public_html-directory
- Selecteer de knop **Bewerken** voor de directory die uw site bevat (public_html als uw site in de web root staat). Er wordt nu een slot symbool weergegeven en Ja onder de privé-kop.
- **Deselecteer** het selectievakje **Beveilig deze directory met een wachtwoord.**.
- Selecteer de knop **Opslaan**.

Om te verifiëren dat de wachtwoordbescherming is verwijderd, gebruik een andere browser om toegang te krijgen tot uw site of sluit en heropen uw huidige browser en bezoek uw site opnieuw. 

*Vertaald door openai.com*  

