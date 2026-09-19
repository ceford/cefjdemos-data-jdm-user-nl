<!--
{
    "source": "https://docs.joomla.org/category-list-override.md",
    "title": "Overschrijving van categorielijst",
    "description": "Leer hoe je een sjabloonoverschrijving maakt om de lay-out van een lijst met contactpersonen in een categorie te verbeteren ",
    "author": ""
}
-->

## De lijst met contacten in een categorie

De standaardindeling van contacten in een categorie wordt beheerd door een template in de code van de com_contacts-component. De standaardindeling ziet er als volgt uit:

![cultuurcommissie met de standaardindeling en -stijl](../../../en/images/contacts/category-list-override/01-contacts-culture-committee.png)

Het is misschien een persoonlijke mening, maar voor mij is de standaardindeling van contacten niet helemaal bevredigend. Mijn problemen:

* De oorspronkelijke portretfoto's waren 500 pixels breed en veel te dominant.
* De naam van het contact wordt niet voldoende benadrukt.
* De lijst met persoonlijke gegevens heeft geen kop en lijkt geïsoleerd.
* De rol van de persoon heeft geen kop.
* De velden voor het adres en de postcode ontbreken.
* De locatiegegevens zijn onvolledig.
* De gegevens voor elk contact worden in een tabel weergegeven en zijn op smalle schermen nogal krap.

Dus hoe kan ik dit naar mijn eigen voorkeur aanpassen? Mijn oplossing is een template-override te maken en enkele aangepaste stijlen toe te voegen. Dit is het resultaat:

![zakelijke commissie die een sjabloonoverschrijving en aangepaste stijlen gebruikt](../../../en/images/contacts/category-list-override/02-contacts-business-committee.png)

## Overschrijving van de sjabloonlay-out

De map com_contact/tmpl/category bevat drie PHP-bestanden: default.php,
default_children.php en default_items.php. Het laatste bestand in deze lijst bevat
de tabelindeling voor de lijst.

De overschrijvingsbestanden worden aangemaakt via Systeem / Sitesjablonen / Cassiopeia
Details en bestanden / Overschrijvingen maken. Selecteer com_contact en vervolgens category.
De map html bevat vervolgens com_contact/category met de drie hierboven genoemde
sjabloonbestanden.

### Het bestand default.php wijzigen in mydefault.php

Het bestand `default.php` bevat een regel die aangeeft welke layout moet worden gebruikt voor 
elk afzonderlijk record. Selecteer dit bestand om het te bewerken en **hernoem** het naar 
`mydefault.php` (of gebruik een ander voorvoegsel in plaats van `my`). Gebruik geen 
underscore in de bestandsnaam!

Wanneer u later naar het formulier Contactpersonen / Categorie / Bewerken gaat, kunt u in het
tabblad Opties via het veld Layout kiezen tussen de componentlayout en uw overschrijvingslayout.
Het ziet er als volgt uit:

```
---From Global Options---
  Use Global
---From Component---
  Default
---From cassiopeia Template---
  mydefault

```

### Het bestand mydefault.php bewerken

Regel 20 van `mydefault.php` bevat `$this->subtemplatename = 'items';`.
Wijzig `items` in `myitems`, zodat regels 18 tot en met 23 er als volgt uitzien:

```html
<div class="com-contact-category">
    <?php
        $this->subtemplatename = 'myitems';
        echo LayoutHelper::render('joomla.content.category_default', $this);
    ?>
</div>
```

### Wijzig het bestand default_items.php in mydefault_myitems.php

Het bestand `default_items.php` bevat de lay-out voor elk contact. Het moet worden
hernoemd om de optie te behouden om de oorspronkelijke lay-out te gebruiken. Het
eerste deel van de naam is onbelangrijk. Het is het gedeelte `myitems` waarnaar in
het bestand `mydefault.php` wordt verwezen dat voor de lay-out wordt gebruikt.

### Bewerk het bestand mydefault_myitems.php

De sectie `<table>...</table>` van dit bestand beslaat de regels 85 tot en met 204. Voor
de lay-outherschrijving heb ik de tabelopmaak vervangen door de volgende Bootstrap-gridopmaak.
Op smalle schermen worden de drie kolommen onder elkaar geplaatst. Op schermen die breder
zijn dan 768 pixels staan de kolommen naast elkaar. In de herziene opmaak zijn de
aangepaste velden onder de contactnaam geplaatst.

