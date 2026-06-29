<!--
{
  "source": "https://docs.joomla.org/jdocmanual?manual=user&heading=fields&filename=subform.md",
  "title": "Unterformularfeld ",
  "description": "", 
  "author": ""
}
-->

## Zweck

Das Unterformularfeld ermöglicht es, eine Auswahl von Feldern in einer wiederholbaren Liste zusammenzufassen.

## Felderstellung

Zuerst erstellen Sie die benötigten Felder im Unterformular. In dem hier beschriebenen Beispiel gibt es ein Kalenderfeld (Erwerbsdatum), ein Textfeld (Preis) und ein Farbfeld (Blütenfarbe), die für eine Liste mehrerer Exemplare verwendet werden sollen.

**Fehler:** Es gibt einen Fehler im Kalenderfeldcode, der zu einem schwerwiegenden Fehler führt, wenn ein Beitrag ein zweites Mal gespeichert wird. Um dieses Problem zu vermeiden, setzen Sie den Wert *Zeitanzeige* im Kalenderfeld auf *Ja*.

Spezielle Optionen für dieses Feld:

- **Titel** und **Beschriftung** In diesem Beispiel sind diese auf *Exemplare* gesetzt.
- **Felder** Fügen Sie die erforderlichen Felder im Unterformular nacheinander hinzu. Jede Zeile hat eine Dropdown-Liste der verfügbaren Felder und einen Umschalter für Werte anzeigen Ja/Nein. Die Reihenfolge der Elemente kann mit dem Ziehsymbol geändert werden.

![Erstellung Unterformular](../../../en/images/fields/subforms/01-fields-subform-edit.png)

**Hinweis:** In diesem Beispiel dient die Einbeziehung des Feldtyps im Titel nur zu Demonstrationszwecken. Lassen Sie ihn in Ihren eigenen Feldtiteln weg.

## Dateneingabe

Im Dateneingabeformular müssen Sie für jedes Exemplar Zeilen hinzufügen. Jede Zeile enthält ein Kalenderfeld, ein Textfeld und ein Farbfeld.

![Unterformular Dateneingabe](../../../en/images/fields/subforms/02-fields-subform-data-entry.png)

## Datenanzeige

Im Beitrag hat das Unterformular mit dem Titel Proben eine Zeile für jede Probe.
Suchen Sie den **Proben**-Eintrag in diesem Screenshot:

![Unterformularseitenanzeige](../../../en/images/fields/subforms/03-fields-subform-site.png)

*Übersetzt von openai.com*

