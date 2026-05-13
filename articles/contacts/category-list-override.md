<!--
{
  "source": "https://docs.joomla.org/category-list-override.md",
  "title": "Kategorienliste Überschreiben ",
  "description": "", 
  "author": ""
}
-->

## Der Menüpunkt "Kontakte in einer Kategorie auflisten"

Es mag eine persönliche Meinung sein, aber für mich ist das Standard-Layout der Kontaktkategorieliste nicht ganz zufriedenstellend. Meine Probleme:

* Die Kontaktfotos sind mit knapp 500 Pixeln Breite zu groß.
* Der Kontaktname wird nicht ausreichend betont.
* Die Aufzählung der persönlichen Details hat keine Überschrift und wirkt isoliert.
* Die Position hat keine Überschrift und könnte daher isoliert wirken.
* Die Adress- und Postleitzahlenfelder fehlen.
* Die Standortdaten sind unvollständig.
* Die persönliche Stellungnahme fehlt.
* Die Liste ist in einer Tabelle angeordnet, was auf schmalen Bildschirmen etwas besser ist, aber dennoch ziemlich beengt wirkt.

Wie kann ich es also nach meinem Geschmack anpassen? 

## Styling

Das Bild hat den CSS-Stil `contact-thumbnail img-thumbnail`. Die Entwicklertools des Browsers zeigen an, dass img-thumbnail auf `max-width: 100%;` gesetzt ist, aber contact-thumbnail wird nicht verwendet. Das einzige Vorkommen dieses Stils auf der gesamten Website befindet sich an dieser Stelle, daher scheint es sicher zu sein, ein Override in user.css einzurichten, um die Bildbreite zu beschränken. Und die Schriftgröße des Kontaktnamens kann mit dem umschließenden `a` Tag vergrößert werden:

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

Die Aufzählungsliste der benutzerdefinierten Felder kann verbessert werden, indem die Aufzählungszeichen und die Einrückung entfernt werden. Dazu wählt man nur Aufzählungslisten aus, die innerhalb eines Tags erscheinen, das die Klasse contactList hat:

```
#contactList ul {
  list-style-type: none;
  padding-left: 0;
}
```

![gestaltetes Geschäftskomitee](../../../en/images/contacts/category-list-override/01-contact-business-committee-styled.png)

Das ist so viel, wie mit dem Styling erreicht werden kann. Besser, aber immer noch nicht gut genug. Um weitere Elemente hinzuzufügen und das Layout zu ändern, wird ein Layout-Override erforderlich sein.

## Template-Layout-Override

Der Ordner com_contact/tmpl/category enthält drei PHP-Dateien: default.php, default_children.php und default_items.php. Die letzte in dieser Liste enthält das Tabellenlayout für die Liste.

Die Override-Dateien werden erstellt über System / Site Templates / Cassiopeia Details and Files / Create Overrides. Wählen Sie com_contact und dann category aus. Der Ordner html enthält dann com_contact/category mit den oben genannten drei Template-Dateien. Die default_items.php ist die, die zum Bearbeiten ausgewählt werden muss. Die Zeilen 83 bis 203 enthalten die Tabelle, die für das Layout verwendet wird.

Es ist möglicherweise nicht offensichtlich, aber $this->items ist ein Array von Kategorietmitgliedern und jedes Mitglied enthält tatsächlich alle Daten für jedes Element, nicht nur die im Menü genannten.

Das Folgende ist ein Ersatz für den `<table>...</table>` Abschnitt der default_items.php Datei unter Verwendung eines Bootstrap-Rasters. Auf schmalen Bildschirmen sind die drei Spalten gestapelt. Auf Bildschirmen, die breiter als 768 Pixel sind, sind die Spalten nebeneinander. Mehr Erklärungen folgen nach dem Code.

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
                                'alt'   => 'offizielles Bild von ' . $item->name,
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
                    <strong>Position</strong><br>
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
                        <strong>Adresse</strong><br>
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
### Erklärung

Die Kontaktliste kann Elemente enthalten, die nicht veröffentlicht sind, oder Veröffentlichungsdaten haben, die nicht aktuell sind. Diese müssen von der Anzeige ausgeschlossen werden und ein separater Zähler wird benötigt, um den Wechsel der Hintergrundfarben in jeder Zeile beizubehalten.

Das img-Tag wird gerendert als:
```
<img src="/j51/images/parliament/Official_portrait_of_Liam_Byrne_crop_2.jpg"
alt="offizielles Bild von Liam Byrne" class="contact-thumbnail img-thumbnail"
width="479" height="639" loading="lazy">
```
Die `<span class="fs-2">...</span>` Klasse setzt den Kontaktnamen auf Schriftgröße 2, was dem von Überschrift 2 entspricht.

Der `show_suburb_headings` Eintrag wird als Stellvertreter verwendet, um die gesamte Adresse anzuzeigen, da einige der einzelnen Adressenelemente keine Anzeigen/Ausblenden-Selektoren im Menüpunkt haben.

### Zusätzliche Stilgebung

Die gegitterte Version der Kontaktliste benötigt zusätzliche Stilgebung in der user.css:
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

### Ergebnis

![gegridder Geschäftsausschuss](../../../en/images/contacts/category-list-override/02-contact-business-committee-grid.png)

*Übersetzt von openai.com*

