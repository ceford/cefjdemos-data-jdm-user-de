<!--
{
  "source": "https://docs.joomla.org/J3.x:Adding_custom_fields",
  "title": "Beispiel für eine Vorlagenüberschreibung",
  "description": "", 
  "author": ""
}
-->

## Automatische Anzeige von Feldern

Jedes der verfügbaren Felder hat eine Option namens *Automatische Anzeige*, die auf eine der folgenden Einstellungen gesetzt werden kann:

* Nach dem Titel
* Vor dem Anzeigeinhalt
* Nach dem Anzeigeinhalt
* Nicht automatisch anzeigen

Wenn der letzte Punkt ausgewählt wird, wird das Feld nicht angezeigt, es sei denn, Sie erstellen eine Template-Überschreibung, um die Anzeige selbst zu steuern. Alternativ könnten Sie `{field ID}` in einem Beitrag hinzufügen, um das Feld an beliebiger Stelle zu platzieren. Aber Sie müssen daran denken, dies in jedem Beitrag zu tun.

Dieses Beispiel zeigt, wie man eine Template-Überschreibung für einen Kontakt erstellt. Die Methoden gelten auch für Inhalts- und Benutzungskomponenten.

## Eine Template-Override erstellen

Im Administrator-Menü:

* Wählen Sie **System / Site Templates / Cassiopeia Details und Dateien**.
* Wählen Sie die Registerkarte **Overrides erstellen**.
* Wählen Sie **com_contact** im Panel *Komponenten*.
* Wählen Sie **Kontakt** aus der Liste der verfügbaren Ansichten. Dies ist das Layout für
einen einzelnen Kontakt.

Im **Editor**-Panel:
* Wählen Sie **html / com_contact / contact / default.php**, was die Datei ist,
die das Gesamt-Layout der Seite für einen einzelnen Kontakt festlegt.
* Scrollen Sie durch diese Datei und achten Sie auf eine Reihe von `<php if (...) : ?>` Blöcken.
Jeder dieser Blöcke zeigt oder verbirgt einen Abschnitt Text, je nach den Kontakt-Einstellungen.
* Beachten Sie die Zeilen, die Folgendes enthalten:
```
    <?php echo $this->item->event->afterDisplayTitle; ?> (Zeile 73)
    <?php echo $this->item->event->beforeDisplayContent; ?> (Zeile 98)
    <?php echo $this->item->event->afterDisplayContent; ?> (Zeile 189)
```
Eine dieser Variablen, oder keine von ihnen, wird je nach Wert des Feldes
Automatische Anzeige gefüllt.

## Verwenden von Feldern in Ihrem Override

Sie haben alle Felder, die dem aktuellen Element entsprechen, über eine
`$this->item->jcfields` Eigenschaft zugänglich, die ein Array ist und die folgenden
Daten für jedes Feld enthält (dieses Beispiel ist für ein Editor-Feld):

```php
    Array
    (
        [4] => stdClass Object
            (
                [id] => 4
                [title] => beitraege-editor
                [name] => beitraege-editor
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
                [context] => com_content.beitrag
                [group_id] => 0
                [label] => beitraege-editor
                [description] =>
                [required] => 0
                [language_title] =>
                [language_image] =>
                [editor] =>
                [access_level] => Öffentlich
                [author_name] => Super Benutzer
                [group_title] =>
                [group_access] =>
                [group_state] =>
                [value] => Bar
                [rawvalue] => Bar
            )
    )
```

## Das Feld rendern

Die Funktion `FieldsHelper::render()` wird verwendet, um jedes Feld zu rendern. Fügen Sie zunächst eine `use Joomla\Component\Fields\Administrator\Helper\FieldsHelper;`-Anweisung zur Liste der `use`-Anweisungen oben in der Override-Datei hinzu:

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

Dann verwenden Sie den folgenden Code überall dort, wo Sie die Felder in Ihrem Template platzieren möchten:
```php
<?php foreach ($this->item->jcfields as $field) : ?>
    <?php echo FieldsHelper::render($field->context, 'field.render', array('field' => $field)); ?><br>
<?php endforeach ?>
```

Oder für ein Raw-Override, das das Label nicht übersetzt:

```php
<?php foreach ($this->item->jcfields as $field) : ?>
    <?php echo $field->label . ':' . $field->value; ?><br>
<?php endforeach ?>
```

## Individuelle Felder laden

Um individuelle Felder zu deinem Inhalt hinzuzufügen, beginne damit, spezifische Namen für deine benutzerdefinierten Felder zu wählen, indem du das **Name**-Feld verwendest, das in dem Override-Code direkt auf dein Feld verweisen wird. Wähle im `Optionen`-Tab **Nein** im `Automatische Anzeige`-Feld, um zu verhindern, dass es automatisch in einer der Standardpositionen angezeigt wird.

Um dann den direkten Zugriff auf benutzerdefinierte Felder per Namen in einem Override zu ermöglichen, platziere den unten stehenden Code am Anfang deiner Datei. Dies solltest du bei jeder Override-PHP-Datei tun, auf der du individuelle benutzerdefinierte Felder platzieren möchtest.

```php
<?php foreach($this->item->jcfields as $jcfield) {
    $this->item->jcFields[$jcfield->name] = $jcfield;
} ?>
```

Und schließlich solltest du den Feldplatzierungscode an der Stelle hinzufügen, an der das Feldlabel oder der Feldwert angezeigt werden soll.

Um das **Label** des Feldes zu deinem Override hinzuzufügen, füge den untenstehenden Code ein, und ersetze `name-of-field` durch den Namen des Feldes.

```php
<?php echo $this->item->jcFields['name-of-field']->label; ?>:&nbsp;
```

Um den **Wert** des Feldes zu deinem Override hinzuzufügen, füge den untenstehenden Code ein, und ersetze `name-of-field` durch den Namen des Feldes.

```php
<?php echo $this->item->jcFields['name-of-field']->rawvalue; ?>
```

Du kannst diesen Code zu jedem Teil deines Overrides hinzufügen. Beispiele: Der Inhalt eines div, die src in einem `img`-Tag, innerhalb eines CSS-Klassenattributs, etc.

*Übersetzt von openai.com*
