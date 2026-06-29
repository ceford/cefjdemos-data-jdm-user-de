<!--
{
  "source": "https://docs.joomla.org/Verifying_permissions",
  "title": "Dateiberechtigungen: Linux",
  "description": "", 
  "author": ""
}
-->

## Einführung

Die folgenden Informationen gelten für Linux-basierte Server. Wenn Ihr Webserver ein Microsoft Windows-basierter Server (IIS) ist, sollten Sie [Berechtigungen: Windows](jdocmanual?article=user/test-installations/permissions-windows) ansehen.

Abhängig von der Sicherheitskonfiguration Ihres Webservers sind die empfohlenen Standardberechtigungen:

- 755 für Verzeichnisse
- 644 für Dateien
- 444 für die `configuration.php` Datei (wenn eine Änderung der globalen Konfiguration gespeichert wird, ändert Joomla zunächst die Berechtigung auf 644, speichert die Änderung und setzt dann die Berechtigung wieder auf 444 zurück)

<div class="alert alert-warning">
Warnung!

Verwenden Sie niemals 777, es sei denn, Sie wissen, was Sie tun! Verwenden Sie keine Erweiterungen, die 777-Berechtigungen erfordern!
</div>

## So lokalisieren Sie die Berechtigungen

Es gibt verschiedene Methoden, um die Berechtigungen von Website-Dateien oder -Ordnern anzuzeigen und zu ändern. Der Dateibrowser im Hosting-Kontrollpanel oder ein allgemeines [File Transfer Protocol (FTP)](https://de.wikipedia.org/wiki/File_Transfer_Protocol)-Programm sollte jeweils eine Methode bieten, um Dateiberechtigungen und Ordnerberechtigungen anzuzeigen und zu ändern. Die Befehlszeile eignet sich für diejenigen, die Terminalzugriff und Vertrautheit mit Systembefehlen haben.

Abhängig davon, was Sie verwenden, sollten Sie etwas sehen, das diesem Bild eines Teils des Joomla-Wurzel-Dateisystems in cPanel ähnelt:

![Berechtigungen in cPanel überprüfen](../../../en/images/test-installations/permissions-linux/01-verifying-permissions-cpanel.png)

Die Berechtigungen befinden sich ganz rechts und werden von einer Null vorangestellt, um zu zeigen, dass es sich um oktale Zahlen handelt. Es sollte ein Formular vorhanden sein, um die Berechtigungen eines oder mehrerer ausgewählter Elemente zu ändern:

![Berechtigungen in cPanel ändern](../../../en/images/test-installations/permissions-linux/02-verifying-permissions-cpanel-change.png)

In einem Terminalfenster werden Datei- und Ordnerberechtigungen als Buchstabengruppen anstelle von Zahlen angezeigt (das führende `d` zeigt an, dass das Element ein Verzeichnis ist):

```sh
drwxr-xr-x   20 ceford  staff     640 14 Okt 22:23 components
-r--r--r--    1 ceford  staff    3485 27 Okt 06:56 configuration.php
drwxr-xr-x    2 ceford  staff      64 20 Okt 14:21 files
-rw-r--r--    1 ceford  staff    6899 30 Sep 09:27 htaccess.txt
drwxr-xr-x   15 ceford  staff     480 24 Okt 12:19 images
```

## Berechtigungszahlen

In einer Berechtigungsanzeige der Form 777 entspricht jede Oktalzahl drei Buchstaben für drei verschiedene Benutzergruppen:

- Erste Ziffer = Besitzer (der Besitzer des Elements - `ceford` in der obigen Befehlszeilenliste)
- Zweite Ziffer = Gruppe (die Gruppe, die Zugriff hat - `staff` in der obigen Liste)
- Dritte Ziffer = andere (alle anderen auf diesem Computer)

## Bedeutung der Zahlen

Jede oktale Ziffer ist die Summe der erteilten Berechtigungen:
```sh
     r = Lesen    = 4
     w = Schreiben = 2
     x = Ausführen = 1
```
Addieren Sie die Zahlen für jede erforderliche Berechtigung einer bestimmten Benutzergruppe:

| "Oktal" \# | (r)ead | (w)rite | e(x)ecute | Benutzer oder Gruppe oder Andere |
|------------|--------|---------|-----------|----------------------------------|
| 0          | nein   | nein    | nein      | `---` 0+0+0 = 0                  |
| 1          | nein   | nein    | ja        | `--x` 0+0+1 = 1                  |
| 2          | nein   | ja      | nein      | `-w-` 0+2+0 = 2                  |
| 3          | nein   | ja      | ja        | `-wx` 0+2+1 = 3                  |
| 4          | ja     | nein    | nein      | `r--` 4+0+0 = 4                  |
| 5          | ja     | nein    | ja        | `r-x` 4+0+1 = 5                  |
| 6          | ja     | ja      | nein      | `rw-` 4+2+0 = 6                  |
| 7          | ja     | ja      | ja        | `rwx` 4+2+1 = 7                  |


## Beispiele

- 755 bedeutet rwx (Besitzer), r-x (Gruppe) und r-x (andere) oder mit anderen Worten, jeder darf lesen und ausführen (starten), aber nur der Besitzer (Sie) darf Änderungen an der Datei vornehmen. Es würde so aussehen, wenn es alles zusammengefügt wird: `-rwxr-xr-x`. Dies ist die normale Einstellung für Ordner.
- 644 ist rw-, r--, r-- oder JEDER kann die Datei lesen, aber nur der Besitzer darf in die Datei schreiben oder `-rw-r--r--`. Dies ist die normale Einstellung für Dateien.
- 777 oder `-rwxrwxrwx` bedeutet, dass JEDER jede Datei lesen, schreiben und ausführen kann.
  <div class="alert alert-warning">
  Dies ist etwas, das Sie auf Ihrem Server/Website **NIEMALS** erlauben möchten, es sei denn, Sie sind absolut sicher, dass Sie wissen, was Sie tun.
  </div>

Berechtigungen werden sowohl für Verzeichnisse als auch für Dateien verwendet, weshalb Sie möglicherweise dies `drwxr-xr-x` sehen, wobei das `d` für Verzeichnis steht.

Für eine vollständige Erklärung lesen Sie den Wikipedia-Beitrag über 
[Dateisystemrechte](https://en.wikipedia.org/wiki/Filesystem_permissions) 

*Übersetzt von openai.com*

