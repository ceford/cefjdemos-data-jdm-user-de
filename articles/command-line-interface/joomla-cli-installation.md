<!--
{
  "source": "https://docs.joomla.org/J4.x:Joomla_CLI_Installation",
  "title": "Joomla CLI-Installation  ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Das Joomla CMS wird normalerweise über eine Webbrowser-Oberfläche installiert. Erfahrene Benutzer möchten Joomla jedoch möglicherweise mit Befehlen in einer Terminaloberfläche installieren. Dies ermöglicht eine schnelle Bereitstellung mehrerer Joomla-Instanzen.

## Systemanforderungen

Joomla benötigt PHP, eine Datenbank und einen Webserver. Für die neuesten Informationen über die unterstützte Software und die minimalen sowie empfohlenen Versionen besuchen Sie bitte die Seite <a href="https://manual.joomla.org/docs/next/get-started/technical-requirements/" rel="noreferrer noopener">Technische Anforderungen</a>.

Die Installation kann auf zwei verschiedene Arten durchgeführt werden:

1.  Manuelle Installation
2.  Script-gesteuerte automatische Installation

## Manuelle Installation

Die manuelle Installation bietet eine gute Kontrolle während des Installationsprozesses. Jeder Schritt ist im Terminal sichtbar und kann bei einer fehlerhaften Eingabe mit `Strg+C` abgebrochen werden.

### Zu erledigende Schritte

1. Laden Sie das Zip- oder Tar-Installationspaket auf den Webserver hoch.
2. Entpacken Sie die Zip- oder Tar-Datei.
3. Benennen Sie den entpackten Ordner um und verschieben Sie ihn an einen geeigneten Ort im Dokumentenstamm des Webservers.
4. Wechseln Sie in den Ordner, der den Joomla-Code enthält, und führen Sie den folgenden Befehl aus:<br>
   `php installation/joomla.php install`
5. Sie werden nach den für die Installation erforderlichen Parametern gefragt, wie im folgenden Beispielprotokoll:
```bash
php installation/joomla.php install

Installiere Joomla
=================

Überprüfe Systemanforderungen...OK
Sammle Konfiguration...

Geben Sie den Namen Ihrer Joomla-Website ein:
> J51
Geben Sie den echten Namen Ihres Super-Benutzers ein:
> John Doe
Legen Sie den Benutzernamen für Ihr Super-Benutzerkonto fest:
> johndoe
Legen Sie das Passwort für Ihr Super-Benutzerkonto fest:
>
Geben Sie die E-Mail-Adresse des Website-Super-Benutzers ein:
> johndoe@example.com
Datenbanktyp. Unterstützte: mysql, mysqli, pgsql [mysqli]:
>
Datenbankserver [localhost]:
>
Datenbankbenutzername:
> j4
Datenbankpasswort:
>
Datenbankname [joomla_db]:
> j51
Präfix für die Datenbanktabellen [u5dke_]:
>
Verschlüsselung für die Datenbankverbindung. Werte: 0=Keine, 1=Einseitig, 2=Zweiseitig [0]:
>
Relativer oder absoluter Pfad zum öffentlichen Ordner []:
>
OK
Überprüfe DB-Verbindung...OK
Erstelle und befülle die Datenbank...OK
Schreibe configuration.php und zusätzliche Einrichtung ...OK
Lösche /installations-Ordner...OK
[OK] Joomla wurde installiert
```

Sobald das Skript erfolgreich abgeschlossen ist, kann auf die neue Website über Ihren Webbrowser zugegriffen werden.

### Hinweise

* Achten Sie genau auf Ihre Eingaben. Im Skript ist es nicht möglich, einen Schritt zurückzugehen. Wenn die Eingabe falsch ist, muss das Skript abgebrochen werden.
* Der Name Ihrer Joomla-Website erscheint in der Titelleiste des Administrators, daher halten Sie ihn kurz und unverwechselbar. Er kann später geändert werden.
* Der tatsächliche Name Ihres Super-Benutzers kann später geändert werden.
* Der Benutzername für Ihr Super-Benutzerkonto sollte nicht ähnlich wie *admin* sein. Es ist potenziell unsicher, da er leicht von einem Hacker erraten werden kann.
* Das Benutzerpasswort muss 12 Zeichen lang sein.
* Der Standard-Datenbanktyp ist *mysqli*. Unterstützte Datenbanktypen sind MySQL (mysql) und PostgreSQL (pgsql) sowie kompatible Typen wie MariaDB.
* Der Datenbankserver ist fast immer `localhost`. Eine IP-Adresse oder ein Hostname sollte hier nur eingegeben werden, wenn der zuständige Datenbankserver auf einem anderen Host installiert ist. Der Terminalbenutzer muss jedoch über Schreibberechtigungen auf dem ausgewählten Host verfügen. Diese Informationen erhalten Sie von Ihrem Internetanbieter (ISP).
* Der Datenbankbenutzername ist in der Regel unterschiedlich zum Namen des Super-Benutzers.
* Das Datenbankpasswort für die Joomla-Datenbank ist fast immer anders als das Super-Benutzerpasswort.
* Der Datenbankname standardmäßig `joomla_db`, aber oft werden andere Namen verwendet.
* Das Präfix für die Datenbanktabellen wird auf eine zufällige Auswahl von fünf Zeichen gesetzt. Der Wert wird verwendet, um Joomla-Tabellen von anderen Tabellen in der Datenbank zu trennen, falls diese auch von anderen Anwendungen genutzt wird.
* Die Verschlüsselungseinstellung für die Datenbankverbindung wird selten verwendet. Wenn von Ihrem ISP nichts anderes empfohlen wird, lassen Sie diesen Wert auf dem Standardwert [0].

## Skriptgesteuerte automatische Installation

Die Installation von Joomla wird durch eine *joomla.php*-Datei gesteuert, die sich im *installation*-Unterordner befindet, nachdem das Joomla-Paket entpackt wurde. Jede Programmiersprache, die das Aufrufen und Ausführen von PHP-Dateien ermöglicht, erlaubt es Ihnen, ein Skript zu erstellen, das die notwendigen Vorbereitungen und die eigentliche Installation mit benutzerdefinierten Variablen automatisiert. Eine Liste von Parametern kann mit dem folgenden Befehl abgerufen werden:
```bash
php installation/joomla.php help install
```
Hier ist ein Beispiel für ein Shell-Skript namens jinstall.sh, das im Joomla-Stammverzeichnis für eine einfache Joomla-Installation erstellt wurde:
```
#!/bin/bash

php installation/joomla.php install \
--site-name=SEITEN-NAME \
--admin-user=ADMIN-BENUTZER \
--admin-username=ADMIN-BENUTZERNAME \
--admin-password=ADMIN-PASSWORT \
--admin-email=johndoe@example.com \
--db-type=mysqli \
--db-host=localhost \
--db-user=j51 \
--db-pass=Garbage1n0ut \
--db-name=j51 \
--db-prefix=xyz12_ \
--db-encryption=0 \
--public-folder=j51
```
Wenn die Berechtigungen auf 700 gesetzt sind, ist es eine einfache Angelegenheit, das Skript von der Kommandozeile mit `./jinstall.sh` aufzurufen, und Joomla ist buchstäblich im Handumdrehen installiert. Das Skript hätte bearbeitet werden können, um Platzhalterwerte zu ändern, oder sie könnten später nach dem Administrator-Login geändert werden.

Wenn Sie diesen Ansatz verwenden, denken Sie daran, Ihr jinstall.sh-Skript zu löschen oder es aus Ihrem Webverzeichnis zu entfernen, um es später an anderer Stelle zu verwenden. Der Installationsordner wird am Ende des Installationsprozesses entfernt. Das heißt, das jinstall.sh-Skript ein zweites Mal auszuführen, wird nicht funktionieren.
*Übersetzt von openai.com*

