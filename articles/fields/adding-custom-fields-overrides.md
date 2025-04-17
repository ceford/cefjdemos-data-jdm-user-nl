<!-- Filename: J3.x:Adding_custom_fields/Overrides / Display title: Voorbeeld Sjabloon Overschrijven -->

## Automatische Weergave van Veld

Elk van de beschikbare velden heeft een optie genaamd *Automatische Weergave* die kan worden ingesteld op een van de volgende:

* Na Titel
* Voor Weergave-inhoud
* Na Weergave-inhoud
* Niet automatisch weergeven

Als de laatste van deze opties is geselecteerd, wordt het veld niet weergegeven, tenzij je een sjabloonoverschrijving maakt om de weergave zelf te beheren. Of je kunt `{field ID}` toevoegen in een artikel om het veld te plaatsen waar je maar wilt. Maar je moet eraan denken dit in elk artikel te doen.

Dit voorbeeld laat zien hoe je een sjabloonoverschrijving maakt voor een Contact. De methoden zijn ook van toepassing op Inhoud en Gebruikerscomponenten.

## Maak een Template Override

Vanuit het Beheerdersmenu:

* Selecteer **Systeem / Sitetemplates / Cassiopeia Details en Bestanden**
* Selecteer het tabblad **Maak Overrides aan**.
* Selecteer **com_contact** uit het *Componenten* paneel.
* Selecteer **Contact** uit de lijst van beschikbare weergaven. Dit is de indeling voor een enkel contact.

In het **Editor** paneel:
* Selecteer **html / com_contact / contact / default.php** wat het bestand is dat de algemene indeling van de pagina voor een enkel contact bepaalt.
* Scroll door dit bestand en let op een reeks `<php if (...) : ?>` blokken. Elk blok zal een tekstgedeelte tonen of verbergen op basis van de contactinstellingen.
* Let ook op de regels die bevatten:
```
    <?php echo $this->item->event->afterDisplayTitle; ?> (regel 73)
    <?php echo $this->item->event->beforeDisplayContent; ?> (regel 98)
    <?php echo $this->item->event->afterDisplayContent; ?> (regel 189)
```
Een van deze variabelen, of geen van hen, wordt ingevuld afhankelijk van de waarde van het veld Automatische Weergave.

## Velden gebruiken in je override

Je hebt toegang tot alle velden die overeenkomen met het huidige item via een
`$this->item->jcfields` eigenschap, wat een array is die de volgende
gegevens voor elk veld bevat (dit voorbeeld is voor een Editor veld):

```php
    Array
    (
        [4] => stdClass Object
            (
                [id] => 4
                [title] => article-editor
                [name] => article-editor
                [checked_out] => 0
                [checked_out_time] => 0000-00-00 00:00:00
                [note] =>
                [state] => 1
                [access] => 1
                [created_time] => 2017-04-07 12:08:59
                [created_user_id] => 856
                [ordering] => 0
                [language] => *
                [fieldparams] => Joomla\Registry\Registry Object
                    (
                        [data:protected] => stdClass Object
                            (
                                [buttons] =>
                                [width] =>
                                [height] =>
                                [filter] =>
                            )

                        [initialized:protected] => 1
                        [separator] => .
                    )

                [params] => Joomla\Registry\Registry Object
                    (
                        [data:protected] => stdClass Object
                            (
                                [hint] =>
                                [render_class] =>
                                [class] =>
                                [showlabel] => 1
                                [disabled] => 0
                                [readonly] => 0
                                [show_on] =>
                                [display] => 2
                            )

                        [initialized:protected] => 1
                        [separator] => .
                    )

                [type] => editor
                [default_value] =>
                [context] => com_content.article
                [group_id] => 0
                [label] => article-editor
                [description] =>
                [required] => 0
                [language_title] =>
                [language_image] =>
                [editor] =>
                [access_level] => Public
                [author_name] => Super User
                [group_title] =>
                [group_access] =>
                [group_state] =>
                [value] => Bar
                [rawvalue] => Bar
            )
    )
```

## Render het veld

De functie `FieldsHelper::render()` wordt gebruikt om elk veld weer te geven. Voeg eerst een `use Joomla\Component\Fields\Administrator\Helper\FieldsHelper;` verklaring toe aan de lijst met `use` verklaringen bovenaan het override-bestand:

```php
defined('_JEXEC') or die;

use Joomla\CMS\Helper\ContentHelper;
use Joomla\CMS\HTML\HTMLHelper;
use Joomla\CMS\Language\Text;
use Joomla\CMS\Layout\FileLayout;
use Joomla\CMS\Layout\LayoutHelper;
use Joomla\CMS\Plugin\PluginHelper;
use Joomla\CMS\Router\Route;
use Joomla\Component\Contact\Site\Helper\RouteHelper;
use Joomla\Component\Fields\Administrator\Helper\FieldsHelper;
```

Vervolgens, waar je de velden in je sjabloon wilt plaatsen, gebruik je de volgende code:
```php
<?php foreach ($this->item->jcfields as $field) : ?>
    <?php echo FieldsHelper::render($field->context, 'field.render', array('field' => $field)); ?><br>
<?php endforeach ?>
```

Of voor een ruwe override, die de label niet vertaalt:

```php
<?php foreach ($this->item->jcfields as $field) : ?>
    <?php echo $field->label . ':' . $field->value; ?><br>
<?php endforeach ?>
```

## Individuele velden laden

Om individuele velden aan je content toe te voegen, begin je met het kiezen van specifieke namen voor je aangepaste velden, gebruikmakend van het **Naam** veld, dat zal worden gebruikt om je veld direct aan te roepen in de overschrijvingscode. In het `Opties` tabblad, selecteer **Nee** in het `Automatisch Weergeven` veld om te voorkomen dat het automatisch wordt weergegeven in een van de standaard posities.

Plaats vervolgens de onderstaande code aan het begin van je bestand om directe toegang per naam tot aangepaste velden in een override mogelijk te maken. Dit moet je doen voor elk override PHP-bestand waarop je individuele aangepaste velden wilt plaatsen.

```php
<?php foreach($this->item->jcfields as $jcfield) {
    $this->item->jcFields[$jcfield->name] = $jcfield;
} ?>
```

Ten slotte moet je de code voor veldplaatsing toevoegen op de plek waar je het veldlabel of de veldwaarde wilt weergeven.

Om het **label** van het veld aan je override toe te voegen, voeg je de onderstaande code in, waarbij je `naam-van-veld` vervangt door de naam van het veld.

```php
<?php echo $this->item->jcFields['naam-van-veld']->label; ?>:&nbsp;
```

Om de **waarde** van het veld aan je override toe te voegen, voeg je de onderstaande code in, waarbij je `naam-van-veld` vervangt door de naam van het veld.

```php
<?php echo $this->item->jcFields['naam-van-veld']->rawvalue; ?>
```

Je kunt deze code aan elk deel van je override toevoegen. Voorbeelden: De inhoud van een div, de src in een `img`-tag, binnen een CSS-classattribute, enzovoort.
