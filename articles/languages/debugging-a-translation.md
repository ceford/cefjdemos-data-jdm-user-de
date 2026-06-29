<!--
{
  "source": "https://docs.joomla.org/Debugging_a_translation",
  "title": "Debuggen einer Übersetzung",
  "description": "", 
  "author": ""
}
-->

## Joomla Sprachdateien

Wann immer Text auf dem Bildschirm ausgegeben werden soll, fügen Joomla-Entwickler eine Sprachkonstante wie JYES oder JNO ein. Während des Renderprozesses werden Sprachdateien mit Übersetzungen in der entsprechenden Sprache geladen. Die Sprachdateien enden alle mit `.ini`. Im Verzeichnis languages/en-GB/joomla.ini finden Sie einige grundlegende Beispiele. Zeilen, die mit einem Semikolon beginnen, werden ignoriert. Sie können für Kommentare verwendet werden. Die verbleibenden Zeilen bestehen aus Schlüssel="Wert"-Paaren. Jede Sprache hat denselben Satz von Schlüsseln, aber die Werte sind die entsprechenden Übersetzungen.

Jede Joomla-Erweiterung hat ihre eigenen Sprachdateien, sodass es insgesamt Hunderte gibt. Manchmal gibt es Probleme wie fehlende Sprachkonstanten, falsch geschriebene Sprachkonstanten oder Syntaxfehler in den Übersetzungszeichenfolgen, die eine ganze Sprachdatei ungültig machen können.

## Debug-Sprache

Joomla bietet einige nützliche Debugging-Mechanismen, die es einfacher machen können, nicht übersetzte Zeichenfolgen zu lokalisieren und Probleme mit Sprachübersetzungen in installierten Erweiterungen zu diagnostizieren. Um es auszuprobieren:

Vom Home Dashboard aus:

* Wählen Sie die Schaltfläche **Globale Konfiguration** im *System* Panel.
* Wählen Sie das *System* Panel und setzen Sie **Debug-Sprache** auf **Ja**.
* **Sprachanzeige** ist normalerweise auf **Wert** eingestellt. Wenn sie auf **Konstante** eingestellt ist, wird das Layout durch lange Konstanten, die nicht umbrechen, gestört.

Wenn Debug-Sprache aktiv ist, werden alle übersetzbaren Werte von speziellen Zeichen umgeben angezeigt, die ihren Status angeben:

* `**Joomla CMS**` Text, der von zwei Sternchen umgeben ist, zeigt an, dass ein Treffer in einer Sprachdatei gefunden wurde und die Konstante übersetzt wurde.
* `??Joomla CMS??` Text, der von Paaren von Fragezeichen umgeben ist, zeigt an, dass die Konstante übersetzbar ist, aber kein Treffer in einer Sprachdatei gefunden wurde.
* `Joomla CMS` Text ohne umgebende Zeichen zeigt an, dass der Wert nicht übersetzbar ist.

## Debug-System

Zusätzliche Debug-Informationen zur Sprache können durch Aktivierung des System-Debuggings erhalten werden.

Vom Home-Dashboard aus:

* Wählen Sie **Plugins** und finden Sie das Plugin **System - Debug**, um es zu aktivieren.
* Wählen Sie erneut das Home-Dashboard und dann...
* Wählen Sie die Schaltfläche **Globale Konfiguration**.
* Wählen Sie das *System*-Panel und setzen Sie **Debug-System** auf **Ja**.

Wenn das **System-Debugging** aktiv ist, haben alle Bildschirme zusätzliche Debug-Informationen am unteren Rand jeder Seite. Diese können von einem Joomla-Symbol aus erweitert werden, und die obere Grenze kann vertikal gezogen werden, um mehr Zeilen anzuzeigen.

Die Debug-Informationen erscheinen unter mehreren Überschriften:

* **J! Info** Grundlegende Installationsinformationen.
* **Request** Serveranforderungsfelder.
* **Sitzung** Sitzungsinformationen.
* **Profil** Die benötigte Zeit, um den Code bis zu verschiedenen Markierungen auszuführen.
* **Abfragen** Die SQL-Abfragen, die im Prozess des Seitenaufbaus ausgeführt wurden.
* **Geladen.** Eine Liste aller Sprachdateien, die im Prozess des Seitenaufbaus geladen wurden, einschließlich vollständiger Pfadangaben. Dies kann nützlich sein, um zu überprüfen, ob die erwarteten Dateien geladen wurden.
* **Unübersetzt** Eine Liste aller nicht übersetzten Konstanten und die wahrscheinliche Dateiposition, an der der Übersetzungsaufruf gemacht wurde.
* **Fehler**

## System - Debug Plugin

Dieses System-Plugin steuert, was angezeigt wird, wenn das Debuggen in der **Globalen Konfiguration** aktiviert ist. Es gibt drei Einstellungen, die für Übersetzer von Interesse sind.

Im **Sprache**-Tab:

![plugin system debug](../../../en/images/languages/debugging-a-translation/01-languages-debug-plugin.png)

* **Fehler beim Parsen von Sprachdateien** Zeigt einen Fehler an, wenn eine Sprachdatei
nicht geladen werden kann.

- **Sprachdateien**. Wenn auf *Anzeigen* gesetzt, dann ...
- **Sprachstring** Wenn auf *Anzeigen* gesetzt, dann ...
- **Erstes Wort entfernen**.
- **Vom Anfang abschneiden**.
- **Vom Ende abschneiden**.

**Die folgende Erklärung bedarf einer Überarbeitung!**

Beachten Sie, dass nicht übersetzte Strings nur den Wert anzeigen, der an die entsprechende **Text**-Methode übergeben wird. Zum Beispiel, mit dem folgenden Code:

    echo Text::_( 'Reports Import Configuration' );

Wenn nicht übersetzt, wird folgendes angezeigt:

    # /administrator/components/com_reports/views/reports/tmpl/default.php
    REPORTS IMPORT CONFIGURATION=Reports Import Configuration

Wenn das Strip Key Prefix auf "Reports" gesetzt ist, wird die Anzeige leicht geändert zu:

    # /administrator/components/com_reports/views/reports/tmpl/default.php
    REPORTS IMPORT CONFIGURATION=Import Configuration

Beachten Sie, dass der angezeigte Pfad nur eine beste Schätzung basierend auf einem Aufruf der PHP-Funktion *debug_backtrace* ist. Manchmal ist er korrekt, manchmal nicht, und es gibt auch Fälle, in denen keine Datei ermittelt werden konnte. In diesen Fällen müssen Sie Ihr bestes Urteilsvermögen einsetzen.

*Übersetzt von openai.com*

