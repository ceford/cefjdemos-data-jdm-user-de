<!--
{
    "source": "https://docs.joomla.org/https:",
    "title": "Untermen\u00fcs ge\u00f6ffnet halten",
    "description": " ",
    "author": ""
}
-->

Ein Menుమodul kann verwendet werden, um ein horizontales Menü (normalerweise oben auf der Seite) oder ein vertikales Menü (normalerweise in einer Seitenleiste links oder rechts) anzuzeigen. In einem horizontalen (oberen) Menü ist es nicht wünschenswert, das Untermenü geöffnet zu halten. Deshalb besteht das Standardverhalten eines Menүлmoduls darin, die Untermenüs beim Laden der Seite zu schließen.

## Verhalten beim Umschalten des Status *open*

In einem vertikalen (Seitenleisten-)Menü ist es jedoch oft wünschenswert, ein Untermenü geöffnet zu lassen, wenn es den aktiven Menüeintrag enthält. In Joomla 6.0 wurde speziell zur Steuerung der automatischen Öffnung von Untermenüs beim Laden der Seite für den aktiven Menüeintrag eine neue CSS-Klasse, `nav-active-open`, eingeführt. Durch das Setzen dieser Klasse ist dies nun möglich. Die Klasse wird im Modul über das Backend gesetzt.

![Einstellung der Menüklasse im Backend für nav-active-open zum Offenhalten beim aktiven Menüeintrag](../../../en/images/menus/keep-submenus-open/01-menu-class-setting.png)

## So erstellen Sie ein Seitenleistenmenü ohne Dropdown-Umschaltung

Wenn Sie alle Untermenüs geöffnet halten möchten, benötigen Sie keine Dropdown-Umschaltung. Verwenden Sie stattdessen ein [Template-Override](jdocmanual?article=user/templates/template-overrides).

So wird dieses spezielle Template-Override erstellt:

1. Wählen Sie zunächst im Administrationsmenü System → Templates → Site-Templates und anschließend den Eintrag Cassiopeia-Details und -Dateien. Dadurch wird das Formular Templates: Anpassen (Cassiopeia) geöffnet.

2. Wechseln Sie zum Tab Overrides erstellen und wählen Sie mod_menu:

![Auswahl des Template-Overrides für das Menümodul](../../../en/images/menus/keep-submenus-open/02-create-override-select-mod-menu.png)

Dadurch werden alle Layoutdateien des Menümoduls in das Override kopiert. Anschließend wird wieder der Tab Editor angezeigt.

3. Erweitern Sie im Tab Editor die Einträge unter HTML → mod_menu.  Hier finden Sie die Datei `default.php`. Öffnen Sie die Datei und kopieren Sie ihren Inhalt an einen sicheren Ort. Schließen Sie die Datei.

4. Erstellen Sie eine neue Datei im Ordner html → mod_menu. Ihr Name darf keinen Unterstrich enthalten. In diesem Beispiel heißt die neue Datei `treedefault.php`. Dadurch können Sie in jedem Ihrer Menümodule entweder das Standardmenü-Layout oder dieses alternative Menü-Layout auswählen. In der folgenden Liste der Override-Dateien ist das Original rot und die neue Alternative grün umrandet.

![Bearbeitungstab des mod_menu-Overrides – default.php geöffnet](../../../en/images/menus/keep-submenus-open/03-edit-mod-menu.png)

4. Bearbeiten Sie die neue Layoutdatei. Die folgenden Schritte sind in umgekehrter Reihenfolge aufgeführt, um während des Bearbeitungsvorgangs die Zeilennummern
beizubehalten:

Ändern Sie Zeile 104 so, dass sie Folgendes enthält:

```
        echo '<ul class="list-unstyled ps-3" aria-hidden="false">';
```

Dadurch bleibt das Menü geöffnet und den Untermenüs wird eine Einrückung hinzugefügt.

Ersetzen Sie die Zeilen 98–101 durch `break`

```php
                    echo '<button class="mod-menu__toggle-sub" aria-expanded="false">' .
                 break;
                    '<span class="icon-chevron-down" aria-hidden="true"></span>' .
                    '<span class="visually-hidden">' . Text::sprintf('MOD_MENU_TOGGLE_SUBMENU_LABEL', $item->title) . '</span>' .
                    '</button>';
```

Entfernen Sie die Zeilen 93–94

```php
                    echo '<span class="icon-chevron-down" aria-hidden="true">' .
                        '</span></button>';
```

Entfernen Sie die Zeilen 66–71

```php
    // The next item is deeper - add toggle only here it is a heading or separator
    if ($item->deeper && (int) $item->level === $startLevel && in_array($item->type, ['separator', 'heading'])) {
        // Add a toggle button.
        echo '<button class="mod-menu__toggle-sub" aria-expanded="false">';
    }
```

Entfernen Sie die Zeilen 15–20

```php
/** @var Joomla\CMS\WebAsset\WebAssetManager $wa */
$wa = $app->getDocument()->getWebAssetManager();
$wa->getRegistry()->addExtensionRegistryFile('mod_menu');
$wa->usePreset('mod_menu.menu');
```

Dies ist die vollständige Override-Datei `treedefault.php`:

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

## Ergebnis

Das Ergebnis ist eine einfache Liste ohne Umschaltfunktion für das Seitenleistenmenümodul, hier links dargestellt:

![Ergebnis mit Template-Override – einfache Liste ohne Umschaltflächen und -funktionalität](../../../en/images/menus/keep-submenus-open/05-site-result.png)

*Übersetzt von openai.com*
