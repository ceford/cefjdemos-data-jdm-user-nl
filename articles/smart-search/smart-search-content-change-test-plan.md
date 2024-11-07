<!-- Filename: Smart_Search_content_change_test_plan / Display title: Smart Search Testplan -->

Het volgende is een globaal testplan dat (voornamelijk) de update van de Smart Search-index behandelt wanneer verschillende soorten inhoudsupdates plaatsvinden.

Smart Search moet worden getest voor elk van de ondersteunde basisinhoudstypen. Deze zijn:

- Artikelen
- Categorieën
- Contacten
- Nieuwsfeeds
- Weblinks

Voor elk van de bovenstaande inhoudstypen moeten we het volgende testen:

## Tekstwijzigingen

Het wijzigen van verschillende tekstvelden binnen een inhoudelijk item zou de zoektermen in de index moeten veranderen (met één opvallende uitzondering die hieronder wordt beschreven). Er is geen noodzaak om alle tekstvelden voor een bepaald type inhoud te testen, aangezien als het werkt voor één, het voor allemaal zal werken. Kies dus gewoon één veld voor elk type inhoud. De volgende tekstvelden worden geïndexeerd voor de kerncomponenten:

- Artikelen
  - Titel
  - Alias
  - Artikeltekst
  - Metadata beschrijving
  - Metadata trefwoorden
  - Metadata auteur
  - Auteur
  - Gemaakt door alias
