<!-- Filename: Installing_Joomla_on_a_Raspberry_Pi / Display title: Raspberry Pi Installation -->

## Vorwort

**Hinweis: Dieses Dokument ist noch nicht vollständig und vollständig getestet.**

Der <a href="https://www.raspberrypi.org/" rel="nofollow noreferrer noopener">Raspberry Pi</a> ist ein kleiner Einplatinencomputer, der ursprünglich entwickelt wurde, um die Vermittlung grundlegender Informatikkenntnisse in Schulen und Entwicklungsländern zu fördern. Aufgrund seiner Vielseitigkeit ist er sehr beliebt geworden und wird als Mediaplayer, kleiner eigenständiger Server usw. verwendet. Sie können ihn als Webserver nutzen und Joomla! darauf installieren. Diese Seite zeigt Ihnen, wie Sie Ihre Joomla!-Website auf dem Raspberry Pi zum Laufen bringen.

## Hardware

- **Raspberry Pi Version 3 Model B** - Es gibt verschiedene Modelle des Raspberry Pi. Sie können die meisten Modelle verwenden, die einen Ethernet-Anschluss haben (die Model B Typen). Für die Leistung verwenden wir jedoch die neueste Version mit dem meisten RAM.
- **microSD-Karte** - Für das Betriebssystem + Webserver + Joomla. (RPi Version 3 Model B verwendet microSD, andere Versionen könnten normale SD-Karten verwenden.)
- **5-Volt-Adapter (1 Ampere)** - Um den Raspberry Pi mit Strom zu versorgen, müssen Sie die Netzspannung (230V oder 110V) auf 5 Volt umwandeln. Der Raspberry Pi benötigt etwa 1 Ampere und möglicherweise mehr, wenn Sie USB-Geräte daran anschließen.
- Standard **Ethernet-Kabel** - um den RPi mit Ihrem lokalen Netzwerk / Router / Internet zu verbinden.

## Installation des Betriebssystems

Das Betriebssystem Raspbian ist eine speziell für den Raspberry Pi kompilierte Debian-Linux-Version. Es gibt zwei Versionen von <a href="https://www.raspberrypi.com/software/" rel="nofollow noreferrer noopener">Raspbian</a>: **Raspbian Jessie mit Pixel Lite** (Version mit PIXEL-Desktop basierend auf Debian Jessie) und **Raspbian Jessie Lite** (minimale Version basierend auf Debian Jessie). Da wir den Raspberry Pi als Webserver für Joomla verwenden, benötigen wir die grafische Benutzeroberfläche nicht.

**Download** von <a href="https://www.raspberrypi.org/downloads/raspbian/" rel="nofollow noreferrer noopener">Raspbian Jessie Lite</a> und entpacken Sie die heruntergeladene Datei, z.B. **2016-09-23-raspbian-jessie-lite.zip** (306 MB) zu **2016-09-23-raspbian-jessie-lite.img** (1,4 GB).

Jetzt müssen wir die .img-Datei auf die (Micro-)SD-Karte kopieren. Sie können ein Tool mit grafischer Benutzeroberfläche wie <a href="https://unetbootin.github.io/" rel="nofollow noreferrer noopener">UNetbootin</a> (für Windows, Mac OS X und Linux) verwenden oder dies in der Befehlszeile tun.

**Vorsicht** beim Schreiben des *.img* Disk-Images auf eine andere Festplatte. Wenn Sie die falsche Zieldiskette angeben, überschreiben Sie diese Diskette mit der *.img*, was die Diskette unbrauchbar macht und zu Datenverlust führt.

### Windows

Überprüfen Sie in einem Terminal (CMD), welches Gerät mit der SD-Karte übereinstimmt und führen Sie etwa Folgendes aus:

```
    dd bs=1M if=c:\temp\2016-09-23-raspbian-jessie-lite.img of=[das Gerät Ihrer SD-Karte]
```

Siehe auch <a href="https://www.raspberrypi.org/documentation/installation/installing-images/windows.md" rel="nofollow noreferrer noopener">Installation von Betriebssystem-Images mit Windows</a>

### Apple OSX

Überprüfen Sie, welches Gerät für Ihre SD-Karte verwendet wird. In unserem Fall ist es *disk1s1* und wir führen im Terminal Folgendes aus:

```
    sudo dd bs=1M if=~/Downloads/2016-09-23-raspbian-jessie-lite.img of=/dev/disk1s1
```

Siehe auch: <a href="https://www.raspberrypi.org/documentation/installation/installing-images/mac.md" rel="nofollow noreferrer noopener">Installation von Betriebssystem-Images auf MacOS</a>

### Linux

Wir verbinden einen SD-Kartenleser mit der (Micro-)SD-Karte mit einem Computer. Mit *dmesg* können wir den Gerätenamen der SD-Karte herausfinden. In unserem Fall zeigt dmesg etwas wie `[xxxxxx.xxxxxxx]  sdd: sdd1 sdd2` an, was bedeutet, dass wir eine SD-Karte mit 2 Partitionen haben. Schreiben Sie das Raspbian-Image nicht auf eine Partition, sondern auf die gesamte Festplatte **sdd**.

Wir verwenden *dd* ("Disk Dump"), um eine Eingabedatei (*if*) zu einer Ausgabedatei (*of*) mit einer angegebenen Blockgröße (*bs*) zu schreiben.

**Vorsicht**: *dd* schreibt ohne Warnung auf ein Gerät. Überprüfen Sie doppelt, dass Sie auf das korrekte Gerät schreiben! Wenn Sie auf die falsche Festplatte schreiben, werden Sie sich immer an den *dd* Befehl als "Disk Destroyer" erinnern.

```bash
    sudo dd if=~/Downloads/2016-09-23-raspbian-jessie-lite.img of=/dev/sdd bs=4M
```

Siehe auch <a href="https://www.raspberrypi.org/documentation/installation/installing-images/linux.md" rel="nofollow noreferrer noopener">Installation von Betriebssystem-Images auf Linux</a>

**WARNUNG für die Raspbian Stretch Version**: Um einen SSH-Server ab dem Start zu aktivieren, müssen Sie eine leere Datei *ssh* auf der Root-Partition erstellen.

## Verbindung des Raspberry Pi mit dem LAN

Nachdem wir das Raspbian-Betriebssystem auf der SD-Karte installiert haben, werden wir:

- Die microSD-Karte in den SD-Kartensteckplatz des Raspberry Pi einlegen.
- Ein Ethernet-Kabel mit dem Raspberry Pi und dem lokalen Netzwerk (z.B. unserem Router) verbinden.
- Das 5V-Netzteil an den Raspberry Pi anschließen.

Der Startvorgang des Raspberry Pi dauert etwa 30 Sekunden. Wir müssen die IP-Adresse herausfinden, um über SSH eine Verbindung herzustellen. Dafür können wir unterschiedliche Ansätze verwenden:

