<!--
{
  "source": "https://docs.joomla.org/J3.x:Adding_custom_fields",
  "title": "Kalenderfeld ",
  "description": "", 
  "author": ""
}
-->

## Zweck

Das Kalenderfeld bietet ein Textfeld zur Eingabe eines Datums. Ein Symbol neben dem Textfeld öffnet einen Kalender-Picker, der verwendet werden kann, um ein Datum aus einem grafischen Kalender auszuwählen.

## Felderstellung

Allgemeine Feldparameter werden in einem separaten Beitrag beschrieben.

* **Titel** Sie können mehrere Datumsfelder in einem Beitrag haben, daher ist Vorsicht geboten bei der Setzung des Titels, um Mehrdeutigkeiten in der Ausgabe zu vermeiden.
* **Label** Dies ist das, was in der Ausgabe angezeigt wird. Wenn es leer gelassen wird, wird es aus dem Inhalt des Titelfeldes übernommen, kann jedoch geändert werden.
* **Zeit anzeigen** Wenn auf *Ja* gesetzt, wird die Zeit dem Datumsfeld, dem Datumsauswahl-Tool und dem Ausgabedatum hinzugefügt. **Achtung**: Auch wenn Sie die Zeit im Standarddatum nicht angeben, wird die Zeit angezeigt, wenn die Option *Zeit anzeigen* aktiv ist.
* **Platzhalter** Dies befindet sich im Reiter Optionen. Es kann auf ein Datumsformat wie *JJJJ-MM-TT* gesetzt werden, um Benutzer an das erforderliche Format zu erinnern und/oder eine Erinnerung daran, wofür das Datum ist, wie z.B. *Ankunftsdatum*.

![Kalenderfeld-Erstellung](../../../en/images/fields/adding-custom-fields-calendar-field/01-fields-calendar-edit.png)

**Hinweis:** In diesem Beispiel dient die Einbeziehung des Feldtyps im Titel nur zu Demonstrationszwecken. Lassen Sie dies in Ihren eigenen Feldtiteln weg.

## Dateneingabe

Die Verwendung des Kalenderfeldes ist einfach. Sie können das Datum im erforderlichen Format eingeben oder ein Datum mit dem Datumsauswahl-Tool auswählen. Es ist Vorsicht geboten beim Eingeben der Daten. Ein Fehler im Datum wird beim Speichern auf ein neues Datum korrigiert. Zum Beispiel wird ein Datum von 2024-14-02 in 2025-02-02 korrigiert.

Der folgende Screenshot zeigt ein Erfassungsdatum:

![Kalenderfeld Dateneingabe](../../../en/images/fields/adding-custom-fields-calendar-field/02-fields-calendar-data-entry.png)

Felder erscheinen nur in einem Beitrag, wenn sie im Dateneingabeformular des Beitrags ausgefüllt sind.

## Datenanzeige

Der folgende Screenshot der Website zeigt das Feld, das in einem Beitrag angezeigt wird. Die Option *Automatische Anzeige* ist verantwortlich für die Position des Feldes und Ihr Template ist für das Design des Feldes verantwortlich.

![Kalenderfeld Website-Anzeige](../../../en/images/fields/adding-custom-fields-calendar-field/03-fields-calendar-site.png)

Die Datumsformate werden mit Sprachstrings lokalisiert.

*Übersetzt von openai.com*

