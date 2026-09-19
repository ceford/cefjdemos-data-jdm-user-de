<!--
{
    "source": "https://docs.joomla.org/localhost",
    "title": "Zahlenfeld",
    "description": "",
    "author": ""
}
-->

## Zweck

Das Zahlenfeld bietet eine Möglichkeit, eine reelle Zahl einzugeben und optional ein Währungs- oder anderes Symbol vor oder nach der Zahl anzufügen. Das Steuerelement kann als Ganzzahlenfeld mit Pfeilen zum Erhöhen und Verringern und einem Standardbereich von 1 bis 100 verwendet werden. Es können jedoch reelle Werte, positive oder negative, in das Feld eingegeben werden. Beispiel: `99.99` könnte so formatiert werden, dass es für den Endbenutzer als `£99.99` erscheint. Oder `-273.15` könnte für den Endbenutzer als `-273.15C` angezeigt werden.

## Felderstellung

### Registerkarte „Allgemein“

![Erstellung eines Zahlenfelds](../../../en/images/fields/adding-custom-fields-number-field/01-fields-number-edit.png)

- **Typ** Zahl, die nach der Auswahl nicht geändert werden kann.
- **Name** Der eindeutige Name des Felds.
- **Bezeichnung** Eine übersetzbare Bezeichnung für das Feld.
- **Beschreibung** Eine optionale übersetzbare Feldbeschreibung.
- **Erforderlich** Auf *Ja setzen, wenn dieses Feld erforderlich ist?
- **Nur im Unterformular verwenden** *Ja oder *Nein.
- **Standardwert** Ein optionaler Standardwert.
- **Minimum** Der Mindestwert, der mithilfe der Aufwärts-/Abwärtspfeile ausgewählt werden kann. Der Standardwert ist 1. Es kann sich um eine negative Zahl handeln. Legen Sie den Wert daher niedriger als die erwartete niedrigste Zahl fest, **andernfalls kann die Auswahl des Abwärtspfeils die vorhandene Zahl löschen**.
- **Maximum** Der Höchstwert, der mithilfe der Aufwärts-/Abwärtspfeile ausgewählt werden kann. Der Standardwert ist 100. Legen Sie den Wert höher als die erwartete höchste Zahl fest, **andernfalls kann die Auswahl des Aufwärtspfeils die vorhandene Zahl löschen**.- **Schrittweite** Die Größe des Schritts, der mithilfe der Aufwärts-/Abwärtspfeile zum aktuellen Feldwert addiert oder davon subtrahiert wird. Dies kann eine ganze Zahl sein, der Standardwert ist 1, oder eine Dezimalzahl wie 0,01. **Legen Sie den kleinsten Betrag fest, um den Sie den Wert erhöhen oder verringern möchten**.
- **Als Währung formatieren** Wenn diese Option ausgewählt ist, werden zusätzliche Felder angezeigt:
    - **Währungssymbol** Dies kann ein einzelnes Symbol wie `£` oder `$` oder eine Zeichenfolge wie `&deg;C` sein, die als *&deg;C* angezeigt wird.
    - **Symbolposition** Wählen Sie *Vor* oder *Nach* der Zahl.
    - **Anzahl der Dezimalstellen** Bei Währungen normalerweise 2, in anderen Zusammenhängen kann es jedoch auch ein anderer Wert sein.

### Registerkarte „Optionen“

#### Bedienfeld „Formularoptionen“:

- **Platzhalter** Platzhaltertext, der als Hinweis für die erforderliche Eingabe im Feld angezeigt wird.
- **Feldklasse** Eine optionale Klasse, die dem Dateneingabeformularfeld hinzugefügt wird.
- **Beschriftungsklasse** Eine optionale Klasse, die der Beschriftung des Dateneingabeformulars hinzugefügt wird.
- **Bearbeitbar in** Zulässige Bearbeitungsoberflächen: *Website*, *Administration* oder *Beide*.
- **Showon-Attribut** Das Feld abhängig vom Wert anderer Felder bedingt ein- oder ausblenden.#### Bereich „Anzeigeoptionen“:
- **Anzeigeklasse** Die Klasse des Feldcontainers in der Ausgabe.
- **Werteklasse** Die Klasse des Feldwerts in der Ausgabe.
- **Beschriftung** *Anzeigen* oder *Ausblenden* der Beschriftung in der Ausgabe. Bei Auswahl von „Anzeigen“:
    - **Beschriftungsklasse (Ausgabe)** Eine Klasse für die Beschriftung in der Ausgabe.
- **Automatische Anzeige** Ob und wo das Feld angezeigt werden soll:
    - **Nach dem Titel**
    - **Vor dem Anzeigeinhalt**
    - **Nach dem Anzeigeinhalt**
    - **Nicht automatisch anzeigen**
- **Präfix** Text, der vor dem Feldwert angezeigt wird.
- **Suffix** Text, der nach dem Feldwert angezeigt wird.
- **Layout** Eine Liste der verfügbaren Layouts.
- **Bei Nur-Lesen anzeigen** Auswahl zwischen *Übernehmen*, *Ja* oder *Nein*.

#### Bereich „Intelligente Suche“

- **Suchindex** Auswahl, ob gesucht werden soll, sowie der Suchmethode.

### Tabs „Veröffentlichung und Berechtigungen“

Der Inhalt dieser Tabs ist selbsterklärend und wird an anderer Stelle behandelt.## Dateneingabe

Dateneingabe: Geben Sie einfach den gewünschten Wert ein. Dieses Beispiel zeigt den Siedepunkt von Argon:

![Dateneingabe in einem Zahlenfeld](../../../en/images/fields/adding-custom-fields-number-field/02-fields-number-data-entry.png)

**Achtung:** Wenn die eingegebene Zahl außerhalb des in den Optionen zur Felderstellung festgelegten Mindest- und Höchstbereichs liegt, weist Sie eine Browser-Hover-Beschriftung darauf hin, aber die bereitgestellten Informationen werden nicht durchgesetzt. Sie können eine Zahl außerhalb des Bereichs eingeben, und sie wird akzeptiert.

## Datenanzeige

Das folgende Bild zeigt die Anzeige eines Beitrags mit einem negativen Wert:

![Anzeige eines Zahlenfelds auf der Website](../../../en/images/fields/adding-custom-fields-number-field/03-fields-number-site.png)

*Übersetzt von openai.com*