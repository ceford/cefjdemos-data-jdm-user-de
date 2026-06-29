<!--
{
  "source": "https://docs.joomla.org/J4.x:Managing_Media",
  "title": "Medienverwaltung",
  "description": "", 
  "author": ""
}
-->

## Einführung

In Joomla sind Medien Bilder und Dateien, die als Illustrationen oder Links in Beiträgen, Modulen, Templates usw. erscheinen. Ein wichtiges Merkmal von Medien ist, dass sie direkt vom Webserver bereitgestellt werden, ohne von Joomla-Code verarbeitet zu werden. Dies ist schnell und effizient. Beachten Sie auch, dass Medien in der Regel im **images**-Ordner Ihrer Joomla-Website gespeichert werden. Verwechseln Sie dies nicht mit dem **media**-Ordner, der Javascript- und Stylesheet-Dateien enthält.

Bild- und Dateimedien werden mit der Medienkomponente von Joomla verwaltet. Sie ermöglicht es Ihnen, Medieninhalte in einer Ordnerstruktur zu organisieren, einzelne Elemente hochzuladen, einige grundlegende Bildbearbeitungsfunktionen durchzuführen und Bilder sowie Links direkt in Beiträge einzufügen.

## Zugriffsmöglichkeiten

Vom Joomla-Administrator-Bereich aus gibt es mehrere Möglichkeiten, die Medien-Komponente zu öffnen:

- Wählen Sie **Inhalt → Medien** aus dem Administrator-Menü.
- Wählen Sie **Site-Panel → Medien** vom Home-Dashboard.
- Wählen Sie **CMS-Inhalt → Medien** von einem Beitrags-Bearbeitungsfenster.

In den ersten beiden Fällen erscheint die Medien-Komponente in einem normalen Komponentenfenster. Im letzten Fall erscheint sie in einem modalen Dialog.

## Bildschirmfoto

Das folgende Bild zeigt die Medienseite direkt nach der Joomla-Installation, jedoch mit dem ausgewählten Ordner cassiopeia/sampledata. Ein *files*-Ordner wurde hinzugefügt, um Nicht-Bild-Dateien zu speichern, und ein zusätzlicher Ordner namens *garbage* wurde hinzugefügt, um das Löschen von Ordnern zu veranschaulichen:

![Medienseite mit Beispieldaten cassiopeia](../../../en/images/media/managing-media/01-media-sample-data-cassiopeia.png)

## Verwalten von Ordnern

Die Unterordnernamen in Ihrem Bilderordnerbaum werden Teil der Bild-URL. Daher ist es wichtig, dass die Namen aus Gründen der Verlinkung und der Suchmaschinenoptimierung einer Konvention entsprechen:

- alles klein geschrieben
- keine Leerzeichen oder Satzzeichen
- falls notwendig, verwenden Sie ein Minuszeichen, um für Menschen lesbare Wörter zu erstellen, zum Beispiel Laubbäume anstelle von laubbäume.

Bevor Sie viel Inhalt für Ihre Website erstellen, könnte es sich lohnen, im Voraus darüber nachzudenken, wie Sie Ihren Inhalt kategorisieren könnten, und vielleicht einen Bilderordnerbaum zu erstellen, der Ihrem Kategoriebaum ähnlich ist. Andernfalls könnten Sie am Ende eine sehr große Anzahl von Bildern und Dateien im Stamm Ihres Bilderbaums haben, was schwer zu verwalten wird. Wenn Sie sich später entscheiden, Bilder in eine bessere Struktur zu verschieben, müssen Sie die Links zu diesen Bildern in Ihren Beiträgen finden und sie ändern. Das könnte eine zeitaufwendige, entmutigende Aufgabe sein!

### Ordnernavigation

Verwenden Sie den Ordnerbaum in der **Lokal**-Spalte, um einen Ordner auszuwählen. Im oben dargestellten Fall wurde zuerst der Ordner cassiopeia ausgewählt. Dadurch wurde der *sampledata*-Ordner angezeigt, der dann ausgewählt wurde, um seinen Inhalt zu zeigen.

