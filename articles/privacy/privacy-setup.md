<!-- Filename: J4.x:Privacy_Setup / Display title: Privacy-instellingen -->

## Privacycomponent

De privacycomponent wordt gebruikt om privacy-informatie te beheren en om verzoeken tot informatie of verzoeken tot verwijdering van informatie te verzamelen. Het is gebaseerd op e-mailadressen en is daarom het meest van toepassing op geregistreerde gebruikers die een e-mailadres moeten opgeven bij de registratie. Het is ook van toepassing op gegevens van niet-geregistreerde gebruikers wier e-mailadressen via de contactcomponent zijn verstrekt. Het implementeert niet de toestemming voor het gebruik van cookies of tracking die vereist is door de AVG.

Wanneer persoonlijk identificeerbare informatie wordt verzameld, moet je ervoor zorgen dat:

- De gebruiker geïnformeerd is waarom je om deze informatie verzoekt, in duidelijke en begrijpelijke taal.
- De gebruiker weet welke gegevens je over hen verzamelt.
- De gebruiker weet waarvoor je de gegevens zult gebruiken.
- De gebruiker actief toestemming heeft gegeven voor jouw gebruik van de gegevens.

Meestal wordt deze informatie beschreven in een privacybeleidartikel.  

## Privacy Dashboard

Het privacy dashboard biedt een overzicht van de site **Privacyverzoeken** en **Privacystatus**. Om toegang te krijgen:

- Selecteer **Gebruikers → Privacy** in het beheerdersmenu.

![privacy dashboard](../../../en/images/privacy/privacy-dashboard.png)

Er worden standaard twee modules getoond in het Privacy Dashboard:

### Privacyverzoeken

Deze module biedt een overzicht van de huidige informatieverzoeken.

### Privacystatus

Deze module toont de status van opties waar site-eigenaren op moeten letten:

- **Gepubliceerde Privacyverklaring** stel een Privacyverklaring-artikel in het **Systeem - Privacytoestemming**-plugin in.
- **Gepubliceerd Verzoekformulier Menu-item** stel een menu-item in om geverifieerde gebruikers verzoeken te laten indienen.
- **Uitstaande Dringende Verzoeken** controleer op bevestigde verzoeken ouder dan de leeftijd die is gespecificeerd in de componentparameters (standaard 14 dagen) en waarschuw de site-eigenaar voor verzoeken die dringende aandacht vereisen.
- **E-mail Verzenden Ingeschakeld** de site moet in staat zijn e-mails te verzenden om informatieverzoeken te verwerken.
- **Databaseversleuteling** dit is relevant wanneer een externe database wordt gebruikt.

## Plugin: Systeem - Privacytoestemming

Als deze plugin is uitgeschakeld, geeft het Dashboard Privacy Status-paneel aan dat het Privacybeleid **Niet Beschikbaar** is en biedt het een link naar het bewerkingsformulier van de plugin. Wanneer ingeschakeld, vraagt de plugin elke nieuwe gebruiker die zich op uw site registreert om in te stemmen met het Privacybeleid. Alle bestaande gebruikers worden doorgestuurd naar hun gebruikersprofiel zodat ze kunnen instemmen.

Om toestemmingen in te stellen:

- Selecteer **Home Dashboard**→** Plugins** in het Administratormenu.
- Zoek de plugin **Systeem - Privacytoestemming** (niet te verwarren met de Privacy - Toestemmingen plugin).
- Selecteer om het gegevensinvoerveld van de plugin te openen.

![plugin systeem privacytoestemming](../../../en/images/privacy/plugin-system-privacy-consent.png)

- Stel de **Status** in op **Ingeschakeld**.
- Optioneel: Selecteer of maak een artikel om te linken vanaf het Registratieformulier. Of stel het Privacytype in op Menu-item en selecteer of maak een menu-item.
- Selecteer het tabblad **Vervaldatum** en **Schakel Inline Hulp in** voor een uitleg van elk veld. Schakel in en pas de parameters aan **als** u wilt dat toestemmingen verlopen na een geselecteerd aantal dagen.

### Privacytoestemmingsaantekeningen voor meertalige sites:

**Korte Privacyverklaring en Doorverwijsbericht** Als u de standaardtekst gebruikt, wordt deze weergegeven in de taal van de gebruiker. Het is niet mogelijk om de aangepaste tekst te vertalen. Als u de tekst wilt aanpassen en in meerdere talen wilt weergeven, moet u dit veld leeg laten en de taaloverschrijvingsfaciliteit van Joomla gebruiken om de `PLG_SYSTEM_PRIVACYCONSENT_NOTE_FIELD_DEFAULT` en de `PLG_SYSTEM_PRIVACYCONSENT_REDIRECT_MESSAGE_DEFAULT` taalstrings aan te passen voor elke geïnstalleerde taal.

**Privacyartikel** en **Privacy Menu-item** Als u dit artikel of menu-item associeert met alternatieven in andere talen, wordt het privacybeleid in de juiste taal voor de gebruiker weergegeven.

## Plugin: Gebruiker - Algemene Voorwaarden

Wanneer deze plugin is ingeschakeld, wordt elke nieuwe gebruiker die zich op je site registreert gevraagd om akkoord te gaan met de Algemene Voorwaarden voor het gebruik van je site. Alle bestaande gebruikers worden omgeleid naar hun gebruikersprofiel zodat ze hun toestemming kunnen geven.

Deze plugin is niet standaard ingeschakeld. Om in te schakelen:

