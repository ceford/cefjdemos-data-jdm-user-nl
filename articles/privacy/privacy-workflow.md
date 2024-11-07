<!-- Filename: J4.x:Privacy_Workflow / Display title: Privacy Workflow  -->

## Een Verzoek Indienen

Het verwerken van verzoeken voor persoonlijke informatie is het hoofddoel van de privacymodule. Gebruikers kunnen vragen om een samenvatting van hun persoonlijke gegevens of om al hun persoonlijke gegevens te laten verwijderen. Een verzoek kan worden ingediend door een geauthenticeerde gebruiker via het aanvraagformulier of door een supergebruiker.

In deze context betekent een gebruiker elk individu of elke organisatie die een verzoek heeft ingediend, ongeacht of er een geregistreerd gebruikersaccount is. Bijvoorbeeld, verzoeken kunnen worden ontvangen door de sitebeheerder van individuen of organisaties die als contacten aan de site zijn toegevoegd.

Persoonlijke gegevens zijn gebaseerd op e-mailadressen en geautomatiseerde verwerking is beperkt tot extensies die privacyfuncties rapporteren.

*BELANGRIJK* Om informatieverzoeken te kunnen maken en verwerken, moet uw website e-mails kunnen verzenden vanwege de vereiste dat de eigenaar van de informatie het verzoek bevestigt.

### Verzoek door een Geauthenticeerde Gebruiker

Geregistreerde gebruikers kunnen een informatieverzoek indienen via een *Privacy Informatie Verzoek* link in het menu die alleen beschikbaar is na inloggen. Een goede plek voor zo'n link is in hetzelfde menu waar een link naar het **Privacybeleid** van de site staat. Een onderste menu in de voettekst van de site is vaak een favoriete locatie. Bij het indienen van een informatieverzoek moet de gebruiker het volgende opgeven:

- Het type verzoek: Exporteren of Verwijderen geselecteerd uit de keuzelijst.

![privacy workflow gebruikersverzoek](../../../en/images/privacy/privacy-workflow-user-request.png)

Bij het indienen verschijnt er een bericht dat aangeeft of het verzoek is geaccepteerd en er een verificatie-e-mail onderweg is:

![privacy workflow gebruikersverzoek geaccepteerd](../../../en/images/privacy/privacy-workflow-user-request-accepted.png)

of dat *Uw informatieverzoek kon niet worden aangemaakt. Er is al een actief informatieverzoek voor dit e-mailadres en type verzoek. Neem contact op met de eigenaar van de site voor updates over dit verzoek.*

### Aanmaak door een Supergebruiker

Via de pagina **Privacy: Informatieverzoeken** kan elke supergebruiker een nieuw informatieverzoek aanmaken. Dit is de enige manier om informatieverzoeken te maken voor gebruikers die GEEN accounts hebben op de website. Om een verzoek te maken:

- Selecteer **Gebruikers → Privacy → Verzoeken** in het Beheerdersmenu.
- Selecteer de knop **Nieuw** in de werkbalk.
- Vul in het veld **E-mail** het e-mailadres van de gebruiker in.
- Selecteer in het veld **Verzoektype** Exporteren of Verwijderen uit de keuzelijst.
- **Opslaan & Sluiten**.

Eenmaal aangemaakt kan het verzoek niet worden bewerkt. Het kan alleen ongeldig worden verklaard of verwerkt.

## Een Verzoek Bevestigen

Zodra een verzoek is aangemaakt, ongeacht hoe het is aangemaakt, ontvangt de gebruiker een e-mail met een link naar een bevestigingsformulier.

![privacy workflow gebruikersverzoek bevestigen](../../../en/images/privacy/privacy-workflow-user-request-confirm.png)

De gebruiker moet de token die in de e-mail is verstrekt invoeren en het formulier indienen. De token is 24 uur geldig. Als een verzoek binnen dat tijdsbestek niet wordt bevestigd, wordt het verzoek als **Ongeldig** gemarkeerd in de Privacy Verzoeklijst en moet een nieuw verzoek worden ingediend.

Zodra de gebruiker het verzoek bevestigt, wordt er een e-mail naar de Supergebruikers gestuurd om aan te geven dat actie vereist is.

- Selecteer **Gebruikers → Privacy → Verzoeken** in het Beheerdersmenu.
- Verzoeken die actie vereisen, worden gemarkeerd als **Bevestigd**.

![privacy workflow informatielijst verzoeken](../../../en/images/privacy/privacy-workflow-information-requests-list.png)

## Verwerken van een Exporteerverzoek

