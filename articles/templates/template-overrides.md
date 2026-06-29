<!--
{
  "source": "https://docs.joomla.org/J4.x:Template_Overrides",
  "title": "Template-Überschreibungen",
  "description": "", 
  "author": ""
}
-->

## Einführung

Joomla-Erweiterungen definieren ihr Erscheinungsbild mithilfe von Template-Dateien, die HTML und PHP-generierte HTML-Markups enthalten, sowie CSS-Dateien, die Layout, Farbschema, Schriftarten usw. festlegen. Das kann völlig ausreichend für Ihre Bedürfnisse sein, insbesondere da Sie das Erscheinungsbild mit Ihren eigenen CSS-Stilen ändern können. Manchmal möchten Sie zusätzliche Informationen anzeigen oder vielleicht weniger Informationen. Dafür müssen Sie ein Template-Override erstellen.

Viele der Joomla-Erweiterungen haben recht komplexe Ausgabe-Templates, die schwer zu lesen sind. Sie benötigen ein gutes Verständnis von HTML, PHP und CSS, um einige davon anzugehen. Dieser Beitrag veranschaulicht den Prozess durch das Erstellen eines Overrides für das Abmeldeformular, das sich tatsächlich im Anmeldemodul, mod_login, befindet. Der Website-Inhaber möchte, dass das Abmeldeformular die Zeit anzeigt, zu der nach einer Phase der Inaktivität eine automatische Abmeldung erfolgt.

## Beispiel: Template-Override für mod_login

Beginnen Sie, indem Sie im Administrator-Menü **System → Vorlagen → Seitenvorlagen** auswählen und dann auf den Punkt „Cassiopeia Details und Dateien“ klicken. Dadurch wird das Formular „Vorlagen: Anpassen (Cassiopeia)“ geöffnet:

![template customise cassiopeia site tab](../../../en/images/templates/template-overrides/01-templates-customise-cassiopeia.png)

**Wichtig:** Bearbeiten Sie keine der Dateien, die als Teil der Cassiopeia-Vorlage geliefert werden. Bei der nächsten Joomla-Aktualisierung könnten diese Dateien überschrieben werden und Ihre Änderungen würden verloren gehen.

Der html-Ordner ist der Ort, an dem sich die Overrides befinden. Wenn Sie den html-Ordner erweitern, sehen Sie, dass bereits Overrides für Layouts, mod_custom, mod_menu und tinymce vorhanden sind. Erweitern Sie jeden, um zu sehen, was darin enthalten ist. Es gibt zu diesem Zeitpunkt kein mod_login.

## Overrides erstellen

Wählen Sie die Registerkarte Overrides erstellen, um die Liste der Module, Komponenten, Plugins und Layouts anzuzeigen, für die Sie Overrides erstellen können:

![templates customise cassiopeia overrides tab](../../../en/images/templates/template-overrides/02-cassiopeia-customisation-create-overrides.png)

Wählen Sie das Element mod_login aus. Die mod_login-Vorlagendateien werden in den Ordner html kopiert, und Sie kehren zur Registerkarte Editor zurück. Erweitern Sie die Ordner html und mod_login. Sie sehen default.php und default_logout.php.

Sie benötigen die Datei default.php nicht, da dies ein Override für das Anmeldeformular ist. Wählen Sie sie aus und dann die Schaltfläche **Datei löschen** in der Toolbar. Bestätigen Sie im Warnhinweis, dass Sie die Datei löschen möchten.

Beachten Sie, wie einfach es ist, Dateien zu löschen, falls Sie Ihre Meinung ändern. Mit der Schaltfläche Ordner verwalten können Sie auch ganze Ordner löschen. Seien Sie vorsichtig, dass Sie nichts löschen, was Sie nicht selbst erstellt haben.

## Bearbeite default_logout.php

Im Editor-Tab wählen Sie die Datei default_logout.php aus. Beachten Sie die
Schaltflächen oben rechts: Originaldatei anzeigen und Unterschiede anzeigen. Letztere ist für den folgenden Screenshot auf Ja gesetzt, um einige hinzugefügte Codezeilen am oberen Rand der Datei zu zeigen. Diese Codezeilen berechnen, wann die Benutzersitzung nach dem Laden der Seite mit dem Logout-Formular abläuft.

