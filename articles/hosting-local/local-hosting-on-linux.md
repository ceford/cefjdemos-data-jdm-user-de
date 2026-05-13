<!--
{
  "source": "https://docs.joomla.org/No_original_yet",
  "title": "Lokales Hosting auf Linux ",
  "description": "", 
  "author": ""
}
-->

Dieser Beitrag behandelt das Hosting von Joomla auf einem persönlichen, auf Linux basierenden Computer zu Test- und Entwicklungszwecken. Die behandelten Linux-Versionen stammen aus der Debian-Ubuntu-Familie, insbesondere Linux Mint. Andere Distributionen sind ähnlich, haben jedoch unterschiedliche Befehlsyntaxen und Speicherorte für Dateien.

Sie müssen eine Reihe von Softwarepaketen installieren, die oft als LAMP-Stack bezeichnet werden. Die Buchstaben stehen für Linux, Apache, MySQL und PHP. Sie können Software entweder über die grafische Benutzeroberfläche (GUI) oder die Befehlszeile in einem Terminalfenster installieren. Sie sind unterschiedliche Methoden zur Nutzung des Synaptic Package Managers.
## Apache mit der GUI installieren

Wählen Sie im Systemmenü, das mit dem LM-Logo gekennzeichnet ist, den Punkt Administration / Synaptic-Paketverwaltung. Sie werden nach Ihrem Passwort gefragt. Geben Sie Ihr Login-Passwort ein, um die GUI zu öffnen. Oben rechts befindet sich ein `Search`-Button. Wählen Sie diesen aus und geben Sie **apache** ein und klicken Sie auf `Search`. Markieren Sie das Kontrollkästchen `apache2` und wählen Sie im Popup-Fenster `Mark for Installation`. Ein weiteres Popup-Fenster zeigt eine Liste zusätzlicher Pakete, die zur Unterstützung von Apache benötigt werden. Wählen Sie `Mark`:

![synaptic package manager](../../../en/images/hosting-local/local-hosting-on-linux/01-synaptic-package-manager-gui.png)

Wählen Sie den `Apply`-Button in der oberen Symbolleiste und den `Apply`-Button im Übersichts-Dialog. Apache wird installiert und konfiguriert, der Prozess endet mit einem Dialog **Änderungen angewendet**. Wählen Sie `Close`.

Sie können überprüfen, dass Apache installiert und funktionsfähig ist, indem Sie Ihren Browser öffnen, standardmäßig Firefox bei einer neuen Linux Mint-Installation, und **localhost** in die URL-Leiste eingeben. Sie sollten die Ubuntu Apache2 Standardseite sehen:

![apache default page](../../../en/images/hosting-local/local-hosting-on-linux/02-apache-default-page.png)

Die Seite enthält einige nützliche Informationen über Dateipfade, die später möglicherweise nicht so leicht verfügbar sind. Vielleicht möchten Sie diese Seite auf Papier oder als PDF-Datei drucken.

## PHP mit der CLI installieren

Es ist wahrscheinlich am besten, PHP über die Befehlszeile zu installieren. Ein Grund dafür ist, dass zum Zeitpunkt des Schreibens der Synaptic Package Manager nur PHP8.1 anbietet, obwohl PHP8.2 schon seit einiger Zeit verfügbar ist und aus einem Drittanbieter-Repository installiert werden kann. Es gibt eine gute Beschreibung des Verfahrens in diesem Tutorial mit Quickstart- und Detailliert-Abschnitten.

Schließen Sie zuerst Ihre Synaptic Package Manager GUI und öffnen Sie dann ein Terminal-Fenster. Geben Sie die folgenden Befehle nacheinander ein:

```bash
sudo add-apt-repository ppa:ondrej/php
sudo apt update
sudo apt install php8.2 php8.2-cli php8.2-{bz2,curl,mbstring,intl}
sudo apt install php8.2-fpm
sudo a2enconf php8.2-fpm
sudo systemctl reload apache2
```
Überprüfen Sie in Ihrem Browser, ob die Standardseite für localhost noch funktioniert.