Der aktuelle Standort wird auch in den Breadcrumbs über den Bildern angezeigt. In diesem Fall **images → cassiopeia → sampledata**.

Wenn Sie einen anderen Ordner auswählen, wird der vorherige Ordner auf derselben Ebene geschlossen.

### Einen Ordner erstellen

- Wählen Sie den übergeordneten Ordner aus, unter dem der neue Ordner erstellt werden soll.
- Wählen Sie die Schaltfläche **Neuen Ordner erstellen**.
- Geben Sie im Popup-Fenster *Neuen Ordner erstellen* einen Namen für den Ordner im Feld **Ordnername** ein.
- Klicken Sie auf die Schaltfläche **Erstellen**.
- Der neue Ordner wird im ausgewählten übergeordneten Ordner zusammen mit einer grünen Erfolgssystemnachricht angezeigt.

### Einen Ordner löschen

**Warnung: Durch das Löschen eines Ordners werden auch alle Inhalte des Ordners gelöscht!**

- Wählen Sie das übergeordnete Element des zu löschenden Ordners aus, indem Sie den im **Lokal**-Bereich angezeigten Verzeichnisbaum verwenden. Dadurch werden alle Ordner und Dateien im übergeordneten Element angezeigt.
- Bewegen Sie den Cursor über den zu löschenden Ordner im Medienbereich. Er wird grau und es erscheint eine Schaltfläche in der Nähe der oberen linken Ecke.
- Wählen Sie die Schaltfläche aus. Ein Häkchen wird angezeigt, um anzuzeigen, dass sie ausgewählt ist.
- Wählen Sie die **Löschen**-Schaltfläche aus der Symbolleiste.
- Wählen Sie im Popup-Dialog **Löschen bestätigen** die Schaltfläche **Löschen** aus. Der Ordner wird zusammen mit allen seinen Dateien, Unterordnern und deren Dateien gelöscht.

Der zur Löschung ausgewählte Ordner wird unten dargestellt:

![Medienseite zeigt Papierkorb-Ordner](../../../en/images/media/managing-media/02-media-sample-data-garbage-select.png)

## Medienbereich-Werkzeugleiste

Dies ist die Leiste über der Liste von Bildern, Dateien und Ordnern, die
Schaltflächen für eine Vielzahl von Aufgaben enthält.

### Auswahlfeld

Ein Kontrollkästchen, das es Ihnen ermöglicht, alle Elemente im Ordner
auszuwählen, die im Medienbereich angezeigt werden. Sie könnten es nutzen, um alle aktuellen Elemente zu löschen, ohne den Ordner selbst zu löschen.

### Breadcrumbs

Verwenden Sie die Ordnernamen über dem Medienbereich, um im Ordnerhierarchie
zurückzugehen.

Doppelklicken Sie auf einen Ordnernamen im Medienbereich, um diesen Ordner zu
öffnen.

### Suche

Wenn Sie eine lange Liste von Bildern und Dateien haben, können Sie nach
Elementen suchen, die eine beliebige Zeichenfolge enthalten. Die Suche ist
progressiv: Während Sie Zeichen zum Suchbegriff hinzufügen, wird die Liste
auf nur diejenigen reduziert, die diese Zeichenfolge enthalten.

### Vergrößern

Verwenden Sie die Vergrößerungsschaltflächen, um die Größe der Miniaturansichten zu
vergrößern oder zu verkleinern. Abhängig von der Größe Ihres Bildschirms sehen Sie
möglicherweise 2, 4, 6 oder 8 Miniaturbilder nebeneinander.

### Listen- oder Miniaturansichten

In der Miniaturansicht wählen Sie das Listensymbol, um zur Listenansicht zu
wechseln. In der Listenansicht wählen Sie das Miniatursymbol, um zur
Miniaturansicht zu wechseln. In der Listenansicht sehen Sie Informationen über
Bildgröße und -abmessungen sowie andere Daten.

### Informationssymbol

Wählen Sie das Informationssymbol, um ein Seitenfenster zu öffnen, das
Informationen über das ausgewählte Element anzeigt.

*Übersetzt von openai.com*

