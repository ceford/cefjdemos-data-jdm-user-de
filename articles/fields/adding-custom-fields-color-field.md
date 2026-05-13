<!--
{
  "source": "https://docs.joomla.org/J3.x:Adding_custom_fields",
  "title": "Farbfläche ",
  "description": "", 
  "author": ""
}
-->

## Zweck

Das Farbfeld bietet einen Picker zur visuellen Auswahl einer Farbe. Das Feld zeigt den resultierenden Hex-Wert an.

## Feld Erstellung

Spezielle Optionen für dieses Feld:

- **Feldklasse** Setzen Sie auf *w-auto*, um das Feld nur so breit wie nötig für den Farbfelder und den Wert zu machen.

![Farbe Feld Erstellung](../../../en/images/fields/adding-custom-fields-color-field/01-fields-colour-edit.png)

**Hinweis:** In diesem Beispiel ist die Aufnahme des Feldtyps im Titel nur zu Demonstrationszwecken. Lassen Sie es in Ihren eigenen Feldtiteln weg.

## Dateneingabe

Sie können einen Hex-Farbwert eingeben, wenn Sie wissen, dass Hex-Zahlen von 0 bis 9 und dann von a bis f reichen. Die Zahlenpaare stehen dabei für Rot, Grün und Blau. Also steht #00ff00 für kein Rot, maximales Grün und kein Blau. Alternativ können Sie einen Cursor verwenden, um eine Farbe visuell auszuwählen.

![Feldeingabe für Farbe](../../../en/images/fields/adding-custom-fields-color-field/02-fields-colour-data-entry.png)


## Datenanzeige

Der folgende Screenshot der Website zeigt das Feld, das in einem Beitrag angezeigt wird. Die Option *Automatische Anzeige* ist verantwortlich für die Position des Feldes und Ihr Template ist verantwortlich für das Design des Feldes.

Die standardmäßige Datenanzeige ist der Hex-Farbwert, der nicht sehr nützlich ist. Die einfache Lösung besteht darin, ein Template-Override für die Felder / den Farb-Plugin zu erstellen. Ersetzen Sie einfach diese Zeile:
```
echo htmlentities($value);
```
durch diese Zeilen:
```
$value = htmlentities($value);
echo '<span style="background-color: ' . $value . ';"> ' . $value . '</span>';
```
Und der Hex-Wert wird durch ein Farbmuster mit der Hintergrundfarbe des Wertes vorangestellt.

Suchen Sie nach dem **Blumenfarbe**-Eintrag.

![Feldanzeige der Farben auf der Website](../../../en/images/fields/adding-custom-fields-color-field/03-fields-colour-site.png)

