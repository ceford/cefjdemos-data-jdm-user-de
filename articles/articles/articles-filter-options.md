<!--
{
  "source": "https://docs.joomla.org/J6.x:Articles:_Filter_Options",
  "title": "Beiträge: Filteroptionen ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Nachdem Sie Ihren ersten Beitrag erstellt haben, wie im Beitrag "Erste Schritte" zum [Hinzufügen eines Beitrags](jdocmanual?article=user/getting-started/adding-an-article) beschrieben wird, enthält Ihre Beitragsliste einen einzelnen Beitrag. Ein Jahr später könnten Sie tausend Beiträge haben und benötigen die *Filteroptionen*, um das Gewünschte zu finden.

Der folgende Screenshot zeigt die Beiträge, die zur Vorbereitung dieses Satzes von Tutorials verwendet wurden. Die Listen-Batchgröße wurde auf 5 festgelegt, um die Länge des Screenshots zu begrenzen.

Die *Filteroptionen* wurden geöffnet, um die verfügbaren Filter anzuzeigen.

![Beitragsliste](../../../en/images/articles/articles-filter-options/01-articles-filter-options.png)

Diese Liste enthält über 20 Beiträge, die aus der Installation der *Mehrsprachigen Beispielinhalte* erstellt wurden, sowie einige weitere Beiträge, die später hinzugefügt wurden.

## Sortierreihenfolge

Beachten Sie, dass die voreingestellte Sortierreihenfolge *ID Absteigend* ist. Dadurch wird der neueste Beitrag an die Spitze der Liste gesetzt, was normalerweise gewünscht ist.

## Seitennummerierung

Wenn die Anzahl der Beiträge größer als die *Batch-Größe* ist, wird eine Seitennummerierungsleiste unterhalb der Liste angezeigt. Sie enthält Symbole, um zur *Ersten Seite*, *Vorherigen Seite*, *Nächsten Seite* oder *Letzten Seite* zu gelangen. Die Zahlen führen zu Beiträgen auf der entsprechenden nummerierten Seite. Die Seitennummerierungsleiste ist nützlich, wenn Sie die Liste der Beiträge durchsuchen müssen.

## Filter

Alle Filter funktionieren *bei Änderung*, aber die Filtereinstellungen werden gespeichert und die *Filteroptionen* bleiben sichtbar, solange mindestens ein Filter ausgewählt ist.

### Auswahl Hervorgehoben

- **- Ausgewählte Hervorgehobene -** Wählt sowohl hervorgehobene als auch nicht hervorgehobene Beiträge aus.
- **Nicht hervorgehobene Beiträge** Wählt nur nicht hervorgehobene Beiträge aus.
- **Hervorgehobene Beiträge** Wählt nur hervorgehobene Beiträge aus.

### Auswahl Status

Die Standardeinstellung der Beiträge umfasst *Veröffentlicht* und *Unveröffentlicht*. Dies ermöglicht es, den Veröffentlichungsstatus über das Symbol in der *Status*-Spalte umzuschalten. *Gelöschte* und *Archivierte* Elemente sind nur enthalten, wenn *Alle* ausgewählt ist.

- **Gelöscht** Wählt nur gelöschte Beiträge aus. Das *Status*-Symbol zeigt ein Papierkorbsymbol, das verwendet werden kann, um das Element zu veröffentlichen. Eine *Löschen*-Schaltfläche in der Symbolleiste ermöglicht das vollständige Löschen eines ausgewählten Beitrags. Es erscheint eine Warnmeldung. Nach dem Löschen verwenden Sie die *Leeren*-Schaltfläche, um zur ungefilterten Liste zurückzukehren.
- **Unveröffentlicht** Wählt nur unveröffentlichte Beiträge aus.
- **Veröffentlicht** Wählt nur veröffentlichte Beiträge aus.
- **Archiviert** Wählt nur archivierte Beiträge aus. Das Status-Symbol erlaubt es, den Artikelstatus auf Unveröffentlicht zu ändern. Archivierte Beiträge sind nicht mehr erforderlich, können aber über ein *Archivierte Beiträge*-Menüelement verfügbar gemacht werden.
- **Alle** Wählt alle Beiträge unabhängig vom Status aus.

Wenn ein Beitrag seinen Status ändern muss, der nicht über das Symbol in der Statusspalte vorgenommen werden kann, kann dies im Bearbeitungsformular des Beitrags erfolgen.

### Auswahl Kategorie

Die Dropdown-Liste zeigt alle Site-Kategorien in einer ähnlichen Baumstruktur wie die, die in der *Beiträge: Kategorien*-Liste verwendet wird. Wenn Sie eine einzelne Kategorie auswählen, werden alle Beiträge in dieser Kategorie zusammen mit allen Beiträgen in ihren Unterkategorien ausgewählt, es sei denn, der *Auswahl Maximalstufen*-Filter ist gesetzt.

Sie können mehrere Kategorien auswählen, die nicht im selben Kategoriebereich liegen.

### Auswahl Zugriff

Die Dropdown-Liste ermöglicht die Auswahl von Beiträgen in festgelegten *Zugriffsebenen*. Zugriffskontrolle wird in einem separaten Beitrag behandelt. Kurz gesagt, beschränkt dies die Sichtbarkeit der Beiträge auf der Site wie folgt:

- **Öffentlich** Beiträge, die für jeden verfügbar sind.
- **Gast** Beiträge, die für jeden verfügbar sind, der nicht angemeldet ist.
- **Registriert** Beiträge, die für alle verfügbar sind, die angemeldet sind.
- **Speziell** Beiträge, die für jeden verfügbar sind, der angemeldet ist und zu einer Benutzergruppe gehört, die speziellen Zugriff hat.
- **Super-Nutzer** Beiträge, die für jeden eingeschränkt sind, der als Super-Nutzer angemeldet ist.

### Auswahl Autor

Die Dropdown-Liste ermöglicht die Auswahl von Beiträgen nach einem bestimmten Autor.

- **Keine** Dies ist ein Sonderfall, in dem ein Beitrag existiert, aber der ursprüngliche Autor nicht mehr. Es kann mehrere Autoren geben, die Beiträge beigesteuert haben, aber keine Benutzerkonten mehr haben.
- **Von mir erstellt** Eine Liste Ihrer eigenen Beiträge.
- **Autorenname** Eine Liste mit den Namen der Beitrag-Autoren, die ziemlich lang sein könnte. Der echte Name wird anstelle des Anmeldenamens verwendet. Wählen Sie einen Autor nach Bedarf aus, um Beiträge dieses Autors zu sehen.

### Auswahl Sprache

Dieser Filter ist nur auf mehrsprachigen Sites vorhanden. Wenn ein Beitrag erstellt wird, kann er allen Sprachen oder einer spezifischen Sprache zugewiesen werden, die den Sprachnamen und den Ländercode im *Sprache*-Feld des Dateneingabeformulars enthält, zum Beispiel *Englisch (en-GB)* oder *Spanisch (es-ES)*. Im Sprachfilter:

- **Alle** Dies filtert Beiträge, die allen Sprachen zugewiesen wurden. Es bedeutet nicht alle Beiträge!
- **Sprachname (xx-YY)** Eine Liste der installierten Sprachen. Wählen Sie eine spezifische Sprache aus, um Beiträge zu sehen, die dieser Sprache zugewiesen sind.

### Auswahl Tag

Eine Liste von Tags. Wählen Sie ein beliebiges Tag aus, um Beiträge zu sehen, die dieses Tag haben. Mehrere Tags können ausgewählt werden.

### Auswahl Maximale Ebenen

Dies beschränkt die Liste der Beiträge auf die festgelegte Anzahl von Ebenen in einer Hierarchie. Wenn kein Wert ausgewählt ist, sind alle Ebenen enthalten. Wenn auf 1 gesetzt, werden nur Beiträge in der ersten Ebene eines Kategoriebaums einbezogen.

## Mehrere Filter

Auf großen, komplexen Websites müssen Sie möglicherweise mehrere Filter verwenden. Die Filter werden innerhalb einer Sitzung gespeichert, bis Sie sich abmelden oder die Sitzung aufgrund von Inaktivität abläuft.

*Übersetzt von openai.com*

