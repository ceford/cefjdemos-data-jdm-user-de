<!--
{
  "source": "https://docs.joomla.org/Setting_up_Apache,_PHP_and_MySQL_manually",
  "title": "Manuelle Einrichtung von Apache, PHP und MySQL ",
  "description": "", 
  "author": ""
}
-->

## Übersicht

Im Folgenden finden Sie eine kurze Übersicht über die Schritte zur Einrichtung von Apache, PHP und MySQL in einer Windows-Umgebung sowie Verweise auf verschiedene verwandte Werkzeuge, um die meisten Aufgaben im Zusammenhang mit Joomla! zu pflegen und zu bearbeiten.

Um die Anweisungen klar und prägnant zu halten, gehen wir davon aus, dass Sie, wo immer wir keine expliziten Anweisungen geben, die Standard-Installationspfade ohne Änderungen übernehmen.

### Warnung

Wenn Sie bereits eine der vorverpackten AMP-Stacks auf Ihrem Rechner installiert haben:

- Zu Ihrem AMP-Stack zurückzukehren wird schwierig sein. Die verschiedenen Installationen, die wir unten durchführen werden, überschreiben Registry-Werte und ändern die allgemeine Umgebung. (Dies gilt zumindest für die PC/Windows-Umgebung.)
- Wenn Sie Konfigurationen (Apache, MySQL oder PHP) oder Daten (Ihre bestehenden Websites und zugehörigen Datenbanken) beibehalten müssen, erstellen Sie vor dem Versuch, dieser Anleitung zu folgen, ordnungsgemäße Sicherungen.

(muss mit spezifischen Ratschlägen erweitert werden, wie das oben Genannte erreicht werden kann...)

## MySQL Einrichtung

1. Laden Sie den passenden <a href="https://dev.mysql.com/downloads/mysql/"
   rel="nofollow noreferrer noopener">MySQL-Installer</a> für Ihre Plattform herunter.
2. Starten Sie die Installation und wählen Sie einen benutzerdefinierten Installationspfad.
3. Klicken Sie sich durch den gesamten Installationsprozess und klicken Sie auf Fertigstellen.
4. Sie werden nun mit dem *MySQL Server Instance Configuration Wizard* konfrontiert.
    1. Stellen Sie sicher, dass die *Standardkonfiguration* ausgewählt ist, und gehen Sie weiter zu Weiter.
    2. Wenn Sie MySQL bereits installiert haben, erhalten Sie möglicherweise die Meldung *Ein Windows-Dienst mit dem Namen MySQL existiert bereits. Bitte deinstallieren Sie diesen Dienst richtig oder wählen Sie einen anderen Namen für den neuen Dienst.* In diesem Fall wählen Sie einen alternativen Dienstnamen.
    3. Im nächsten Fenster überprüfen Sie das *Include Bin Directory in Windows PATH*. Dadurch können Sie die verschiedenen MySQL-Utilities von der Befehlszeile aus aufrufen.
    4. Im nächsten Fenster können Sie ein Passwort für Ihren MySQL-root-Benutzer erstellen, den Benutzer mit dem höchsten Zugriffslevel auf Ihrem Server.
    5. Im letzten Fenster werden alle Änderungen, die Sie bisher konfiguriert haben, gespeichert, wenn Sie auf die Schaltfläche *Execute* klicken, und der Windows-Dienst für diese Instanz wird gestartet.

### Hinweise

1. Um die Anleitung so zugänglich wie möglich zu gestalten, haben wir einige Konfigurationsszenarien Ihrer MySQL-Instanz übersprungen, z.B. die Möglichkeit, Ihre Datenbankdateien zu verlagern.
2. MySQL wird standardmäßig im STRICT-Modus installiert, was zu einigen Fehlern führen kann, wenn Erweiterungen oder Anwendungen verwendet werden, die dies nicht berücksichtigt haben.

### MySQL Ressourcen

