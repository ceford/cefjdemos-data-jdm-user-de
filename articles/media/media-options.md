<!--
{
  "source": "https://docs.joomla.org/J4.x:Media:_Options",
  "title": "Medien: Optionen ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Die Seite *Medien: Optionen* wird verwendet, um den Upload und die Speicherung von Medien, sowohl Bilder als auch Dateien, zu steuern. **Achtung:** Es gibt Sicherheitsaspekte, die mit einigen Arten von Dateien verbunden sind - ein möglicher Zugang für Hacker.

Um das Formular *Medien: Optionen* zu öffnen, wählen Sie die **Optionen**-Schaltfläche in der Toolbar auf der Medienseite aus. Die Felder sind gut kommentiert und mit Standardwerten versehen, die für fast alle Seiten geeignet sein sollten. Sie müssen das Optionsformular normalerweise nur verwenden, wenn Sie Dateien getrennt von Bildern halten möchten oder wenn Sie ein ungewöhnliches Dateiformat haben, das nicht in der Standardliste enthalten ist.

## Screenshot

![Das Medienoptionen-Formular](../../../en/images/media/media-options/01-media-options.png)

## Pfad zu Dateien und Ordnern

Dies sind separate Elemente im Konfigurationsformular, aber beide verweisen auf den *images*-Ordner in einer neuen Joomla-Installation. Wenn Sie nicht-bildhafte Medien separat speichern möchten (zum Beispiel PDFs, Tabellenkalkulationen und Textdateien), verwenden Sie die folgenden Schritte:

1. Erstellen Sie einen Ordner namens *files* im Stammverzeichnis Ihrer Joomla-Installation.
2. Aktivieren Sie das Plugin *Dateisystem - Lokal* und konfigurieren Sie es, wie im Beitrag zu [Medien-Datei-Locations](jdocmanual?article=user/media/media-file-locations) beschrieben.
3. Geben Sie den Ordnernamen *files* in das Feld *Pfad zu Dateien Ordner* des Medien-Optionen-Formulars ein.

Geben Sie im Optionen-Formular den Ordnernamen im Feld **Pfad zu Dateien Ordner** ein. Achten Sie darauf, keinen Namen eines bestehenden Joomla-Kernordners zu verwenden.

Wenn alles eingerichtet ist, können Sie im lokalen Teil der Medienansicht zwischen den Ordnern für Bilder und Dateien wählen.

![Die Medienseite](../../../en/images/media/media-options/02-media-sample-data-cassiopeia.png)

## Zusätzliche Bild- oder Dokumenttypen

Es kann vorkommen, dass ein Bild oder Dokument nicht hochgeladen werden kann. Überprüfen Sie in diesem Fall, ob die Erweiterung zu den *Zulässigen Erweiterungen* gehört, ob die Erweiterung zu den *Erlaubten Erweiterungstypen* für das Medium gehört und ob sie zu den *Erlaubten MIME-Typen* gehört (möglicherweise müssen Sie dies nachschlagen). Alle drei müssen korrekt sein, ansonsten wird der Upload verweigert.
*Übersetzt von openai.com*

