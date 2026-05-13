<!--
{
  "source": "https://docs.joomla.org/How_do_UNIX_file_permissions_work%3F",
  "title": "UNIX-Dateiberechtigungen ",
  "description": "", 
  "author": ""
}
-->

Unix/Linux-Dateiberechtigungen können verwirrend sein. Die grundlegenden UNIX-Berechtigungen gibt es in drei Varianten:

    Besitzerberechtigungen: Kontrollieren Sie den Zugriff auf Ihre eigenen Dateien.
    Gruppenberechtigungen: Kontrollieren Sie den Zugriff für Sie und alle in Ihrer Gruppe.
    Andere Berechtigungen: Kontrollieren Sie den Zugriff für alle anderen.

In Unix können Sie, wenn Berechtigungen konfiguriert sind, dem Server erlauben, unterschiedliche Berechtigungen für jede dieser drei Benutzerkategorien festzulegen. In einer Webserver-Umgebung werden Berechtigungen verwendet, um zu kontrollieren, welche Website-Besitzer auf welche Verzeichnisse und Dateien zugreifen können.

## Wie sehen Unix-Berechtigungen aus?

Wenn Sie Ihre Dateien über die Befehlszeile mit dem Unix-Befehl `ls -l` anzeigen, sehen Sie Zeilen wie die folgenden, eine für jede Datei und jedes Verzeichnis:
```
drwxr-xr-x@  7 benutzername  benutzergruppe   224 13 Feb 10:48 includes
-rw-r--r--@  1 benutzername  benutzergruppe  1060 13 Apr 21:00 index.php
```
Erklärung:
* Das erste Zeichen in der Zeile ist ein d für Verzeichnis oder - für Datei, oder ...
* Die nächsten 9 Zeichen sind 3 Gruppen von 3 Zeichen, die für Lesen (r), Schreiben (w) und Ausführen (x) stehen oder ein Minuszeichen (-), was keinen Zugang für Eigentümer, Gruppe und Andere bedeutet.
* Das @-Zeichen ist eines von mehreren möglichen erweiterten Attributen,
* Die Zahl vor dem Benutzernamen ist die Verzeichnistiefe.
* Die zwei Namen sind der Besitzer-Benutzername und die Benutzergruppe,
* Die folgende Ganzzahl ist die Dateigröße in Bytes.
* Das folgende Datum enthält die Uhrzeit für aktuelle Objekte oder das Jahr für ältere Objekte.
* Zuletzt ist der Datei- oder Verzeichnisname.

In einem FTP-Utilität kann die Reihenfolge anders sein und es kann mehr oder weniger Informationen geben.

### Eigentümer (Benutzer) bezieht sich auf den Benutzernamen

Der Eigentümer (Benutzer) ist normalerweise Sie, diese Berechtigungen werden auf Ihrem Hosting-Konto durchgesetzt.

### Gruppe bezieht sich auf die Benutzergruppe

Die Gruppenberechtigungen werden für andere Personen durchgesetzt, die sich in derselben Gruppe wie Sie befinden. Innerhalb einer Hosting-Umgebung gibt es sehr selten andere Personen in derselben Gruppe wie Sie. Dies schützt Ihre Dateien und Verzeichnisse davor, für jemanden anderen verfügbar gemacht zu werden, der möglicherweise auch ein Hosting-Konto auf demselben Server hat.

### Andere bezieht sich auf alle anderen

Die Berechtigungen für Andere werden für alle anderen auf dem Server durchgesetzt, die weder Sie sind noch zu Ihrer Gruppe gehören. In einer Webserver-Umgebung bedeutet das, dass dies für alle gilt, die den Server betreten, außer für Sie. Jede der drei Berechtigungsgruppen wird wie folgt definiert:

    r = Lese-Berechtigungen
    w = Schreib-Berechtigungen
    x = Ausführungs-Berechtigungen

    Eigentümer Gruppe Andere
    r w x r w x r w x

Wie viele von Ihnen bereits wissen, werden Berechtigungen normalerweise als numerischer Wert ausgedrückt, etwas wie 755 oder 644. Also, wie verhält sich das zu dem, was wir oben diskutiert haben? Jedes Zeichen der Berechtigungen wird einem numerischen Wert zugeordnet, dieser wird für jede Gruppe von drei Zeichen zugewiesen, sodass wir nur drei Werte verwenden und für jede Gruppe wiederverwenden müssen.

    Eigentümer Gruppe Andere
    r w x r w x r w x
    4 2 1 4 2 1 4 2 1

