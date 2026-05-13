<!--
{
  "source": "https://docs.joomla.org/J3.x:Adding_custom_fields",
  "title": "SQL Feld ",
  "description": "", 
  "author": ""
}
-->

## Zweck

Das SQL-Feld bietet eine Dropdown-Liste von Einträgen, die aus einer Datenbankabfrage gewonnen wurden. Um dieses Feld zu verwenden, müssen Sie wissen, wie man eine Abfrage erstellt, und Sie sollten diese in phpMyAdmin testen.


## Feld Erstellung

Besondere Optionen innerhalb dieses Feldes sind:

- **Mehrfach** Erlaubt die Auswahl mehrerer Werte. Wenn auf *Ja* gesetzt, zeigt die Liste 4 Elemente an. Andernfalls zeigt sie 1 Element an. In beiden Fällen gibt es eine lange Liste, durch die gescrollt werden muss, um eine Auswahl zu treffen - falls aktiviert.
- **Abfrage** Die SQL-Abfrage, welche die Daten für die Dropdown-Liste bereitstellt. Die Abfrage muss zwei Spalten zurückgeben; eine mit dem Namen 'value', die die Werte der Listenelemente enthält; die andere mit dem Namen 'text', die den Text in der Dropdown-Liste enthält.

In diesem Beispiel wird eine Tabelle mit einer Liste von Ländernamen verwendet. Dies ist die Abfrage:
```
SELECT `id` AS value, `title` AS text
FROM `#__countrybase_countries`
WHERE `state` = 1
ORDER BY `title` ASC
```
![SQL Feld Erstellung](../../../en/images/fields/adding-custom-fields-sql-field/01-fields-sql-edit.png)

**Hinweis:** In diesem Beispiel ist die Aufnahme des Feldtyps im Titel nur zu Demonstrationszwecken vorgesehen. Lassen Sie es in Ihren eigenen Feldtiteln weg.

## Dateneingabe

Einfach - aus der Liste auswählen.

![SQL-Feld-Dateneingabe](../../../en/images/fields/adding-custom-fields-sql-field/02-fields-sql-data-entry.png)


## Datenanzeige

Der folgende Screenshot der Seite zeigt das Feld, das in einem Beitrag angezeigt wird. Die Option *Automatische Anzeige* ist für die Position des Feldes verantwortlich, und Ihr Template ist für das Design des Feldes verantwortlich.

![SQL-Feld-Anzeige auf der Seite](../../../en/images/fields/adding-custom-fields-sql-field/03-fields-sql-site.png)

Die Ausgabe ist ein einzelnes Element oder eine durch Kommas getrennte Liste von Elementen (Ländernamen) nach dem Feldlabel (Herkunftsland).

*Übersetzt von openai.com*

