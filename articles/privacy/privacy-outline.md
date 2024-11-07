<!-- Filename: Help4.x:Components_Privacy_Outline / Display title: Privacyoverzicht  -->

## Inhoud

De Joomla Privacy Tool Suite bestaat uit de volgende onderdelen:

- **Administrator Component** Beheert gebruikersverzoeken met betrekking tot privacy-informatie.
- **Module - Privacy Dashboard** Plaatst een privacypaneel op het Home Dashboard.
- **Module - Privacy Requests** Plaatst een panel voor privacyverzoeken op het Privacy Dashboard.
- **Module - Privacy Status** Plaatst een panel voor de privacystatus op het Privacy Dashboard.
- **Menu item - Verzoek maken** Toont een formulier om een informatieverzoek weer te geven. Moet nog worden aangemaakt.
- **Plugin - Systeem - Privacytoestemming** Voegt toestemmingsvelden toe aan persoonlijke informatieformulieren zoals Registratie. Moet geactiveerd worden.
- **Plugin - Gebruiker - Algemene Voorwaarden** Vraagt de toestemming van de gebruiker voor de voorwaarden van de site. Moet geactiveerd worden.
- **Plugin - Inhoud - Bevestig Toestemming** Voegt een verplichte selectievakje toe aan een formulier, bijvoorbeeld het standaard contactformulier. Moet geactiveerd worden.
- **Plugin - Privacy - Diversen** Meer plugins, standaard ingeschakeld, zonder significante parameters om in te stellen.

Bij installatie is de Privacy Tool Suite klaar voor gebruik door de beheerder, zonder het inschakelen van plugins of het aanmaken van een menu-item.

## Workflow

Dit is een typische reeks gebeurtenissen:

- Een informatieverzoek komt binnen. Dit moet een geldig e-mailadres bevatten voor een gegevenssubject. Het subject hoeft geen geregistreerde gebruiker te zijn. Bijvoorbeeld, het subject kan een contact zijn dat door een beheerder is toegevoegd.
- Als het bericht niet door het subject is ingediend via een persoonlijk informatieformulier op de site:
  - De beheerder gaat naar **Gebruikers → Privacy → Verzoeken → Nieuw** om een nieuw informatieverzoek te maken. Er wordt een bericht naar het opgegeven e-mailadres gestuurd waarin het subject wordt uitgenodigd om te bevestigen dat dit een authentiek verzoek is.
- Als het bericht via een persoonlijk informatieformulier op de site is ingediend, wordt automatisch een bevestigingsverzoek naar het subject verzonden.
- Het subject selecteert de link in het e-mailbericht om het bevestigingsformulier te openen. Na indiening ziet het subject een bevestigingsbericht.
- De beheerder ziet dat er privéberichten in de titelbalk wachten. Er zal ook een systeem-e-mailbericht zijn.
- De beheerder gaat naar **Gebruikers → Privacy → Verzoeken** en ziet dat de status van het verzoek is veranderd naar **Bevestigd**.
- Voor een verzoek tot gegevensexport zijn er aangrenzende export- en e-mailknoppen.
  - De beheerder selecteert de exportknop om de te exporteren gegevens te bekijken. Dit is in XML-formaat maar wordt fatsoenlijk weergegeven in Firefox.
  - De beheerder selecteert de e-mailknop om de geëxporteerde gegevens naar het subject te sturen.
- Voor een verwijderverzoek van gegevens is er een aangrenzende delete-knop.
  - De beheerder selecteert de delete-knop om de gegevens voor de gebruiker te anonimiseren. De gebruiker kan niet langer inloggen.
- Selecteer het e-mailadres van het gegevenssubject om het beoordelingsformulier voor informatieverzoek te openen.
- Selecteer de knop Voltooien in de werkbalk.
- De lijst met informatieverzoeken toont de status als Voltooid en de actiekoppen zijn verdwenen.

Opmerking: deze suite toont geen toestemmingsformulier voor cookies.

*Vertaald door openai.com*

