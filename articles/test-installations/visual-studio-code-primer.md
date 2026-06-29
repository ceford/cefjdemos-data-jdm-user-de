<!--
{
  "source": "https://docs.joomla.org/Visual_Studio_Code_Primer",
  "title": "Visual Studio Code Einführung",
  "description": "", 
  "author": ""
}
-->

## VS Code - Eine Beliebte Kostenlose IDE

Aus Wikipedia:

> Visual Studio Code, auch allgemein bekannt als VS Code, ist ein
> Quelltext-Editor, der von Microsoft für Windows, Linux und macOS
> entwickelt wurde. Zu den Funktionen gehören Unterstützung beim Debugging,
> Syntaxhervorhebung, intelligente Codevervollständigung, Snippets,
> Code-Refaktorisierung und eingebettetes Git. Nutzer können das Thema,
> Tastenkombinationen, Einstellungen ändern und Erweiterungen installieren,
> die zusätzliche Funktionalitäten hinzufügen.

## Installation

Die Standardseite der VS Code-Website hat eine Dropdown-Liste für jede unterstützte Plattform. Es ist sehr wahrscheinlich, dass Ihre Plattform bereits vorausgewählt ist. Laden Sie also herunter und installieren Sie, und Sie sind startklar.

### Erste Schritte

Die *Erste Schritte* Seite von VS Code enthält einige *Start*-Elemente, eine Liste von *Zuletzt* genutzten Elementen und eine kurze Liste von *Erläuterungen*. Wenn Sie komplett neu bei VS Code sind, wird empfohlen, diese anzuschauen. Sie dauern nur ein paar Minuten.

