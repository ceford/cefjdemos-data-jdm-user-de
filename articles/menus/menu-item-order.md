<!--
{
  "source": "https://docs.joomla.org/J4.x:Menu_Item_Order",
  "title": "Reihenfolge der Menüeinträge",
  "description": "", 
  "author": ""
}
-->

## Einführung

Wenn ein neues Menüelement erstellt wird, ist seine Standardposition am Ende der Liste der Menüelemente. Oft ist dies nicht der geeignetste Platz, und ein einzelnes Menüelement muss verschoben werden, zusammen mit allen Unterelementen, falls es ein übergeordnetes Menüelement ist. Es stehen zwei Methoden zur Verfügung, um die Reihenfolge eines Menüelements zu ändern:

- Drag and Drop
- Listenauswahl

Beide Methoden bewegen Untermenüs zusammen mit ihren übergeordneten Menüs. Unterelemente können mit diesen Methoden nicht zu einem anderen übergeordneten Element verschoben werden.

## Drag-and-Drop-Methode

Ausgehend vom Administrator-Menü:

- Wählen Sie **Menüs** → **Hauptmenü** oder das Menü, das den zu verschiebenden Eintrag enthält.
- Wählen Sie das **Sortier**symbol in der Kopfzeile der Liste der Menüeinträge aus. Es ist die Überschrift der zweiten Spalte und hat kein sichtbares Etikett. Wenn die Sortierspalte ein zweites Mal ausgewählt wird, wird die Sortierreihenfolge umgekehrt. Wählen Sie so, dass das Symbol am Anfang der Spalte ein nach oben zeigendes Chevron ist. Dies ist die normale Sortierreihenfolge.
- Wenn das Sortiersymbol ausgewählt ist, erscheinen in dieser Spalte Ziehgriffe. Sie sind mit vertikalen Auslassungszeichen markiert.
- Wählen Sie das Symbol des zu verschiebenden Elements aus und ziehen Sie es.
- Lassen Sie das gezogene Element an seiner neuen Position fallen.

![Menüeintragsreihenfolge ziehen](../../../en/images/menus/menu-item-order/01-menus-menu-item-order-drag.png)

Diese Methode kann unpraktisch sein, wenn es übergeordnete Menüeinträge mit vielen untergeordneten Einträgen gibt. Sie können ein übergeordnetes Element leichter verschieben, indem Sie die untergeordneten Elemente ausblenden:

- Wählen Sie **Filteroptionen**
- Setzen Sie **- Maximale Ebenen auswählen -** auf 1
- Drag and Drop

Dies funktioniert nicht, wenn die Reihenfolge eines untergeordneten Menüeintrags geändert werden soll. In diesem Fall:

- Wählen Sie **Filteroptionen**
- Stellen Sie den Filter **- Übergeordneten Menüpunkt auswählen -** auf das entsprechende übergeordnete Element ein
- Drag and Drop

## Methode zur Auswahl aus der Liste

Ausgehend vom Administrator-Menü:

- Wählen Sie **Menüs → Hauptmenü** oder das Menü, das den zu verschiebenden Eintrag enthält.
- Wählen Sie den Titellink des Menüeintrags, den Sie verschieben möchten, um das Bearbeitungsformular für den Menüeintrag zu öffnen.
- Wählen Sie im Formular "Menüs: Eintrag bearbeiten" das Feld **Reihenfolge** aus, nach welchem Eintrag der zu verschiebende Eintrag platziert werden soll, oder die Positionen *- Erster -* oder *- Letzter -*.

![Reihenfolge der Menüeinträge](../../../en/images/menus/menu-item-order/02-menus-menu-item-order-list.png)

- **Speichern** oder **Speichern & Schließen**

## Seitenüberprüfung

Gehe zu deiner Webseite und lade jede Seite neu, die das geänderte Menü enthält, um zu überprüfen, ob die Elemente in der gewünschten Reihenfolge sind.

*Übersetzt von openai.com*  

