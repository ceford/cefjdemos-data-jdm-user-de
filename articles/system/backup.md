<!--
{
  "source": "https://docs.joomla.org/jdocmanual?manual=user&heading=system&filename=backup.md",
  "title": "Sicherung",
  "description": "", 
  "author": ""
}
-->

## Unfälle passieren!

Es fließt viel Zeit, Mühe und Geld in die Erstellung und Pflege einer Website. Schade, alles durch einen unvorhergesehenen Unfall zu verlieren. Die Sicherung ist für durchschnittliche Websites einfach. Große oder spezialisierte Websites benötigen wahrscheinlich speziellen Rat.

## Backup-Strategie

Joomla!-Websites bestehen aus zwei Teilen:

* Den **Dateien**, die sich im Stammverzeichnis-Baum von Joomla! befinden. Zwischen den Aktualisierungen ändern sich die Dateien möglicherweise nicht viel, da sie hauptsächlich mit dem Code zusammenhängen. Neue Bilder und Dokumente können hinzugefügt werden und eventuell Vorlagenüberschreibungen.
* Der **Datenbank**, die sich an einem anderen Ort auf dem Host-Server befindet. Die Datenbank enthält den Großteil des Website-Inhalts und kann sich stark ändern, wenn Benutzer Inhalte hinzufügen oder bearbeiten.

Jeder Website-Betreiber benötigt eine Strategie für die Wiederherstellung der Website im Falle einer Katastrophe. Häufiger Rat in den Foren ist, das **letzte Backup wiederherzustellen**. Entscheiden Sie also, was gesichert werden soll und wie oft.

Hosting-Dienste erstellen häufig **Snapshots** von Kundenwebsites und können möglicherweise eine Website auf ihren Zustand von gestern, letzter Woche oder letztem Monat zurücksetzen. Das könnte jedoch alles im Konto abdecken, wie E-Mails und andere Softwarepakete. Verlassen Sie sich nicht darauf, um eine Joomla-Website wiederherzustellen.

Dieser Beitrag beschreibt einige gängige **kostenlose** Methoden, um Joomla-Websites zu sichern. Sie könnten sich dafür entscheiden, für Backup-Tools und/oder -Dienste zu bezahlen, aber das wird hier nicht behandelt.

## Akeeba Backup

Wenn Sie das Administratormenü verwenden, um zu **System / Erweiterungen installieren / Vom Web installieren** zu navigieren, ist der erste Eintrag in der Liste *Akeeba Backup*. Es steht an erster Stelle, weil es die größte Anzahl positiver Bewertungen hat. Es versteht sich von selbst, dass es eine sehr lange Geschichte und einen tadellosen Ruf hat. Es gibt eine kostenlose Version und eine kostenpflichtige Version mit einigen zusätzlichen Features. Das ist ein gängiges Geschäftsmodell für Entwickler von Erweiterungen. Keine Sorge! Die kostenlose Version ist einfach zu bedienen, hat keine Ablenkungen und reicht für die meisten Websites aus. Was sie macht:

* Akeeba Backup analysiert Ihre Installation, um die optimalen Einstellungen zur Erstellung einer Sicherungsdatei zu bestimmen.
* Es erstellt eine zusammengesetzte Sicherungsdatei, die alle Website-Dateien und den Datenbankinhalt enthält.
* Es speichert zeitgestempelte Backups, die Sie verwalten, herunterladen oder bei Bedarf löschen können.
* Der Download ist eine .jpa-Datei. Es wird empfohlen, den Download mit FTP durchzuführen.
* Es gibt eine separate Akeeba Kickstart-Anwendung zum Entpacken der .jpa-Datei. Dies wird alles auf der Seite Akeeba Backups verwalten beschrieben.
* Nach dem Entpacken wird die Seite mit einem Akeeba Installer in einer Sequenz installiert, die einer Joomla-Installation ähnelt.
* Der Installer ändert die Konfiguration für die Wiederherstellung an einem anderen Ort und fordert die neuen Datenbankdetails an.

Das einzige Problem, das wahrscheinlich auftreten kann, ist, dass die Sicherungsdatei sehr groß sein kann und Sie möglicherweise Ihr Dateispeicherkontingent überschreiten, wenn Sie die Backups ansammeln lassen.

Probieren Sie es aus! Es kostet nichts und dauert Minuten statt Stunden.

## Host-Tools

Die meisten Hosting-Dienste bieten Backup-Tools an. Beispiel:

### cPanel

Auf der Seite **Tools** gibt es im Abschnitt *Dateien* einen *Backup*-Link. Die **Backup**-Seite hat drei Optionen:

