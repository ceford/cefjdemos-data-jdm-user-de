<!--
{
    "source": "https://docs.joomla.org/https:",
    "title": "Docker-Einrichtung",
    "description": "",
    "author": ""
}
-->

## Einrichten einer lokalen Joomla-Umgebung mit Docker

Damit Joomla auf Ihrem Computer läuft, benötigen Sie vier Dinge: 
- das Herunterladen und Konfigurieren eines Webservers wie **Apache** oder **nginx**, 
- einen Datenbankdienst wie **MySQL oder** **MariaDB**, 
- und natürlich **PHP** 
- sowie **Joomla.** 

Damit all diese verschiedenen Komponenten tatsächlich miteinander kommunizieren können, verlassen sich die meisten von uns auf gebündelte Software wie **XAMPP**, **Laragon** oder **FlyEnv**.

Traditionelle Setups können jedoch leicht zu Portkonflikten oder Datenbankservern führen, die sich aus unerklärlichen Gründen weigern zu starten. Wenn ein lokaler Server abstürzt, kann es passieren, dass Sie komplette Joomla-Websites immer wieder manuell herunterladen und neu installieren müssen, nur um einen einzelnen PR zu testen, wobei Sie möglicherweise Ihre Arbeit verlieren, während Sie einen Fehler beheben. Das kostet wertvolle Zeit, und die Lösungen sind normalerweise nur vorübergehende Notlösungen.