- Selecteer **Home Dashboard → Plugins** in het beheerdersmenu.
- Zoek de **Gebruiker - Algemene Voorwaarden** plugin.
- Selecteer om het invoerformulier voor plugingegevens te openen.
- Stel de **Status** in op **Ingeschakeld**.
- Optioneel: Selecteer of maak een artikel om naar te linken vanuit het registratieformulier.

### Notities Gebruiker - Algemene Voorwaarden voor meertalige sites

**Korte Algemene Voorwaarden** Als je de standaardtekst gebruikt, wordt deze in de taal van de gebruiker weergegeven. Het is niet mogelijk om de aangepaste tekst te vertalen. Als je de tekst wilt aanpassen en in meerdere talen wilt weergeven, dien je dit veld leeg te laten en de Joomla faciliteit voor taaloverschrijvingen te gebruiken om de `PLG_USER_TERMS_NOTE_FIELD_DEFAULT` taalstrings voor elke geïnstalleerde taal aan te passen.

**Artikel Algemene Voorwaarden** Als je dit artikel associeert met alternatieven in andere talen, zal het privacybeleid in de juiste taal voor de gebruiker worden weergegeven.

## Gebruikersregistratie Toestemmingsweergave

Samen verschijnen de twee plugins op het Gebruikersregistratieformulier zoals in de volgende screenshot:

![privacy toestemmingen siteweergave](../../../en/images/privacy/privacy-consents-site.png)

## Menu-item: Verzoek om Informatie over Privacy

Geregistreerde gebruikers kunnen via een menu-item een samenvatting van informatie aanvragen of deze laten verwijderen. Stel het als volgt in:

- Selecteer **Menu's** → **Onderste Menu** vanuit het Administrator-menu (gebruik het menu dat het meest geschikt is).
- Voer een geschikte **Titel** in, bijvoorbeeld: **Verzoek om Informatie over Privacy**.
- Gebruik de **Selecteer** knop om het Menu-itemtype popupvenster te openen.
- Kies in de **Privacy** sectie het item **Verzoek aanmaken**.
- Stel het **Toegang**-veld in op **Geregistreerd**.
- **Opslaan & Sluiten**.

Ga naar de weergave van je site en controleer of het menu-item niet wordt weergegeven als je niet bent ingelogd en dat het wel wordt weergegeven na inloggen. Gebruik de link en probeer de **Exporteren** optie uit. Je kunt later de **Verwijderen** optie proberen met een dummy-account. Als er een verzoek in behandeling is, zie je een foutmelding:

“Uw informatieverzoek kon niet worden aangemaakt. Er is al een actief informatieverzoek voor dit e-mailadres en type verzoek. Neem contact op met de site-eigenaar voor updates over dit verzoek.”

## Menu-item: Privacy Verzoek Bevestigen

Voor SEF-doeleinden kun je een verborgen menu-item maken voor de gebruiker om het verzoek te bevestigen. Dit wordt opgenomen in de link die per e-mail verzonden wordt.

- Selecteer **Menu's** → **Verborgen Menu** in het beheerdersmenu (maak een verborgen menu zonder toegewezen modulepositie, of zie hieronder).
- Voer een passende **Titel** in, bijvoorbeeld: **Privacy Verzoek Bevestigen**.
- Gebruik de **Selecteer**-knop om het Menu-item Type popup dialoogvenster te openen.
- Selecteer in de **Privacy**-sectie het item **Verzoek Bevestigen**.
- Als je geen Verborgen Menu hebt, gebruik dan je hoofdmenu en stel in het Tabblad Linktype **Weergeven in Menu** in op **Nee**.
- **Opslaan & Sluiten**.

## Beheerdersmenu-items

Bekijk de andere menu-items van het Privacycomponent.

### Beheerders privacyverzoeken

Dit scherm is de centrale locatie voor het verwerken en beheren van gebruikersinformatieaanvragen. Raadpleeg het gerelateerde artikel over Privacy Workflow voor begeleiding bij het verwerken van verzoeken.

![privacy informatie aanvragen](../../../en/images/privacy/privacy-information-requests.png)

### Extensiecapaciteiten

Dit scherm verzamelt en toont informatie over de privacygerelateerde mogelijkheden die door afzonderlijke extensies worden gemeld. Het is bedoeld om te helpen bij de voorbereiding van documentatie, zoals een privacybeleidsartikel of een artikel over de gebruiksvoorwaarden.

![privacy informatie aanvragen](../../../en/images/privacy/privacy-extension-capabilities.png)

De inhoud van de pagina komt van taalstrings in de core, in het privacycomponent en in plugins die het onPrivacyCollectAdminCapabilities-evenement implementeren. Dat omvat:

- Authenticatie
- Captcha
- Installer
- Privacy
- Systeem
- Gebruiker

De informatie zal worden weergegeven in de taal die is geselecteerd voor het inloggen van de beheerder.

### Toestemmingen

Dit scherm toont een lijst van toestemmingen, met de meest recente bovenaan. Het zal in de taal zijn die in het toestemmingsformulier wordt gebruikt, meestal tijdens registratie. U kunt op naam zoeken naar een specifieke gebruiker. Houd er rekening mee dat toestemming om akkoord te gaan met de sitevoorwaarden hier niet wordt geregistreerd. Dat staat alleen in het Actieslogboek van gebruikers.

![privacy toestemmingen](../../../en/images/privacy/privacy-consents.png)

*Vertaald door openai.com*

