<!-- Filename: J4.x:Media:_Uploading_SVG_files / Display title: SVG-bestanden uploaden -->

## Inleiding

SVG (Scalable Vector Graphics) bestanden worden standaard niet ondersteund in Joomla. Er zijn een paar stappen nodig om de Media-component ze te laten ondersteunen.

## Media-opties

Via het menu van de beheerder:

* Selecteer **Media** vanaf het *Home Dashboard* of vanuit het *Inhoud*-menu.
* Selecteer de **Opties**-knop in de Media-*Werkbalk*.

Er zijn 3 velden die bijgewerkt moeten worden; allemaal zijn het komma-gescheiden lijsten, dus je hoeft alleen een komma en de juiste waarde toe te voegen:

- Voeg aan het einde van de reeds beschikbare lijst in *Toegestane extensies* toe: `,svg`.
- Voeg aan het einde van de reeds beschikbare lijst in *Legale afbeeldings-extensies* toe: `,svg`.
- Voeg aan het einde van de reeds beschikbare lijst in *Legale MIME-typen* toe: `,image/svg+xml`.
- **Opslaan & Sluiten**

Vanaf nu zou je SVG-bestanden moeten kunnen uploaden in de Media Manager. Tenzij...

## Voorkomt Joomla nog steeds het uploaden van SVG-bestanden?

SVG is geen rasterafbeeldingformaat (zoals PNG-bestanden, die pixels bevatten), maar is geschreven in XML (Extensible Markup Language). Het is tekstgebaseerd, direct bruikbaar binnen het DOM (Document Object Model), CSS kan eigenschappen wijzigen en JavaScript kan interactiviteit toevoegen.

Als zodanig zijn SVG-bestanden vatbaar voor alle XML-gerelateerde aanvalspatronen:

- Cross-site scripting – of XSS (via het `<script>`-tag en evenementen).
- HTML-injecties (via het `<foreignObject>`-element – foreignObject stelt je in staat om elementen uit een andere XML-namespace op te nemen).
- Denial of service (als het `<xlink:href>`-element verkeerd wordt gebruikt).

Vanaf Joomla 4.1 wordt een saneringstool gebruikt om de inhoud van elk SVG-bestand dat via de Media Manager wordt geüpload te controleren. De regels zijn streng en zorgen ervoor dat bestanden de site niet kunnen schaden. Daarom moeten sommige bestanden mogelijk handmatig worden **gereinigd** (onthoud dat SVG-bestanden tekstbestanden zijn en in een teksteditor kunnen worden bewerkt) of met behulp van een externe tool voordat ze met succes kunnen worden geüpload.

**Tip:** deze sites reinigen svg-bestanden die zijn gemaakt in *Inkscape*:

* [SVG Sanitizer Test](https://svg.enshrined.co.uk/)
* [SVG Cleaner & Optimizer](https://iconly.io/tools/svg-cleaner)
* [SVGminify.com](https://www.svgminify.com/)

*Vertaald door openai.com* 