Die Dokumentation von VS Code ist über das Menü *Hilfe / Dokumentation* verfügbar. Die [Einführungsvideos](https://code.visualstudio.com/docs/getstarted/introvideos) sind sehr sehenswert. Jedes dauert 2 bis 6 Minuten und gibt eine ausgezeichnete Einführung in die Funktionen von VS Code.

Die offizielle Dokumentation ist der richtige Ort, wenn Sie spezifische Informationen nachschlagen möchten.

### VS Code-Erweiterungen

VS Code kann für jede Art von Text verwendet werden, einschließlich einer Vielzahl von Programmiersprachen. Es funktioniert mit JavaScript ohne Erweiterungen. Andere Sprachen werden kontextabhängig erkannt, sodass Sie wahrscheinlich aufgefordert werden, ein PHP-Supportpaket zu installieren, wenn Sie PHP-Code erstellen und speichern.

Klicken Sie auf das *Erweiterungen*-Symbol in der linken *Aktivitätsleiste*, um zu sehen, was Sie installiert haben und was empfohlen wird. Sie benötigen die PHP Debug-Erweiterung!

### Das Bildschirm-Layout von VS Code

Einige Begriffe, die in den folgenden Anweisungen verwendet werden:

- **Aktivitätsleiste** die schmale Leiste auf der linken Seite des Bildschirms. Wählen Sie ein beliebiges Symbol, um die Haupt-Sidebar zu öffnen oder zu schließen.
- **Haupt-Sidebar** zeigt im geöffneten Zustand Details der ausgewählten Aktivität an.
- **Statusleiste** am unteren Rand des Bildschirms. Sie zeigt an, was vor sich geht.
- **Panel** ein Bereich unterhalb der Texteditoren, um andere Informationen anzuzeigen.

Wählen Sie ein Layoutsymbol oben rechts aus, um eines dieser Elemente zu öffnen oder zu schließen.

## Codierung einer Joomla-Erweiterung

Um eine Erweiterung zu erstellen, ist Ihr Ziel, eine ZIP-Datei zu erstellen, die Sie auf einer funktionierenden Joomla-Website installieren können. Daher benötigen Sie einen Ordner, der Ihren Code enthält. Dieser sollte sich im persönlichen Dateibereich auf Ihrem Laptop oder Desktop-Computer für die lokale Entwicklung befinden. Er sollte nicht im Verzeichnisbaum Ihrer Website sein. Zum Beispiel könnten Sie *~/jextensions* verwenden, um Unterordner für verschiedene Erweiterungen zu speichern. Ich verwende *~/git*, weil es kurz und einfach zu buchstabieren ist, obwohl es potenziell verwirrend ist, da jeder Unterordner ein eigenes Git-Repository nutzt.

### Beispielcode

Wenn Sie Beispielcode benötigen, an dem Sie arbeiten können, gibt es eine Erweiterung auf GitHub namens *mod_debugme*. Wie der Name schon sagt, handelt es sich um ein Modul mit einigen Bugs. Zusätzlich zum Modulcode gibt es eine *build.xml*-Datei, die eine Möglichkeit zeigt, das Erstellen für Tests und das Erstellen einer ZIP-Datei zu automatisieren.

Das Modul ist dafür ausgelegt, die nächsten paar (standardmäßig 3) Ereignisse (Geburtstage) aus einer Liste anzuzeigen, die in einer Datenbanktabelle gespeichert ist. Sie könnten sich vorstellen, dass dies in einer Büro- oder Familienwebsite verwendet wird, in der Erwartung von Kuchen.

Es ist möglicherweise am besten, mit Git-Befehlen über die Kommandozeile zu arbeiten. Erstellen Sie zuerst einen Ordner für Ihren Code und klonen Sie dann das Remote-Repository:
```sh
    mkdir ~/git
    cd ~/git
    git clone https://github.com/ceford/j4xdemos-mod-debugme
```
Die Antwort sollte nur ein paar Sekunden dauern:
```sh
    Cloning into 'j4xdemos-mod-debugme'...
    remote: Enumerating objects: 23, done.
    remote: Counting objects: 100% (23/23), done.
    remote: Compressing objects: 100% (16/16), done.
    remote: Total 23 (delta 3), reused 23 (delta 3), pack-reused 0
    Unpacking objects: 100% (23/23), done.
```
Sie sollten sich einen Moment Zeit nehmen, um sich den Inhalt des Ordners anzusehen:
```sh
    cd j4xdemos-mod-debugme
    ls -al
    total 16
    drwxr-xr-x   6 ceford  staff   192  2 Sep 17:48 .
    drwxr-xr-x   3 ceford  staff    96  2 Sep 17:48 ..
    drwxr-xr-x  12 ceford  staff   384  2 Sep 17:48 .git
    -rw-r--r--   1 ceford  staff  1402  2 Sep 17:48 README.md
    -rw-r--r--   1 ceford  staff   927  2 Sep 17:48 build.xml
    drwxr-xr-x   8 ceford  staff   256  2 Sep 17:48 mod_debugme
```
Der *.git*-Ordner enthält Informationen über das Repository. Die *README.md*-Datei ist ein Markdown-Dokument, das dieses Repository beschreibt. Die *build.xml*-Datei wird verwendet, um die Erweiterung mit einem externen Tool, Phing - später beschrieben, zu erstellen. Der *mod_debugme*-Ordner enthält den Code der Erweiterung.

### Installation in Joomla

Komprimieren Sie den Erweiterungsordner, um eine installierbare ZIP-Datei zu erstellen:
```sh
    zip -r mod_debugme.zip mod_debugme
```
Sie können jetzt die ZIP-Datei auf der Joomla-Site installieren, die Sie für Tests verwenden. Nach der Installation müssen Sie ein Website-Modul erstellen und es einem Modulposition zuweisen. Da es sich um ein fehlerhaftes Modul handelt, könnten Sie es auf *Alle Seiten* zuweisen, während Sie daran arbeiten; oder Sie könnten es auf eine einzelne Seite zuweisen; oder Sie könnten es in einem Beitrag positionieren, der einen eigenen Menüpunkt hat.

Nach der Installation die ZIP-Datei löschen.

### Debug-Modus aktivieren

Setzen Sie in der globalen Konfiguration von Joomla *Debug System* auf *Ja* und *Fehlermeldungen* auf *Maximal*.

Wenn Sie eine Seite öffnen, die das fehlerhafte Modul enthält, sehen Sie eine Stack-Trace, die Ihnen zeigt, wo ein Fehler ausgelöst wurde.

![vscode stack trace](../../../en/images/test-installations/visual-studio-code-primer/01-vscode-primer-stack-trace.png)

Manchmal befindet sich der Programmierfehler auf der ersten Zeile des Stack-Traces. Andernfalls, wenn der Fehler in Bibliothekscode ausgelöst wird, zum Beispiel durch das Übergeben ungültiger Daten an eine Datenbankfunktion, kann der Programmierfehler weiter unten in der Liste der Funktionsaufrufe liegen.

## Erweiterungsordner in VS Code öffnen

In VS Code nutzen Sie den Menüpunkt Datei / Ordner öffnen, um den Ordner zu finden und zu öffnen, der Ihre lokale Kopie des *mod_debugme* Erweiterungscodes enthält. Sie sollten etwas Ähnliches wie das Folgende sehen:

![vscode Ordneransicht](../../../en/images/test-installations/visual-studio-code-primer/02-vscode-primer-screen.png)

Möglicherweise können Sie das Problem nur durch das Lesen des Codes diagnostizieren. Im Falle des Fehlers *Klasse "DebugHelper" nicht gefunden* werden Sie sehen, dass eine *use*-Anweisung einige Zeilen zuvor auskommentiert wurde. Das Vergessen, eine *use*-Anweisung einzufügen, ist ein häufiger Fehler während der anfänglichen Entwicklung!

Beheben Sie dieses Problem und komprimieren und installieren Sie das Modul erneut. Dieser Schritt wird etwas mühsam, wenn Sie mehrere Probleme haben. Hier kommen Build-Tools nützlich ins Spiel.

## Phing

Phing ist ein Kommandozeilen-Tool, das für alle Plattformen verfügbar ist und zur Erstellung von Softwarepaketen dient, indem Anweisungen aus einer XML-Datei, die standardmäßig build.xml heißt, verwendet werden. Bei der Arbeit mit Erweiterungscode kann es für zwei Dinge verwendet werden:

- Geänderte Dateien aus Ihrem Erweiterungs-Quellordner an die richtigen Stellen in Ihrem Website-Ordner kopieren.
- Eine neue ZIP-Datei für neue Installationen erzeugen.

Laden Sie Phing herunter und installieren Sie es. Andere Build-Tools sind ebenfalls verfügbar! Sie können Phing in Ihrem eigenen Bin-Ordner oder in einem System-Bin-Ordner installieren. Sie müssen den Pfad zu Ihrem Phing-Code notieren. In diesem Beispiel ist es *~/bin/phing-latest.phar*. Sie können es von der Kommandozeile ausprobieren, nachdem Sie in den Ordner mit Ihrem Erweiterungscode gewechselt sind:
```sh
    cd ~/git/j4xdemos-mod-debugme
    php ~/bin/phing-latest.phar
```
Antwort:
```sh
    Buildfile: /Users/ceford/git/j4xdemos-mod-debugme/build.xml

    mod_debugme > main:
          ... Alle kopierten Dateien werden hier erwähnt
          [zip] Erstellung von ZIP: /Users/ceford/zips/mod_debugme.zip

    BUILD ABGESCHLOSSEN

    Gesamtzeit: 0,0863 Sekunden
```

## VS Code Aufgaben

Um Phing innerhalb von VS Code auszuführen, müssen Sie eine *tasks.json*-Datei im *.vscode*-Ordner im Stammverzeichnis des *j4xdemos-mod-debugme*-Ordners erstellen. Falls Letzterer nicht existiert, erstellen Sie ihn zuerst. Erstellen Sie dann die *tasks.json*-Datei und geben Sie den folgenden Code ein:
```json
    {
        // Siehe https://go.microsoft.com/fwlink/?LinkId=733558
        // für die Dokumentation zum tasks.json-Format
        "version": "2.0.0",
        "tasks": [
          {
            "label": "Build mod_debugme",
            "type": "shell",
            "command": "php ~/bin/phing-latest.phar",
            "windows": {
              "command": "php ~/bin/phing-latest.phar"
            },
            "group": "build",
            "presentation": {
              "reveal": "always",
              "panel": "shared"
            }
          }
        ]
    }
```
Windows-Nutzer müssen den Windows-spezifischen Befehl anpassen. Sie können die Erweiterung jetzt über das Menü *Terminal / Build-Aufgabe ausführen* erstellen. Das Ergebnis des Befehls sollte im Terminal-Panel unterhalb des Bearbeitungsbereichs erscheinen.
```sh
      *  Aufgabe ausführen: php ~/bin/phing-latest.phar

    Build-Datei: /Users/ceford/git/gitdemo/j4xdemos-mod-debugme/build.xml

    mod_debugme > main:

          [zip] Nichts zu tun: /Users/ceford/zips/mod_debugme.zip ist aktuell.

    BUILD ABGESCHLOSSEN

    Gesamtzeit: 0,1031 Sekunden

     *  Terminal wird von Aufgaben wiederverwendet, drücken Sie eine Taste, um es zu schließen.
```
Es können unverständliche Fehlermeldungen auftreten. Der wahrscheinlichste Grund ist, dass ungültige Pfade zu Ordnern in der *build.xml*-Datei vorhanden sind oder ein Ordner nicht erstellt wurde. Nur ein weiteres Problem zum Debuggen!

## Debugging

Den ersten Fehler sollten Sie durch Code-Inspektion beheben können. Kompliziertere Probleme erfordern ein Durchlaufen des Codes mit dem Debugger. Dadurch können Sie Variablen überprüfen, um zu sehen, ob sie die erwarteten Werte enthalten, beispielsweise beim Übergeben von Argumenten an Bibliotheksfunktionen.

### *php.ini* Einstellungen

Um Debugging mit Xdebug einzurichten, müssen Sie einige Einträge am Anfang Ihrer *php.ini*-Datei vornehmen.
```ini
    zend_extension="xdebug.so"
    xdebug.mode="debug"
    xdebug.client_port=9003
    xdebug.start_with_request = yes
```
Nach dem Speichern der Änderungen starten Sie Ihren Apache-Server neu.

### Website-Fenster hinzufügen

Ihr Erweiterungsordner enthält nur wenige Dateien, die ***Quellen*** der in Ihrer Website installierten Dateien. Laufzeit-Debugging erfordert das Setzen von Haltepunkten in Ihren ***Site***-Dateien, daher benötigen Sie Zugriff auf diese Dateien. Sie könnten das Menü *Datei / Ordner zum Arbeitsbereich hinzufügen...* verwenden, um den Site-Ordner zu Ihrem Arbeitsbereich hinzuzufügen. Es besteht jedoch eine sehr große Wahrscheinlichkeit, dass Sie Änderungen an Site-Dateien statt an Quelldateien vornehmen. Daher ist es wahrscheinlich am besten, ein separates VS Code-Fenster für das Debuggen zu öffnen.

- **Neues Fenster öffnen:** Wählen Sie im VS Code-Menü *Datei / Neues Fenster* und wählen Sie den Ordner aus, der Ihre Joomla-Website enthält.
- **Ordner öffnen:** Wählen Sie im neu geöffneten Fenster *Datei / Ordner öffnen...* im VS Code-Menü. Suchen und wählen Sie Ihren Website-Ordner. Sie sollten eine Liste aller Dateien in Ihrer Joomla-Website in der Primärleiste sehen.

### Startkonfiguration

Damit das Debugging in VS Code funktioniert, benötigen Sie eine Startkonfiguration. Erstellen Sie im Stammverzeichnis Ihrer Website einen Ordner mit dem Namen *.vscode* (beachten Sie den führenden Punkt), der eine Datei mit dem Namen *launch.json* mit folgendem Inhalt enthält:
```json
    {
        "configurations": [
            {
                "name": "Listen for XDebug",
                "type": "php",
                "request": "launch",
                "hostname": "0.0.0.0",
                "port": 9003,
                "stopOnEntry": true,
                "pathMappings": {
                    "/Users/ceford/Sites/j421rc2": "${workspaceFolder}"
                }
            }
        ]
    }
```
Denken Sie daran, den pathMappings-Eintrag in diesem Beispiel durch die tatsächlichen pathMappings auf Ihrer Website zu ersetzen. Der stopOnEntry-Eintrag wird die Ausführung an der allerersten Zeile des ausgeführten PHP-Codes unterbrechen.

### Debuggen von *mod_debugme*

Nun sind Sie bereit, die Fehler im installierten Modul zu finden und zu beheben.

- **Modulcode finden:** Finden Sie den ersten Fehler in Zeile 16 von JROOT/modules/mod_debugme/mod_debugme.php.
- **Haltepunkt setzen:** Klicken Sie in den Bereich links neben der Nummer 16. Ein blasser roter Punkt erscheint, wenn Sie mit der Maus über ihn fahren, und wird nach dem Klicken vollständig rot, um anzuzeigen, dass ein Haltepunkt gesetzt wurde.
- **Debugging starten:** Wählen Sie im VS Code-Menü *Ausführen / Debugging starten*. Laden Sie Ihre Site im Browser neu. Ihr VS Code-Fenster sollte mit dem gestoppten Code an der ersten Zeile der Site *index.php*-Datei wieder erscheinen. Am oberen Bildschirmrand befinden sich einige Symbole, um den Debug-Prozess zu steuern. Sie sollten selbsterklärend sein. Wenn nicht, schauen Sie in der VS Code-Hilfe/ Dokumentation nach.
- **Fortfahren:** Wählen Sie die Fortsetzen-Schaltfläche - der Code läuft bis zu Ihrem ersten Haltepunkt. Untersuchen Sie den Code, um zu sehen, wo das Problem liegt.
- **Hover:** Wenn Sie mit der Maus über eine Variable fahren, der ein Wert zugewiesen wurde, erscheint ein kleines Tooltip, das die Attribute dieser Variable zusammenfasst. Es gibt kein Tooltip für Variablen, denen keine Werte zugewiesen wurden.
- **Variablen:** Die linke Spalte enthält mehr Informationen über den Status des Codes am Haltepunkt. Es gibt zu viele, um hier alle zu behandeln. Erforschen Sie sie nach Bedarf!
- **Debugging beenden:** Am besten wählen Sie das Fortsetzen-Symbol, sonst wird die Webseite leer ausgeliefert. Alternativ könnten Sie die Stop-Schaltfläche oder das Menü Ausführen / Debugging stoppen verwenden.

### Einen Fehler beheben

**Erinnerung:** Beheben Sie den Fehler nicht im Website-Code! Beheben Sie ihn im Quellcode!

Beheben Sie den Quellcode und verwenden Sie dann *Terminal / Build-Aufgabe ausführen...*.

Starten Sie das Debugging neu.

### Tipps

Einige weniger offensichtlich Probleme:

- Sie beheben den ersten Fehler, aber er stürzt immer noch an dieser Zeile ab. Schauen Sie in die mod_debugme.xml, um zu sehen, wo der src von Namespaced-Klassen definiert ist. Wenn es im Quellcode behoben wurde, müssen Sie die Zip-Datei neu installieren oder *administrator/cache/autoload_psr4.php* löschen. Wenn sie abwesend ist, baut Joomla diese Datei aus den Manifestdateien neu auf. Aber wenn es einen falschen oder fehlenden Eintrag gibt, wird dieser nicht korrigiert, bis die Erweiterung neu installiert wird.
- Manchmal müssen Sie ein paar Zeilen vor dem Fehler einen Haltepunkt setzen, besonders wenn Sie Werte überprüfen möchten, die an Funktionsaufrufe übergeben werden.
- Tabelle *xxx.yyy\\debugme* existiert nicht. Ah ja, der Code zum Erstellen einer Tabelle bei der Installation und zum Entfernen bei der Deinstallation wurde nie erstellt. Sie müssen eine SQL-Abfrage in phpMyAdmin mit dem Inhalt der Datei *mod\\debugme.sql* ausführen. Denken Sie daran, *\#\\* in den Tabellennamen für Ihr Datenbankpräfix zu ändern. Und wenn es immer noch fehlschlägt, überprüfen Sie den Tabellennamen im Code.

## Screenshot

Wenn alles behoben ist, könnte dies folgendermaßen aussehen:

![vscode debugged module site view](../../../en/images/test-installations/visual-studio-code-primer/03-vscode-primer-debugme-fixed.png)

Kuchentage?

## Referenzen

Aus der Joomla!-Dokumentation: [Visual Studio Code](https://docs.joomla.org/Visual_Studio_Code) behandelt auch die Konfiguration anderer Werkzeuge, zum Beispiel CodeSniffer und PHPUnit.

*Übersetzt von openai.com*

