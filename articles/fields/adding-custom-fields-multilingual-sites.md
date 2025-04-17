<!-- Filename: J3.x:Adding_custom_fields/Multilingual_Sites / Display title: Meertalige Sites -->

## Inleiding

Als je een meertalige site hebt, kun je de labels en beschrijvingen van velden en veldgroepen in de taal van de gebruiker weergeven. Om dit te doen:

1. Definieer de Titel en Beschrijving van je veldgroep als taalconstanten.
2. Definieer het Label en de Beschrijving van je veld als taalconstanten.
3. Stel die taalconstanten in als overschrijvingen voor elk van je talen.

In het volgende voorbeeld wordt een contactveldgroep en veld aangemaakt voor de persoonlijke voorkeuren van een contactpersoon. De veldgroep heet Favorieten en het voorbeeldveld heet Auto. Natuurlijk kunnen er meer velden worden toegevoegd voor andere favoriete dingen, zoals eten of films.

Om dit voorbeeld te volgen, wordt aangenomen dat je een meertalige site hebt opgezet, zoals beschreven in de tutorial [Meertalige Sites](jdocmanual?article=user/languages/setup-a-multilingual-site).

## Taalconstanten

Taalconstanten zijn plaatsaanduidingen die worden vervangen door taalwaarden wanneer een pagina wordt weergegeven. De constanten en hun waarden worden opgeslagen in taalbestanden zoals JPATH_SITE/languages/nl-NL/com_contact.ini en JPATH_SITE/administrator/languages/nl-NL/com_contact.ini, respectievelijk voor de frontend en backend. Volgens conventie beginnen de meeste taalconstanten met de extensienaam in hoofdletters, bijvoorbeeld COM_CONTACT_...

Taaloverschrijvingen zijn door de gebruiker gedefinieerde vervangingen voor bestaande taalconstanten en waarden of geheel nieuwe constanten en waarden, zoals in dit voorbeeld. Ze worden allemaal opgeslagen in aparte bestanden, één voor de Site-pagina's en een andere voor de Beheerder-pagina's:
```
SITE_ROOT/language/overrides/nl-NL.override.ini
SITE_ROOT/administrator/language/overrides/nl-NL.override.ini
```
Het is belangrijk om nieuwe door de gebruiker gedefinieerde taalconstanten uniek te maken om te voorkomen dat bestaande constanten worden overschreven. Bijvoorbeeld:

COM_CONTACT_CUSTOM_FIELDGROUP_FAVOURITES="Favorieten"
COM_CONTACT_CUSTOM_FIELDGROUP_FAVOURITES_DESCRIPTION="Favoriete auto, film, enz."
COM_CONTACT_CUSTOM_FIELD_FAVOURITE_CAR="Favoriete Auto"
COM_CONTACT_CUSTOM_FIELD_FAVOURITE_CAR_DESCRIPTION="Soms gebruikt als een beveiligingsvraag"

Als er iets mis is met de syntaxis van een taalbestand, wordt het niet geladen en kunnen alle constanten erin in de uitvoerpagina's verschijnen. En let op dat een bestand in alfabetische volgorde wordt gesorteerd.

## Het Definiëren van de Overrides

Het is belangrijk om Engelse (GB) overrides te maken. Joomla laadt eerst en-GB vertaald bestanden en overschrijft vervolgens de waarden met een geselecteerd taalbestand. Dit zorgt ervoor dat gebruikers nooit een tekstconstante zouden moeten zien. Als er een vertaalde waarde ontbreekt, dan verschijnt de Engelse tekst in de output. Dit ziet er vreemd uit, maar het is beter dan een zeer lange constante zien die meestal de lay-out verstoort.

Vanuit het Beheerdersmenu:

* Selecteer **Systeem / Beheer paneel / Taal Overrides**
* Selecteer **Engels (Verenigd Koninkrijk) - Site** uit de lijst *Selecteer Taal & Client*
* Selecteer de **Nieuw** knop van de Toolbar.
* Voer in het veld **Taalconstante** de waarde *COM_CONTACT_CUSTOM_FIELDGROUP_FAVOURITES* in
* Voer in het veld **Tekst** de waarde *Favorieten* in
* Vink het selectievakje **Voor Beide Locaties** aan. Dit zal de creatie van overrides voor zowel Site- als Beheerderpagina's veroorzaken.
* Selecteer **Opslaan & Nieuw** uit de *Opslaan & Sluiten* vervolgkeuzelijst.
* Herhaal dit voor elk van de andere vereiste constanten.
* Selecteer **Sluiten** nadat het laatste item is opgeslagen.
* Herhaal dit voor elke geïnstalleerde taal.

De volgende schermafbeelding toont een voorbeeld van het aanmaken van een override voor een Duitse taalconstante.

![Override creatie in het Duits](../../../en/images/fields/fields-overrides-creation-de.png)

## Het veldgroep definiëren

Van het menu Beheerder:

* Selecteer het menu-item **Componenten / Contacten / Veldgroepen**.
* Selecteer de **Nieuw** knop in de werkbalk.
* Voer in het Titelveld de constante COM_CONTACT_CUSTOM_FIELDGROUP_FAVOURITES in.
* Voer in het Beschrijvingsveld de constante COM_CONTACT_CUSTOM_FIELDGROUP_FAVOURITES_DESCRIPTION in.
* Selecteer **Opslaan & Sluiten** in de werkbalk.

## Het Veld Definiëren

Om een favoriete auto te selecteren, kunt u een dropdownlijst met auto's aanbieden die u definieert, of een dropdownlijst met auto's verkregen uit een databasetabel, of een lijst met keuzerondjes met labels die u definieert. In dit geval zal een eenvoudig tekstinvoerveld het mogelijk maken om elk merk en model van auto in te voeren uit de gehele wereldgeschiedenis van de auto-industrie.

Vanuit het Beheerdersmenu:

* Selecteer het menu-item **Componenten / Contacten / Velden**.
* Selecteer de knop **Nieuw** in de werkbalk.
* Voer in het Titelveld de constante COM_CONTACT_CUSTOM_FIELD_FAVOURITE_CAR in.
* Selecteer in het Typeveld **Tekst (text)** als het nog niet is geselecteerd.
* Voer in het Beschrijvingsveld de constante COM_CONTACT_CUSTOM_FIELD_FAVOURITE_CAR_DESCRIPTION in.
* Selecteer in het veld **Veldgroep** (rechts) de Veldgroep die u heeft gemaakt.
* Selecteer **Opslaan & Sluiten** in de werkbalk.

## Een Contact Bewerken

Met Engels geselecteerd vóór de Administrator-login, zou het contactgegevensformulier een tabblad moeten bevatten met de Engelse naam van je veldgroep en velden in die groep ook met Engelse waarden.

![Gegevensinvoer in het Engels](../../../en/images/fields/fields-overrides-entry.png)

Met Duits geselecteerd vóór de Administrator-login, zou je de Duitse vertalingen van je taalconstanten moeten zien:

![Gegevensinvoer in het Duits](../../../en/images/fields/fields-overrides-entry-de.png)

Let op: vertaling door translate.google.co.uk!

## Een contact weergeven

In het Engels:

![Gegevensweergave in het Engels](../../../en/images/fields/fields-overrides-display.png)

En in het Duits:

![Gegevensweergave in het Duits](../../../en/images/fields/fields-overrides-display-de.png)

*Vertaald door openai.com*

