<!--
{
    "source": "https://jdocmanual.org/jdocmanual?article=user/templates/pagination-wrap",
    "title": "Paginering omwikkelen",
    "description": "Leer een eenvoudige methode om de pagineringslijst op smalle schermen te laten omwikkelen. ",
    "author": ""
}
-->

In Joomla kunnen lijsten met artikelen, gebruikers en andere items erg lang zijn. Daarom worden ze in batches weergegeven, standaard 20.

## De normale pagineringsbalk

Om door de batches te navigeren, bevindt zich onder de lijst met items een pagineringsbalk waarmee de gebruiker de volgende batch items kan selecteren, zoals in deze illustratie:

![de normale pagineringsbalk van de lijst](../../../en/images/templates/pagination-wrap/01-pagination-wide-screen.png)

## Paginering op smalle schermen

De pagineringsbalk werkt goed op brede schermen. Op smalle schermen kan de pagineringsbalk echter breder zijn dan het scherm. Hierdoor moet u naar rechts scrollen om andere elementen op de pagina te vinden, zoals hamburgermenu's.

![de pagineringsbalk op een smal scherm](../../../en/images/templates/pagination-wrap/02-pagination-narrow-screen.png)

In de bovenstaande illustratie zijn elementen in het grijze gebied aan de rechterkant aanvankelijk *buiten beeld* en worden ze waarschijnlijk over het hoofd gezien. De gebruiker moet naar rechts scrollen om ze te zien. In dit geval zijn de elementen buiten beeld het werkbalkpictogram rechtsboven en het menupictogram rechtsonder.

## Oplossing met een sjabloonoverride

Deze oplossing voegt een klasse *flex-wrap* toe aan de code die de paginabalk genereert.

- Ga in de backend naar Systeem > Beheerdersjablonen > Atum-details en -bestanden
- Selecteer eventueel html > layouts om te zien wat daar staat
- Selecteer het tabblad **Overrides maken**
- Selecteer in het vak Layouts **joomla** en vervolgens **pagination**
- Selecteer in het tabblad Editor html > layouts > joomla > pagination > **links.php**
- Zoek regel 70 met `<ul class="pagination ms-auto me-0">`
- Voeg `flex-wrap` toe aan de lijst met klassen: `<ul class="pagination ms-auto me-0 flex-wrap">`
- **Opslaan en sluiten**
- Optioneel: je kunt /html/layouts/joomla/pagination/link.php en /html/layouts/joomla/pagination/links.php verwijderen

Bekijk het resultaat op zowel brede als smalle schermen. Op het smalle scherm worden het werkbalkpictogram en menupictogram nu weergegeven binnen de normale schermbreedte:

![de gewijzigde paginabalk op een smal scherm](../../../en/images/templates/pagination-wrap/02-modified-pagination-narrow-screen.png)
Volg voor de sitesjabloon deze instructies, maar maak een override in de Cassiopeia-sjabloon.

*Vertaald door openai.com*