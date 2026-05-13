<!--
{
  "source": "https://docs.joomla.org/Help4.x:Components_Version_History",
  "title": "Beitrag: Versionen ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Im Joomla-Bearbeitungsformular für Beiträge wird jedes Mal, wenn ein Beitrag gespeichert wird, automatisch eine neue Version erstellt. Die Anzahl der zu speichernden Versionen für jeden Beitrag kann auf der Seite *Beiträge: Optionen*, im Tab *Layout bearbeiten* festgelegt werden. Die Standardeinstellung ist 10. Beachten Sie, dass dies nicht der *Optionen*-Tab der Seite *Beiträge: Bearbeiten* ist. Die aktuelle Version ist in der Regel die zuletzt gespeicherte Version.

Eine oder mehrere Versionen können mit *Für immer behalten* markiert werden. Solche Versionen werden nicht automatisch gelöscht, selbst wenn die maximale Anzahl an Versionen überschritten wird.

Der *Versionen*-Popupdialog wird verwendet, um frühere Versionen des bearbeiteten Elements zu verwalten. Ähnliche Versionshistorien sind für Beiträge, Banner und Kunden, Kontakte, News-Feeds, Benutzerhinweise und alle Kategorien verfügbar.

Hinweis: Benutzerdefinierte Felder werden nicht in verschiedenen Versionen gespeichert.

## Zugriffsmethoden

Wählen Sie die Schaltfläche **Versionen** in der Symbolleiste aus, während Sie den Beitrag bearbeiten.

## Screenshot

![Versions-Popup-Dialog](../../../en/images/articles/article-versions/01-articles-versions.png)

## Spaltenüberschriften

- **Checkbox** Diese Checkbox wird verwendet, um alle sichtbaren Versionen in der Liste auszuwählen oder deren Auswahl aufzuheben. Wenn eine Checkbox ausgewählt ist, werden die Toolbar-Schaltflächen aktiviert und können verwendet werden, um eine Aktion für die ausgewählten Elemente auszuführen.
- **Datum** Die Zeit und das Datum, an dem die Version gespeichert wurde. Durch Klicken auf diesen Link wird eine Vorschau dieser Version in einem Pop-up-Fenster geöffnet. Beachten Sie, dass eines der Daten mit einem Sternsymbol versehen ist. Dies weist darauf hin, dass dies die Version ist, die derzeit gespeichert und bearbeitet wird.
- **Versionshinweis** Beim Bearbeiten eines Elements haben Sie die Möglichkeit, einen Versionshinweis einzugeben. Dieser kann Ihnen helfen, sich daran zu erinnern, welche Version welche Informationen enthält. Wenn Sie vor dem Speichern des Elements einen Versionshinweis eingegeben haben, wird er in dieser Spalte angezeigt.
- **Für immer behalten** Diese Spalte zeigt an, ob Sie die Version als "Für immer behalten" markiert haben. Normalerweise wird jede Version gemäß den Einstellungen auf der Komponentenoptionsseite beibehalten. Die Standardeinstellungen sind, maximal 10 frühere Versionen für ein Element zu speichern. In diesem Fall wird beim Speichern eines Elements, das bereits 10 gespeicherte Versionen hat, die älteste Version gelöscht. Wenn eine Version als "Für immer behalten" markiert ist, wird sie nicht als eine der gespeicherten Versionen gezählt und wird nicht gelöscht, wenn die maximale Anzahl erreicht ist. Um das "Für immer behalten" ein- oder auszuschalten, markieren Sie das Kontrollkästchen der Version und wählen dann die *Ein/Aus*-Schaltfläche in der Toolbar.
- **Autor** Der Benutzer, der diese Version gespeichert hat.
- **Zeichenzahl** Die Gesamtanzahl der in dieser Version gespeicherten Zeichen. Dies umfasst sowohl die Datenbankspaltennamen als auch die Zeichenzahl des Elements.

## Symbolleiste

Am oberen Rand der Seite sehen Sie die Symbolleiste, die im
obigen Screenshot gezeigt wird. Die Funktionen sind:

- **Wiederherstellen** Die aktuelle Version des Beitrags ist mit einem Stern rechts neben dem Datum markiert. Wenn Sie eine der anderen gespeicherten Versionen wiederherstellen möchten, aktivieren Sie das Kontrollkästchen für die gewünschte Version und wählen Sie die Schaltfläche *Wiederherstellen*. Die aktuelle Version des Beitrags wird durch die ausgewählte Version ersetzt und der Bearbeitungsbildschirm wird neu geladen, wobei die wiederhergestellte Version im Editor geladen wird.
- **Vorschau** Um eine Version in der Vorschau anzuzeigen, wählen Sie entweder den Beitrag in der Datumsspalte aus oder aktivieren Sie das Kontrollkästchen und klicken Sie auf die Vorschau-Schaltfläche. Ein separates Browserfenster wird geladen und zeigt die ausgewählte Version des Beitrags an, ähnlich wie im Screenshot unten. Schließen Sie das Browserfenster, nachdem Sie die Version angezeigt haben.
![Versionsvorschau-Dialog](../../../en/images/articles/article-versions/02-articles-versions-preview.png)
- **Vergleichen** Um zwei Versionen zu vergleichen und zu sehen, was geändert wurde, aktivieren Sie die Kontrollkästchen für jede der Versionen und klicken Sie auf die Vergleichen-Schaltfläche. Ein neues Browserfenster wird geöffnet, wie im Screenshot unten gezeigt. Die erste Spalte ist der Feldname, die zweite die ältere Version, die dritte die neuere Version und die letzte Spalte hebt die Unterschiede zwischen den beiden Versionen hervor.
![Versionsvergleich-Dialog](../../../en/images/articles/article-versions/03-articles-versions-compare.png)
- **Behalten Ein/Aus** Mit dieser Schaltfläche können Sie die Behalten-für-immer-Funktion für eine Version ein- oder ausschalten. Normalerweise wird die älteste Version eines Beitrags automatisch gelöscht, wenn die maximale Anzahl an Versionen (in den Optionen für die Komponente festgelegt) überschritten wurde. Wenn Sie die Behalten-für-immer-Eigenschaft für eine Version festlegen, wird sie niemals automatisch gelöscht.
- **Löschen** Mit dieser Schaltfläche können Sie eine oder mehrere Versionen manuell löschen. Wählen Sie das Kontrollkästchen für die Versionen, die Sie löschen möchten, und wählen Sie dann die Löschen-Schaltfläche. Beachten Sie, dass dies *nicht* den zu bearbeitenden Beitrag löscht. Es löscht nur die ausgewählte Version des Beitrags.

*Übersetzt von openai.com*
```

