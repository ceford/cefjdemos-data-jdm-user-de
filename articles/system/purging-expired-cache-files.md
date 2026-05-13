<!--
{
  "source": "https://docs.joomla.org/Purging_expired_cache_files",
  "title": "Abgelaufenen Cache löschen  ",
  "description": "", 
  "author": ""
}
-->

## Cache-Dateien

Cache-Dateien sind temporäre Dateien, die erstellt werden, um die Leistung Ihrer Website zu verbessern. Sie müssen sicherstellen, dass abgelaufene Cache-Dateien, die nicht mehr benötigt werden, aus dem System entfernt werden. Andernfalls läuft der Speicherplatz irgendwann voll.

Abgelaufene Cache-Dateien können über die Administrator-Oberfläche oder die Kommandozeilen-Oberfläche (CLI) bereinigt werden.

## Bereinigung - Administrator-Methode

Vom *Home-Dashboard*
* Wählen Sie die Option **Cache** im *System*-Panel.
* Auf der Seite *Wartung: Cache leeren* wählen Sie die Schaltfläche **Abgelaufenen Cache leeren** in der Symbolleiste.

## Bereinigung - Befehlszeilen-Methode

Öffnen Sie ein Terminalfenster und navigieren Sie mit dem Befehl `cd` in das CLI-Verzeichnis im Stammverzeichnis Ihrer Website.  
Wenn Sie nicht wissen, welche CLI-Befehle verfügbar sind, geben Sie folgenden Befehl ein:
```bash
php joomla.php
```
Sie sehen eine Liste der verfügbaren Befehle. Der Befehl für den Cache lautet:
```bash
php joomla.php cache:clean
```
Es sollte eine grüne Bestätigungsmeldung oder möglicherweise eine kastanienbraune Fehlermeldung erscheinen.

## Automatisches Bereinigen abgelaufener Cache-Dateien

Sie können abgelaufene Cache-Dateien automatisch mit einem Cron-Job bereinigen. Hosting-Dienste machen dies einfach, indem sie ein Formular bereitstellen, mit dem Sie auswählen können, wie häufig ein Job ausgeführt wird und welchen Befehl Sie verwenden möchten. So könnten Sie den Cron so einstellen, dass er jeden Tag um 05:00 Uhr mit dem folgenden Befehl ausgeführt wird:
```
 /usr/local/bin/ea-php82 /home/username/public_html/cli/joomla.php cache:clean
 ```
Die meisten *Cron*-Job-Manager erlauben es Ihnen, eine E-Mail-Adresse einzugeben, an die die Cron-Ausgabe gesendet wird. Wenn Sie keine Nachricht erhalten möchten, fügen Sie ` > /dev/null 2>&1` an den Befehl an.

Die PHP-Version, die in der Befehlszeile verwendet wird, ist oft anders als die, die zur Bereitstellung einer Website verwendet wird. Sie könnte mit Joomla inkompatibel sein. Verwenden Sie daher den vollständigen Pfad zu der PHP-Version, die Sie verwenden möchten, anstatt nur `php`.

*Übersetzt von openai.com*

