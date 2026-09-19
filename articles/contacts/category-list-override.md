<!--
{
    "source": "https://docs.joomla.org/category-list-override.md",
    "title": "\u00dcberschreibung der Kategorieliste",
    "description": "Erfahren Sie, wie Sie eine Template-\u00dcberschreibung erstellen, um das Layout einer Kontaktliste in einer Kategorie zu verbessern ",
    "author": ""
}
-->

## Die Kontaktliste in einer Kategorie

Das Standardlayout von Kontakten in einer Kategorie wird durch ein Template im 
Code der Komponente com_contacts gesteuert. Das Standardlayout sieht so aus:

![Kulturausschuss mit dem Standardlayout und -stil](../../../en/images/contacts/category-list-override/01-contacts-culture-committee.png)

Es mag eine persönliche Meinung sein, aber für mich ist das Standardlayout der Kontakte nicht ganz 
zufriedenstellend. Meine Probleme:

* Die ursprünglichen Porträtbilder waren 500 Pixel breit und viel zu dominant.
* Der Name des Kontakts ist nicht ausreichend hervorgehoben.
* Die Aufzählung der persönlichen Daten hat keine Überschrift und wirkt isoliert.
* Die Rolle der Person hat keine Überschrift.
* Die Felder für Adresse und Postleitzahl fehlen.
* Die Standortdaten sind unvollständig.
* Die Daten jedes Kontakts sind in einer Tabelle angeordnet und auf schmalen Bildschirmen ziemlich beengt.

Wie kann man es also nach meinem Geschmack anpassen? Meine Lösung besteht darin, eine Template-Überschreibung
zu erstellen und einige benutzerdefinierte Stile hinzuzufügen. Hier ist das Ergebnis:

![Wirtschaftsausschuss mit einer Template-Überschreibung und benutzerdefinierten Stilen](../../../en/images/contacts/category-list-override/02-contacts-business-committee.png)

## Überschreibung des Template-Layouts

Der Ordner com_contact/tmpl/category enthält drei PHP-Dateien: default.php,
default_children.php und default_items.php. Die letzte Datei in dieser Liste enthält
das Tabellenlayout für die Liste.

Die Überschreibungsdateien werden über System / Site-Templates / Cassiopeia
Details und Dateien / Überschreibungen erstellen angelegt. Wählen Sie com_contact und anschließend category.
Der Ordner html enthält dann com_contact/category mit den drei oben genannten Template-Dateien. 

### Die Datei default.php in mydefault.php ändern

Die Datei `default.php` enthält eine Zeile, die festlegt, welches Layout für
jeden einzelnen Datensatz verwendet werden soll. Wählen Sie diese Datei zur Bearbeitung aus und **benennen Sie sie um** in
`mydefault.php` (oder verwenden Sie anstelle von `my` ein beliebiges Präfix). Verwenden Sie keinen
Unterstrich im Dateinamen!

Wenn Sie später das Formular Kontakte / Kategorie / Bearbeiten öffnen, können Sie im Feld
Layout auf der Registerkarte Optionen zwischen dem Komponentenlayout und Ihrem Überschreibungslayout wählen.
Es sieht so aus:

```
---From Global Options---
  Use Global
---From Component---
  Default
---From cassiopeia Template---
  mydefault
```

### Die Datei mydefault.php bearbeiten

Zeile 20 von `mydefault.php` enthält `$this->subtemplatename = 'items';`.
Ändern Sie `items` in `myitems`, sodass die Zeilen 18 bis 23 wie folgt aussehen:

```html
<div class="com-contact-category">
    <?php
        $this->subtemplatename = 'myitems';
        echo LayoutHelper::render('joomla.content.category_default', $this);
    ?>
</div>
```

### Die Datei default_items.php in mydefault_myitems.php ändern

Die Datei `default_items.php` enthält das Layout für jeden Kontakt. Sie muss
umbenannt werden, damit die Möglichkeit erhalten bleibt, das ursprüngliche Layout zu verwenden. Der erste Teil
des Namens ist unwichtig. Für das Layout wird der Teil `myitems` verwendet, auf den in der
Datei `mydefault.php` verwiesen wird.

### Die Datei mydefault_myitems.php bearbeiten

Der Abschnitt `<table>...</table>` dieser Datei erstreckt sich über die Zeilen 85 bis 204. Für die
Layout-Überschreibung habe ich die Tabellen-Auszeichnung durch die folgende Bootstrap-Grid-
Auszeichnung ersetzt. Auf schmalen Bildschirmen werden die drei Spalten untereinander angeordnet. Auf Bildschirmen mit einer Breite von mehr als
768 Pixeln stehen die Spalten nebeneinander. Die überarbeitete Auszeichnung hat die
benutzerdefinierten Felder unter den Namen des Kontakts verschoben.

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

## Gestaltung

Bootstrap-Stilklassen können in der Datei `mydefault_myitems.php` definiert werden.
Beispielsweise wird `<span class="fs-2">...</span>` verwendet, um die Schriftgröße des Kontaktnamens zu erhöhen. Weitere Stile können in der Datei
`user.css` hinzugefügt werden, beispielsweise die Anpassung von Aufzählungslisten, die nur innerhalb eines Tags mit der Klasse
`contactList` erscheinen.

Hier sind die in die Datei user.css eingetragenen Stile, mit denen das oben dargestellte Layout
des Wirtschaftsausschusses erzielt wurde.

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

*Übersetzt von openai.com*