![templates anpassen cassiopeia Überschreibungen Tab](../../../en/images/templates/template-overrides/03-cassiopeia-customisation-edit-logout-override.png)

Der Diff-Bereich zeigt hinzugefügte Zeilen mit einem grünen Hintergrund und gelöschte Zeilen mit einem roten Hintergrund. In diesem Fall gibt es keine gelöschten Zeilen. Der Code wird hier angezeigt, falls Sie ihn kopieren und selbst ausprobieren möchten.

```php
    use Joomla\CMS\Factory;

    date_default_timezone_set('Europe/London');
    $config = Factory::getContainer()->get('config');
    $lifetime = $config->get('lifetime', 0);
    $time = time() + $lifetime * 60;
    $endTime = date('H:i:s', $time); // time() gibt bereits eine Zeit in Sekunden zurück
```

Weiter unten in der Überschreibungsdatei, Zeile 36, wurden weitere Zeilen hinzugefügt, um die gewünschte Nachricht auszugeben:

```html
<p class="text-center">
Ihre Sitzung läuft um <br><?php echo $endTime; ?>
</p>
```

Speichern Sie die Seite und laden Sie sie erneut, die das Logout-Formular enthält.

![templates anpassen cassiopeia Überschreibungen Tab](../../../en/images/templates/template-overrides/04-cassiopeia-customisation-logout-override-result.png)

Sie sollten sehen, dass sich das Logout-Formular jedes Mal ändert, wenn die Seite neu geladen wird. Aber was, wenn Sie Ihre Meinung ändern? Oder verschiedene Optionen für verschiedene Benutzergruppen haben? Willkommen bei Layouts, dem Thema eines separaten Beitrags.

## Weitere Überschreibungen

Die Registerkarte Erstellen von Überschreibungen im Formular Vorlagen: Anpassen (Cassiopeia) wird verwendet, um beliebige Elemente der Joomla-Ausgabe zu erstellen, für die Überschreibungen möglich sind. Die Namen der Überschreibungsordner beginnen meist mit com\_, mod\_ oder plg\_. Beachten Sie, dass der zweite Teil eines Plugin-Überschreibungsordners die Plugin-Gruppe angibt. Hier ist eine beispielhafte Auswahl von Überschreibungsordnern:

![Vorlagen anpassen Cassiopeia Überschreibungen Tab](../../../en/images/templates/template-overrides/05-templates-customise-example-override-folder.png)

## Layout-Overrides

Kleine Layout-Dateien werden oft für einzelne Elemente von Joomla!-Seiten verwendet. Der „Weiterlesen“-Button bei Beiträgen, das Vorschaubild und das Hauptbild sind alles Beispiele für Elemente, die durch ihre eigenen Layout-Dateien generiert werden. Diese Mikro-Layouts befinden sich im Ordner /layouts. Zum Beispiel enthält die Datei blog_item.php in der Kategorie-Übersicht den Code, um den Beitragstitel, ein Vorschaubild, den Einführungstext sowie verschiedene andere relevante Teile der Seite zu platzieren. Dies geschieht durch einen Aufruf von LayoutHelper, wobei das zu verwendende Layout als Parameter übergeben wird. Hier ist ein Beispiel, der Aufruf, um den Beitragstitel im Blog-Layout einzufügen:

```php
<?php echo LayoutHelper::render('joomla.content.blog_style_default_item_title', $this->item); ?>
```

Der Speicherort der Datei für dieses spezielle Element wird gefunden, indem die Punktsymbole durch Schrägstrich-Symbole ersetzt, /layouts/ vorangestellt und .php angehängt wird:

```php
    JOOMLAROOT/layouts/joomla/content/blog_style_default_item_title.php
```

Wenn eine Override-Datei erstellt wird, befindet sie sich in:

```php
    JOOMLAROOT/templates/cassiopeia/html/layouts/joomla/content/blog_style_default_item_title.php
```

## Weitere Informationen

- Grundlagen der Vorlagen
- Cassiopeia Vorlagenordner und -dateien
- Anpassung der Cassiopeia Vorlage
- Vorlagen-Overrides
- Vorlagenlayouts
- Cassiopeia Vorlage vereinfacht - Eine Fallstudie - eine einfache Vorlage
  basierend auf Cassiopeia

*Übersetzt von openai.com*