- sich in die Weboberfläche des Routers einloggen und die verbundenen Geräte nachschauen;
- ein mit dem WLAN-Router verbundenes Mobiltelefon mit einer Netzwerk-Scan-App namens **Fing Overlook** verwenden;
- einen Befehl wie **nmap** verwenden. Angenommen, unser PC hat die IP-Adresse **192.168.0.25**, können wir alle anderen Geräte im selben Netzwerkbereich finden, indem wir Folgendes eingeben:
```
    sudo nmap -sP 192.168.0/24
```
Dies könnte folgende Details zeigen:

    Starting Nmap 6.47 ( http://nmap.org ) at 2016-10-22 17:42 CEST
    Nmap scan report for 192.168.0.35
    Host is up (0.00042s latency).
    MAC Address: 42:42:42:42:42:42 (Raspberry Pi Foundation)

Um sich in unseren Raspberry Pi einzuloggen, verwenden wir den Befehl **ssh**.

```
    ssh pi@192.168.0.35
```

Beim ersten Verbindungsaufbau wird Folgendes angezeigt:

    The authenticity of host '192.168.0.35 (192.168.0.35)' can't be established.
    ECDSA key fingerprint is 42:42:42:42:42:42:42:42:42:42:42:42:42:42:42:42.
    Are you sure you want to continue connecting (yes/no)?

Wir wählen **Ja**

    Warning: Permanently added 192.168.0.35 (ECDSA) to the list of known hosts.
    pi@192.168.0.35's password:

und geben das *Standardpasswort*: *raspberry* ein, welches bei erfolgreicher Anmeldung folgendes zeigt:

    The programs included with the Debian GNU/Linux system are free software;
    the exact distribution terms for each program are described in the
    individual files in /usr/share/doc/*/copyright.

    Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
    permitted by applicable law.
    pi@raspberrypi:~ $

Wir können den Raspberry Pi über eine Textoberfläche konfigurieren mit:

    sudo raspi-config

### Raspberry Pi Software-Konfigurationstool (raspi-config)

Mit diesem Konfigurationstool ändern wir nur die folgenden Einstellungen.

#### 1 Dateisystem erweitern

Standardmäßig hat der Speicherplatz auf der SD-Karte die gleiche Größe wie die 1,4 GB .img-Datei, die Sie zur Erstellung der SD-Karte für Ihren Raspberry Pi verwendet haben. Sie können diese Option verwenden, um den restlichen Speicherplatz zu erhalten.

#### 2 Benutzerpasswort ändern

Aus Sicherheitsgründen ist es am besten, das **Standardpasswort** "raspberry" so schnell wie möglich **zu ändern**.

#### 3 Boot-Optionen

Wir möchten, dass der Raspberry Pi die Textkonsole startet

##### B2 Konsole Autologin Textkonsole, automatisch als 'pi'-Benutzer angemeldet

#### 9 Erweiterte Optionen

##### A3 Speicheraufteilung

Da wir den Raspberry Pi als Headless-Server ohne Anschluss an einen Monitor verwenden werden, können wir den für die GPU verwendeten Speicher von 64 auf **16** reduzieren.

#### 5 Internationalisierungsoptionen

##### I2 Zeitzone ändern

Wir ändern die Zeitzone auf unsere eigene Zeitzone (z.B. Europa/Amsterdam)

Nach allen Änderungen starten wir den Raspberry Pi neu und melden uns erneut mit unserem neuen Passwort an.

    ssh pi@192.168.0.35

Nun ist es an der Zeit, alles andere zu installieren.

## Software aktualisieren

Bevor wir etwas anderes installieren, werden wir:

- die **Liste der Softwareversionen** aus allen externen
  Repositories **aktualisieren**
    sudo apt-get update

- **alle installierte Software aktualisieren**
    sudo apt-get upgrade

**Das Aktualisieren der Versionsliste und das Aktualisieren aller Software
sollte regelmäßig durchgeführt werden.**

## Nginx-Webserver

Eine schnelle und ressourcenschonende Alternative zum Apache-Webserver ist der zunehmend beliebter werdende **Nginx**-Webserver.

### Installation von Nginx

Wir werden Nginx und alle Abhängigkeiten (lies: Software, die Nginx zum Arbeiten benötigt) mit folgendem Befehl installieren:

```bash
sudo apt-get install nginx
```

Wir erhalten eine Nachricht wie:

```bash
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
 fontconfig-config fonts-dejavu-core libfontconfig1 libgd3 libjbig0 libtiff5 libvpx1 libxpm4 libxslt1.1 nginx-common nginx-full
Suggested packages:
 libgd-tools fcgiwrap nginx-doc ssl-cert
The following NEW packages will be installed:
 fontconfig-config fonts-dejavu-core libfontconfig1 libgd3 libjbig0 libtiff5 libvpx1 libxpm4 libxslt1.1 nginx nginx-common nginx-full
0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,550 kB of archives.
After this operation, 8,666 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
```

Durch die Auswahl von "y" werden Nginx und alle benötigten Pakete installiert.

Sie können die Installation mit einem Browser überprüfen. Gehen Sie zur IP-Adresse Ihres Raspberry Pi, in unserem Fall
<a href="http://192.168.0.35/" rel="nofollow noreferrer noopener">http://192.168.0.35/</a>. Wir sollten eine Nachricht wie diese sehen:

```plaintext
Welcome to nginx on Debian!
If you see this page, the nginx web server is successfully installed and working on Debian. Further configuration is required.
For online documentation and support please refer to nginx.org
Please use the reportbug tool to report bugs in the nginx package with Debian.
However, check existing bug reports before reporting a new bug.
Thank you for using debian and nginx.
```

#### Starten und Stoppen von Nginx

Nach der Installation wird Nginx automatisch gestartet. Sie können:

- Nginx stoppen: `sudo service nginx stop`
- Nginx starten: `sudo service nginx start`
- Nginx neu starten: `sudo service nginx restart`

### Konfiguration von Nginx

#### Globale Nginx-Konfiguration

In der globalen Konfiguration von Nginx können wir Standard-Caching usw. konfigurieren. Der Raspberry Pi 3 verwendet einen 1,2 GHz 64-Bit **quad-core** ARM Cortex-A53 Prozessor. Wenn Sie eine frühere Version mit weniger CPU-Kernen haben, sollten Sie

```bash
sudo nano /etc/nginx/nginx.conf
```

verwenden, um die "worker_processes" an die Anzahl der CPUs Ihres Geräts anzupassen. Standardmäßig ist es konfiguriert als

```plaintext
worker_processes 4;
```

Für Raspberry Pi 3 müssen Sie dies nicht ändern.

Nach einer Änderung der Nginx-Konfiguration oder der virtuellen Domänenkonfiguration müssen Sie

```bash
sudo nginx reload
```

ausführen, um die Änderungen wirksam zu machen.

#### Virtuelle Domänen

Es ist möglich, mehrere Joomla-Websites auf demselben Server mit virtuellen Domänen zu betreiben.

Legen Sie jede Website in einem separaten Ordner im Standard-Webroot /var/www/ an, z. B.:

- /var/www/example.com/
- /var/www/voorbeeld.nl/
  
```bash
sudo mkdir /var/www/example.com
sudo mkdir /var/www/voorbeeld.nl
```

Für jede Seite erstellen wir eine virtuelle Domäne, die im Grunde eine Textdatei mit domain-spezifischen Informationen ist:

- /etc/nginx/sites-available/example.com

```plaintext
server {
  listen 80;
  server_name example.com www.example.com;
  root /var/www/example.com;

  access_log /var/log/nginx/example.com.access_log;
  error_log /var/log/nginx/example.com.error_log info;

  location / {
    index index.php index.html index.htm;
  }
}
```

- /etc/nginx/sites-available/voorbeeld.nl

```plaintext
server {
  listen 80;
  server_name voorbeeld.nl www.voorbeeld.nl;
  root /var/www/voorbeeld.nl;

  access_log /var/log/nginx/voorbeeld.nl.access_log;
  error_log /var/log/nginx/voorbeeld.nl.error_log info;

  location / {
    index index.php index.html index.htm;
  }
}
```

Wir müssen jede Seite aktivieren, indem wir von /etc/nginx/sites-enabled/ auf die virtuelle Domäne in "sites-available" verlinken. Wir erstellen für jede virtuelle Domäne einen symbolischen Link:

```bash
sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/example.com
sudo ln -s /etc/nginx/sites-available/voorbeeld.nl /etc/nginx/sites-enabled/voorbeeld.nl
```

Um diese Konfiguration der virtuellen Domänen wirksam zu machen, führen wir

```bash
sudo nginx reload
```

und wenn alles korrekt konfiguriert wurde, wird es antworten:

```plaintext
Reloading nginx configuration: nginx.
```

## Datenbank

Wir können MariaDB oder MySQL installieren; Joomla funktioniert mit beiden. Lassen Sie uns MariaDB installieren mit:

    sudo apt-get install mariadb-server

Während der Installation müssen Sie ein Passwort für den **root**-Benutzer festlegen. Erstellen wir ein **Datenbankpasswort**, zum Beispiel **correcthorsebatterystaple**.

Zum Schluss verbessern wir die Sicherheit unserer MariaDB-Installation, indem wir Root-Konten entfernen, die von außerhalb des lokalen Hosts zugänglich sind, anonyme Benutzerkonten und die Testdatenbank. Das können wir mit folgendem Befehl tun:

    mysql_secure_installation

## PHP

Für PHP werden wir den **php-fpm** (FastCGI Process Manager) installieren, der als Daemon läuft und Fast/CGI-Anfragen entgegennimmt. Außerdem werden wir **php5-mysql** installieren, ein Modul für MySQL-Datenbankverbindungen direkt aus PHP-Skripten.

Die neuere PHP-Version php7 sollte mit dem folgenden Befehl installiert werden:

```bash
sudo apt-get install php-fpm php-mysql
```

Jetzt müssen wir Nginx mitteilen, dass es php-fpm für .php-Dateien verwenden soll. Dafür fügen wir ein paar Zeilen zu unseren virtuellen Domains hinzu:

```bash
sudo nano /etc/nginx/sites-available/example.com
```

Fügen Sie hinzu:

```nginx
location ~ \.php$ {
    fastcgi_pass unix:/var/run/php/php7.0-fpm.sock;
    fastcgi_index index.php;
    include fastcgi_params;
}
```

Testen Sie es, indem Sie die folgende PHP-Datei erstellen:

```bash
sudo nano /var/www/example.com/test.php
```

Wir verwenden einen Browser, um zu prüfen, ob wir die PHP-Konfigurationsseite unter <a href="http://192.168.0.35/example.com/test.php" rel="nofollow noreferrer noopener">http://192.168.0.35/example.com/test.php</a> sehen.

## Joomla!

- zu erledigen
```
    sudo wget https://github.com/joomla/joomla-cms/releases/download/3.6.3/Joomla_3.6.3-Stable-Full_Package.zip
    sudo unzip -x Joomla_3.6.3-Stable-Full_Package.zip
```

## Verbindung des Raspberry Pi mit dem Internet

Wir möchten, dass Menschen im Internet unsere Joomla-Website auf unserem Raspberry Pi besuchen können. Dazu müssen wir unseren **Internet-Router konfigurieren**, um den gesamten **eingehenden Verkehr** auf Port 80 **an unseren Raspberry Pi** weiterzuleiten.

Verwenden Sie Ihren Webbrowser, um sich mit der Weboberfläche Ihres Routers zu verbinden. Ein Router befindet sich normalerweise an der ersten Zahl Ihres IP-Bereichs, in unserem Fall an 192.168.0.1. In unserem Router konfigurieren wir das **Port-Forwarding**:

- Externe IP-Adresse: 0.0.0.0
- Externer Startport: 80
- Externer Endport: 80
- Interne IP-Adresse: 192.168.0.35 ( = unser Raspberry Pi)
- Interner Startport: 80
- Interner Endport: 80
- Protokoll: TCP

Stellen Sie sicher, dass es aktiviert ist.

Wenn alles richtig funktioniert, sollten Sie Ihre eigene Joomla-Website auf dem Raspberry Pi sehen, indem Sie Ihre externe IP-Adresse besuchen (Finden Sie Ihre externe IP-Adresse mit einem Tool wie <a href="http://www.whatsmyip.org/" rel="nofollow noreferrer noopener">whatsmyip.org</a>).

### Verwendung eines Domainnamens

Nehmen wir an, dass unsere externe IP-Adresse 42.42.42.42 ist. Nehmen wir auch an, dass wir einen Domainnamen namens example.com registriert haben. Wir möchten unsere Joomla-Seite auf unserem Raspberry Pi für Besucher bereitstellen, die example.com besuchen. Wenn uns unser Domainnamen-Registrar die Möglichkeit bietet, den **Domain Name System (DNS)**-Server zu konfigurieren, müssen wir einen **MX-Eintrag** im DNS erstellen, der unseren **Domainnamen auf** unsere **IP-Adresse** 42.42.42.42 verweist. Beachten Sie, dass es bis zu 24 Stunden dauern kann, bis alle Internetanbieter den Traffic ihrer Kunden zum konfigurierten MX-Eintrag umleiten.

### Statische IP-Adresse

Die meisten Router werden weiterhin dieselbe interne IP-Adresse an Ihren Raspberry Pi vergeben. Manchmal ist es besser, Ihren Raspberry Pi so zu konfigurieren, dass er eine statische IP-Adresse verwendet:

```shell
sudo nano /etc/network/interfaces
```

ändern in

```shell
iface eth0 inet static
address 192.168.0.35
netmask 255.255.255.0
gateway 192.168.0.1
```

Das Gateway ist die IP-Adresse Ihres Routers. Sie können sie auch mit dem Befehl

```shell
route
```

finden.

# Externe Links

- <a href="https://raspberrypi.org" rel="nofollow noreferrer noopener">Raspberry Pi Foundation</a> (RPF) - offizielle Website und Foren
- <a href="http://elinux.org/RaspberryPiBoard" rel="nofollow noreferrer noopener">Raspberry Pi Wiki</a>, unterstützt von der RPF
- Video der Präsentation <a href="https://youtu.be/u2MFQCoexD0" rel="nofollow noreferrer noopener">Joomla auf Raspberry Pi (mit Nginx)</a> auf dem Joomladay Deutschland 2013 in Nürnberg, Deutschland

*Übersetzt von openai.com*