Jetzt, da wir einen Wert haben, der jede Berechtigung repräsentiert, können wir sie in numerischer Form ausdrücken. Die Werte werden in den jeweiligen Gruppierungen von 3 einfach zusammenaddiert, was uns schließlich nur drei Zahlen ergibt, die uns mitteilen, welche Berechtigungen festgelegt werden. Wenn uns gesagt wird, dass eine Datei die Berechtigungen 777 hat, würde dies bedeuten, dass Folgendes zutrifft.

    Eigentümer Gruppe Andere
    r w x r w x r w x
    4 2 1 4 2 1 4 2 1

Also...

      4+2+1 4+2+1 4+2+1
    =   7     7     7

Der Eigentümer der Datei hätte volle Lese-, Schreib- und Ausführungs-Berechtigungen, die Gruppe hätte ebenfalls volle Lese-, Schreib- und Ausführungs-Berechtigungen, und der Rest der Welt könnte die Datei ebenfalls lesen, schreiben und ausführen. Die standardmäßigen, vorgegebenen Berechtigungen, die vom Server Dateien und Verzeichnissen zugewiesen werden, sind normalerweise:

    Dateien = 644
    Verzeichnisse = 755

Diese Berechtigungen würden für Dateien Folgendes erlauben:

    644 = rw- r-- r--
    Eigentümer hat Lesen und Schreiben
    Gruppe hat nur Lesen
    Andere haben nur Lesen

und für Verzeichnisse:

    755 = rwx r-x r-x
    Eigentümer hat Lese-, Schreib- und Ausführungs-Berechtigungen
    Gruppe hat nur Lese- und Ausführungs-Berechtigungen
    Andere haben nur Lese- und Ausführungs-Berechtigungen

Die Dinge können ein wenig kompliziert werden, wenn wir anfangen über geteilte Webserver zu sprechen. Die Webserver-Software läuft mit ihrem eigenen Benutzernamen und Gruppennamen, die meisten Server sind so konfiguriert, dass sie entweder "apache" und "apache" oder "nobody" und "nobody" als Benutzername und Gruppenname verwenden. Hier liegt das Problem. Ihr Webserver läuft als eigener Benutzer, und dieser Benutzer sind nicht Sie oder in Ihrer Gruppe, also gelten die ersten beiden Berechtigungsgruppen nicht für ihn. Nur die Welt (andere) Berechtigungen gelten. Daher, wenn Sie eine Berechtigungsgruppe ähnlich wie 640 auf Ihre Website-Dateien konfigurieren, kann Ihr Webserver Ihre Website-Dateien nicht ausführen.

    640 = rw- r-- ---
    Eigentümer hat Lesen und Schreiben
    Gruppe hat nur Lesen
    Andere haben keine Rechte

Der Webserver erhält keine Berechtigungen und kann nicht ausführen, schreiben oder, noch wichtiger, die Datei lesen, um deren Inhalt an den Browser eines Website-Besuchers auszuliefern. Wenn ein Verzeichnis mit 750-Berechtigungen zugewiesen würde, hätte dies denselben Effekt, weil der Webserver dann nicht einmal Berechtigungen hat, Dateien im Verzeichnis zu lesen, selbst wenn die Dateien innerhalb dieses Verzeichnisses günstige Berechtigungen hätten.

    750 = rw- r-x ---
    Eigentümer hat Lesen und Schreiben
    Gruppe hat Lesen und Ausführen
    Andere haben keine Rechte

Verzeichnisse haben eine zusätzliche Eigenart: Wenn ein Verzeichnis im Welt-Set nicht die Ausführungs-Berechtigung gesetzt hat, dann kann, selbst wenn Lesen und Schreiben gesetzt sind, das Programm nicht die Dateien im Verzeichnis ausführen, es sei denn, es wird als Benutzer oder Gruppe ausgeführt. Die Ausführungs-Einstellung erlaubt es dem Programm, Befehle im Verzeichnis auszuführen, sodass ohne sie das Programm (in unserem Fall ein Webserver) den "Lesen"-Befehl nicht ausführen und somit Ihre Datei nicht an den Webbrowser der Benutzer ausliefern kann.

## Wie hängt das mit Joomla! zusammen?

