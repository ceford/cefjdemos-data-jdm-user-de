<!--
{
  "source": "https://docs.joomla.org/J3.x:Adding_custom_fields",
  "title": "Textbereichsfeld ",
  "description": "", 
  "author": ""
}
-->

## Zweck

Das Textarea-Feld ist ein Bereich für die Eingabe von mehrzeiligem Text. Ein einfaches Textfeld verfügt nicht über einen WYSIWYG-Editor.

### Optionen

Spezielle Optionen innerhalb dieses Feldes sind:

- **Zeilen** Die Höhe des sichtbaren Textbereichs in Zeilen. Wenn nicht angegeben, wird die Höhe vom Browser bestimmt. Der Wert begrenzt nicht die Anzahl der einzugebenden Zeilen. Die Zeilen sind im Backend aktiv, während ein Beitrag, ein Kontakt oder eine Drittanbieterkomponente, die benutzerdefinierte Felder unterstützt, erstellt wird. Diese Option hat keinen Einfluss auf die Größe des Feldes im Frontend.
- **Spalten** Die Breite des sichtbaren Textbereichs in Zeichen. Wenn nicht angegeben, wird die Breite vom Browser bestimmt. Der Wert begrenzt nicht die Anzahl der einzugebenden Zeichen. Die Spalten sind im Backend aktiv, während ein Beitrag, ein Kontakt oder eine Drittanbieterkomponente, die benutzerdefinierte Felder unterstützt, erstellt wird. Diese Option hat keinen Einfluss auf die Größe des Feldes im Frontend.
- **Maximale Länge** Die maximale Anzahl der einzugebenden Zeichen.
- **Filter** Ermöglicht dem System, bestimmte HTML-Tags oder Rohdaten zu speichern.

![Textarea-Felderstellung](../../../en/images/fields/adding-custom-fields-textarea-field/01-fields-textarea-edit.png)

**Hinweis:** In diesem Beispiel dient die Einbeziehung des Feldtyps im Titel nur zu Demonstrationszwecken. Lassen Sie ihn bei Ihren eigenen Feldtiteln weg.

## Dateneingabe

Einfach: Geben Sie den Text ein, der angezeigt werden soll.

![textarea field data entry](../../../en/images/fields/adding-custom-fields-textarea-field/02-fields-textarea-data-entry.png)


## Datenanzeige

Der folgende Screenshot der Seite zeigt das Feld, das in einem Beitrag angezeigt wird. Die Option *Automatische Anzeige* ist für die Position des Feldes verantwortlich und Ihr Template ist für das Design des Feldes verantwortlich.

![Textarea-Feld Seitenanzeige](../../../en/images/fields/adding-custom-fields-textarea-field/03-fields-textarea-site.png)

Das Feldlabel startet einen Textblock, es sei denn, Sie haben HTML-Tags wie `<p>...</p>` eingegeben.

