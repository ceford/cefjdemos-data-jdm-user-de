<!--
{
  "source": "https://docs.joomla.org/J4.x:FatalError",
  "title": "FatalError  ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Von Zeit zu Zeit kann es vorkommen, dass Joomla statt der erwarteten Seite eine Fehlerseite anzeigt. Es gibt zwei Arten von Fehlerseiten:

- Die Systemfehlerseite hat einen roten Hintergrund. Sie wird angezeigt, wenn ein schwerwiegender Fehler auftritt, bevor das Site- oder Administrator-Template gerendert wird.
- Die Template-Fehlerseite sieht aus wie das normale Site- oder Administrator-Template, aber der Inhaltsbereich wird durch eine Fehlermeldung ersetzt. Diese wird aufgerufen, wenn der Fehler im Code des Inhalts auftritt.

### Systemfehlerseite

![System schwerwiegende Fehlerseite](../../../en/images/problems/fatalerror/01-fatal-error.png)

### Template-Fehlerseite

![Template-Fehlerseite](../../../en/images/problems/fatalerror/02-template-error.png)

## So beheben Sie das Problem

Es gibt eine Reihe möglicher Gründe, warum fatale Fehler auftreten können. Hier sind nur ein paar davon:

- Eine Änderung bei Ihrem Host, zum Beispiel eine aktualisierte PHP-Version, die mit Joomla oder einer Ihrer Erweiterungen nicht kompatibel ist.
- Ein Problem mit dem Speicherplatz, der Speichernutzung oder der Skript-Timeout.
- Eine neu installierte oder aktivierte Erweiterung, die mit Joomla nicht kompatibel ist. Ein fehlerhaftes Plugin kann den Administrator-Login deaktivieren!

### Debugging aktivieren

Wenn Ihre Administratoroberfläche **noch** funktioniert:
- Gehen Sie zu **Start-Dashboard → Systemfeld → Globale Konfiguration**.
- Setzen Sie im Reiter System *Debug System* auf *Ja*.
- Setzen Sie im Reiter Server *Fehlermeldungen* auf *Maximum*.
- Dann auf *Speichern & Schließen* klicken.

Wenn Ihre Administratoroberfläche **nicht** funktioniert, bearbeiten Sie die
Datei *configuration.php* im Stammordner Ihrer Joomla-Website.

1. Ändern Sie die Berechtigungen von *444* oder *-r--r--r--* (niemand hat
   Schreibberechtigung für die Datei) zu *644* oder *-rw-r--r--* (nur der
   Eigentümer darf die Datei schreiben).
2. Bearbeiten Sie die Datei mit einem Texteditor und setzen Sie `$debug` auf `true` und 
   `$error_reporting` auf `'maximum'`.
3. *Speichern* Sie die Datei ab.

Nachdem die Änderungen vorgenommen wurden, laden Sie die Seite erneut, die den Fehler verursacht hat. Nun sollten Sie eine Stack-Tracelog sehen. Beispiel:

![Vorlagen-Fehlerseite](../../../en/images/problems/fatalerror/03-template-error-stack-trace.png)

Der erste Eintrag im Stack-Tracelog zeigt an, wo der Fehler ausgelöst wurde. Manchmal reicht das aus, um die fehlerhafte Erweiterung zu identifizieren. Manchmal liegt die fehlerhafte Erweiterung weiter unten im Stack-Tracelog. Das mag für Sie vielleicht nicht viel bedeuten, aber das Stack-Tracelog ist äußerst wertvoll für die Experten, die Fragen in den Joomla-Foren beantworten.

Wenn Sie die fehlerhafte Erweiterung identifizieren können, deaktivieren Sie diese. Sie können dies über die Administratoroberfläche tun, wenn sie funktioniert. Andernfalls verwenden Sie phpMyAdmin, um die Erweiterung in der `#__extensions` Datenbanktabelle zu finden und setzen deren `enabled` Wert auf `0`. Sie sollten keine der Joomla-Kern-Erweiterungen deaktivieren müssen.

## Forum-Beitragsassistent

Um Probleme zu lösen, sollten Sie den [Forum-Beitragsassistenten (FPA)](https://forumpostassistant.github.io/docs/) herunterladen und im Root-Verzeichnis Ihrer Joomla-Website speichern. Der Link dazu befindet sich auch in der Nähe des oberen Bereichs jeder Joomla-Forum-Seite. Der FPA ist ein eigenständiges PHP-Skript, das Ihre Joomla-Installation analysiert und Ihnen mitteilt, was möglicherweise falsch ist. Es könnte für Sie nicht viel bedeuten, aber die Experten, die Fragen in den Foren beantworten, könnten darum bitten, es einzusehen.

## Aufräumen

Wenn Ihr Problem gelöst ist:

1. Gehen Sie zu **Start-Dashboard → Systemsteuerung → Globale Konfiguration**.
2. Wählen Sie die Registerkarte System und setzen Sie *Debug-System* auf *Nein*.
3. Wählen Sie die Registerkarte Server und stellen Sie *Fehlerberichterstattung* auf *Systemstandard* ein.
4. *Speichern & Schließen*.
5. Entfernen Sie den Forum Post Assistant.

Die Berechtigungen der `configuration.php`-Datei werden auf schreibgeschützt (444 oder *r--r--r--*) gesetzt, wenn das Formular der Globalen Konfiguration gespeichert wird. Es ist nicht notwendig, dies manuell zu tun.

*Übersetzt von openai.com*