Gute Frage. Zunächst einmal wäre dies während des Web-Installationsprozesses wichtig. Wenn Sie sich daran erinnern, als Sie den Joomla!-Web-Installer ausgeführt haben, haben wir nach bestimmten Verzeichnissen gesucht, die als beschreibbar festgelegt werden sollten. Wir sehen eine Vielzahl von Beiträgen, in denen entweder Probleme bei der Installation mit Berechtigungen gemeldet werden oder nach empfohlenen Berechtigungen gefragt wird. Einige halten die Meldung, die nach "Beschreibbar"-Berechtigungen fragt, sogar für zu vage.

Leider weiß der Web-Installer nicht, wie Ihr Server konfiguriert ist, daher kann er nicht spezifischer sein. Sobald Sie jedoch die Berechtigungseinstellungen verstehen und ein wenig über Web-Hosting-Umgebungen wissen, werden Sie feststellen, dass der Begriff *beschreibbar* tatsächlich sehr spezifisch und mehr als ausreichend ist, um zu beschreiben, was Joomla! benötigt. Den obigen Informationen nachdenkend, erinnern Sie sich vielleicht, dass es drei Stellen gibt, an denen *Schreib*-Berechtigungen festgelegt werden können:

    Besitzer beschreibbar
    Gruppe beschreibbar
    Andere beschreibbar

Denken Sie auch daran, dass der Webserver im Allgemeinen nicht als Ihr eigener Benutzer oder in derselben Gruppe ausgeführt wird. Wenn Sie den Web-Installer aus einem Browser ausführen, versucht der Webserver, auf die Dateien zuzugreifen, daher gelten hierfür die "Anderen"-Berechtigungen. Wenn die "Anderen"-Berechtigungen dem Web-Server nicht erlauben, Lese-, Schreib- oder Ausführungskommandos in den Joomla!-Verzeichnissen auszuführen, erhalten Sie die Meldung, dass die Verzeichnisse nicht *beschreibbar* sind.

In diesem Fall müssen Sie die "Anderen"-Berechtigungen auf "7" für die im Web-Installer aufgeführten Verzeichnisse konfigurieren. Ihre Gesamtberechtigungen könnten also so etwas wie 757 sein, im schlimmsten Fall müssten Sie möglicherweise auf 777 einstellen. Diese sehr offenen Berechtigungen können nach dem Ausführen des Installers auf 755 zurückgesetzt werden, um die Sicherheit Ihrer Verzeichnisse und Dateien zu unterstützen.

    757 = rwx r-x rwx
    Besitzer hat Lesen, Schreiben und Ausführen
    Gruppe hat Lesen und Ausführen
    Andere haben Lesen, Schreiben und Ausführen

Um die Verwirrung zu steigern, nutzen viele Hosting-Unternehmen Software namens phpsuExec oder suExec, diese Tools ändern die Art, wie der Webserver läuft, wo der Webserver normalerweise nicht als Ihr Benutzername läuft – in diesem Fall tut er es. Die Nutzung der *anderen* Berechtigungen ist möglicherweise nicht erforderlich, jetzt müssen Sie Verzeichnisse möglicherweise nur so konfigurieren, dass sie für Ihren eigenen Benutzernamen und Gruppennamen *beschreibbar* sind. Dadurch können Verzeichnisberechtigungen auf 755 oder 775 statt 757 oder 777 gesetzt werden.

    755 = rwx r-x r-x
    Besitzer hat Lesen, Schreiben und Ausführen
    Gruppe hat Lesen und Ausführen
    Andere haben Lesen und Ausführen

    775 = rwx rwx r-x
    Besitzer hat Lesen, Schreiben und Ausführen
    Gruppe hat Lesen, Schreiben und Ausführen
    Andere haben Lesen und Ausführen

Der Webserver benötigt weiterhin die Ausführung für den Benutzernamen und die Lese- und Ausführungsgruppenberechtigungen, damit er das Lese-Kommando für Dateien im Verzeichnis ausführen kann. Auch hier können diese Berechtigungen nach Abschluss des Web-Installers wieder auf 755 zurückgesetzt werden. Das ist das Wesentliche für Verzeichnisse, aber was ist mit Dateien? Hier wird es etwas einfacher. Die meisten der Dateien, die Joomla! verwendet, sind mit den Standardberechtigungen 644 einverstanden.

    644 = rw- r-- r--
    Besitzer hat Lesen und Schreiben
    Gruppe hat Lesen
    Andere haben Lesen