**Der Wechsel zu Docker ([Mehr über Docker erfahren](https://docs.docker.com/get-started/))** 
Mit Docker können SieÜberspringen Sie die manuelle Konfiguration vollständig. Statt Webserver direkt auf Ihrem Computer zu installieren, schreiben Sie einfach eine einzelne „Rezept“-Datei. Docker lädt automatisch alles im Hintergrund herunter, isoliert und verbindet es. Wenn etwas kaputtgeht, müssen Sie nicht Ihre gesamte Einrichtung neu installieren; Sie starten einfach den Container neu.

In diesem Leitfaden lernen Sie, wie Sie auf einfachste Weise eine lokale Joomla-Umgebung mit Docker zum Laufen bringen und dadurch weniger Zeit mit der Reparatur von Servern und mehr Zeit mit Beiträgen verbringen.

### Voraussetzungen

Bevor wir beginnen, müssen Sie nur eine Sache installiert haben: **Docker Desktop**.

- Laden Sie es von [**docker.com**](https://www.docker.com/) herunter und führen Sie das
  Installationsprogramm aus
- Lassen Sie unter Windows die Option „Use WSL 2 instead of Hyper-V“ aktiviert –
  dadurch geht alles schneller
- Öffnen Sie Docker Desktop und warten Sie, bis unten links der grüne Status
  **Engine running** angezeigt wird.

![Docker Desktop](../../../en/images/hosting-local/docker-setup/01-docker-setup-desktop.png)

Das ist alles.

### Die Datei docker-compose.yml

Wenn mehrere Dienste miteinander kommunizieren müssen – beispielsweise ein Webserver
(Apache/Nginx), PHP und eine Datenbank (MySQL/MariaDB) –, verwenden Sie eine spezielle
Orchestrierungsdatei namens `docker-compose.yml`. Diese Datei dient als
Vorlage für Ihr Projekt und definiert alle erforderlichen Dienste sowie deren
Zusammenarbeit. (Das offizielle Docker-Joomla-Image basiert tatsächlich auf einem
PHP- und Apache-Image. Das bedeutet, dass Sie durch die Verwendung dieses einen
Joomla-Images PHP, Apache und Joomla gebündelt erhalten.)

Erstellen Sie zunächst auf Ihrem Computer einen neuen Ordner für Ihr Projekt (zum
Beispiel auf Ihrem Desktop einen Ordner namens `joomla-docker`).

Erstellen Sie in diesem Ordner eine neue Textdatei und nennen Sie sie genau so:

    docker-compose.yml

Öffnen Sie diese Datei in einem beliebigen Texteditor (z. B. VS Code oder Notepad), fügen Sie den
folgenden Code genau wie angegeben ein und speichern Sie die Datei:

```
    services:
      joomla:
        image: joomla:latest
        ports:
          - "8080:80"
        environment:
          - JOOMLA_DB_HOST=db
          - JOOMLA_DB_USER=joomla
          - JOOMLA_DB_PASSWORD=joomlapass
          - JOOMLA_DB_NAME=joomladb
        depends_on:
          - db
      db:
        image: mariadb:10.11
        environment:
          - MYSQL_ROOT_PASSWORD=rootpass
          - MYSQL_DATABASE=joomladb
          - MYSQL_USER=joomla
          - MYSQL_PASSWORD=joomlapass
        volumes:
          - db_data:/var/lib/mysql
    volumes:
      db_data:
```

### Starten der Umgebung

Öffnen Sie Ihr Terminal (oder PowerShell unter Windows), navigieren Sie zu Ihrem Ordner `joomla-docker` und führen Sie Folgendes aus:

```
    docker compose up -d
```

Wenn Sie dies zum ersten Mal ausführen, lädt Docker die Joomla- und MariaDB-Images herunter, was je nach Internetgeschwindigkeit ein bis zwei Minuten dauern kann. Danach ist jeder weitere Start, wie unten zu sehen, nahezu sofort abgeschlossen.

![Ausgabe des Terminalbefehls zum Starten von Docker](../../../en/images/hosting-local/docker-setup/02-docker-setup-terminal-transcript.png)

### Der Joomla-Installer

Öffnen Sie Ihren Browser und gehen Sie zu `http://localhost:8080`. Sie sollten den
Joomla-Installationsbildschirm sehen.

![Joomla-Installer: Einrichtung des Seitennamens](../../../en/images/hosting-local/docker-setup/03-docker-setup-joomla-installer-sitename.png)

Geben Sie auf dem ersten Bildschirm Ihren Seitennamen und die Administratordaten ein.

![Joomla-Installer: Anmeldedaten](../../../en/images/hosting-local/docker-setup/04-docker-setup-joomla-installer-login-data.png)

Wenn Sie den Bildschirm **Datenbankkonfiguration** erreichen, bleiben die meisten
Benutzer hier hängen:

**Geben Sie nicht `localhost` als Hostnamen ein.**

Da die Datenbank in ihrem eigenen Container ausgeführt wird, benötigt Joomla den
Dienstnamen des Containers – nicht localhost. Verwenden Sie genau diese Werte:

- **Datenbanktyp:** MySQLi
- **Hostname:** `db`
- **Benutzername:** `joomla`
- **Passwort:** `joomlapass`
- **Datenbankname:** `joomladb`

![Joomla-Installer: Datenbankeinrichtung](../../../en/images/hosting-local/docker-setup/05-docker-setup-joomla-installer-database-config.png)

Klicken Sie sich durch die Schritte, schließen Sie die Installation ab, und schon
sind Sie fertig.

Wenn Sie Ihre Arbeit für den Tag beendet haben, führen Sie `docker compose stop` aus, um denpausieren Sie die Container und geben Sie Speicher frei. Ihre Website wird beim nächsten Mal genau dort sein,
wo Sie sie verlassen haben.

------------------------------------------------------------------------

### Häufige Probleme

- **Die Seite unter localhost:8080 wird direkt nach dem Start nicht geladen:** Der
  Datenbank-Container benötigt einige Sekunden, um die Initialisierung abzuschließen. Warten Sie 30
  Sekunden und aktualisieren Sie die Seite.
- **Port 8080 wird bereits verwendet:** Ändern Sie `"8080:80"` in `"8081:80"` in der Compose-Datei und
  rufen Sie die Seite stattdessen unter `localhost:8081` auf.
- **Die Container wurden gestartet, aber Joomla zeigt einen Datenbankfehler an:** Überprüfen Sie noch einmal,
  dass der Hostname im Installationsprogramm `db` und nicht `localhost` lautet.
  
### Profi-Tipp: Zugriff auf die Joomla-Dateien für die Entwicklung

Derzeit läuft Ihre Joomla-Website, aber die eigentlichen PHP-Dateien
sind im Docker-Container verborgen. Wenn Sie zu Joomla beitragen,
PRs testen oder eigene Plugins schreiben möchten, benötigen Sie diese
Dateien auf Ihrem Computer, damit Sie sie in VS Code oder Ihrem
bevorzugten Editor öffnen können.

Um die Dateien aus dem Container auf Ihre lokale Festplatte zu
synchronisieren, müssen Sie lediglich zwei Zeilen (`volumes: `) und
(`- ./site_joomla:/var/www/html`) zum Abschnitt `joomla` Ihrer
`docker-compose.yml`-Datei hinzufügen, wie unten gezeigt:

```yml
services:
  joomla:
    image: joomla:latest
    ports:
      - "8080:80"
    volumes:
      - ./site_joomla:/var/www/html
    # ... (rest of your settings)
```

**Was dies bewirkt:** 

Wenn Sie das nächste Mal `docker compose up -d` ausführen, erstellt
Docker automatisch einen Ordner namens `site_joomla` direkt neben Ihrer
Compose-Datei. Es kopiert den gesamten Joomla-Kern (einschließlich des
Administrations-Dashboards, der Komponenten und der Templates) in
diesen Ordner.

![IDE-Explorer der Joomla-Installation in Docker](../../../en/images/hosting-local/docker-setup/06-docker-setup-ide-explorer.png)

Alle Codeänderungen, die du in diesem Ordner auf deinem Computer vornimmst, werden sofort im laufenden Container aktualisiert! Du bist jetzt vollständig für die lokale Entwicklung eingerichtet.

### Bonus-Tipp 1: Bestimmte Joomla- und PHP-Versionen testen

Beim Testen von PRs werden Maintainer dich häufig bitten, gegen
bestimmte PHP-Versionen zu testen. Mit XAMPP ist ein Downgrade oder Upgrade von PHP ein
Albtraum. Mit Docker dauert es zwei Sekunden.

Anstatt **`image: `**`joomla:latest`** in deiner
**`docker-compose.yml`** zu verwenden, kannst du mithilfe von Tags
genaue Versionen angeben. Wenn du beispielsweise **Joomla 5.2** unter
**PHP 8.3** testen musst, ändere einfach diese eine Zeile in:
**`image: joomla:5.2-php8.3-apache`**

Führe erneut **`docker compose up -d`** aus, und Docker tauscht deine
Serverumgebung sofort aus. Alle verfügbaren Versions-Tags findest du auf der
<a href="https://hub.docker.com/_/joomla" class="ng-star-inserted"
target="_blank" rel="noopener" data-hveid="0"
data-ved="0CAAQ_4QMahgKEwjl8vi347CTAxUAAAAAHQAAAAAQkgI">offiziellen Joomla
Docker-Hub-Seite</a>.

### Bonus-Tipp 2: phpMyAdmin hinzufügen

Wenn Sie von **XAMPP** kommen, vermissen Sie möglicherweise eine visuelle
Oberfläche, um Ihre Datenbank zu betrachten. Sie können **phpMyAdmin** ganz einfach zu
Ihrer Einrichtung hinzufügen, indem Sie am Ende Ihrer
**`docker-compose.yml`**-Datei einen neuen **Service-Block** hinzufügen:

```yml
    phpmyadmin:
        image: phpmyadmin/phpmyadmin:latest
        ports:
          - "8081:80"
        environment:
          - PMA_HOST=db
        depends_on:
          - db
```

Starten Sie Ihre Container neu. Anschließend können Sie auf phpMyAdmin zugreifen, indem Sie
in Ihrem Browser **http://localhost:8081** aufrufen. Melden Sie sich einfach mit **`joomla`**
als Benutzernamen und **`joomlapass`** als Passwort an.

*Übersetzt von openai.com*