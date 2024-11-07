<!-- Filename: Adding_an_image_to_an_article / Display title: Artikel: Bewerken - Afbeeldingen   -->

## Inleiding

Het is belangrijk te begrijpen dat afbeeldingen voor webdocumenten apart van HTML-tekst worden opgeslagen. Wanneer een webpagina wordt opgevraagd, haalt de browser eerst de tekst en afzonderlijke ondersteunende bestanden op, zoals stijlbladen en JavaScript-scripts. Afbeeldingen worden later opgehaald. Vaak onderhandelen de browser en de webserver over welke versie van een afbeelding opgehaald moet worden, aangepast aan de grootte en resolutie van het browserscherm. Er is zelfs een Joomla-extensie beschikbaar die verschillende versies van een ouderafbeelding in verschillende formaten en maten maakt om de snelheid van levering en rendering te verbeteren.

Afbeeldingen worden in webpagina's opgenomen door middel van naar behoren opgemaakte links. Er zijn twee verschillende mechanismen om afbeeldingen in artikelen op te nemen: 

- Het *Content*-tabblad van het bewerkingsformulier staat toe dat een of meer afbeeldingslinks direct in de tekst van het artikel worden ingevoegd. Dat is het onderwerp van dit artikel.
- Het tabblad *Afbeeldingen en Links* in het bewerkingsformulier biedt de mogelijkheid om een afbeelding op te nemen als een *Intro-afbeelding* of een *Volledig artikel-afbeelding* of beide. Dat wordt behandeld in een apart artikel over [Afbeeldingen en Links](jdocmanual?article=user/articles/article-images-and-links).

Het is het waard om een onderscheid te maken tussen lokale en externe afbeeldingen:

- **Lokale Afbeeldingen** bevinden zich op dezelfde site als de Joomla-installatie, meestal in de *images*-map. De afbeeldingslinks hoeven het protocol en domeinnaam niet te bevatten omdat ze uit de site-instellingen worden gehaald.
- **Externe Afbeeldingen** bevinden zich ergens anders op het internet. Ze moeten het protocol en domeinnaam in de link bevatten. Het gebruik van externe afbeeldingen door middel van zogenaamd *hot-linking* kan vandaag toegestaan zijn maar morgen niet meer. Het gebruik van externe afbeeldingen zonder toestemming wordt als slechte etiquette of zelfs diefstal beschouwd. 

## Een lokale afbeelding toevoegen

De beste manier om lokale afbeeldingen in te voegen is door de **CMS Content → Media** knop in de TinyMCE bewerkwerkbalk te gebruiken. Daarmee wordt een Media-dialoogvenster geopend waarmee je een afbeelding kunt selecteren in de afbeeldingsmap van de site.

**Belangrijk:** Plaats eerst de cursor waar je de afbeelding wilt invoegen. Dat kan aan het begin of het einde van een alinea zijn, of in een lege alinea.

![De media popup-dialoog](../../../en/images/articles/articles-edit-images-media.png)

Navigeer in het popup-dialoogvenster naar de afbeelding die je wilt gebruiken en selecteer deze. Bij selectie verschijnt er een formulier waarin om aanvullende gegevens wordt gevraagd.

- **Afbeeldingsbeschrijving (Alt Text)** Dit is belangrijk voor toegankelijkheidsdoeleinden en om te voldoen aan webstandaarden.
- **Afbeeldingsklasse** Als een afbeelding zonder bijschrift wordt gebruikt, kunnen hier enkele aangepaste klassen worden toegepast. Bijvoorbeeld, *float-end ms-2 mb-1* zal de afbeelding rechts uitlijnen en tekst eromheen laten vloeien met marges aan de linkerkant en eronder om te voorkomen dat de tekst de afbeelding raakt.
- **Figuurklasse** Als er een bijschrift is ingesteld, kan een uitlijningsklasse, indien van toepassing, worden toegepast op de figuur. Merk op dat in Cassiopeia marges voor de figuur worden toegepast door de sjabloon-stylesheet, dus *float-start* of *float-end* zijn voldoende.
- **Figuur Bijschrift** Maakt het bijschrift mogelijk dat de inhoud van dit veld als bijschrift onder de afbeelding weergeeft.

