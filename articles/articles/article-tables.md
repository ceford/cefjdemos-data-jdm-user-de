<!--
{
  "source": "https://docs.joomla.org/J4.x:Article_Tables",
  "title": "Beitrag: Bearbeiten - Tabellen  ",
  "description": "", 
  "author": ""
}
-->

## Über Tabellen

In HTML bestehen Tabellen aus Reihen und Spalten von Zellen. Einfache Tabellen bestehen beispielsweise aus 4 Reihen und 4 Spalten und ergeben so 16 Zellen. Zellen können jedoch entweder horizontal oder vertikal kombiniert werden, um recht komplexe Tabellenstrukturen zu schaffen. Tabellen verfügen auch über weniger offensichtliche Merkmale wie einen Kopfbereich, einen Körper, einen Fußbereich und Beschriftungen. Tabellen können sogar verschachtelt werden!

Standardmäßig dehnen sich Tabellenzellen aus, um ihren Inhalt aufzunehmen. Die einzige Formatierung ergibt sich aus dem Tabellenauszeichnung: Standardmäßig haben Kopfzellen (`<th>`) fettgedruckten, zentrierten Text, während Datenzellen (`<td>`) normalen, linksbündigen Text aufweisen.

Die Verwendung von Tabellen sollte auf strikt tabellarische Daten beschränkt bleiben, wie beispielsweise einen Stundenplan oder einen Kalender, bei denen es wichtig ist, die Struktur von Reihen und Spalten beizubehalten. Tabellen sollten nicht für Layoutzwecke verwendet werden, wie z. B. das nebeneinander Anordnen von Bildern oder Text.

Es gibt weitere Informationen in den folgenden Beiträgen:

- [Grundlagen von Tabellen](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Basics)
- [Erweiterte Funktionen und Barrierefreiheit](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Advanced)
- [Styling von Tabellen](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Styling_tables)

Tabellen sind ein Dilemma! Wenn Sie eine Tabelle mit den TinyMCE-Tabellenwerkzeugen einfügen, sieht die Tabelle im Bearbeitungsbildschirm und auf der Website gut aus, aber das Layout wird mit Inline-CSS-Stilen erreicht, die umfangreich und schwer zu bearbeiten sein können. Wenn die Tabelle als reines HTML eingefügt wird, sieht das Ergebnis im TinyMCE-Texteditor nicht gut aus, aber es können Bootstrap-Klassen verwendet werden, um auf der Website viel besser auszusehen. Beide Methoden werden unten behandelt.

## Einfügen einer Tabelle mit TinyMCE-Werkzeugen

Um eine Tabelle zu starten:

- Öffnen Sie den Beitrag, den Sie bearbeiten möchten.
- Setzen Sie den Cursor auf eine leere Zeile, an der die Tabelle erscheinen soll.
- Wählen Sie die *Tabelle* Schaltfläche in der ersten Reihe der TinyMCE-Werkzeuge aus.
- Wählen Sie im Dropdown-Menü Tabelle und bewegen Sie dann den Cursor, um die Anzahl
  der Zeilen und Spalten zu definieren. Die Pfeiltasten können dafür ebenfalls verwendet werden.
- Wählen Sie die letzte Zelle in der 4x4 Matrix.
- Füllen Sie die Tabellenzellen aus.

Bearbeitungsoptionen:

- Sie können eine Zeile über oder unter einer ausgewählten Zelle einfügen.
- Sie können eine Spalte vor oder nach einer ausgewählten Zelle einfügen.
- Sie können eine Zeile oder Spalte löschen.
- Sie können die Spaltenränder ziehen, um die Breite oder Höhe zu ändern.
- Sie können Zellen zusammenführen - ziehen Sie über die Zellen, um sie auszuwählen, und verwenden Sie dann
  Tabelle -> Zelle -> Zellen zusammenführen.
- Sie können Tabelleneigenschaften auswählen, einschließlich Rahmenbreite, Stil und Farbe sowie
  Hintergrundfarbe.

Wenn Sie die Schaltfläche Editor umschalten verwenden, sehen Sie, dass das Layout mit
Inline-Stil-Anweisungen in jeder Zeile und jeder Zelle erreicht wird. Hier ist ein kurzes Beispiel:

```html
<table style="border-collapse: collapse; width: 100%; height: 96px;" border="1"><colgroup><col style="width: 24.9735%;"><col style="width: 24.9735%;"><col style="width: 24.9735%;"><col style="width: 24.9735%;"></colgroup>
<tbody>
<tr style="height: 24px;">
<td style="height: 24px;">Tag</td>
<td style="height: 24px;">Morgen</td>
<td style="height: 24px;">Nachmittag</td>
<td style="height: 24px;">Abend</td>
</tr>
<tr style="height: 24px;">
<td style="height: 24px;">Dienstag</td>
<td style="height: 24px;">Begrüßung</td>
<td style="height: 24px;">Präsentationen</td>
<td style="height: 24px;">Grillabend</td>
</tr>
...
</tbody>
</table>
```

## Einfügen einer Tabelle als HTML

Wenn Sie möchten, können Sie auf Inline-Stile verzichten und stattdessen Bootstrap-Klassen verwenden. Sie müssten die von den TinyMCE-Tabellentools erstellte Tabelle anpassen oder selbst schreiben. Es würde so aussehen:

```html
<div class="table-responsive">
<table class="table table-striped table-bordered table-group-divider">
<thead>
<tr>
<th>Tag</th>
<th>Vormittag</th>
<th>Nachmittag</th>
<th>Abend</th>
</tr>
</thead>
<tbody class="table-group-divider">
<tr>
<th>Dienstag</th>
<td>Willkommen</td>
<td>Präsentationen</td>
<td>Grillfest</td>
</tr>
...
</tbody>
</table>
</div>
```

Hier haben die Bootstrap-Klassen die folgenden Effekte:

- `table` - Wendet mehrere Stile an, um ein schönes Standardtabelldesign zu erzeugen.
- `table-striped` - Abwechselnde Zeilen sind dunkel und hell.
- `table-bordered` - Wendet Ränder auf die Zellen an.
- `table-group-divider` - Wendet eine fette Linie über einem Element an.
- `table-responsive` - Ermöglicht einer breiten Tabelle, nach rechts und links zu scrollen.

Der folgende Screenshot der Website zeigt eine Tabelle für ein Konferenzprogramm mit den Standard-Inline-Stilen von TinyMCE und eine ähnliche Tabelle mit Bootstrap-Stilen:

![Beispieltabelle](../../../en/images/articles/article-tables/01-articles-site-tables.png)

Weitere Optionen finden Sie in der Bootstrap-Dokumentation zu [Tabellen](https://getbootstrap.com/docs/5.3/content/tables/).

## Nachgedanke

Sie könnten das HTML für eine Tabelle in einem benutzerdefinierten Modul platzieren und dieses Modul in den Beitrag einfügen. In dem Beitrag erscheint dies als `{loadmoduleid xx}`, wobei xx die Modul-ID ist.

*Übersetzt von openai.com*