## Installieren von MySQL oder MariaDB

Sie können im Internet nach Informationen zu jedem dieser Datenbankpakete suchen. MySQL ist die traditionelle Wahl, wurde jedoch von Oracle übernommen und ist jetzt weniger populär. MariaDB ist ein Open-Source-Ersatz mit zusätzlichen Funktionen. Beide funktionieren mit Joomla! 5, aber es ist nicht einfach, von einem zum anderen zu wechseln. Tabellen müssen exportiert und importiert werden. Joomla! 5 erfordert spezifische Mindestversionen, die Linux Mint über den Synaptic-Paketmanager anbietet.

Öffnen Sie die Synaptic-Paketmanager GUI und suchen Sie nach mysql-server oder mariadb-server. Wählen Sie das Kontrollkästchen für den Eintrag, der auf -server endet. Wählen Sie `Zur Installation vormerken` und dann `Anwenden` in der oberen Symbolleiste. Sie können das Detailfeld öffnen, um zu sehen, was während der Installation passiert. Wählen Sie `Schließen`, wenn Sie fertig sind.

Sie können testen, ob Ihre Datenbank funktioniert, indem Sie `mysql` in die Befehlszeile eingeben. Dies ist bei MySQL und MariaDB gleich. Sie sollten eine Fehlermeldung `Access denied` sehen, was in Ordnung ist, denn das zeigt an, dass Ihre Datenbankinstallation tatsächlich funktioniert.

## phpMyAdmin installieren

phpMyAdmin ist ein GUI-Datenbankverwaltungswerkzeug, das Sie zum Erstellen und Verwalten Ihrer Datenbanken benötigen. Suchen Sie im Synaptic-Paketmanager-GUI nach **phpmyadmin**. Wählen Sie das Kontrollkästchen aus und `Markieren zur Installation`. Nach dem Download gibt es eine Aufforderung, den `Webserver automatisch neu zu konfigurieren`. Wählen Sie das Kontrollkästchen für `apache2` und anschließend die `Weiter`-Schaltfläche. Lassen Sie im nächsten Konfigurationsbildschirm das Kontrollkästchen `Datenbank konfigurieren...` aktiviert und wählen Sie `Weiter`.

Wählen Sie ein Anwendungskennwort für den Benutzer phpmyadmin. Test: Geben Sie in Ihrem Browser localhost/phpmyadmin in die URL-Leiste ein. Sie sollten den phpMyAdmin-Anmeldebildschirm sehen. Mit dem Benutzernamen phpmyadmin und dem Kennwort, das Sie während der Installation eingegeben haben, können Sie sich anmelden. Sie können jedoch keine Datenbanken erstellen! Um das Problem zu lösen, müssen Sie die Konfigurationsdatei als Root im Terminalfenster bearbeiten:

```bash
sudo nano /etc/phpmyadmin/config.inc.php
```

Suchen Sie die beiden Zeilen, die // $cfg['Servers'][$i]['AllowNoPassword'] = TRUE; enthalten, und entfernen Sie die führenden Schrägstriche, um sie zu kommentieren. Beide!

Dann melden Sie sich von der Kommandozeile aus bei MySQL an und erstellen einen neuen Benutzer und gewähren diesem Benutzer alle Berechtigungen:
```bash
sudo mysql
CREATE USER 'admin'@'localhost' IDENTIFIED BY '';
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'localhost' WITH GRANT OPTION;
exit
```

Anschließend gehen Sie zurück zu phpMyAdmin und versuchen, sich mit dem Benutzernamen **admin** und keinem Passwort anzumelden. Sie sollten alle Datenbanken sehen und in der Lage sein, neue Datenbanken zu erstellen.


## Priorität der Index-Datei

