<!-- Filename: J6.x:Workflow_Scenarios_Example_2 / Display title: Voorbeeld Workflow 2  -->

## Introductie

Dit voorbeeld betreft twee gebruikers, Alice en Bob, die respectievelijk de voorzitter en secretaris van een commissie zijn. De werkwijze omvat het voorbereiden en goedkeuren van agenda's en notulen van commissievergaderingen. Charlie is een commissielid dat toegang zal hebben tot commissiedocumenten wanneer deze worden gepubliceerd. De werkwijze maakt enkel gebruik van de frontend.

## Gebruikersgroepen

Maak eerst nieuwe gebruikersgroepen aan, allemaal kinderen van *Geregistreerd*.

- **Commissie** Een kind van *Geregistreerd* 
- **Voorzitter** Een kind van *Commissie*
- **Secretaris** Een kind van *Commissie*

![Aangepaste gebruikersgroepen](../../../en/images/workflows/example-2-user-groups.png)

## Gebruikerstoegangsniveau

- Maak een nieuw niveau, **Comité** en voeg *Comité* toe aan Gebruikersgroepen met Kijktoegang.
- Voeg in het *Speciale* Toegangsniveau *Comité* toe aan de Gebruikersgroepen met Kijktoegang.

![Kijktoegangsniveaus](../../../en/images/workflows/example-2-viewing-access-levels.png)

## Gebruikers Aanmaken

- **Alice** in de *Voorzitter* groep.
- **Bob** in de *Secretaris* groep.
- **Charlie** in de *Commissie* groep.

## Maak de Workflow

- **Naam** *Commissie Workflow*
- **Beschrijving** *Workflow voor de voorbereiding van commissiedocumenten.*
- **Rechten**
  - **Commissie** Allemaal ingesteld op *Geërfd* Niet toegestaan (geërfd).
  - **Voorzitter** Allemaal ingesteld op *Toegestaan* behalve *Verwijderen*. Misschien...
  - **Secretaris** Allemaal ingesteld op *Toegestaan* behalve *Verwijderen* en *Status Bewerken*.

![Lijst van Workflows](../../../en/images/workflows/example-2-workflows-list.png)

### Maak de Workflow Stadia

- **Ontwerp**
  - **Notitie** *Documenten in voorbereiding.*
  - **Rechten** Allemaal op *Geërfd* gelaten.
- **Beoordeling**
  - **Notitie** *Documenten wachten op goedkeuring.*
  - **Rechten** Allemaal op *Geërfd* gelaten.
- **Publiceren**
  - **Notitie** *Documenten gepubliceerd.*
  - **Rechten** Allemaal op *Geërfd* gelaten.

![Workflow stadia](../../../en/images/workflows/example-2-stages-committee-workflow.png)

### Maak de Workflow Overgangen

#### Ontwerp naar Beoordeling

Dit is de normale voorwaartse overgang in de volgorde van stadia.

- **Naam** *Ontwerp/Beoordeling*
- **Overgangstab**
  - **Huidig Stadium** *Ontwerp*
  - **Doelstadium** *Beoordeling*
  - **Notitie** *Overgang naar volgende stadium.*
- **Overgangsactiestab**
  - **Kenmerkend Stadium** *- Geen Geselecteerd -*
  - **Publicatiestatus** *- Geen Geselecteerd -*
- **Notificatietab**
  - **Verstuur Notificatie** *Ja* Ontvangers moeten *Systeem E-mails Ontvangen* ingeschakeld hebben om e-mailmeldingen te ontvangen.
  - **Extra Berichttekst** Iets specifiek voor deze workflow?
  - **Gebruikersgroepen** *Voorzitter*
  - **Gebruikers** Een alternatief voor het gebruik van Gebruikersgroepen.
- **Rechtentab** Allemaal ingesteld op **Geërfd**.

#### Beoordeling naar Ontwerp

Dit is de terugkeer naar een vorige stadium in de volgorde die wordt opgeroepen wanneer de Voorzitter meer werk door de Secretaris vereist. De formuliervelden zijn vergelijkbaar met de Ontwerp/Beoordeling velden behalve voor de Notitie en de *Huidig Stadium* en *Doelstadium* die omgekeerd zijn.

#### Beoordeling naar Publiceren

Dit is de overgang die de status van een item verandert van *Ongepubliceerd* naar *Gepubliceerd*. Alleen de Voorzitter heeft toestemming om die verandering te maken.

- **Naam** *Beoordeling/Publiceren*
- **Overgangstab**
  - **Huidig Stadium** *Beoordeling*
  - **Doelstadium** *Publiceren*
  - **Notitie** *De laatste overgang naar publicatie.*
- **Overgangsactiestab**
  - **Kenmerkend Stadium** *- Geen Geselecteerd -*
  - **Publicatiestatus** *Gepubliceerd*
- **Notificatietab**
  - **Verstuur Notificatie** *Ja* Ontvangers moeten *Systeem E-mails Ontvangen* ingeschakeld hebben om e-mailmeldingen te ontvangen.
  - **Extra Berichttekst** *Een commissiedocument is gepubliceerd en is nu beschikbaar om te bekijken.*
  - **Gebruikersgroepen** *Commissie*
  - **Gebruikers** Een alternatief voor het gebruik van Gebruikersgroepen.