* **Komplettes Backup:** Ein komplettes Backup erstellt ein Archiv all Ihrer Website-Dateien und Konfigurationen. Sie können diese Datei verwenden, um Ihr Konto auf einen anderen Server zu verschieben oder um eine lokale Kopie Ihrer Dateien aufzubewahren.
* **Teilweises Backup**
    - Herunterladen eines Home-Verzeichnis-Backups
    - Herunterladen eines Datenbank-Backups (mit einer Liste der Datenbanken)

Es gibt auch Optionen zum **Wiederherstellen** jeder dieser Backup-Typen. Möglicherweise stehen auch Optionen für automatische Backups zur Verfügung.

Einzelne Ordner können in diversen Formaten, die für den Download geeignet sind, mit dem cPanel-Dateimanager komprimiert werden. Eine Datenbank kann mit phpMyAdmin exportiert werden. Keine dieser Methoden wird hier behandelt.

## Lokale Werkzeuge

Es gibt Gelegenheiten, bei denen Sie ein Backup einer Website lokal auf einem Laptop oder Büro-Desktop-Computer erstellen müssen. Zum Beispiel möchten Sie möglicherweise eine Website von/zu einem Hosting-Dienst zu/von Ihrem lokalen Computer kopieren. Wenn Sie eine lokale Joomla-Installation haben, können Sie Akeeba Backup wie oben beschrieben verwenden. Andernfalls können Sie die Datenbank und Joomla-Dateien separat sichern.

### mysqldump

Wenn Sie MySQL verwenden, haben Sie wahrscheinlich das Befehlszeilentool *mysqldump* zur Verfügung. Probieren Sie diesen Befehl aus:

```bash
/usr/local/mysql/bin/mysqldump -u root -p dbname > ~/tmp/dbname-dump.sql
```
wobei `root` ein Benutzer ist, der Zugriff auf die Datenbank hat und `dbname` der Name der Datenbank ist, die Sie exportieren möchten. Möglicherweise werden Sie aufgefordert, das Passwort einzugeben.

Sie könnten die Ausgabe auch an einen zip- oder gzip-Befehl weiterleiten:
```bash
/usr/local/mysql/bin/mysqldump -u root -p dbname | gzip > ~/tmp/dbname-dump.sql.gz
```

### phpMyAdmin

Um die gleiche Aufgabe mit Ihrer lokalen Installation von phpMyAdmin durchzuführen, öffnen Sie diese und wählen Sie die Datenbank aus, die Sie exportieren möchten. Wählen Sie die **Exportieren** Schaltfläche oben auf dem Bildschirm. Standardmäßig verwendet der *Schnell*-Export SQL als Ausgabeformat. Wählen Sie die **Exportieren** Schaltfläche, um das auszuprobieren. Sie werden aufgefordert, eine Ausgabedatei zu benennen.

Wenn Sie die Option *Benutzerdefiniert* wählen, können Sie eine Kompressionsoption für die Ausgabe wählen, entweder keine, gezippt oder gzip-komprimiert. Versuchen Sie einen komprimierten Export und wählen Sie die **Exportieren** Schaltfläche.

Sie müssen die exportierte Datenbank **überprüfen**. Erstellen Sie eine neue Datenbank, vielleicht `animporttest`, damit sie oben in Ihrer Liste der Datenbanken ist. Mit der ausgewählten neuen leeren Datenbank verwenden Sie die **Importieren** Schaltfläche oben auf dem Bildschirm. Im Importformular **Durchsuchen** Sie, um die Datei zu finden, die Sie exportiert haben, und wählen Sie dann die **Importieren** Schaltfläche.

Es hat sich gelohnt, die **Überprüfung** durchzuführen. Der gzip-Export exportierte nur drei Tabellen. Der zip-Export funktionierte einwandfrei. Das wurde an den Größen der exportierten Dateien deutlich. Die zip-Datei war 4 Mb, aber die gzip-Datei nur 75 Kb. Da muss irgendwo ein Fehler sein!

### Zip und Gzip

Diese Befehlszeilentools sind ziemlich allgegenwärtig und werden oft innerhalb von grafischen Oberflächen verwendet. Zum Beispiel kann ich im Finder auf dem Mac ein Verzeichnis auswählen, das eine Joomla-Website enthält, mit der rechten Maustaste klicken und **Komprimieren** auswählen. Es dauert ein paar Sekunden, um ein Zip-Archiv zu erstellen, und es beeinträchtigt das Original nicht.

## Wiederherstellung eines Backups

Häufiger Rat aus den Joomla-Foren:

* Stellen Sie kein Backup über einer fehlerhaften Website wieder her.
* Leeren Sie Ihre Datenbank, indem Sie alle Tabellen löschen, oder erstellen Sie eine neue Datenbank und weisen Sie ihr einen Datenbankbenutzer zu.
* Löschen Sie alle Verzeichnisse und Dateien innerhalb Ihres Joomla-Stammverzeichnisses.