Der Standardort für Webseiten auf Ubuntu/Linux Mint ist /var/www/html. Wenn du den Inhalt dieses Verzeichnisses auflistest, wirst du sehen, dass es eine Datei namens index.html enthält, die den Inhalt der Ubuntu Apache2 Default Page beinhaltet. Erstelle eine Datei namens index.php in diesem Verzeichnis mit folgendem Inhalt:

```php
<?php echo phpinfo();
```
Lade localhost erneut. Es gibt keine Änderung! Gib **localhost/index.php** in die URL-Leiste ein und du wirst eine Seite mit PHP-Versionsinformationen sehen. Dieses Verhalten wird durch die standardmäßige Apache-Konfiguration gesteuert, die geändert werden kann, indem das Apache `dir`-Modul aktiviert und seine Konfiguration bearbeitet wird:

```bash
sudo a2enmod dir
sudo nano /etc/apache2/mods-enabled/dir.conf
```

Verschiebe index.php an den Anfang der Liste. Starte dann Apache neu:

```bash
sudo systemctl restart apache2
```

Dieses Mal solltest du beim Verwenden von **localhost** allein in der URL-Leiste den Inhalt der index.php-Datei sehen, eine PHP-Informationsseite.

## Virtuelle Hosts

In einer Standard-Linux-Installation befinden sich die Systemdateien im Root-Verzeichnis (/)
und die Benutzerdaten im Home-Verzeichnis (/home/meinbenutzername). Dies ist ein 
potenzielles Problem, da der Standard-Apache-Benutzer www-data möglicherweise keine entsprechenden 
Berechtigungen hat, Dateien im Benutzerbereich zu erstellen. Die beste Lösung ist die Erstellung 
von virtuellen Hosts.

Zuerst wird ein Modul benötigt, das es Apache ermöglicht, Benutzer und Gruppe 
für jeden Benutzer anzupassen:

```bash
sudo apt-get install libapache2-mpm-itk
sudo a2enmod mpm_itk
```

Als Nächstes wird eine Kopie der Standard-Site-Konfigurationsdatei erstellt und bearbeitet:

```bash
cd /etc/apache2/sites-available
sudo cp 000-default.conf benutzername.localhost.conf
sudo nano benutzername.localhost.conf
```

Die Standard-Site-Konfigurationsdatei enthält Kommentare zur Erklärung ihres
Inhalts. Diese sind im folgenden Beispiel ausgelassen. Kommentieren Sie die
ServerName-Zeile ein und ändern Sie alle Vorkommen von `benutzername` in Ihren eigenen
Benutzernamen.

```xml
<VirtualHost *:80>
        ServerName benutzername.localhost
        ServerAdmin webmaster@localhost
        DocumentRoot /home/benutzername/public_html
        <IfModule mpm_itk_module>
                AssignUserId benutzername benutzername
        </IfModule>
        <Directory /home/benutzername/public_html/ >
                Options Indexes FollowSymLinks
                AllowOverride None
                Require all granted
        </Directory>
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

Aktivieren Sie die neue Site und starten Sie Apache neu:

```bash
sudo a2ensite benutzername.localhost
sudo systemctl reload apache
```

Fügen Sie einen Eintrag in der Datei /etc/hosts hinzu, um einen Eintrag für den neuen virtuellen Host hinzuzufügen.
Andernfalls wird Ihr Browser im Internet danach suchen.

```bash
sudo nano /etc/hosts
```
Wenn Sie fertig sind, sieht es in etwa so aus:

```bash
127.0.0.1       localhost
127.0.0.1       benutzername.localhost
127.0.1.1       hostname

