<!-- Filename: category-list-override.md / Display title: Categorie Lijst Overschrijven   -->

## De Menu-optie Contacten in een Categorie Weergeven

Het kan een persoonlijke mening zijn, maar voor mij is de standaard layout van de Contactcategorielijst niet helemaal bevredigend. Mijn problemen:

* De contactfoto's zijn te groot, net iets minder dan 500 pixels breed.
* De contactnaam krijgt niet voldoende nadruk.
* De opsomming van persoonlijke gegevens heeft geen titel en lijkt geïsoleerd.
* De positie heeft geen titel, waardoor het geïsoleerd kan lijken.
* De velden voor het adres en de postcode ontbreken.
* De locatiegegevens zijn niet compleet.
* De persoonlijke verklaring ontbreekt.
* De lijst is opgesteld in een tabel, wat iets beter is op smalle schermen, maar nogal krap overkomt.

Dus hoe kan ik het naar mijn smaak aanpassen?

## Stijlen

De afbeelding heeft de CSS-stijl `contact-thumbnail img-thumbnail`. De ontwikkelaarstools van de browser geven aan dat `img-thumbnail` is ingesteld op `max-width: 100%;`, maar `contact-thumbnail` wordt niet gebruikt. De enige keer dat deze stijl voorkomt op de gehele site is op deze locatie, dus lijkt het veilig om een overschrijving in user.css in te stellen om de afbeeldingsbreedte te beperken. En de lettergrootte van de contactnaam kan worden vergroot met behulp van de omhullende `a`-tag:

```
.contact-thumbnail {
  max-width: 200px;
  margin-right: 1rem;
}
a:has(.contact-thumbnail) {
  font-weight: 700;
  font-size: larger;
}
```

De opsomming van aangepaste velden kan worden verbeterd door de opsommingstekens en de opvulling te verwijderen door alleen opsommingen te selecteren die verschijnen binnen een tag met de klasse `contactList`:

```
#contactList ul {
  list-style-type: none;
  padding-left: 0;
}
```
![gestileerd zakelijk comité](../../../en/images/contacts/contact-business-committee-styled.png)

Dat is zoveel mogelijk wat er gedaan kan worden met stijlen. Beter, maar nog steeds niet goed genoeg. Om meer items toe te voegen en de indeling te veranderen, is een indelingsoverschrijving nodig.

## Sjabloonlay-out Aanpassing

De map com_contact/tmpl/category bevat drie PHP-bestanden: default.php, default_children.php en default_items.php. Het laatste in deze lijst bevat de tabelindeling voor de lijst.

De aanpassingsbestanden worden gemaakt via Systeem / Site Templates / Cassiopeia Details en Bestanden / Aanpassingen Maken. Selecteer com_contact en vervolgens category. De html-map bevat dan com_contact/category met de drie hierboven genoemde sjabloonbestanden. De default_items.php is degene die je moet selecteren om te bewerken. Regels 83 tot 203 bevatten de tabel die voor de lay-out wordt gebruikt.

Het is misschien niet meteen duidelijk, maar $this->items is een array van categorielede en elk lid bevat eigenlijk alle gegevens voor elk item, niet alleen die in de menuinstellingen worden vermeld.

Het volgende is een vervanging voor de `<table>...</table>`-sectie van het default_items.php-bestand met een Bootstrap-grid. Op smalle schermen worden de drie kolommen gestapeld. Op schermen breder dan 768 pixels staan de kolommen naast elkaar. Meer uitleg volgt na de code.

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
                                'alt'   => 'officiële afbeelding van ' . $item->name,
                                'class' => 'contact-thumbnail img-thumbnail',
                            ]
                        ); ?>
                    <?php endif; ?>
                <?php endif; ?>
            </div>
            <div class="col-12 col-md-3">
                <a href="<?php echo Route::_(RouteHelper::getContactRoute($item->slug, $item->catid, $item->language)); ?>">
                    <span class="fs-2"><?php echo $this->escape($item->name); ?></span>
                </a>
            </div>
            <div class="col-12 col-md-6 text-start">
                <?php if ($this->params->get('show_position_headings') && !empty($item->con_position)) : ?>
                    <strong>Positie</strong><br>
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
                        <strong>Adres</strong><br>
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
### Uitleg

De contactlijst kan items bevatten die niet gepubliceerd zijn, of publicatie- en einddatums hebben die niet actueel zijn. Deze moeten worden uitgesloten van weergave en een aparte teller is nodig om de afwisseling van achtergrondkleuren in elke rij te behouden.

De img-tag wordt gerenderd als:
```
<img src="/j51/images/parliament/Official_portrait_of_Liam_Byrne_crop_2.jpg"
alt="officiële afbeelding van Liam Byrne" class="contact-thumbnail img-thumbnail"
width="479" height="639" loading="lazy">
```
De `<span class="fs-2">...</span>`-klasse stelt de contactnaam in op lettergrootte 2, wat overeenkomt met Kop 2.

Het item `show_suburb_headings` wordt gebruikt als een proxy om het hele adres te tonen, aangezien sommige van de individuele adresitems geen Toon/Verberg-selectors hebben in het menu-item.

### Extra Styling

De rasterversie van de contactlijst heeft extra styling nodig in user.css:
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
```

### Resultaat

![gerasterde zakencommissie](../../../en/images/contacts/contact-business-committee-grid.png)

*Vertaald door openai.com*

