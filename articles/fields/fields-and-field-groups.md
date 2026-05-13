<!--
{
  "source": "https://docs.joomla.org/J4.x:Fields_and_Field_Groups",
  "title": "Felder und Feldgruppen ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Felder werden verwendet, um zusätzliche Attribute von Beiträgen, Kontakten oder Benutzern anzuzeigen. Die Daten werden in einem Administrator-Editierformular eingegeben und auf der Website angezeigt. Ein Beispiel:

Angenommen, Sie schreiben Beiträge über Aspekte der Natur, manchmal über Blumen, manchmal über Tiere. Ein Feld, das Sie möglicherweise aufzeichnen und anzeigen möchten, ist der lateinische Name. Dafür benötigen Sie ein Textfeld. Ein weiteres könnte der Lebensraum sein: Wald, Teich, Wiese usw., was eine Dropdown-Liste erfordert. Für Blumen möchten Sie vielleicht die Blütezeit mit 4 Kontrollkästchen aufzeichnen, eines für jede Jahreszeit, oder mit 12 Kontrollkästchen, eines für jeden Monat.

Leere Felder im Eingabeformular werden im Website-Ausgang nicht angezeigt. Daher könnten Sie alle Felder in einer langen Liste behalten. Es ist jedoch meistens besser, Kategorien für Ihre Beiträge zu verwenden, sagen wir Blumen und Tiere. Felder können mehr als einer Kategorie zugeordnet werden. Also würden die Felder Lateinischer Name und Lebensraum beiden Kategorien zugeordnet werden, aber die Blütezeit würde nur der Kategorie Blumen zugeordnet werden.

Wenn ein Feld keiner Gruppe zugeordnet ist, erscheint es im Editierformular auf einer Registerkarte "Felder". Wenn ein Feld einer Gruppe zugeordnet ist, erscheint es auf einer Registerkarte mit diesem Namen. Für die Gruppe Blumen scheint es angemessen, eine Feldgruppe namens Blumendaten (oder einfach nur Blumen, obwohl die Verwendung desselben Namens für verschiedene Dinge verwirrend sein kann) zu erstellen. Und für die anderen gemeinsamen Felder könnten Sie eine Naturgruppe verwenden.

## Ein Durchgearbeitetes Beispiel - Naturnotizen

Für Beiträge über die Natur könnten die Beitrag-Kategorie und Unterkategorien für jeden Zweig der lebenden Welt wie im folgenden Beispiel erscheinen:

![Beitragskategorien für die Natur](../../../en/images/fields/fields-and-field-groups/01-fields-articles-categories-list.png)

Einige offensichtliche Merkmale der Natur, die zu beachten sind:

- Die Kategorie Natur ist für Beiträge, die sich im Allgemeinen mit der Natur befassen, anstatt mit spezifischen Pflanzen- oder Tierarten.
- Die Unterkategorien sind für Beiträge, die spezifischer sind, und diese benötigen möglicherweise ihre eigenen Unterkategorien.
- Alle Lebensformen haben gebräuchliche Namen und lateinische Namen.
- Blumen und Bäume haben eine Blütezeit, Höhe und Ausbreitung, während Vögel und Säugetiere dies nicht haben.
- Vögel haben eine Flügelspannweite und Länge, während Säugetiere eine Höhe und Länge haben.
- Die Farbe kann konstant oder variabel sein.

Der Punkt hier ist, dass es notwendig sein kann, Felder oder Feldgruppen für gemeinsame Merkmale, wie den lateinischen Namen, einzurichten und separate Feldgruppen für jede Kategorie der Natur zu erstellen. 

## Feldgruppen

Das Erstellen von Feldgruppen für Beiträge ist sehr einfach:

- Wählen Sie **Inhalt → Feldgruppen** aus dem Administratormenü.
- Klicken Sie auf die **Neu**-Schaltfläche in der Symbolleiste.
- Geben Sie einen passenden **Titel** ein.
- Geben Sie eine **Beschreibung** ein. Diese erscheint unter dem Feld im Beitragsbearbeitungsformular, wenn *Inline-Hilfe umschalten* ausgewählt ist.
- Wählen Sie **Speichern & Schließen** aus der Symbolleiste.

![Liste der Inhaltsfeldgruppen](../../../en/images/fields/fields-and-field-groups/02-fields-field-groups-list.png)

### Reihenfolge

In den Beitragsdateneingaben erscheinen die Feldgruppen in der Reihenfolge, wie sie in dieser Liste zu sehen sind. Per Drag-and-Drop können Sie die Reihenfolge ändern.

## Felder

Um ein neues Beitragsfeld zu erstellen, wählen Sie **Content → Felder** aus dem Administrator-Menü und füllen Sie das Formular aus. Einige Beispiele sind unten illustriert.

### Text - Lateinischer Name

Beachten Sie, dass in dem untenstehenden Screenshot dieses Feld der Feldergruppe Natur und der Kategorie Natur zugewiesen wurde. Das stellt sicher, dass es immer in Beiträgen der Kategorie Natur und jeder Unterkategorie erscheint.

![Textfeld - lateinischer Name in Naturgruppe](../../../en/images/fields/fields-and-field-groups/03-fields-latin-name.png)

### Kontrollkästchen - Blütezeit

Kontrollkästchen erscheinen im Beitragsbearbeitungsformular, damit Sie die Blütezeit auswählen können. In der Beitragsanzeige werden nur diejenigen mit einem Häkchen aufgelistet. Wenn Sie beispielsweise Frühling und Sommer wählen, wird die Ausgabe Blütezeit: Frühling, Sommer anzeigen.

Beachten Sie, dass in diesem Screenshot das Feld der Gruppe Blumen und der Kategorie Blumen zugewiesen wurde. Das sollte sicherstellen, dass das Feld nur in Beiträgen über Blumen vorhanden ist.

![Kontrollkästchenfeld - Blütezeit](../../../en/images/fields/fields-and-field-groups/04-fields-flowering-season.png)

### Farbe - Color

Nur um es verwirrend zu machen, ist der Name des Feldtyps Color (US-Schreibweise), aber das Label in der Dokumentation ist Colour (britische Schreibweise).

![Feld Farbe](../../../en/images/fields/fields-and-field-groups/05-fields-colour.png)

Das Feld Farbe ist der Feldergruppe Natur und der Kategorie Natur zugewiesen, da es nicht einzigartig für Blumen ist.

### Ganzzahl - Winterhärte

Die Winterhärte einer Pflanze kann als Ganzzahl von 1 bis 7 dargestellt werden. Es gibt kein Feld für eine reelle Zahl, also könnten Länge und Breite Ganzzahlen mit einer Skala (cm oder m oder ft) im Label sein. Es gibt *Präfix*- und *Suffix*-Einstellungen im Tab *Optionen*. Wenn es keine offensichtliche obere Grenze gibt, lassen Sie das Feld *Letztes:* leer.

![Feld Winterhärte](../../../en/images/fields/fields-and-field-groups/06-fields-hardiness.png)

RHS Winterhärte ist eine Eigenschaft, die üblicherweise auf Blumen angewendet wird.

Es gibt ein Problem mit dem Ganzzahlfeld. Es hat immer einen Wert und erscheint daher immer in der Ausgabe. Sie können dieses Problem mit einem Template-Override für *Plugins / Integer* umgehen. Zum Beispiel könnten Sie einen Wert über oder unter den erwarteten Grenzen verwenden, um das Feld aus der Ausgabe auszuschließen.

## Beitragsbearbeitungsformular

Wenn ein neues Beitragsformular geöffnet wird, ist die Standardkategorie
„Nicht kategorisiert“ und die Formularreiter enthalten nicht die Felder
und Pflanzen. Wählen Sie die Kategorie „Pflanzen“ aus und das Formular wird
mit diesen Reitern neu geladen.

### Naturreiter

![Bluebell-Artikel Naturreiter](../../../en/images/fields/fields-and-field-groups/07-field-article-bluebell-nature-tab.png)

- **Lateinischer Name** Dies ist ein Texteingabefeld, sodass es einfach eine Frage des
  Eingebens des lateinischen Namens der Lebensform ist, die der Beitrag abdeckt.
  Allerdings umfasst die Kategorie Natur das Leben im Allgemeinen sowie bestimmte
  Tiere oder Pflanzen. Daher ist dies kein *erforderliches* Feld.
- **Farbe** Das Farbauswahlsfeld kann entweder die Tastatureingabe eines
  Hexadezimalwertes für die Farbe aufnehmen oder eine Farbe, die aus dem
  Farbauswahlwerkzeug ausgewählt wurde. Die Hexadezimalnummer ist xrrggbb, wobei
  rr die Rotwerte, gg die Grünwerte und bb die Blauwerte sind. Beim Output zeigt
  die Webseite den Hexadezimalwert an, was nicht sehr hilfreich ist!

### Pflanzenreiter

![Bluebell-Artikel Pflanzenreiter](../../../en/images/fields/fields-and-field-groups/08-field-article-bluebell-flowers-tab.png)

- **Blütezeit** Das Kontrollkästchenfeld - Bluebells sind bekannte Frühlingsblumen,
  daher ist die Auswahl eines Kontrollkästchens angebracht.
- **Winterhärte** Das Zahlenfeld. Es gibt hier ein Problem: Es gibt keine Möglichkeit,
  dieses Feld leer zu lassen. Es ist also immer im Output vorhanden, selbst für
  allgemeinere Beiträge über Pflanzen, bei denen es nicht passt. Es gibt ein
  Workaround, das eine Template-Überschreibung beinhaltet.

## Seitenergebnis

Schauen Sie sich das Ergebnis auf Ihrer Seite an. In diesem Beispiel wurde ein einzelnes Beitragsmenüelement erstellt:

![Bluebell-Beitragsansicht](../../../en/images/fields/fields-and-field-groups/09-field-article-bluebell-site.png)

### Die hexadezimale Farbe

Die Standardanzeige ist der hexadezimale Farbwert, der nicht besonders nützlich ist. Die einfache Lösung besteht darin, ein Template-Override für die Felder/Color-Plugin zu erstellen, was im obigen Screenshot gezeigt wird.

Ersetzen Sie einfach diese Zeile:
```
echo htmlentities($value);
```
mit diesen Zeilen:
```
if (is_array($value)) {
  $list = [];
  foreach ($value as $v) {
    $x = htmlentities($v);
    $list[] = '<span class="ps-5 pe-5" style="background-color: ' . $x . ';">&nbsp</span> ' . $x;
    echo implode(', ', $list);
  }
} else {
    $x = htmlentities($value);
    echo '<span class="ps-5 pe-5" style="background-color: ' . $x . ';">&nbsp</span> ' . $x;
}
```
Und der hexadezimale Wert wird von einem Farbfeld mit der Hintergrundfarbe des Wertes begleitet werden.

*Übersetzt von openai.com*