- <a href="https://www.heidisql.com/" class="external text" rel="nofollow noreferrer noopener">HeidiSQL</a> Eine einfach zu bedienende und erweiterbare Voll-Client-Alternative zu phpMyAdmin, die ständig weiterentwickelt wird.
- <a href="https://dev.mysql.com/downloads/workbench/" class="external text" rel="nofollow noreferrer noopener">MySQL Workbench</a> Verschiedene Tools, unter denen Sie den Administrator schätzen werden, der Ihnen hilft, Ihre MySQL-Instanz zu konfigurieren. Erfordert das <a href="https://dotnet.microsoft.com/en-us/" class="external text" rel="nofollow noreferrer noopener">.Net Framework</a>.
- <a href="https://www.phpmyadmin.net/" class="external text" rel="nofollow noreferrer noopener">phpMyAdmin</a> Ein leistungsstarker webbasierten MySQL-Client zur Verwaltung von allem rund um MySQL.
- <a href="https://dev.mysql.com/doc/" class="external text" rel="nofollow noreferrer noopener">MySQL-Dokumentation</a>

## Apache-Einrichtung

1.  <a href="https://httpd.apache.org/download.cgi" class="external text"
     rel="nofollow noreferrer noopener">Laden Sie den
    Installer</a> Ihrer Wahl herunter.
2.  Führen Sie den Installationsassistenten aus und klicken Sie durch jeden Schritt, bis Sie das Fenster Serverinformationen erreichen. Geben Sie die folgenden Optionen in jeder der Felder in der angegebenen Reihenfolge ein, es sei denn, Sie haben spezielle Anforderungen daran, wie Ihr Webserver eingerichtet werden soll:
    1.  localhost,
    2.  localhost und
    3.  admin@localhost
3.  Klicken Sie den Assistenten durch, der den Apache-Webserver als Windows-Dienst installiert und startet.
4.  In der Windows-Statusleiste sehen Sie nun eine rosa gefärbte Feder mit einem grün gefärbten Play-Button, was darauf hinweist, dass Apache läuft. Zeigen Sie Ihren Browser auf
    <a href="http://localhost/"
    rel="nofollow noreferrer noopener">http://localhost/</a> und Sie sollten eine Seite sehen, die anzeigt, dass es funktioniert.
5.  Gehen wir nun zu dem Ort, an dem Apache installiert ist, der üblicherweise unter *C:\Program Files\Apache Software Foundation\Apache2.2* zu finden ist, und gehen Sie die verschiedenen Verzeichnisse durch
    1.  *bin* - enthält die verschiedenen Binärdateien, von denen einige unten aufgelistet sind. Um auf diese Anwendungen zuzugreifen, von denen die meisten befehlsbasiert sind, müssen wir den Pfad zum *bin*-Verzeichnis zu unserer globalen PATH-Variable hinzufügen. Dazu klicken Sie mit der rechten Maustaste auf Arbeitsplatz \> Eigenschaften \> Erweitert \> Umgebungsvariablen, und in der Liste der Systemvariablen suchen und wählen Sie die Variable PATH und klicken auf Bearbeiten und fügen Sie ein abschließendes Semikolon hinzu, falls noch nicht vorhanden, gefolgt vom absoluten Pfad zu Ihrem bin-Verzeichnis. Bestätigen Sie die Änderungen, um das Systemeigenschaften-Dialogfenster zu schließen.
        1.  *httpd.exe* ist der Apache-Webserver selbst, der in mehrere Kindprozesse aufgeteilt wird, um so viele gleichzeitige eingehende Client-Anforderungen zu bedienen, wie es durch die MaxClients-Direktive erforderlich ist.
        2.  *ab.exe* ist ein Benchmark-Tool, das mit Apache geliefert wird und Ihnen ermöglicht zu sehen, wie gut Ihre Anwendung pro Zeiteinheit arbeiten kann.
    2.  *conf* - Ordner, in dem sich verschiedene Konfigurationsdateien befinden, von denen die folgenden in unserem Fall von größtem Interesse sind
        1.  *httpd.conf* - die meisten Serverdirektiven befinden sich in dieser Datei, und für einen einfachen Zugriff sollten Sie den Dateityp *.conf* mit einem benutzerfreundlichen Editor verknüpfen, d.h. alles außer dem Standard-Notepad.
        2.  *extra\httpd-vhosts.conf* - enthält Direktiven, die Ihnen erlauben, Ihren lokalen Server als virtuellen Host zu verwenden, d.h. mehrere Server auf Ihrem PC betreiben zu können. Ein Anwendungsszenario ist, dass Sie in einer Entwicklungsphase, wenn Sie die tatsächliche Domain, für die Sie arbeiten, auf Ihre lokale Kopie abbilden möchten, dies durch kleinere Anpassungen in dieser Datei tun können. Wir werden dies weiter unten im Detail besprechen.
    3.  *htdocs* - das Standard-Webserver-Root, hier wird
        <a href="http://localhost/"
        rel="nofollow noreferrer noopener">http://localhost/</a> zugeordnet, d. h. wenn Sie es nicht oben in *httpd.conf* umkonfigurieren.
    4.  *logs* - Zugriffs- und Fehlerprotokolle, wenn Sie versuchen, verschiedene Probleme im Zusammenhang mit Ihrem Server oder sogar Ihrer Anwendung zu beheben