```
<div class="container-fluid text-center border border-2">
<?php $nrows = 0; foreach ($this->items as $i => $item) : ?>
    <?php if ($item->published !== 1 ||
        (!empty($item->publish_up) && strtotime($item->publish_up) > strtotime(Factory::getDate())) ||
        (!empty($item->publish_down) && strtotime($item->publish_down) < strtotime(Factory::getDate()))) { continue; } ?>
        <div class="row cat-list-row<?php echo $nrows % 2; $nrows += 1; ?> align-items-center">
            <div class="col-12 col-md-3">
                <?php if ($this->params->get('show_image_heading')) : ?>
                    <?php if ($item->image) : ?>
                        <?php echo LayoutHelper::render(
                            'joomla.html.image',
                            [
                                'src'   => $item->image,
                                'alt'   => 'official image of ' . $item->name,
                                'class' => 'contact-thumbnail img-thumbnail',
                            ]
                        ); ?>
                    <?php endif; ?>
                <?php endif; ?>
            </div>
            <div class="col-12 col-md-3">
                <div class="parliament-committee-fields">
                <a href="<?php echo Route::_(RouteHelper::getContactRoute($item->slug, $item->catid, $item->language)); ?>">
                    <span class="fs-2"><?php echo $this->escape($item->name); ?></span>
                </a>
                    <?php echo $item->event->beforeDisplayContent; ?>
                </div>
            </div>
            <div class="col-12 col-md-6 text-start">
                <?php if ($this->params->get('show_position_headings') && !empty($item->con_position)) : ?>
                    <strong><?php echo Text::_('COM_CONTACT_FIELD_INFORMATION_POSITION_LABEL'); ?></strong><br>
                    <?php echo $item->con_position; ?><br>
                <?php endif; ?>
                <?php if ($this->params->get('show_suburb_headings')) : ?>
                    <?php $location = []; ?>
                    <?php if (!empty($item->address)) : ?>
                        <?php $location[] = $item->address; ?>
                    <?php endif; ?>
                    <?php if (!empty($item->suburb)) : ?>
                        <?php $location[] = $item->suburb; ?>
                    <?php endif; ?>
                    <?php if (!empty($item->state)) : ?>
                        <?php $location[] = $item->state; ?>
                    <?php endif; ?>
                    <?php if (!empty($item->postcode)) : ?>
                        <?php $location[] = $item->postcode; ?>
                    <?php endif; ?>
                        <strong><?php echo Text::_('COM_CONTACT_FIELD_INFORMATION_ADDRESS_LABEL'); ?></strong><br>
                    <?php echo implode("<br>\n", $location); ?><br>
                <?php endif; ?>
                <?php if (!empty($item->misc)) : ?>
                    <?php echo $item->misc; ?>
                <?php endif; ?>
            </div>
        </div>
    <?php endforeach; ?>
</div>
```

## Styling

Bootstrap-stijlklassen kunnen worden gedefinieerd in het bestand `mydefault_myitems.php`.
Bijvoorbeeld: `<span class="fs-2">...</span>` wordt gebruikt om de tekengrootte
van de naam van het contact te vergroten. Andere stijlen kunnen worden toegevoegd in het bestand
`user.css`, bijvoorbeeld het aanpassen van opsommingslijsten die alleen verschijnen binnen een tag met
een klasse `contactList`.

Hier volgen de stijlen die in het bestand user.css zijn ingevoerd om de lay-out
van de hierboven geïllustreerde Business Committee te verkrijgen.

```
.contact-thumbnail {
  max-width: 200px;
  margin-right: 1rem;
}
a:has(.contact-thumbnail) {
  font-weight: 700;
  font-size: larger;
}
#contactList ul {
  list-style-type: none;
  padding-left: 0;
}
.cat-list-row0 {
  background-color: #efefef;
}
.cat-list-row0:hover, .cat-list-row1:hover  {
  background-color: #ddd;
}
div.parliament-committee-fields {
  text-align: left;
  margin-top: 1rem;
}
div.parliament-committee-fields ul.fields-container {
  list-style-type: none;
  padding-left: 0;
}
div.parliament-committee-fields ul.fields-container span.field-label {
  font-weight: 700;
}
```

*Vertaald door openai.com*