<!-- Filename: J3.x:Adding_custom_fields/Parameters_for_all_Custom_Fields / Display title: Toevoegen van extra velden/Parameters voor alle extra velden -->

## Parameters voor alle extra velden

**Artikelen in deze reeks**

1.  Inleiding
2.   Parameters voor alle extra
    velden
3.   Kalender
    veld
4.   Selectievakjes
    veld
5.   Kleur
    veld
6.   Tekstverwerker
    veld
7.   Integer
    veld
8.   Lijst
    veld
9.   Lijst met afbeeldingen
    veld
10.  Media
    veld
11.  Keuzerondje
    veld
12.  Herhalend
    veld
13.  SQL
    veld
14.  Tekst
    veld
15.  Tekstvak
    veld
16.  URL
    veld
17.  Gebruiker
    veld
18.  Gebruikersgroep
    veld
19.  Hoe kunt u extra velden
    groeperen
20.  Welke componenten ondersteunen extra
    velden
21.  Implementatie in uw
    component
22.  Extra velden gebruiken in uw
    overrides

## Parameters voor alle extra velden

De extra velden lijst zal initieel leeg zijn. Klik op **Nieuw** om een
veld toe te voegen.
Op het tabblad **Algemeen** moet u de verplichte gegevens invullen:

- Titel
  De titel van het veld. De titel wordt getoond op de veldbeheer pagina,
  waar u het veld kunt openen om te bewerken door op de titel te
  klikken. De titel is wordt niet getoond als u een artikel of een
  contactpersoon aanmaakt nog op de website.
- Naam
  De naam die gebruikt wordt om het veld te definiëren. Indien deze leeg
  wordt gelaten zal Joomla! deze met een standaardwaarde vanuit de titel
  vullen.
- Type
  Als u een veld aanmaakt kunt u één van de 16 veldtypes kiezen. Als het
  veld opgeslagen wordt staat het type vast. U kunt het later niet
  veranderen.

Voor ieder veld kunt u deze parameters gebruiken:

- Label
  Gebruik een beschrijvende tekst van het veld voor het label van het
  veld. Deze tekst is niet vertaalbaar. Als u geen tekst voor het label
  opgeeft, dan wordt de titeltekst ook gebruikt als labeltekst.
- Beschrijving
  De beschrijving van het veld. Een tekst die getoond wordt als tool-tip
  als de gebruiker de muis over de tekstbox beweegt in het
  beheergedeelte bij het aanmaken van een artikel of contactpersoon of
  een component van derden die extra velden ondersteund. Deze tekst is
  niet vertaalbaar. U ziet de beschrijving niet op de website.
- Verplicht
  Is dit een verplicht veld? In dit geval moet het veld ingevuld worden
  voor het verzenden van een artikel, contactpersoon of component van
  derden die speciale velden ondersteunt. U kunt de opties *Ja* of *Nee*
  kiezen.
- Standaardwaarde
  Hier kunt u een standaardwaarde opgeven voor het extra veld. Deze
  tekst is niet vertaalbaar. Merk op dat in sommige lijstvelden de
  waarde als standaard moet worden opgegeven en bij andere de index.
- Status
  U kunt een publicatiestatus instellen. Is het veld *Gepubliceerd*,
  *Gedepubliceerd*, *Gearchiveerd* or *Verplaatst naar prullenbak*?
  - Gepubliceerd: Het veld is zichtbaar bij het bewerken van een artikel
    of contactpersoon en het is zichtbaar op de website.
  - Gedepubliceerd: Het veld wordt niet zichtbaar voor gebruikers bij
    het bewerken van een artikel of een contactpersoon.
  - Gearchiveerd: Het veld zal niet meer getoond worden bij het bewerken
    van een artikel of contactpersoon. U kunt het openen bij veldbeheer
    als u het filter op 'Gearchiveerd' zet.
  - Verplaatst naar prullenbak: Het veld is verwijderd maar nog in de
    database. Het kan definitief verwijderd worden uit de database via
    de 'Prullenbak legen' functie bij veldbeheer.
- Veldgroepen
  U kunt een extra veld koppelen aan één of meer veldgroepen.
- Categorie
  U kunt een speciaal veld koppelen aan één of meer categorieën. Bedenk
  dat de standaard 'Alle' niet de 'uncategorized' artikelen omvat.
- Toegang
  Het
  Toegangsniveau
  voor dit item.
- Taal
  Selecteer de taal voor dit extra veld. Als u geen  meertalige
  functie
  van Joomla gebruikt, houd dan de standaard van *Alle*.
- Notitie
  Een optioneel veld om persoonlijke notities voor het veld te maken.

Op het tabblad **Opties** kunt u de volgende opties gebruiken:

- Tijdelijke aanduiding
  Een tijdelijke tekst die verschijnt binnen het extra veld als hint
  voor de invoer. De tijdelijke aanduiding is in het beheergedeelte
  actief bij het aanmaken van een artikel, contactpersoon of een
  component van derden die extra velden ondersteunt. U ziet het niet op
  de website.
- Veld class
  Het class attribuut van het veld als het veld gegenereerd wordt.
  Indien verschillende classes nodig zijn, scheid ze dan door spaties.
- Bewerk class
  De class attributen van het veld in het bewerkformulier. Als
  verschillende classes nodig zijn scheid ze dan door spaties.
- Bewerkbaar in
  Op welk deel van de site moet het veld getoond worden. In het
  Beheergedeelte, op de website of beide?
- Label
  Toon of verberg het label als het veld gegenereerd wordt.
- Automatische weergave
  Joomlaǃ biedt inhoud-'events' die uitgevoerd worden tijdens het
  aanmaak-proces. Dit is de plek om aan te geven hoe extra velden in de
  inhoud moeten worden opgenomen. U kunt kiezen voor 'Na de titel',
  'Voor de weergave van inhoud', 'Na weergave van inhoud' of 'Niet
  automatisch weergeven'.
- Uitgeschakeld
  Moet het veld uitgeschakeld zijn in het bewerkformulier.
- Alleen lezen
  Moet het veld alleen-lezen zijn in het bewerkformulier.

<a href="https://docs.joomla.org/J3.x:Adding_custom_fields"
id="content-button" class="button expand success">Vorig: Inleiding</a>
<a
href="https://docs.joomla.org/J3.x:Adding_custom_fields/Calendar_Field"
id="content-button" class="button expand">Volgende: Kalender veld</a>