## Akeeba Quickstart

Wenn Sie Akeeba Backup verwendet haben, nutzen Sie Akeeba Quickstart, um Ihr Backup wiederherzustellen.
* Konsultieren Sie das [Video-Tutorial](http://akee.ba/abrestoreanywhere).
* Laden Sie Akeeba Quickstart (PDF 94Kb) kostenlos herunter.
* Prüfen Sie, ob die wiederhergestellte Website ordnungsgemäß funktioniert!

Akeeba Quickstart stellt sowohl die Datenbank als auch die Joomla-Dateien wieder her. Andere Methoden stellen die Datenbank und die Joomla-Dateien separat wieder her.

## Datenbank wiederherstellen

Wenn Sie über ein Datenbank-Backup verfügen, ist es am besten, Systemwerkzeuge zur Wiederherstellung zu verwenden. *phpMyAdmin* kann mittelgroße Datenbanken installieren, aber bei großen Datenbanken kann es zu Zeit- oder Speichermangel kommen.

Wenn Sie cPanel bei einem Hosting-Dienst verwenden, können Sie eine Datenbank über die Seite *Backup / Wiederherstellen* importieren. Dies wird hier nicht beschrieben.

Wenn Sie Zugriff auf die Kommandozeile haben, entweder bei einem Hosting-Dienst oder auf Ihrem lokalen Laptop oder Desktop-Computer, können Sie die `mysql` Kommandozeile verwenden, um den Import durchzuführen. Laden Sie das Datenbankarchiv an einen temporären Ort außerhalb Ihres Webverzeichnisses hoch und entpacken Sie es, sodass Sie eine Datei mit der Endung `.sql` haben. Verwenden Sie dann den folgenden Befehl:
```
mysql -u dbusername -p -D dbname < db_dump_file.sql
```
Ersetzen Sie `dbusername`, `dbname` und `db_dump_file.sql` durch die tatsächlichen Werte für Ihre Seite. Es kann sein, dass Sie nach einem Passwort für den Datenbank-Benutzernamen gefragt werden. Es kann eine Weile dauern, aber es sollte abgeschlossen werden.

## Dateien wiederherstellen

Dies ist einfach eine Frage des Entpackens der komprimierten Datei aus Ihrem letzten Backup. Außer dass es manchmal nicht so einfach ist. Abhängig von Ihrem Betriebssystem und der gewählten Methode könnten die archivierten Verzeichnisse und Dateien alle im aktuellen Verzeichnis oder einem neuen Verzeichnis erscheinen, oder Sie werden aufgefordert, ein Zielverzeichnis zu benennen. Bis Sie wissen, was Ihr System tut, ist es möglicherweise am besten, das Archiv in ein leeres Verzeichnis zu legen, es dort zu entpacken und dann das enthaltene Verzeichnis an seinen Bestimmungsort zu verschieben.

Einige Benutzer bevorzugen es, SFTP zu verwenden, um Dateien von den lokal extrahierten Archivdateien auf einen Hosting-Service hochzuladen. Es gibt Tausende von Dateien, daher ist dies ziemlich zeitaufwendig.

Im Stammverzeichnis Ihrer Website gibt es eine Datei namens `configuration.php`. Sie enthält den Datenbanknamen und die Zugangsdaten. Stellen Sie sicher, dass diese für Ihre wiederhergestellte Seite korrekt sind. Die Datei hat den Zugriffsberechtigungswert 444. Dieser muss auf 644 geändert werden, damit Sie alle notwendigen Bearbeitungen speichern können.

Wenn alles gut läuft, sollte Ihre wiederhergestellte Seite funktionieren und in dem Zustand sein, in dem sie beim Erstellen des Backups war.

## Eine Website kopieren

Es gibt mehrere gute Gründe, eine gesamte Website von einem Server auf einen anderen zu kopieren. Zum Beispiel empfehlen die Foren-Experten oft, dass Benutzer eine lokale Version einer Website auf einem Laptop oder Desktop-Computer für Testzwecke erstellen, wie das Ausprobieren neuer Erweiterungen oder Designs. Manchmal entscheidet sich eine Person aus Kosten- oder Leistungsgründen, zu einem neuen Hosting-Service zu wechseln.

Egal aus welchem Grund, der Vorgang ist relativ einfach: Machen Sie ein Backup der Originalseite und stellen Sie es auf der Zielseite wieder her. Es gibt einige Dinge, auf die man achten sollte:

* Stellen Sie sicher, dass der Zielhost die Mindestanforderungen an Joomla erfüllt. Das bedeutet normalerweise Server-, PHP- und Datenbankversionen.
* Nach der Installation kann es sein, dass einige wesentliche Module nicht aktiviert sind. Die meisten Hosting-Services beheben solche Probleme auf Anfrage.

