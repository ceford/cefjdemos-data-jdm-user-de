<!--
{
  "source": "https://docs.joomla.org/",
  "title": "Lokales Hosting mit XAMPP  ",
  "description": "", 
  "author": ""
}
-->

## Einführung

XAMPP ist ein einfach zu installierendes Paket, das den Apache-Webserver, PHP, XDEBUG und die MySQL-Datenbank bündelt. Dies ermöglicht es Ihnen, die Umgebung zu erstellen, die Sie benötigen, um Joomla! auf Ihrem lokalen Rechner auszuführen. Die neueste Version von XAMPP ist auf der Webseite von [Apache Friends](https://www.apachefriends.org/index.html) verfügbar. Downloads sind für Linux, Windows und Mac OS X erhältlich. Laden Sie das Paket für Ihre Plattform herunter.

*Wichtiger Hinweis zu XAMPP und Skype:* Apache und Skype verwenden beide Port 80 als Alternative für eingehende Verbindungen. Wenn Sie Skype nutzen, gehen Sie in das Tools-Optionen-Erweitert-Verbindung-Panel und deaktivieren Sie die Option *Ports 80 und 443 als Alternativen für eingehende Verbindungen verwenden*. Wenn Apache als Dienst startet, wird es Port 80 belegen, bevor Skype startet, und es wird kein Problem auftreten. Aber zur Sicherheit deaktivieren Sie die Option in Skype.

## Installation

Die Installation auf jeder Plattform ist sehr einfach - benutzen Sie den Installer. Es gibt kein wirkliches Handbuch oder Handbuch für XAMPP. Die Dokumentation liegt in Form von FAQs vor, die von der Downloads-Seite verlinkt sind.

### Installation auf Windows

Für Windows wird empfohlen, XAMPP in „c:\xampp“ (nicht in „c:\programme“) zu installieren. Wenn Sie das tun, werden Ihr Joomla! (und alle anderen lokalen Webseiten-Ordner) in den Ordner „c:\xampp\htdocs“ abgelegt. (Nach Konvention gehen alle Webinhalte in den „htdocs“-Ordner.)

Wenn Sie mehrere http-Server haben (wie z.B. IIS), können Sie den XAMPP-Abhörport ändern. In \apache\conf\httpd.conf ändern Sie die Zeile Listen 80 in Listen \[portnummer\] (z.B.: „Listen 8080“).

<div class="alert alert-info">
<h4>Joomla Community Magazin Tutorial<h4>
<p>Ein detailliertes Tutorial zur Installation von XAMPP auf Windows, zusammen mit dem Joomla 4 Beta, dem Joomla Patch Tester und Git finden Sie in diesem <a href="https://magazine.joomla.org/all-issues/june-2020/github-installing-git" rel="noreferrer noopener">Beitrag des Joomla Community Magazins</a>.</p></div>

Um XDebug zu installieren: [XAMPP - XDebug Setup für PHP 8](https://odan.github.io/2020/12/03/xampp-xdebug-setup-php8.html)

### Installation auf Linux

#### XAMPP installieren

Auf der Download-Seite wird ein Installer xampp-linux-x64-8.2.12-0-installer.run heruntergeladen, wobei 8.2.12 die neueste Version ist. Führen Sie die Installationsdatei aus, um Apache2, MySQL und PHP zu installieren.

Nach der Installation verwenden Sie die folgenden Befehle, um die Dienste zu starten und zu stoppen:
```sh
    sudo /opt/lampp/lampp start
    sudo /opt/lampp/lampp stop
```

#### Testen Sie Ihren XAMPP-Localhost-Server

Öffnen Sie Ihren Browser und richten Sie ihn auf

    http://localhost

Die index.php wird umleiten zu

    http://localhost/xampp

Dort finden Sie Anweisungen, wie Sie Standard-Benutzernamen/Passwörter ändern können. Auf einem PC, der keine Dateien ans Internet oder LAN dient, ist das Ändern der Standardeinstellungen eine persönliche Entscheidung.

#### Joomla holen

* Laden Sie die neueste Joomla-Installations-Zip-Datei herunter
* Entpacken Sie sie auf Ihre Festplatte
* Verbinden Sie sich mit einem FTP-Client mit dem localhost
* Erstellen Sie einen Ordner für Ihr Joomla auf dem localhost-Server
* Übertragen Sie die entpackten Joomla-Installationsdateien in den neu erstellten Joomla-Ordner.

##### Wichtig:

- Die xammp-Installation setzt die korrekten Dateibesitzrechte und Berechtigungen.
- Die Verwendung des **CHOWN-Befehls** wird **Besitzerprobleme mit xampp verursachen**.
- **Nautilus zu verwenden**, um Ordner/Dateien auf localhost zu bearbeiten, wird **Besitzerprobleme mit xampp verursachen**.

#### Datenbankinformationen

- Host: localhost
- Standard-Datenbankname: test
- Standard-Datenbankbenutzer: root
- Standard-Passwort: Es gibt **kein** Standard-Passwort.
- Administrator-Passwort: Ihre Wahl.

Das Installieren von Beispieldaten wird für den unerfahrenen Benutzer empfohlen.

Nach der Installation löschen Sie das Installationsverzeichnis und richten Sie Ihren Browser auf: `http://localhost/yournewjoomlafolder` oder `http://localhost/yournewjoomlafolder/administrator`.

####  Erstellen eines Links im Ubuntu-Menü

##### Um eine GUI für xampp an Ihr Ubuntu-Menü anzuschließen

Öffnen Sie das Terminal und geben Sie ein

    sudo nano /usr/share/applications/xampp-control-panel.desktop

Kopieren Sie dann das Folgende in den Nano-Editor und speichern Sie.

    [Desktop Entry]
    Encoding=UTF-8
    Name=XAMPP-Kontrollpanel
    Comment=XAMPP starten und stoppen
    Exec=gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"
    Icon=/usr/share/icons/Tango/scalable/devices/network-wired.svg
    Terminal=false
    Type=Application
    Categories=GNOME;Application;Network;
    StartupNotify=true

Wenn das Kontrollpanel nicht startet, versuchen Sie den Befehl Exec direkt im Terminal auszuführen:

    gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"

Sollten Sie den Fehler erhalten:

    Error importing pygtk2 and pygtk2-libglade

Installieren Sie die fehlenden Bibliotheken:

    sudo apt-get install python-glade2

#### XDebug PHP-Debugger

Das XAMPP-Paket für Linux enthält nicht den XDebug PHP-Debugger. Um XDebug auf Debian oder Ubuntu zu installieren:

- Installieren Sie das Paket *build-essential*:

    sudo apt-get update
    sudo apt-get install build-essential
    sudo apt-get install autoconf

- Laden Sie das [Entwicklungspaket](http://www.apachefriends.org/en/xampp-linux.html) für Ihre Version von XAMPP herunter und extrahieren Sie es über Ihrer bestehenden Installation:

    sudo tar xvfz xampp-linux-devel-1.7.7.tar.gz -C /opt

- Bauen Sie XDebug:

    wget http://xdebug.org/files/xdebug-2.1.3.tgz
    tar xzf xdebug-2.1.3.tgz
    cd xdebug-2.1.3/
    /opt/lampp/bin/phpize

Danach erhalten Sie die folgende Ausgabe auf Ihrer Konsole…

    Konfiguration für:
    PHP Api Version:         20090626
    Zend Module Api No:      20090626
    Zend Extension Api-No:   20090626

    ./configure --with-php-config=/opt/lampp/bin/php-config
    make
    sudo make install

Dann wird die Ausgabe dies sein.. bitte überwachen Sie das angegebene Verzeichnis.

    Installiere gemeinsame Erweiterungen: /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/

Erstellen Sie einen Ordner in Ihrem temporären Ordner, der die datendatei von XDebug speichert:

    sudo mkdir /opt/lampp/tmp/xdebug
    sudo chmod a+rwx -R /opt/lampp/tmp/xdebug

Alternative Installationen:

Installation mit der PHP-Erweiterungs-Community-Bibliothek (PECL), die mit xampp gebündelt ist:

    sudo /opt/lampp/bin/pecl install xdebug

Auf Ubuntu/Debian können Sie installieren mit:

    apt-get install php5-xdebug

(Achtung: dies installiert auch Apache und PHP aus den apt-Repositorys.)

##### Warnung für 64-Bit-Benutzer

Beim Kompilieren von XDebug oder der Installation über apt-get erhalten Sie beim (Neu-) Starten von xampp einen Fehler:

    /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/xdebug.so: falsche ELF-Klasse: ELFCLASS64

Das liegt daran, dass xampp im 32-Bit-Modus läuft, aber XDebug 64-Bit ist. Um dieses Problem zu beheben, machen Sie entweder xdebug.so auf einer 32-Bit-Maschine oder laden Sie es herunter von:

    http://code.activestate.com/komodo/remotedebugging/

Laden Sie die Datei herunter: "PHP Remote Debugging Client" für "Linux (x86)" Entpacken Sie den Inhalt der Datei auf Ihrem Computer, diese komprimierte Datei enthält mehrere Ordner mit Versionsnummern, z.B.: 4.4, 5.0, 5.1 ... 5.3 und so weiter, gehen Sie in den Ordner mit der höheren Versionsnummer oder den, der für Sie funktioniert, kopieren Sie dann die Datei „xdebug.so“ manuell an den folgenden Ort, überschreiben Sie sie, falls nötig

    /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/

Denken Sie daran, dass dieser Ort auf Ihrem Computer anders sein könnte

### Installation auf Mac OS X

Mac OS X enthält tatsächlich einen Apache-Server von Haus aus, aber die meisten Entwickler bevorzugen die integrierten Tools und die Konfigurierbarkeit, die XAMPP bietet.

Wie bei den meisten Programmen auf Mac ist die Installation ein Kinderspiel. Besuchen Sie die [Apache Friends](https://www.apachefriends.org/) Webseite und laden Sie den Installer (xampp-osx-8.2.4-0-installer.dmg) herunter. Doppelklicken Sie auf den heruntergeladenen Installer, um den Installationsprozess zu starten.

Um den Server zu starten, öffnen Sie "XAMPP Control.app" und drücken Sie die Starttaste neben Apache.

#### Ein wenig Fehlersuche

Viele Mac-Benutzer haben in diesem Stadium einige Schwierigkeiten, wenn sie versuchen, eine weitere Instanz von Apache auf ihrem Rechner einzurichten. Wenn Sie Apache von XAMPP nicht starten können, haben Sie zwei Möglichkeiten:
**Sie können den Abhörport von XAMPP ändern.** In \Applications\XAMPP\xamppfiles\etc\httpd.conf ändern Sie die Zeile, die sagt, "Listen 80" in Listen \[portnummer\]. Beispiel:

    Listen 8080

**Sie können den Abhörport des vorinstallierten Apache-Servers ändern.** Im Finder gehen Sie zu „/etc“ (CMD+SHIFT+G); von hier aus können Sie durch die normalerweise versteckten Apache-Dateien navigieren. Finden Sie den Ordner Apache2 und bearbeiten Sie die "http.conf"-Datei. Ändern Sie die Zeile, die sagt, "Listen 80" in Listen \[portnummer\]. Beispiel:

    Listen 8080

*Hinweis: Wenn Sie sich dafür entscheiden, den Port des vorinstallierten Apache-Servers zu ändern, müssen Sie möglicherweise Ihren Computer neu starten, damit die Änderungen wirksam werden. Sie müssen sich auch als Administrator authentifizieren, um diese Dateien zu ändern.*

### XAMPP-Installation testen

Sobald XAMPP installiert ist und Sie den Apache-Dienst mit dem XAMPP Control Panel-Tool gestartet haben, können Sie es testen, indem Sie Ihren Browser öffnen und zu `http://localhost` navigieren. Sie sollten den XAMPP-Willkommensbildschirm sehen, der dem unten gezeigten ähnlich ist.

![Die XAMPP-Startseite](../../../en/images/hosting-local/local-hosting-with-xampp/01-local-hosting-xampp.png)

Wählen Sie den im Top-Menü genannten Link `phpinfo()`. Dies wird einen langen Bildschirm mit Informationen zur PHP-Konfiguration anzeigen, wie unten gezeigt.

![Die XAMPP PHP-Version Informationsseite](../../../en/images/hosting-local/local-hosting-with-xampp/02-local-hosting-xampp-php.png)

An diesem Punkt ist XAMPP erfolgreich installiert. Beachten Sie die *Geladene Konfigurationsdatei*. Wir werden diese Datei im nächsten Abschnitt bearbeiten, um XDebug zu konfigurieren.

*Übersetzt von openai.com*