Zodra een exportverzoek is bevestigd, zijn er twee acties beschikbaar voor supergebruikers.

- Gegevens Exporteren: Dit verzamelt alle gegevens voor het onderwerp van het informatieverzoek en creëert een XML-bestand dat naar uw computer wordt gedownload. Dit is nuttig om site-eigenaren in staat te stellen de gegevensexport te beoordelen voordat deze naar de gebruiker wordt verzonden.
- Gegevensexport E-mailen: Dit verzamelt alle gegevens voor het onderwerp van het informatieverzoek, creëert een XML-bestand (hetzelfde als gegenereerd door de Gegevens Exporteren actie), en stuurt een e-mail naar de gebruiker met het geëxporteerde databestand als bijlage.

**Belangrijk:** De exportactie kan alleen gegevens verzamelen van extensies die privacyondersteuning hebben. Daarom moet de supergebruiker die het verzoek behandelt, de export bekijken en indien nodig gegevens opnemen die zich in extensies bevinden die persoonlijke gegevens opslaan maar geen privacyondersteuning hebben.

## Verwerking van een Verwijderingsverzoek

Zodra een verwijderingsverzoek is bevestigd, is er slechts één actie beschikbaar voor supergebruikers.

- Gegevens verwijderen: Dit proces anonimiseert en/of verwijdert gegevens die verband houden met het informatie-onderwerp. Voor verzoeken waarbij de informatie-eigenaar ook een geregistreerd gebruikersaccount heeft, zal dit proces de naam, gebruikersnaam en e-mailadres van het account anonimiseren, evenals voorkomen dat het account kan worden ingelogd en de gebruiker uitloggen van de site indien ze zijn ingelogd op het moment dat het verzoek wordt verwerkt.

**Belangrijk:** De verwijderactie kan alleen gegevens verzamelen van extensies die privacy-ondersteuning hebben. Daarom moet de supergebruiker die het verzoek behandelt de export beoordelen en indien nodig handmatig gegevens anonimiseren of verwijderen die zich in extensies bevinden die persoonlijke gegevens opslaan, maar geen privacy-ondersteuning hebben.

Bij selectie van de **Gegevens verwijderen**-knop is er een bevestigingsbericht **Gegevens verwijderd**, maar de Privacy: Informatie Verzoeken-lijst blijft verder ongewijzigd. De gebruikersgegevens worden verwijderd of geanonimiseerd, maar niet de gegevens in de \#\_\_actie_logs, \#\_\_berichten en \#\_\_privacy_verzoeken tabellen (zie hieronder).

## Een Verzoek Afronden

Nadat het verzoek is verwerkt, moet het als voltooid worden gemarkeerd. Dit geeft aan dat het verzoek is vervuld en er geen verdere actie nodig is.

- Selecteer in de lijst **Privacy: Informatie Verzoeken** het e-mailadres van het verzoek dat wordt verwerkt.
- In het formulier **Privacy: Informatie Verzoek Beoordelen**:
  - Beoordeel de gegevens.
  - Selecteer de juiste knop **Exporteren**, **E-mailen** of **Verwijderen** uit de werkbalk als dit nog niet was gedaan in de lijstweergave.
- Selecteer de knop **Voltooien** uit de werkbalk (of de knop **Ongeldig verklaren** als dit verzoek als ongeldig wordt beschouwd).

![privacy workflow informatieverzoek beoordelen](../../../en/images/privacy/privacy-workflow-review-information-request.png)

## Tot slot

Om gegevens van het Gebruikersactielogboek te verwijderen:

- Selecteer **Gebruikers → Gebruikersactielogboek** in het Administrator-menu.
- Zoek naar de gebruikersnaam of het e-mailadres van de verwijderde gebruiker.
- Vink het selectievakje **Alle items selecteren** aan.
- Selecteer de knop **Verwijderen** in de werkbalk.

Om gegevens van Privéberichten en Privacyverzoeken te verwijderen:

- Er is geen gemakkelijke manier om een van deze soorten gegevens in Joomla
  batchgewijs te verwijderen. De snelste methode is om in de database met phpMyAdmin
  naar de gebruikersnaam (e-mailadres) te zoeken en de records daar te verwijderen. Hier is een voorbeeldscreenshot:

![privacy workflow verwijderen met phpmyadmin](../../../en/images/privacy/privacy-workflow-delete-with-phpmyadmin.png)

## Aanvullende Bronnen

-  [Ontwikkelaarsgids voor de Privacy Tool Suite](https://docs.joomla.org/Special:MyLanguage/J3.x:Integrate_Extensions_with_the_Privacy_Component)

*Vertaald door openai.com*

