<!--
{
  "source": "https://docs.joomla.org/Installing_Joomla!_using_BitNami_Joomla!_stack",
  "title": "Bitnami-Installation ",
  "description": "", 
  "author": ""
}
-->

## Vorwort

**HINWEIS:** Der BitNami Joomla!-Stack existiert nicht mehr als eigenständiger Installer. Stattdessen wird er bereitgestellt als: 1) Eine cloudbasierte Instanz, 2) Ein Container, entweder Kubernetes oder Docker oder 3) Eine virtuelle Maschine. Die virtuelle Maschine läuft auf Ihrem Betriebssystem in einem Hypervisor wie VirtualBox oder VMware Player. Sie wird weiterhin mit allen erforderlichen Abhängigkeiten wie im eigenständigen Installer geliefert.

Option 1 unten ist nicht mehr anwendbar. Darüber hinaus wird in Option 2, BitNami Lamp Stack weiter unten, in der Cloud oder als virtuelle Maschine bereitgestellt. In jedem Fall macht Bitnami eine leistungsfähige lokale Installation von Joomla! einfach und vollständig.

Sie können die neueste Version des Bitnami-Pakets für Joomla! für Windows, Linux und Mac unter <a href="http://bitnami.org/stack/joomla" rel="nofollow noreferrer noopener">http://bitnami.org/stack/joomla</a> herunterladen.

**Überarbeitung benötigt!**

Der BitNami Joomla!-Stack ist ein All-in-One-Installer, der es einfach macht, Joomla auf Ihrem Computer zu installieren. Er ist kostenlos, benutzerfreundlich und eigenständig. Das bedeutet, dass er alle Softwarekomponenten (Abhängigkeiten), die notwendig sind, um Joomla für Entwicklungs- oder Produktionszwecke zu betreiben, einschließlich Apache HTTP Server, MySQL und PHP, bündelt und automatisch konfiguriert.

## Option 1: Joomla! Stack (Empfohlen)