- Categorieën
  - Titel
  - Alias
  - Beschrijving
  - Link ??? (niet zeker of er zo'n veld is)
  - Metadata beschrijving
  - Metadata trefwoorden
  - Metadata auteur
  - Auteur
- Contacten
  - Naam
  - Alias
  - Gekoppelde gebruikersnaam
  - Andere informatie
  - Positie (indien ingeschakeld in Opties)
  - Adres (indien ingeschakeld in Opties)
  - Stad (indien ingeschakeld in Opties)
  - Regio (indien ingeschakeld in Opties)
  - Land (indien ingeschakeld in Opties)
  - Postcode (indien ingeschakeld in Opties)
  - Telefoon (indien ingeschakeld in Opties)
  - Fax (indien ingeschakeld in Opties)
  - E-mail (indien ingeschakeld in Opties)
  - Mobiel (indien ingeschakeld in Opties)
  - Webpagina (indien ingeschakeld in Opties)
- Nieuwsfeeds
  - Titel
  - Alias
  - Link
  - Metadata beschrijving
  - Metadata trefwoorden
  - Metadata auteur
  - Auteur
  - Gemaakt door alias
- Weblinks
  - Titel
  - Alias
  - URL
  - Beschrijving
  - Metadata beschrijving
  - Metadata trefwoorden
  - Metadata auteur
  - Auteur
  - Gemaakt door alias

Om te testen, voeg gewoon een willekeurige string toe, zoals "xyz", binnen een reeks reguliere tekst en aan de bovenkant, probeer vervolgens die term te zoeken in de front-end.

- je willekeurige string zou in de lijst met autocomplete-opties moeten verschijnen terwijl je deze typt.
- je willekeurige string zou 3 keer in de lijst met autocomplete-opties moeten verschijnen.
  - op zichzelf
  - samen met het volgende woord erachter
  - samen met de volgende 2 woorden erachter
- het inhoudelijk item dat je willekeurige string bevat, zou in de lijst met zoekresultaten moeten verschijnen.
- je willekeurige string zou gemarkeerd moeten worden in de zoekresultaten, op voorwaarde dat je deze dicht bij de bovenkant van de tekst hebt ingevoerd (omdat de tekst in de zoekresultaten wordt ingekort).

Verwijder je willekeurige string uit de tekst: Dit zou de 3 zoektermen/zinnen uit de index moeten verwijderen. Het zoeken naar een van de 3 zoektermen zou geen zoekresultaten moeten opleveren.

Verwijder het inhoudelijk item: Dit verwijdert alle zoektermen/zinnen die in het inhoudelijk item worden gebruikt uit de index, behalve waar die zoektermen/zinnen nog steeds worden gebruikt in andere inhoudelijke items.<sup>[\[1\]](#cite_note-1)</sup>

Het verwijderde inhoudelijk item zou in geen enkele lijst met zoekresultaten moeten verschijnen.

## Statuswijzigingen van inhoudselement

Zoek een inhoudselement van het vereiste type met behulp van Slim Zoeken. Voer vervolgens deze tests uit:

- Verplaats het item naar de prullenbak en herhaal de zoekopdracht. Het item zou niet langer in de zoekresultaten moeten verschijnen.
- Publiceer het item opnieuw en herhaal de zoekopdracht. Het item zou weer in de zoekresultaten moeten verschijnen.
- Depubliseer het item en herhaal de zoekopdracht. Het item zou niet langer in de zoekresultaten moeten verschijnen.
- Archiveer het item en herhaal de zoekopdracht. Het item zou weer in de zoekresultaten moeten verschijnen.

## Wijzigingen in contentmap (taxonomie)

Hoewel wijzigingen in de categorie een speciaal geval zijn van veranderingen in de contentmap, moeten we ook wijzigingen testen aan niet-categorieën contentmaptakken, omdat categorie-wijzigingen een andere code aanspreken. Dit zijn de niet-categorische velden die onderhevig zijn aan contentmaps in de kerncomponenten:

- Artikelen
  - Auteur
  - Categorie
  - Taal
- Contacten
  - Categorie
  - Land
  - Taal
  - Regio
- Nieuwsfeeds
  - Categorie
  - Taal
- Weblinks
  - Categorie
  - Taal

Kies dus een van de bovenstaande opties (als er eentje werkt, zullen ze allemaal werken voor dat type content) die geschikt is voor het contenttype en controleer dat:

- het wijzigen van het veld ertoe leidt dat het item verschijnt in een zoekopdracht met behulp van het relevante vervolgkeuzemenu (bij geavanceerd zoeken) voor het veld dat u hebt gewijzigd. <sup>[\[2\]](#cite_note-2)</sup>
- het contentitem niet verschijnt in een zoekopdracht met de oude waarde van het veld.

Verwijder het contentitem en controleer dat het niet langer verschijnt in de zoekresultaten met behulp van de relevante vervolgkeuzefilter. Merk op dat er **niet** van wordt verwacht dat een ongebruikt knooppunt wordt verwijderd uit het relevante vervolgkeuzemenu. <sup>[\[3\]](#cite_note-3)</sup>

## Wijzigingen in categorie status

Het veranderen van de status van de categorie waartoe een item behoort, zou de index voor dat item moeten bijwerken. Bovendien, het veranderen van de status van een bovenliggende categorie van de categorie waartoe een item behoort, zou ook de index voor dat item moeten bijwerken. Om te testen, vind of maak een item met de volgende structuur:

    Categorie A bevat Categorie A.1 met daarin een inhoudsitem

Verander de status van Categorie A.1 en test als volgt:

- Verwijder Categorie A.1 naar de prullenbak en herhaal de zoekopdracht. Het item zou niet langer in de zoekresultaten moeten verschijnen.
- Publiceer Categorie A.1 opnieuw en herhaal de zoekopdracht. Het item zou weer in de zoekresultaten moeten verschijnen.
- Depubliceer Categorie A.1 en herhaal de zoekopdracht. Het item zou niet langer in de zoekresultaten moeten verschijnen.
- Archiveer Categorie A.1 en herhaal de zoekopdracht. Het item zou weer in de zoekresultaten moeten verschijnen.

Herstel Categorie A.1, verander vervolgens de status van Categorie A en test als volgt:

- Verwijder Categorie A naar de prullenbak en herhaal de zoekopdracht. Het item zou niet langer in de zoekresultaten moeten verschijnen.
- Publiceer Categorie A opnieuw en herhaal de zoekopdracht. Het item zou weer in de zoekresultaten moeten verschijnen.
- Depubliceer Categorie A en herhaal de zoekopdracht. Het item zou niet langer in de zoekresultaten moeten verschijnen.
- Archiveer Categorie A en herhaal de zoekopdracht. Het item zou weer in de zoekresultaten moeten verschijnen.

## Wijzigingen in toegangsniveau van contentitems

Wijzig het toegangsniveau van een contentitem naar iets dat een frontendgebruiker niet zou mogen zien.

- controleer dat het contentitem niet in de zoekresultatenlijsten verschijnt.

Wijzig het toegangsniveau terug naar iets dat een frontendgebruiker zou mogen zien.

- controleer dat het contentitem nu in de zoekresultatenlijsten verschijnt.

Merk op dat zoektermen binnen het contentitem nog steeds in de aanvulfunctie van de autocompleter verschijnen, zelfs als de gebruiker geen toegang heeft tot het contentitem zelf. Dit is verwacht gedrag, hoewel het iets is dat we wellicht verder willen onderzoeken. <sup>[\[4\]](#cite_note-4)</sup>

## Wijzigingen in het toegangslevel van categorieën

Het wijzigen van het toegangslevel van de categorie waartoe een item behoort, moet de index voor dat item bijwerken. Bovendien moet het wijzigen van het toegangslevel van een bovenliggende categorie van de categorie waartoe een item behoort, ook de index voor dat item bijwerken. Om te testen, vind of maak een item met de volgende structuur:

    Categorie A met daarin Categorie A.1 met daarin een inhoudsitem

Voer de volgende tests uit:

- Wijzig het toegangslevel van Categorie A.1 naar iets dat een front-end gebruiker niet zou moeten kunnen zien.
  Controleer dat het inhoudsitem niet in zoekresultatenlijsten verschijnt.
- Wijzig het toegangslevel van Categorie A.1 terug naar iets dat een front-end gebruiker zou moeten kunnen zien.
  Controleer dat het inhoudsitem nu wel in zoekresultatenlijsten verschijnt.
- Wijzig het toegangslevel van Categorie A naar iets dat een front-end gebruiker niet zou moeten kunnen zien.
  Controleer dat het inhoudsitem niet in zoekresultatenlijsten verschijnt.
- Wijzig het toegangslevel van Categorie A terug naar iets dat een front-end gebruiker zou moeten kunnen zien.
  Controleer dat het inhoudsitem nu wel in zoekresultatenlijsten verschijnt.

## Wijzigingen in de Smart Search-status

In het scherm Beheerder → Componenten → Slim Zoeken → Inhoudskaarten
is het mogelijk om de publiceer-/depubliceerstatus van inhoudskaarttakken en -knopen te wijzigen. De volgende tests moeten worden uitgevoerd:

- Depubliceer een inhoudskaarttak (bijv. Auteur).
  Controleer dat het filtervervolgkeuzemenu voor die tak niet meer zichtbaar is in geavanceerd zoeken.
- Depubliceer een inhoudskaartknoop (binnen een gepubliceerde tak). Bijvoorbeeld, "Dieren" binnen de "Categorie" tak.
  Controleer dat de knoop niet wordt weergegeven in het filtervervolgkeuzemenu voor de tak in geavanceerd zoeken.

In het scherm Beheerder → Componenten → Slim Zoeken → Geïndexeerde Inhoud voer de volgende test uit:

- Depubliceer een inhoudselement.
  Controleer dat het inhoudselement niet langer in de zoekresultaten verschijnt.

In het scherm Beheerder → Extensies → Invoegtoepassingenbeheer voer de volgende test uit:

- Stel het "Selecteer type" filter in op "finder" of "slim zoeken".
- Kies een van de inhoudstype-invoegtoepassingen en depubliseer deze.
  Alle gegevens voor dat inhoudstype moeten uit de index worden verwijderd.

Opmerking: Als je de invoegtoepassing opnieuw publiceert, worden de gegevens niet opnieuw aan de index toegevoegd. Dit is verwacht gedrag. Je moet de indexeerder opnieuw uitvoeren om de gegevens terug te krijgen.

*Vertaald door openai.com*

