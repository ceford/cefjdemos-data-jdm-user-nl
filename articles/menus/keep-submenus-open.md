<!--
{
    "source": "https://docs.joomla.org/https:",
    "title": "Submenu's open houden",
    "description": " ",
    "author": ""
}
-->

Een menumodule kan worden gebruikt om een horizontaal menu (meestal bovenaan de pagina) of een verticaal menu (meestal in een zijbalk, links of rechts) weer te geven. In een horizontaal (bovenste) menu is het niet wenselijk om het submenu open te houden. Daarom is het standaardgedrag van een menumodule om de submenu's bij het laden van de pagina te sluiten.

## Gedrag van de schakelstatus *open*

In een verticaal (zijbalk)menu is het echter vaak wenselijk om een submenu open te laten wanneer het het actieve menu-item bevat. In Joomla 6.0 is een nieuwe CSS-klasse, `nav-active-open`, geïntroduceerd om specifiek te bepalen of submenu's bij het laden van de pagina automatisch worden geopend voor het actieve menu-item. Door deze klasse in te stellen, is dit nu mogelijk. De klasse wordt via de backend in de module ingesteld.

![menu class setting in backend for nav-active-open for toggle stay open on active menu](../../../en/images/menus/keep-submenus-open/01-menu-class-setting.png)

## Een zijbalkmenu maken zonder uitklapschakelaar

Als je alle submenu's open wilt houden, heb je geen uitklapschakelaar nodig. Gebruik in plaats daarvan een [template-override](jdocmanual?article=user/templates/template-overrides).

Zo maak je deze specifieke template-override:

1. Selecteer eerst Systeem → Templates → Sitetemplates in het menu van de Administrator en selecteer vervolgens het item Cassiopeia Details en bestanden. Hierdoor wordt het formulier Templates: Aanpassen (Cassiopeia) geopend.

2. Ga naar het tabblad Overrides maken en selecteer mod_menu:

![module menu template override selection](../../../en/images/menus/keep-submenus-open/02-create-override-select-mod-menu.png)

Hiermee worden alle layoutbestanden van de menumodule naar de override gekopieerd. Vervolgens wordt het tabblad Editor weer geopend.

3. Vouw in het tabblad Editor de items onder HTML → mod_menu uit. Hier vind je het bestand `default.php`. Open het bestand en kopieer de inhoud naar een veilige locatie. Sluit het bestand.

4. Maak een nieuw bestand in de map html → mod_menu. De naam mag geen underscore bevatten. In dit voorbeeld heet het nieuwe bestand `treedefault.php`. Hierdoor kun je in al je menumodules kiezen tussen de standaard menulayout en deze alternatieve menulayout. In de volgende lijst met overridebestanden is het origineel rood omlijnd en het nieuwe alternatief groen omlijnd.

![mod_menu override edit tab - open default.php](../../../en/images/menus/keep-submenus-open/03-edit-mod-menu.png)

4. Bewerk het nieuwe layoutbestand. De volgende stappen worden in omgekeerde volgorde weergegeven om de regelnummers tijdens het bewerkingsproces te behouden:

Wijzig regel 104 zodat deze het volgende bevat:

```
        echo '<ul class="list-unstyled ps-3" aria-hidden="false">';
```

Hierdoor blijft het menu open en wordt inspringing aan submenu's toegevoegd.

Vervang de regels 98 - 101 door `break`

```php
                    echo '<button class="mod-menu__toggle-sub" aria-expanded="false">' .
                 break;
                    '<span class="icon-chevron-down" aria-hidden="true"></span>' .
                    '<span class="visually-hidden">' . Text::sprintf('MOD_MENU_TOGGLE_SUBMENU_LABEL', $item->title) . '</span>' .
                    '</button>';
```

Verwijder de regels 93 - 94

```php
                    echo '<span class="icon-chevron-down" aria-hidden="true">' .
                        '</span></button>';
```

Verwijder de regels 66-71

```php
    // The next item is deeper - add toggle only here it is a heading or separator
    if ($item->deeper && (int) $item->level === $startLevel && in_array($item->type, ['separator', 'heading'])) {
        // Add a toggle button.
        echo '<button class="mod-menu__toggle-sub" aria-expanded="false">';
    }
```

Verwijder de regels 15 - 20

```php
/** @var Joomla\CMS\WebAsset\WebAssetManager $wa */
$wa = $app->getDocument()->getWebAssetManager();
$wa->getRegistry()->addExtensionRegistryFile('mod_menu');
$wa->usePreset('mod_menu.menu');
```

Dit is het volledige overridebestand `treedefault.php`:

```
<?php

/**
 * @package     Joomla.Site
 * @subpackage  mod_menu
 *
 * @copyright   (C) 2009 Open Source Matters, Inc. <https://www.joomla.org>
 * @license     GNU General Public License version 2 or later; see LICENSE.txt
 */

defined('_JEXEC') or die;

use Joomla\CMS\Helper\ModuleHelper;
use Joomla\CMS\Language\Text;

$tagId      = $params->get('tag_id', '') ?: 'mod-menu' . $module->id;
$id         = ' id="' . htmlspecialchars($tagId, ENT_QUOTES, 'UTF-8') . '"';
$startLevel = (int) $params->get('startLevel', 1);

// The menu class is deprecated. Use mod-menu instead
?>
<ul<?php echo $id; ?> class="mod-menu mod-list nav <?php echo $class_sfx; ?>">
<?php foreach ($list as $i => &$item) {
    $itemParams = $item->getParams();
    $class      = 'nav-item item-' . $item->id;

    if ($item->id == $default_id) {
        $class .= ' default';
    }

    if ($item->id == $active_id || ($item->type === 'alias' && $itemParams->get('aliasoptions') == $active_id)) {
        $class .= ' current';
    }

    if (in_array($item->id, $path)) {
        $class .= ' active';
    } elseif ($item->type === 'alias') {
        $aliasToId = $itemParams->get('aliasoptions');

        if (count($path) > 0 && $aliasToId == $path[count($path) - 1]) {
            $class .= ' active';
        } elseif (in_array($aliasToId, $path)) {
            $class .= ' alias-parent-active';
        }
    }

    if ($item->type === 'separator') {
        $class .= ' divider';
    }

    if ($item->deeper) {
        $class .= ' deeper';
    }

    if ($item->parent) {
        $class .= ' parent';
    }

    echo '<li class="' . $class . '">';

    switch ($item->type) :
        case 'separator':
        case 'component':
        case 'heading':
            require ModuleHelper::getLayoutPath('mod_menu', 'default_' . $item->type);
            break;
        default:
            require ModuleHelper::getLayoutPath('mod_menu', 'default_url');
            break;
    endswitch;

    // The next item is deeper.
    if ($item->deeper) {
        // Check type - add only on first level
        // @todo aria-label - set in menu item ???
        if ((int) $item->level === $startLevel) {
            switch ($item->type) {
                case 'heading':
                case 'separator':
                    break;

                default:
                    break;
            }
        }
        echo '<ul class="list-unstyled ps-3" aria-hidden="false">';
    } elseif ($item->shallower) {
        // The next item is shallower.
        echo '</li>';
        echo str_repeat('</ul></li>', $item->level_diff);
    } else {
        // The next item is on the same level.
        echo '</li>';
    }
}
?></ul>
```

## Resultaat

Het resultaat is een gewone lijst, zonder schakel functionaliteit voor de zijbalkmenumodule, hier links weergegeven:

![result with template override - plain list without toggle buttons and functionality](../../../en/images/menus/keep-submenus-open/05-site-result.png)

*Vertaald door openai.com*