- **Rechtentab**
  - **Secretaris** Stel *Uitvoeren Overgang* in op *Geweigerd*.

#### Publiceren naar Beoordeling

Dit is een verandering van Publiceren terug naar Beoordeling. Is het echt nodig? Een gepubliceerd artikel kan nog steeds worden bewerkt door de Secretaris of Voorzitter. Misschien is een Commissiedocument met gevoelige gegevens per ongeluk gepubliceerd.

Indien nodig maak een Overgang vergelijkbaar met de *Beoordeling naar Publiceren* overgang maar met de Stadia omgekeerd, de *Overgangsacties / Publicatiestatus* ingesteld op *Ongepubliceerd* en een generieke *Extra Berichttekst*.

#### Archiveren

Dit is de overgang die wordt uitgevoerd wanneer een commissiedocument niet langer nodig is. In de workflow blijft het in het Publiceren stadium maar de artikelstatus wordt veranderd van Gepubliceerd naar Gearchiveerd.

- **Naam** *Archiveren*
- **Overgangstab**
  - **Huidig Stadium** *Publiceren*
  - **Doelstadium** *Publiceren*
  - **Notitie** *Verander artikelstatus van Gepubliceerd naar Gearchiveerd.*
- **Overgangsactiestab**
  - **Kenmerkend Stadium** *- Geen Geselecteerd -*
  - **Publicatiestatus** *Gearchiveerd*
- **Notificatietab**
  - **Verstuur Notificatie** *Nee* Dit is geen overgang die actie vereist.
- **Rechtentab**
  - **Secretaris** Stel *Uitvoeren Overgang* in op *Geweigerd*.

![Workflow overgangen](../../../en/images/workflows/example-2-transitions-committee-workflow.png)

## Maak een Nieuwe Categorie

<div class="alert alert-warning">Deze stap is heel belangrijk! Nieuwe 
commissiepapieren moeten met deze categorie worden aangemaakt, anders krijgen ze de standaardworkflow die door een Supergebruiker moet worden gewijzigd.</div>

- **Titel** *Commissie*
- **Workflow** Selecteer *Commissieworkflow* uit de lijst met Workflows.
- **Rechten** 
  - Auteur, Redacteur en Uitgever: Allemaal ingesteld op *Niet Toegestaan* of 
    achtergelaten op *Niet Toegestaan (Geërfd)*.
  - Commissie: Allemaal achtergelaten op *Geërfd*.
  - Voorzitter: Alles behalve *Verwijderen* ingesteld op *Toegestaan*.
  - Secretaris: Alles behalve *Verwijderen* en *Status Bewerken* ingesteld op *Toegestaan*.

## Maak een Menu-item

- **Titel** *Commissie Documenten*
- **Type Menu-item** Categorie Lijst
- **Kies een Categorie** *Commissie*
- **Toegang** *Commissie*

![Menu-item voor commissie documenten](../../../en/images/workflows/example-2-menu-item.png)

## Controleer de Site

Log in als Alice, Bob, Charlie en een Supergebruiker om te bekijken wat zij kunnen zien:

Alice, Bob en Charlie kunnen het Menu-item zien, maar niemand anders kan dat, zelfs een Supergebruiker niet. Na het selecteren van het menu-item kunnen Alice en Bob een tabel zien van Commissie-documenten, inclusief alle die niet zijn gepubliceerd. Charlie kan alleen een tabel van gepubliceerde Commissie-documenten zien of een verklarend bericht als er geen zijn gepubliceerd.

Alice en Bob kunnen ook een Bewerken-link zien voor elk artikel en een **Nieuw Artikel**-knop. Dit wordt meestal door Bob gebruikt om een Commissie-document te maken, maar Alice kan dat ook doen.

![Bobs weergave van de categorieënlijstpagina van commissie-documenten](../../../en/images/workflows/example-2-committee-papers.png)

### Om een Commissie-document te maken en te publiceren

- Log in als een Secretaris en selecteer de **Nieuw Artikel**-knop op de 
  *Commissie Documenten*-pagina.
- Voer de tekst in en *Sla op*. Dit kan over meerdere bewerk-sessies worden gedaan, 
  mogelijk over meerdere dagen of weken. Het artikel blijft Ongepubliceerd en in 
  de Conceptfase totdat...
- Selecteer het *Publiceren*-tabblad in het bewerkformulier en stel de *Workflow Fase* in op 
  Run Transitie **Concept/Beoordeling**. 
- Selecteer **Opslaan & Sluiten** om de transitie uit te voeren.
- Het werk van de Secretaris is voorlopig voltooid en een bericht is verzonden aan
  de Commissievoorzitter.
- De Voorzitter logt in, controleert het document dat klaar is voor Beoordeling en gebruikt de 
  **Beoordeling/Publiceren** transitie om het document *Gepubliceerd* te maken. Het werk van de
  Voorzitter is voorlopig voltooid en een bericht wordt verzonden aan de Commissieleden.
- Commissieleden kunnen inloggen en toegang krijgen tot het gepubliceerde document.

*Vertaald door openai.com*

