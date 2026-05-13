<!--
{
  "source": "https://docs.joomla.org/J4.x:Installing_Joomla",
  "title": "Joomla installieren ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Die Installation von Joomla! zum ersten Mal ist sehr einfach. Nach Abschluss der vorbereitenden Schritte, dem Einrichten einer Hosting-Umgebung und dem Erstellen einer Datenbank wird der integrierte Web-Installer von Joomla Ihre neue Seite in nur wenigen Minuten einrichten. Die vorherigen Schritte:

### Hosting-Einrichtung

Wenn Sie noch keine Hosting-Umgebung eingerichtet haben, müssen Sie dies jetzt tun, entweder bei einem Hosting-Service oder auf Ihrem lokalen Computer.

Außerdem gibt es einige PHP-Einstellungen, die ausreichend sein müssen, damit Joomla installiert werden kann. Die Einstellungen befinden sich normalerweise in einer *php.ini* oder *user.ini* Konfigurationsdatei auf dem Server. Wenn Sie Shared Hosting nutzen, sprechen Sie mit Ihrem Hosting-Service darüber, wie Sie diese Einstellungen ändern können, falls dies möglich ist. Wenn Sie auf einem localhost arbeiten, zum Beispiel mit XAMPP, oder einem VPS oder dedizierten Host, sollten Sie nicht durch diese Einstellungen eingeschränkt sein und können sie selbst festlegen.

Die Mindestwerte für die *php.ini*-Datei sind unten aufgeführt:

Bitte nutzen Sie das Wort Beiträge anstelle von Artikel.:

- *memory_limit:* 256M
- *upload_max_filesize:* 64M
- *post_max_size:* 64M
- *max_execution_time:* 30

Es ist möglich, mit niedrigeren Werten von upload_max_filesize und post_max_size zu arbeiten, aber größere Erweiterungen werden fehlschlagen und unvorhersehbare Probleme verursachen.

### Datenbankeinrichtung

Wenn Sie noch keine Datenbank eingerichtet haben, tun Sie es jetzt. Es wird im [cPanel Hosting](jdocmanual?article=user/hosting/cpanel-hosting) Tutorial für einen cPanel Hosting-Service behandelt. Es gibt auch ein Tutorial *Erstellen einer Datenbank für Joomla!*, das die Methoden localhost und phpMyAdmin abdeckt.

Sie müssen grundlegende Datenbankinformationen notieren, die benötigt werden, wenn die eigentliche Joomla-Installation gestartet wird.

- Standort der Datenbank, normalerweise *localhost*, auch bei einem Hosting-Service.  
  Es kann sich um den Server eines bestimmten Hosts handeln, wie z. B. *`dbserver1.yourhost.com`*.
- Der Name der Datenbank
- Der Name des Datenbankbenutzers
- Das Passwort des Datenbankbenutzers

## Vorbereitung zur Installation

### Herunterladen und Hochladen von Joomla!-Paketdateien

Laden Sie die aktuelle Version von Joomla! über den Link auf der [Download Joomla](https://downloads.joomla.org/) Seite herunter.

Verschieben Sie die heruntergeladene Joomla-Installationspaket-Zip-Datei auf den Server.  
Für einen Hosting-Service können Sie die Upload-Funktion des cPanel-Dateimanagers verwenden oder einen FTP-Client nutzen, um die heruntergeladene Joomla 5.x-Zip-Datei auf Ihren Server zu übertragen. Es sind mehrere FTP-Clients verfügbar. Hier ist ein detaillierter [Vergleich von FTP-Client-Software](https://en.wikipedia.org/wiki/Comparison_of_FTP_client_software).  
Im Zweifelsfall verwenden Sie FileZilla.

Es ist besser, das heruntergeladene ZIP-Paket auf Ihren Server zu verschieben und es dort zu entpacken, als es lokal zu entpacken und dann die Dateistruktur zu verschieben. Normalerweise laden Sie Ihre Webdateien in den Stammordner Ihres Hosting-Dienstes hoch. Dieser wird typischerweise `public_html` genannt, aber andere Varianten sind `htdocs`, und dies hängt davon ab, wie Ihr Host den Server eingerichtet hat. Für Joomla-Zwecke können Sie die Dateien direkt in *public_html* oder einen von Ihnen darin erstellten Unterordner laden.

**Warnung:** Wenn Sie die Dateien auf Ihrem eigenen Computer entpacken und dann auf Ihren Server kopieren, stellen Sie sicher, dass Sie nur die Ordner und Dateien bewegen, die **innerhalb** des Joomla-Pakets enthalten sind. Wenn Sie die Ordner und Dateien in einen Ordner entpacken, zum Beispiel genannt *`Joomla`*, und dann diesen Ordner hochladen, muss Ihre Seite unter *`yoursitename.com/Joomla`* anstelle von *`yoursitename.com`* aufgerufen werden. Sie können das Unterverzeichnis von Joomla in etwas umbenennen, das besser zur Seite passt, wie zum Beispiel jblog, was möglicherweise praktisch ist. **Hinweis:** Verzeichnisnamen sollten klein geschrieben werden, ohne Leerzeichen und mit Bindestrichen anstelle von Unterstrichen zur Trennung von Wörtern.

Die Dateien des Zip-Pakets können direkt auf dem Host mit verschiedenen Befehlszeilen-Tools (z.B. unzip) extrahiert werden, die auf dem Server installiert sein müssen. Wenn Ihr Hosting-Service das Admin-Tool cPanel verwendet, kann im Dateimanager die Schaltfläche Extrahieren gedrückt werden. Außerdem kann das kostenlose Drittanbieter-Tool Akeeba Kickstart zu diesem Zweck verwendet werden. Die entpackten Dateien und Verzeichnisse werden im aktuellen Ordner abgelegt. Die Extraktion auf Ihrem lokalen Computer hängt von Ihrem Betriebssystem ab. Versuchen Sie einen Rechtsklick und prüfen Sie, ob es ein Extraktionsmenü gibt. In diesem Fall kann Ihr Betriebssystem die Dateien in einen Ordner mit demselben Namen wie die Zip-Datei legen. Nach der Extraktion können Sie die Zip-Datei löschen und den Extraktionsordner in etwas Kurzes und Geeignetes für die Verwendung in einer URL umbenennen.

## Installation starten

Mit den oben genannten Anforderungen erfüllt, einer erstellten Datenbank und den erforderlichen Joomla-Dateien an Ort und Stelle, sind Sie bereit, Joomla zu installieren. Starten Sie den Joomla-Webinstaller, indem Sie Ihren bevorzugten Browser öffnen und zur Domain der Website navigieren. Bei einer Hosting-Installation verwenden Sie *`https://www.yoursitename.com`*. Wenn Sie Joomla lokal installieren, verwenden Sie *`http://localhost/`* und Sie sollten den Installationsbildschirm sehen.

![Joomla installer part 1, installation language and site name](../../../en/images/getting-started/installing-joomla/01-installing-joomla-installer-1.png)

Joomla wird versuchen, das Feld *Sprache auswählen* automatisch anhand der Sprache Ihres Browsers zu identifizieren. Sie können dies bei Bedarf ändern.

Füllen Sie die folgenden Informationen aus.

- **Webseitenname** Der Name Ihrer Webseite – dieser kann jederzeit später auf der Seite der globalen Konfiguration der Webseite geändert werden.

Wenn alles auf der ersten Seite abgeschlossen ist, wählen Sie die Schaltfläche *Login-Daten einrichten* aus, um fortzufahren.

## Anmeldedaten

Du solltest jetzt den Bildschirm mit den Anmeldedaten sehen.

![Joomla installer part 2, login data](../../../en/images/getting-started/installing-joomla/02-installing-joomla-installer-2.png)

Füllen Sie die folgenden Informationen aus.

- **Echter Name** Der Name des Superbenutzers. So wird Joomla Sie begrüßen, wenn Sie sich anmelden.
- **Benutzername des Superbenutzerkontos** Der Benutzername für den *Superbenutzer*. Vermeiden Sie die Verwendung von *admin* als Administratornamen!
- **Administratorkennwort** Denken Sie daran, dass ein Superbenutzer maximalen Zugriff auf die Site- und Administratoroberflächen hat, daher verwenden Sie ein schwieriges Passwort. Verwenden Sie **Mein Profil** in der *Verwaltungsschnittstelle*, um es später zu ändern.
- **E-Mail-Adresse des Superbenutzers** Die E-Mail-Adresse des Superbenutzers. Geben Sie eine gültige E-Mail-Adresse an, falls Sie Ihr Passwort vergessen. Dies ist die E-Mail-Adresse, an die Sie einen Link zum Ändern des Superbenutzerpassworts erhalten.

Wenn alles auf der zweiten Seite abgeschlossen ist, wählen Sie die Schaltfläche *Datenbankverbindung einrichten*, um fortzufahren.

## Datenbankkonfiguration

Geben Sie die Datenbankinformationen ein, die Sie notiert haben, als Sie die Datenbank für diese Installation erstellt haben.

![Joomla installer part 3, database configuration](../../../en/images/getting-started/installing-joomla/03-installing-joomla-installer-3.png)

Zur Vereinfachung dienen diese Anweisungen als Referenz zur Installation mit einer MySQLi-Datenbank. Die Anweisungen auf der Installationsseite sind selbsterklärend, aber hier sind sie noch einmal:

- **Datenbanktyp** MySQLi ist die übliche verwendete Datenbank  
- **Hostname** Wo sich Ihre Datenbank befindet. Häufig ist *localhost*, sogar bei Hosting-Diensten. Einige Hosts verwenden jedoch einen spezifischen Datenbankserver wie *dbserver1.yourhost.com*.  
- **Benutzername** Der Benutzername, der für die Verbindung zur Datenbank verwendet wird  
- **Passwort** Das Passwort für den Datenbankbenutzer (nicht Ihr Administrator-Passwort)  
- **Datenbankname** Der Name der Datenbank  
- **Tabellenpräfix** Dies wird automatisch als Sicherheitsmerkmal generiert. Sie können den zufällig generierten Standard akzeptieren oder ändern. Vergessen Sie nur nicht, das Unterstrichzeichen (`_`) am Ende des Präfixes hinzuzufügen.  
- **Verschlüsselung der Verbindung** gibt an, wie die Verbindung zur Datenbank verschlüsselt werden soll. Wenn Sie es nicht wissen - dann ist es am besten, beim Standard zu bleiben. Dies ermöglicht jedoch Unternehmen, die eine ein- oder zweiseitige Authentifizierung für die Datenbankverbindung verwenden, diese bereitzustellen.  

All diese Einstellungen und mehr können auf der Seite zur globalen Konfiguration der Website unter *Server-Optionen* bearbeitet werden, nachdem die Installation abgeschlossen ist. Beachten Sie, dass Sie Ihre Installation beschädigen, wenn Sie diese Einstellungen nach der Installation ändern, es sei denn, Sie haben eine vollständige Kopie der aktuellen Datenbank, die von der Joomla-Installation verwendet wird. Häufige Verwendungszwecke wären, den Benutzernamen und das Passwort der Datenbank zu aktualisieren oder eine bestehende Installation auf einen neuen Host mit anderen Parametern zu übertragen.

Nachdem Sie die Schaltfläche *Install Joomla* ausgewählt haben, sollten Sie die Fortschrittsleiste der Joomla-Installation sehen.

![Joomla installer part 4, installation progress bar](../../../en/images/getting-started/installing-joomla/04-installing-joomla-installer-4.png)

Sobald die Installation abgeschlossen ist, sollten Sie die Erfolgsseite sehen.

## Abschluss

### Erfolg und Abschluss der Installation

Herzlichen Glückwunsch! Ihre Joomla-Seite ist bereit.

![Joomla installer part 5, your joomla site is ready](../../../en/images/getting-started/installing-joomla/05-installing-joomla-installer-5.png)

Der obige Screenshot zeigt eine Entwicklerinstallation. Eine Produktionsinstallation entfernt automatisch den Installationsordner.

Wenn Sie Joomla sofort nutzen möchten, ohne zusätzliche Sprachen zu installieren, können Sie *Open Administrator* auswählen, um zum *Administrator Dashboard* zu gelangen, oder *Open Site* wählen, um zur Startseite der Seite zu gelangen. Möglicherweise sehen Sie einen Abschnitt mit empfohlenen PHP-Einstellungen.

- **Empfohlene Einstellungen** Diese Einstellungen werden in Ihrer PHP-Konfiguration empfohlen, verhindern jedoch nicht die Installation von Joomla!. Sie können sich auf die obigen Anweisungen beziehen, wie sie geändert werden können, falls dies erforderlich ist.

### Zusätzliche Sprachen

Als Teil des Joomla-Installationsprozesses haben Sie die Möglichkeit, zusätzliche Sprachen zu installieren, bevor Sie die Installation abschließen.

Um dies zu tun, wählen Sie die Schaltfläche Zusätzliche Sprachen installieren.

Dadurch gelangen Sie zu einer zusätzlichen Installationsseite, auf der Sie die gewünschten Sprachen auswählen können.

#### Zusätzliche Sprachen installieren

Eine Liste von Sprachpaketen wird angezeigt.

![Joomla installer part 6, install additional languages](../../../en/images/getting-started/installing-joomla/06-installing-joomla-installer-6.png)

Wählen Sie bis zu 3 Sprachen aus, die Sie installieren möchten. (Mehr als 3 auf einmal kann zu Zeitüberschreitungsprobleme führen; Sie können später weitere installieren.)

Erinnere dich an Folgendes:

- In benutzerdefinierten Distributionen enthaltene Sprachpakete werden in diesem Stadium nicht aufgelistet, da sie bereits installiert sind.
- Eine Version der vorgeschlagenen Pakete wird zur Joomla-Hauptversion passen (5.0.x, 5.1.x, etc.). Die Nebenversionsnummer des Pakets muss nicht übereinstimmen, z.B. installieren Sie Version 5.0.3 und ein 5.0.2-Sprachpaket wird angezeigt.
- Nicht übereinstimmende Sprachpakete im obigen Beispiel können unübersetzte Zeichenfolgen aufweisen.
- Die nicht übereinstimmenden Sprachpakete werden als Update angeboten, wenn die Pakete von den registrierten Übersetzungsteams aktualisiert werden. Das verfügbare Update wird sowohl im Kontrollzentrum als auch in **Erweiterungen → Update** angezeigt. Dieses Verhalten ist ähnlich wie bei **Erweiterungen → Sprachen installieren**.

Wählen Sie *Weiter* und ein Fortschrittsbalken wird angezeigt, während das oder die Sprachpakete installiert werden.

#### Standardsprache auswählen

Wenn die Installation der Sprachen abgeschlossen ist, wird Ihnen nun ein ähnlicher Bildschirm mit der Nachricht *Herzlichen Glückwunsch! Ihre Joomla-Seite ist bereit.* angezeigt. Der Unterschied wird eine Liste der installierten Sprachen sein, die es Ihnen ermöglicht, die Standardsprache für die Seite und die Administrator-Oberfläche auszuwählen.

![Joomla installer part 7, choose default language](../../../en/images/getting-started/installing-joomla/07-installing-joomla-installer-7.png)

- Wählen Sie die Standardsprache aus, die Sie verwenden möchten.
- Wenn Sie die Standardsprache ausgewählt haben, klicken Sie auf die Schaltfläche *Standardsprache festlegen*, um zu bestätigen.
- Es wird eine Systemnachricht angezeigt, die bestätigt, dass Joomla die STANDARD-ADMINISTRATOR- und SEITENSPRACHE festgelegt hat. Diese Nachricht kann geschlossen werden.

#### Abschließen

Sie können jetzt zum *Administrator-Dashboard* navigieren. Melden Sie sich an, indem Sie *Administrator öffnen* auswählen, oder gehen Sie direkt zur Startseite Ihrer Website, indem Sie *Seite öffnen* auswählen.

*Übersetzt von openai.com*