**Belangrijk:** Als het veld *Figuur Bijschrift* leeg is, wordt de afbeelding binnen een `<img...>` tag ingevoegd en zal het veld *Figuurklasse* niet worden gebruikt. Als het veld *Figuur Bijschrift* tekst bevat, wordt de `<img...>` tag verpakt in `<figure>...</figure>` tags. De meest bruikbare klassen om toe te voegen zijn *float-start* en *float-end* om de afbeelding links of rechts van de pagina te plaatsen met de tekst die eromheen loopt.

Selecteer de knop *Media Invoegen* om de afbeelding in te voegen. Het Invoegen Afbeelding scherm sluit en de afbeelding wordt in de editor weergegeven. Of selecteer de knop *Annuleren* om het Invoegen Afbeelding scherm te verlaten.

**Tip** selecteer de knop Editor Wisselen om de toegepaste Afbeelding- en Figuurstijlen te bekijken. Mogelijk moet je een figuur of afbeelding knippen en plakken om deze te verplaatsen.

### Het gebruik van Slepen en Neerzetten voor lokale afbeeldingen

Je kunt een afbeelding van het bureaublad of een bestandsbrowser direct naar de tekst van het artikel slepen en de afbeelding wordt naar de mediamap geüpload en in het artikel geplaatst. Het enige nadeel is dat al deze geüploade afbeeldingen in dezelfde mediamap worden geplaatst.

De locatie van de *Afbeeldingenmap* die voor uploaden wordt gebruikt en of deze functie is ingeschakeld (standaard ingeschakeld) worden ingesteld in de TinyMCE-configuratie-opties.

## Een externe afbeeldingslink toevoegen

Als de afbeelding die u wilt gebruiken niet in de afbeeldingsmap van uw Joomla-installatie staat, is een iets andere procedure nodig.

- Selecteer **Invoegen → Afbeelding** in de TinyMCE-werkbalk om een dialoogvenster te openen.
- Voer de afbeelding-URL in het veld **Bron** in.
- Vul de andere velden naar wens in.
- Het tabblad **Geavanceerd** biedt enkele opmaakopties die als inline-stijlen worden toegepast. Experimenteer met 1rem, 2, groove.

![De afbeelding invoegen pop-up dialoog](../../../en/images/articles/articles-edit-images-external-image.png)

### Drag en Drop gebruiken om externe afbeeldingslinks in te voegen

U kunt een afbeeldingslink van een externe website direct naar uw artikeltekst slepen. Maar wees ervan bewust dat dit ook de HTML van de afbeeldingcontainer kan kopiëren met klasseverklaringen die niet geldig zijn voor uw site.

## Afbeeldingen uploaden met behulp van de Mediakader

Je kunt nieuwe afbeeldingen uploaden naar je afbeeldingsmap vanaf de 
*CMS Content -> Media* pagina.

- Open het Mediakader en navigeer naar de map waar je nieuwe afbeeldingen voor het huidige artikel wilt opslaan.
- Selecteer de Upload-knop linksboven op het Media-scherm om een 
  bestandsbrowser te openen.
- Selecteer de afbeeldingsbestanden die je wilt uploaden. Selecteer Openen in de bestandsbrowser om de selectie te bevestigen. Opmerking: De stijl en indeling van de bestandsbrowser zijn afhankelijk van de browser en het besturingssysteem dat je gebruikt.
- De geselecteerde bestand(en) verschijnen in alfabetische volgorde op het Media/Afbeelding-scherm.
- Wanneer de upload voltooid is, verschijnt er een groene bevestigingsmelding bovenaan het scherm.

Je kunt nu de geüploade afbeelding selecteren en invoegen zoals voorheen.

*Vertaald door openai.com*

