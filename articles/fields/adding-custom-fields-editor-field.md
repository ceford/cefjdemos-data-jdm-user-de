<!--
{
  "source": "https://docs.joomla.org/J3.x:Adding_custom_fields",
  "title": "Bearbeitungsfeld",
  "description": "", 
  "author": ""
}
-->

## Zweck

Das Editor-Feld ermöglicht die WYSIWYG-Dateneingabe für einige beitragsbezogene Inhalte zusätzlich zum Hauptinhalt.

## Felderstellung

Spezielle Optionen innerhalb dieses Feldes sind:

- **Buttons** Anzeigelang oder Verbergen der CMS-Inhalts-Dropdown-Liste. Für Beitragsergänzungstexte kann es unpassend sein, einige oder alle der Schaltflächen in der Liste anzuzeigen. Der Standardwert des Plugins ist Verbergen.
- **Schaltflächen verbergen** Wenn *Buttons* auf *Ja* gesetzt ist oder der Standardwert des Plugins *Anzeigen* ist, können ausgewählte Schaltflächen in der CMS-Inhalts-Dropdown-Liste verborgen werden.
- **Breite und Höhe** Werte umfassen den Platz, der von der Editor-Symbolleiste eingenommen wird, sodass es wahrscheinlich am besten ist, sie zunächst leer zu lassen.
- **Breite** Der Wert für die Breite definiert die Breite des WYSIWYG-Editors in % oder Pixeln. Der Standardwert ist 100%.
- **Höhe** Der Wert für die Höhe definiert die Höhe (in Pixeln) des WYSIWYG-Editors. Der Standardwert dafür ist 250px. Der Wert kann als Bruchteil der Bildschirmhöhe dargestellt werden, zum Beispiel 50vh.
- **Filter** Erlauben Sie dem System, bestimmte HTML-Tags oder Rohdaten zu speichern.

![Erstellung eines Editor-Feldes](../../../en/images/fields/adding-custom-fields-editor-field/01-fields-editor-edit.png)

**Hinweis:** In diesem Beispiel dient die Aufnahme des Feldtyps in den Titel nur zu Demonstrationszwecken. Lassen Sie ihn in Ihren eigenen Feldtiteln weg.

## Dateneingabe

Im Beitragsbearbeitungsformular ähnelt das zusätzliche Editor-Feld dem Hauptinhalt-Editor-Feld.

![Editor-Feld Dateneingabe](../../../en/images/fields/adding-custom-fields-editor-field/02-fields-editor-data-entry.png)

## Datenanzeige

Der folgende Screenshot der Website zeigt das Feld, das in einem Beitrag angezeigt wird. Die Option *Automatische Anzeige* ist für die Position des Feldes verantwortlich und Ihr Template ist für das Design des Feldes verantwortlich.

In der Beitragsanzeige erscheint der eingegebene Text unter der Überschrift, jedoch als Teil der Aufzählungsliste für dieses Feld.

Suchen Sie nach dem **Anbauhinweise**-Element.

![Editor-Feld-Website-Anzeige](../../../en/images/fields/adding-custom-fields-editor-field/03-fields-editor-site.png)

*Übersetzt von openai.com*

