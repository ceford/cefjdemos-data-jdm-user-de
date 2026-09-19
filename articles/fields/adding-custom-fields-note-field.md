<!--
{
    "source": "https://docs.joomla.org/localhost",
    "title": "Notizfeld",
    "description": "",
    "author": ""
}
-->

## Zweck

Der Notizformularfeldtyp ermöglicht das Erstellen von Titeln, Texten, Beschreibungen und sogar Hinweisfeldern. Außerdem können Sie damit Ordnung in die Einstellungen für Erweiterungen bringen, indem Sie sie durch aussagekräftige Titel voneinander trennen. Oder Beschreibungen für bestimmte Einstellungen hinzufügen (ohne auf Tooltips angewiesen zu sein). Oder jeden anderen gewünschten Text hinzufügen.

## Felderstellung

### Allgemeiner Tab

![Erstellung eines Hinweisfelds](../../../en/images/fields/adding-custom-fields-note-field/01-fields-note-edit.png)

- **Typ** Zahl, die nach der Auswahl nicht geändert werden kann.
- **Name** Der eindeutige Name des Feldes.
- **Bezeichnung** Eine übersetzbare Bezeichnung für das Feld.
- **Beschreibung** Eine optionale übersetzbare Feldbeschreibung.
- **Nur im Unterformular verwenden** *Ja* oder *Nein*.
- **Überschrift des Hinweises** Diese wird im Dateneingabeformular angezeigt.
- **Inhalt des Hinweises** Der Text des Hinweises.
- **Klasse des Hinweises** Beliebige vorhandene oder neue Klassen. Der Standardwert *alert alert-info* erzeugt ein Bootstrap-Hinweisfeld.
- **Überschriften-Tag** Wählen Sie aus der Liste der Überschriftenebenen aus.
- **Schließen-Schaltfläche anzeigen** Dieses Feld steuert die Anzeige eines „x“ zum Schließen des Hinweises. Es nimmt den Wert „true“ (für Alerts) oder den Wert für das data-dismiss-Attribut des Bootstrap-Schließsymbols an.### Registerkarte „Optionen“
- **Automatische Anzeige** Ob und wo das Feld angezeigt werden soll:
    - **Nach dem Titel**
    - **Vor dem Anzeigeinhalt**
    - **Nach dem Anzeigeinhalt**
    - **Nicht automatisch anzeigen**
- **Layout** eine Liste der verfügbaren Layouts.
- **Im Frontend anzeigen** *Ja* oder *Nein*.

## Dateneingabe

Im Dateneingabeformular erscheint das Notizfeld neben anderen Feldern als Text, der entsprechend den im Feld festgelegten Stilauswahlen formatiert ist. Es kann Anweisungen oder Informationen enthalten.

![Dateneingabe des Zahlenfelds](../../../en/images/fields/adding-custom-fields-note-field/02-fields-note-data-entry.png)

**Tipp:** Verwenden Sie den Mechanismus zum Sortieren von Feldern, um die Reihenfolge der Notizen zwischen anderen Feldern festzulegen. Sie können mehrere verschiedene Notizfelder verwenden, um Ihren Feldern Struktur und Informationen zu geben.

## Datenanzeige

Wenn *Im Frontend anzeigen* auf *Ja* gesetzt ist, erscheint das Notizfeld neben anderen Feldern im Frontend. Dort kann es allgemeine Informationen enthalten, die für eine Gruppe von Beiträgen gelten.

*Übersetzt von openai.com*