# Die folgenden Zeilen sind für IPv6-fähige Hosts wünschenswert
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```
**Hostname:** Dies ist der Name, den Sie Ihrem Computer bei der Installation 
von Linux gegeben haben. Sie werden ihn gleich benötigen. Sie können ihn ändern, wenn Sie möchten - aber 
es ist ratsam, sich vorher darüber zu informieren und ihn dann zuerst zu ändern.

Wenn alles gut läuft, sehen Sie mit einer URL der Form benutzername.localhost 
eine Verzeichnisauflistung Ihres public_html-Verzeichnisses. Die öffentliche Anzeige 
von Verzeichnisauflistungen wird als schlechte Praxis, als Sicherheitsrisiko angesehen und wird 
normalerweise durch eine andere Apache-Konfigurationseinstellung deaktiviert. Für eine 
persönliche Webseite auf einem persönlichen Computer, der für Entwicklung und Tests verwendet wird, 
ist dies jedoch sehr nützlich. Viele verschiedene Seiten können in verschiedenen Unterverzeichnissen 
eingerichtet werden. Zum Beispiel Joomla 4 und Joomla 5 Seiten, Bulletin Boards, Wikis und so weiter. 
Wenn Sie viele Testseiten haben, ist es schwierig, sich alle Unterverzeichnisnamen zu merken!

## Zugriff auf das Heimnetzwerk

Wenn Sie einen weiteren Computer in Ihrem Heimnetzwerk haben, möchten Sie wahrscheinlich auch von dort auf Ihre Linux-Website zugreifen. Damit das funktioniert, benötigen Sie einen weiteren virtuellen Host. Kopieren und bearbeiten Sie den gerade erstellten:

```bash
cd /etc/apache2/sites-available
sudo cp username.localhost.conf username.conf
sudo nano username.conf
```

Ändern Sie den ServerName von username.localhost zu username.hostname und aktivieren Sie dann den neuen virtuellen Standort und starten Sie Apache neu.

```bash
sudo a2ensite username
sudo apachectl restart
```

Gehen Sie zu Ihrem anderen Computer im Heimnetzwerk und bearbeiten Sie dessen persönliche Hosts-Datei. Bearbeiten Sie zum Beispiel auf einem Mac die Datei /private/etc/hosts und fügen Sie unten die folgende Zeile hinzu:

```bash
192.168.178.20 username.hostname www.username.hostname
```

Dabei ist 192.168.178.20 die IP-Adresse Ihres Linux-Computers.

Nun sollten Sie auf Ihrem zweiten Computer auf den Webserver Ihres Linux-Computers zugreifen können, indem Sie username.hostname in die URL-Leiste Ihres Browsers eingeben.

## Partitionshinweise

Software, die mit dem Synaptic-Paketmanager installiert wird, befindet sich normalerweise im Linux-Root-Verzeichnis (/). Benutzerdaten befinden sich im Home-Verzeichnis (/home). Bei einer einfachen Installation befinden sich diese Verzeichnisse in derselben physischen Festplattenpartition.

Bei einer komplexeren Installation, möglicherweise mit der Option, verschiedene Betriebssysteme (Windows oder Linux) oder verschiedene Versionen desselben Betriebssystems zu starten, befinden sich das Root-Verzeichnis und die Benutzerdaten oft in separaten Partitionen. Dies ermöglicht den Zugriff auf dieselben Benutzerdaten von jedem Betriebssystem aus.

Es gibt jedoch ein Problem: Eine Joomla-Seite, die sich in einem /home/username-Verzeichnis befindet, benötigt Datenbankdaten, die sich normalerweise im Root-Verzeichnis befinden, genauer gesagt in /var/lib/mysql. Sie können das MySQL/MariaDB-Datenverzeichnis an einen Ort verschieben, der für beide Betriebssysteme verfügbar ist, entweder in der /home-Partition oder in einer separaten Partition. Dieses Tutorial beschreibt, wie man das MySQL-Datenverzeichnis in Ubuntu und Debian Linux ändert. Das muss für jedes Betriebssystem separat durchgeführt werden, wird hier jedoch nicht behandelt.