Dies gilt, wenn Sie nicht die Notwendigkeit haben, vom Webserver auf Dateien zu schreiben, dieselben Regeln gelten wie für Verzeichnisse, wenn Sie diese Notwendigkeit haben. Eine Datei, die Sie gerne vom Webserver beschreibbar haben möchten, ist Ihre configuration.php-Datei. Dies ist die Joomla! Konfigurationsdatei, wenn Sie planen, die Konfiguration über die Web-Admin-Oberfläche zu ändern, dann muss diese Datei für den Webserver beschreibbar sein.

Wenn auf Ihrem Server Verzeichnisberechtigungen auf "Andere" Beschreibbar für die Installation gesetzt werden mussten, dann wird diese Datei wahrscheinlich auch auf 757 oder 777 eingestellt werden müssen. Diese Datei als 757 oder 777 zu belassen, ist jedoch gefährlich, da Sie jedem erlauben, "Schreibzugriff" zu haben. Viele Website-Sicherheitslücken nutzen dies aus, sodass es generell nicht empfohlen wird, diese Datei mit diesen Berechtigungen zu belassen.

Wenn Ihr Webserver eines der SU-Tools installiert hat und Sie nur 755 für die Installation auf Verzeichnissen konfigurieren mussten, müssen Sie wahrscheinlich auch nur 755 oder 775 auf dieser Datei einstellen, um Änderungen über die Admin-Oberfläche zu ermöglichen, und diese Berechtigungen werden generell als sicherer angesehen als 757 oder 777.

Zusammenfassend, welche Berechtigungen sollten für die Joomla!-Installation gesetzt werden? Nun, wie Sie sehen können, hängt es davon ab!

Das ist nicht so hilfreich, wie Sie es sich gewünscht hätten, und sicherlich keine endgültige Antwort, aber im Allgemeinen können nach der Installation alle unsicheren "7" Einstellungen auf etwas Sichereres zurückgesetzt werden. Zum Beispiel:

    Dateien = 644
    Verzeichnisse = 755

Diese Berechtigungen würden für Dateien erlauben;

    644 = rw- r-- r--
    Besitzer hat Lesen und Schreiben
    Gruppe hat nur Lesen
    Andere haben nur Lesen

und für Verzeichnisse,

    755 = rwx r-x r-x
    Besitzer hat Lesen, Schreiben und Ausführen
    Gruppe hat nur Lesen und Ausführen
    Andere haben nur Lesen und Ausführen

Wenn Sie SSH-Shell-Zugriff haben, können die folgenden Befehle von der Kommandozeile ausgeführt werden, um alle Dateien und Verzeichnisse auf die Serverse-standards von 755 und 644 zurückzusetzen. Wechseln Sie zum Hauptverzeichnis ("/") Ihrer Joomla!-Installation, dann führen Sie aus:

    find . -type f -exec chmod 644 {} \;
    find . -type d -exec chmod 755 {} \;

Wenn Sie nur FTP-Zugang haben, kann dies eine sehr zeitaufwändige Aufgabe sein, jedoch, es sei denn, Sie haben während der Installation mehr Verzeichnisse geändert, als angefordert wurde, sollten Sie nur etwa 10 Verzeichnisse und die *configuration.php*-Datei zurücksetzen müssen.

Denken Sie daran, dass Sie nach der tatsächlichen Joomla!-Installation möglicherweise die Standardberechtigungen für die entsprechende Verzeichnisse während der Installation von Erweiterungen oder Vorlagen vorübergehend wieder erhöhen müssen, danach können Sie sie wieder zurücksetzen.

Wenn Sie sich entscheiden, *Caching* zu verwenden, muss das Cache-Verzeichnis vom Webserver-Benutzer beschreibbar sein, damit es seine temporären Dateien schreiben kann.

## Berechtigungen rekursiv festlegen

In einem Terminalfenster, beginnend vom Joomla-Website-Root, verwenden Sie die folgenden Befehle, um Datei- und Ordnerberechtigungen auf die Joomla-Standardeinstellungen zu setzen.

find . -type f -exec chmod 644 {} \;
find . -type d -exec chmod 755 {} \;

Hinweis: Der find-Befehl geht davon aus, dass er vom aktuellen Verzeichnis ausgehen soll. Gehen Sie zur Sicherheit in Ihr public_html-Verzeichnis und geben Sie einen Pfad als erstes Argument an. Einige Shells, wie beispielsweise bash unter Apple OS X, erfordern, dass ein Pfad im find-Befehl angegeben wird.

Testen Sie alle Erweiterungen von Drittanbietern, nachdem Sie die Berechtigungen geändert haben.

*Übersetzt von openai.com*