### Apache-Ressourcen

- Die
  <a href="https://httpd.apache.org/docs/current/" class="external text"
   rel="nofollow noreferrer noopener">Apache-Referenzdokumentation</a>

## PHP-Setup

1.  <a href="https://windows.php.net/download/" class="external text" rel="nofollow noreferrer noopener">Laden Sie PHP herunter</a> und wählen Sie üblicherweise VC6 x86 Thread Safe im Zip-Format. Die verschiedenen Optionen beziehen sich darauf, wie der PHP-Code als Binärdatei kompiliert wurde und sind vermutlich momentan nichts, worüber Sie sich Sorgen machen sollten.
2.  Erstellen Sie ein Verzeichnis unter Ihrem C:\Programme\ (oder wo sich Ihr Programmverzeichnis befindet) mit dem Namen PHP.
3.  Suchen Sie Ihre heruntergeladene Zip-Datei, verschieben Sie sie in das neu erstellte Verzeichnis und entpacken Sie sie direkt in dieses Verzeichnis.
4.  Lassen Sie uns nun den PHP-Pfad zu unserer globalen PATH-Variablen hinzufügen, indem wir der obigen Anweisung folgen.

### PHP-konfigurieren

Die Konfiguration besteht darin, die *php.ini*-Datei zu bearbeiten. Eine Beispieldatei für verschiedene Szenarien befindet sich bereits in Ihrem PHP-Ordner. Lassen Sie uns *php.ini-development* in *php.ini* umbenennen und sie in Ihrem bevorzugten Texteditor öffnen. Die gängigen zu ändernden Werte sind wie folgt und alle diese Variablen sind in der *php.ini*-Datei gut dokumentiert. (Beachten Sie, dass dies eine serverweite Einstellung ist, die für alle Ihre Projekte gilt.):

- *max_execution_time* - wenn Sie Skripte haben, die zu lange laufen und der Server verschiedene unerwartete Ergebnisse zurückgibt, von denen Sie denken, dass sie nicht durch den gesamten Prozess laufen können
- *memory_limit*
- *error_reporting*
- *display_errors*
- *log_errors* - eine Variable, die Sie in Produktionsszenarien beachten sollten
- *upload_tmp_dir*
- *upload_max_filesize*
- *extension_dir* - um Komplikationen zu vermeiden, weisen wir auf das Verzeichnis hin, in dem sich die folgenden Erweiterungen befinden, indem wir diese Variable auskommentieren und den absoluten Ort des Verzeichnisses zuweisen. Die gesamte Zeile sollte wie folgt lauten: 
   extension_dir = "C:\Programme\PHP\ext"