Diese Methode setzt voraus, dass Sie bereits eine
(**W**indows/**L**inux/**M**ac)...**AMP**(Apache HTTP Server, MySQL &
PHP)-Umgebung installiert haben.

### Installation von Joomla! Stack

Unabhängig davon, welches Betriebssystem Sie verwenden (Windows / Linux / Mac), ist der Installationsprozess derselbe.

Laden Sie die neueste Version des Joomla! Stacks von der
<a href="http://bitnami.org/stack/joomla" rel="nofollow noreferrer noopener">BitNami-Website</a> herunter.

Finden Sie den gerade heruntergeladenen Installer (der Dateiname wird ähnlich sein wie bitnami-joomla-VERSION-linux-installer.run). Doppelklicken Sie auf das Symbol, um den Installer zu starten.

Wenn Sie Linux verwenden, müssen Sie der Datei zuerst Ausführungsberechtigungen erteilen, indem Sie diesen Befehl verwenden:

chmod +x /pfad/zum/bitnami-joomla-VERSION-linux-installer.run

<img src="https://docs.joomla.org/images/a/a0/Joomla_welcome2.png" decoding="async" data-file-width="614" data-file-height="538" width="614" height="538" alt="Joomla Bitnami lampstack setup" />

Klicken Sie auf „Weiter“.

<img src="https://docs.joomla.org/images/5/5f/Joomla_components2.png" decoding="async" data-file-width="614" data-file-height="538" width="614" height="538" alt="Joomla Bitnami lampstack components" />

Wählen Sie die Komponenten aus, die Sie installieren möchten. Wenn Sie sich nicht sicher sind, lassen Sie die Standardkomponenten aktiviert. Klicken Sie auf „Weiter“, wenn Sie fertig sind.

<img src="https://docs.joomla.org/images/0/0a/Joomla_directory2.png" decoding="async" data-file-width="614" data-file-height="538" width="614" height="538" alt="Joomla Bitnami lampstack installation directory" />

Jetzt wird gefragt, wo Sie das Programm installieren möchten. Geben Sie den Speicherort an, an dem Sie den BitNami Joomla! Stack installieren möchten, und klicken Sie auf „Weiter“.

<img src="https://docs.joomla.org/images/3/3c/Joomla_userdata2.png" decoding="async" data-file-width="614" data-file-height="538" width="614" height="538" alt="Joomla Bitnami lampstack sdmin account" />

Der Benutzername und das Passwort, die Sie hier angeben, werden verwendet, um das Admin-Konto in Joomla! zu erstellen. Klicken Sie auf „Weiter“, wenn Sie fertig sind.

<img src="https://docs.joomla.org/images/8/8b/Joomla_sitename2.png" decoding="async" data-file-width="614" data-file-height="538" width="614" height="538" alt="Joomla Bitnami lampstack sitename" />

Geben Sie den Namen ein, den Sie für Ihre Joomla-Seite verwenden möchten, und klicken Sie auf „Weiter“.

<img src="https://docs.joomla.org/images/d/dd/JoomlaReadytoinstall2.png" decoding="async" data-file-width="614" data-file-height="538" width="614" height="538" alt="Joomla Bitnami lampstack Ready to install2" />

Der Installer erlaubt Ihnen, ein E-Mail-Konto zu konfigurieren, sodass Joomla! Nachrichten per E-Mail senden kann. Klicken Sie auf „Weiter“.

<img src="https://docs.joomla.org/images/9/9d/JoomlaCopyingfiles2.png" decoding="async" data-file-width="614" data-file-height="538" width="614" height="538" alt="Joomla Bitnami lampstack Copying files" />

Warten Sie einen Moment, während der Installer die Dateien kopiert und Ihre Joomla!-Installation konfiguriert.

<img src="https://docs.joomla.org/images/e/ea/Joomlafinalscreen2.png" decoding="async" data-file-width="614" data-file-height="538" width="614" height="538" alt="Joomla Bitnami lampstack final screen" />

Joomla! ist jetzt eingerichtet und bereit zur Verwendung. Klicken Sie auf „Fertigstellen“, um die Anwendung zu starten.

<img src="https://docs.joomla.org/images/8/8d/JoomlaManager.png" decoding="async" data-file-width="784" data-file-height="586" width="784" height="586" alt="Joomla Bitnami lampstack Manage servers" />

Mit dem Manager-Tool können Sie die Apache- und MySQL-Server einfach starten/stoppen.

<img src="https://docs.joomla.org/images/7/73/Joomlaapplicationscreen2.png" decoding="async" data-file-width="982" data-file-height="729" width="982" height="729" alt="Joomla application screen" />

Sie können die Joomla! Datenbank mit phpMyAdmin einfach verwalten.

<img src="https://docs.joomla.org/images/f/f3/JoomlaphpMyAdmin.png" decoding="async" data-file-width="982" data-file-height="751" width="982" height="751" alt="phpMyAdmin screen" />

## Option 2: BitNami LAMPStack und Joomla!

### Was ist BitNami LAMPStack?

BitNami LAMPStack ist ein kostenloses, einfach zu installierendes Paket, das alle notwendigen Softwarekomponenten (Abhängigkeiten) bündelt, um eine LAMP-Umgebung (Apache, MySQL und PHP für Linux) für Entwicklungs- oder Produktionszwecke einzurichten und auszuführen. Es ist eigenständig, macht keine Änderungen an Ihrem System und kann leicht deinstalliert werden. Sie können die neueste Version von BitNami LAMPStack für Linux unter <a href="http://bitnami.org/stack/lampstack" rel="nofollow noreferrer noopener">http://bitnami.org/stack/lampstack</a> herunterladen. Eine <a href="http://bitnami.org/stack/wampstack" rel="nofollow noreferrer noopener">Windows-Version</a> und eine <a href="http://bitnami.org/stack/mampstack" rel="nofollow noreferrer noopener">OS X-Version</a> sind ebenfalls verfügbar.

Unabhängig davon, welches Betriebssystem Sie verwenden (Windows / Linux / Mac), ist der Installationsvorgang derselbe.

### Installation von BitNami LAMPStack

Finden Sie den Installer, den Sie gerade von der BitNami-Website heruntergeladen haben (der Dateiname wird ähnlich wie bitnami-lampstack-VERSION-linux-installer.run sein). Doppelklicken Sie auf das Symbol, um den Installer zu starten.

<img src="https://docs.joomla.org/images/1/14/Lampstack_welcome.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Bitnami lampstack welcome" />

Klicken Sie auf "Weiter".

<img src="https://docs.joomla.org/images/7/78/Lampstack_directory.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Bitnami lampstack directory" />

Nun wird gefragt, wo Sie das Programm installieren möchten. Wählen Sie den Speicherort auf Ihrem Computer aus und klicken Sie auf "Weiter", wenn Sie fertig sind.

<img src="https://docs.joomla.org/images/2/22/Lampstack_passwd.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Bitnami lampstack password" />

Geben Sie Ihr MySQL-Root-Passwort ein. Dies wird das Passwort für den "root"-Benutzer der Datenbank sein.

<img src="https://docs.joomla.org/images/7/72/LampstackReadytoinstall.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Bitnami lampstack Ready to install" />

Der Installer ist nun bereit, den Installationsprozess zu beginnen. Klicken Sie auf "Weiter".

<img src="https://docs.joomla.org/images/1/19/LampstackCopyingfiles.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Bitnami lampstack Copying files" />

Warten Sie einen Moment, während der Installer die Dateien kopiert und Ihre LAMPStack-Installation konfiguriert.

<img src="https://docs.joomla.org/images/b/bc/Lampstackfinalscreen.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Bitnami lampstack final screen" />

BitNami LAMPStack ist jetzt eingerichtet und bereit zur Verwendung. Klicken Sie auf "Fertigstellen", um die Anwendung zu starten.

### Joomla! manuell installieren

Folgen Sie den Anweisungen, die im Beitrag „Joomla! installieren“ beschrieben sind.

*Übersetzt von openai.com*