- Der Abschnitt für dynamische Erweiterungen enthält verschiedene zusätzliche Module, die geladen werden sollen, und die auskommentierten sind diejenigen, die mit PHP vorverpackt sind und sich im *ext*-Verzeichnis in Ihrem PHP-Ordner befinden. Wenn Sie eines aktivieren möchten, entfernen Sie einfach das Auskommentieren, wie bei den folgenden Erweiterungen:
  - php_curl.dll
  - php_gd2.dll
  - php_mbstring.dll
  - php_mysql.dll
  - php_mysqli.dll
  - php_pdo.dll
  - php_pdo_mysql.dll
  - php_xsl.dll
- session.save_path

### Apache für die Zusammenarbeit mit PHP-konfigurieren

Nachdem wir PHP so konfiguriert haben, dass es wie gewünscht funktioniert, wenden wir uns Apache zu und tun dasselbe.

- Öffnen Sie *httpd.conf* und fügen Sie im Abschnitt "Dynamic Shared Object (DSO) Support" die folgenden Anweisungen hinzu. (Wenn Sie Ihren PHP-Ordner anders platziert haben, nehmen Sie bitte die entsprechende Änderung für php5apache2_2.dll unten vor.):
    LoadModule php5_module "C:/Programme/PHP/php5apache2_2.dll"
    AddType application/x-httpd-php .php

- Fügen Sie im DirectoryIndex *index.php* und *index.htm* als mögliche Dateien hinzu, die angezeigt werden sollen, wenn ein Verzeichnis angefordert wird:
    DirectoryIndex index.html index.htm index.php

- Fügen Sie am Ende der Datei die folgende Zeile hinzu, welche den Ort der *php.ini*-Datei angibt:
    PHPIniDir "C:/Programme/PHP"

### Neustart und Testen von PHP

Sobald Sie Änderungen an *php.ini*, *httpd.conf* oder anderen Konfigurationsdateien vornehmen, müssen Sie Apache neu starten, um die Auswirkungen der Änderungen zu sehen. Lassen Sie uns nun Apache mit dem Apache-Monitor-Tool neu starten, das Sie in Ihrer Windows-Statusleiste finden. Hoffentlich werden Sie nicht mit Dialogen aufgefordert und der Apache-Monitor läuft weiterhin grün.

Wir werden nun testen, ob PHP funktioniert. Gehen Sie zum Dokumentenstamm Ihres Webservers (im Standardfall C:\Programme\Apache Software Foundation\Apache2.2\htdocs) und fügen Sie eine Datei namens *phpinfo.php* mit folgendem Inhalt hinzu:

    <?php
    phpinfo();
    ?>

Dies wird eine Seite generieren, die Informationen über Ihre PHP-Installation und die momentan geladenen Module/Erweiterungen enthält. Geben Sie <a href="http://localhost/phpinfo.php" rel="nofollow noreferrer noopener">http://localhost/phpinfo.php</a> in Ihren Browser ein.

### Installieren und Konfigurieren von *XDebug*

1.  Öffnen Sie Ihren Browser und besuchen Sie den
    <a href="https://xdebug.org/wizard" class="external text" rel="nofollow noreferrer noopener">Xdebug Installationsassistenten</a>. Diese Seite hilft Ihnen, eine geeignete Version von Xdebug zu finden.
2.  Kopieren Sie die gesamte Seite der oben ausgeführten *phpinfo*-Seite und fügen Sie sie in das Textfeld ein, und folgen Sie den Anweisungen, um zu installieren.

### XDebug-Ressourcen

- Das <a href="https://www.php.net/docs.php" class="external text" rel="nofollow noreferrer noopener">PHP-Handbuch</a>
  Ausgezeichnete und aktuelle Dokumentation mit wertvollen zusätzlichen Kommentaren von Nutzern. Herunterladbare Versionen sind verfügbar.
- Die
  <a href="https://xdebug.org/docs/" class="external text" rel="nofollow noreferrer noopener">Xdebug 3 Dokumentation</a>

*Übersetzt von openai.com*

