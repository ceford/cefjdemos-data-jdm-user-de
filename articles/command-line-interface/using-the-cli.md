<!--
{
  "source": "https://docs.joomla.org/J4.x:Using_the_CLI",
  "title": "Verwendung der CLI",
  "description": "", 
  "author": ""
}
-->

## Die Befehlszeilenschnittstelle (CLI)

Wenn Sie Terminalzugang zu dem Server haben, auf dem Ihre Website läuft, können Sie das Joomla CLI verwenden, um routinemäßige Aufgaben auszuführen, ohne die Joomla-Benutzeranmeldedaten eingeben zu müssen. Selbst ohne Terminalzugang, wie es bei manchen Shared-Hosting-Konten der Fall ist, können Sie CLI-Befehle mit Hilfe von Cron-Jobs ausführen. CLI-Befehle sind oft schneller oder bequemer als die entsprechenden Aufgaben, die über die Joomla (oder cPanel) Administrator-Oberfläche erledigt werden. Das Erstellen von Backups der Website oder das Festlegen der Website auf offline/online sind Beispiele, bei denen Sie möglicherweise das CLI verwenden möchten.

Das Joomla-Kernsystem verfügt über etwa 30 nützliche Befehle, und Sie können mit zusätzlichen Erweiterungen noch mehr hinzufügen. Zum Beispiel könnten Sie externe Daten wie Geolokations- oder Wechselkursdaten für eine benutzerdefinierte Komponente abrufen.

## Verwendung der Kommandozeile

Die Kommandozeile (CLI) wird verwendet, indem das PHP-Kommandozeilenprogramm aufgerufen wird. Dies unterscheidet sich häufig von dem, das von einem Webserver wie Apache verwendet wird. Wenn Sie einen Cron-Job verwenden, müssen Sie eventuell den vollständigen Pfad zum PHP-Programm angeben, etwa so:

    /usr/local/bin/php /home/username/public_html/[optional unterordner]/cli/joomla.php

Andernfalls, wenn Sie die Kommandozeile im Terminal verwenden, wechseln Sie in das Joomla-CLI-Verzeichnis und führen Sie den Befehl ohne Parameter aus:

    cd /home/username/public_html/[optional unterordner]/cli
    php joomla.php

![Liste der Befehle](../../../en/images/command-line-interface/using-the-cli/01-cli-command-list.png)

Probieren Sie einige Hilfebefehle aus, um sich mit den Erwartungen vertraut zu machen:

    php joomla.php help
    php joomla.php list
    php joomla.php help cache:clean
    php joomla.php help config:get

Jede der Hilfe-Beschreibungen und Gebrauchsanweisungen sind fest kodiert in den Konsolenbibliotheksdateien oder in Plugins von Drittanbietern.

Versuchen Sie einige einfache Aktionsbefehle:

    php joomla.php config:get debug
    php joomla.php cache:clean
    php joomla.php site:down
    php joomla.php site:up

## Optionen

Wenn Sie Befehle aus einem Cron aufrufen, möchten Sie möglicherweise keine Ausgabe sehen:

    php joomla.php -q cache:clean

Beachten Sie, dass Optionen entweder ein Leerzeichen oder ein =-Zeichen verwenden können, aber Variablen müssen ein =-Zeichen verwenden:

    php joomla.php session:gc --application administrator
    php joomla.php session:gc --application=administrator

    php joomla.php config:set debug=true

## Befehle

Eine kurze Erklärung zu jedem Kernbefehl.

### Cache

Löschen Sie abgelaufene Einträge aus dem System-Cache:

    php joomla.php cache:clean --help
    php joomla.php cache:clean

![Ausgabe von Cache-Reinigung](../../../en/images/command-line-interface/using-the-cli/02-cli-cache-clean.png)

    php joomla.php cache:clean expired

![Ausgabe von Cache-Reinigung abgelaufen](../../../en/images/command-line-interface/using-the-cli/03-cli-cache-clean-expired.png)

### Konfiguration

Holen oder setzen Sie eine Konfigurationsvariable, eine der Variablen in
configuration.php oder eine Gruppe von Variablen. Gültige Gruppen sind db, session,
mail,

    php joomla.php config:get debug --help
    php joomla.php config:get debug

![Ausgabe von Konfig. get debug](../../../en/images/command-line-interface/using-the-cli/04-cli-get-debug.png)

    php joomla.php config:set debug=true

![Ausgabe von Konfig. set debug](../../../en/images/command-line-interface/using-the-cli/05-cli-set-debug.png)

    php joomla.php config:get --group session

![Ausgabe von Konfig. get group session](../../../en/images/command-line-interface/using-the-cli/06-cli-config-get-group-session.png)

### Kern

Überprüfen Sie auf Updates oder aktualisieren Sie Joomla.

    php joomla.php core:check-updates --help
    php joomla.php core:check-updates

![Ausgabe von Kern-Updates prüfen](../../../en/images/command-line-interface/using-the-cli/07-cli-check-updates.png)

    php joomla.php core:update --help
    php joomla.php core:update

![Ausgabe von Kern-Update](../../../en/images/command-line-interface/using-the-cli/08-cli-core-update.png)

### Datenbank

Exportieren oder importieren Sie die Datenbank. Sie können alle Tabellen oder eine
ausgewählte Tabelle exportieren oder importieren. Verwenden Sie diese Funktion nicht, um alle Tabellen einer
mehrsprachigen Website zu importieren. Es gibt ein Problem, das Smart Search
vollständig blockieren könnte.

    php joomla.php database:export --help
    php joomla.php database:export --table f4rc2_banners --folder /home/username/tmp/mydb (eine Tabelle)
    php joomla.php database:export --folder /home/username/tmp/mydb (alle Tabellen)

    php joomla.php database:import --help
    php joomla.php database:import --table /home/username/tmp/mydb/f4rc2_banners (eine Tabelle)
    [FEHLER] Die Datei /home/username/tmp/mydb/f4rc2_banners.xml existiert nicht.
    php joomla.php database:import --folder /home/username/tmp/mydb (alle Tabellen in diesem Ordner)

### Erweiterung

Listen, Entdecken, Installieren oder Entfernen von Erweiterungen.

    php joomla.php extension:list --help
    php joomla.php extension:list
    php joomla.php extension:list --type component
    php joomla.php extension:list --type file
    php joomla.php extension:list --type language
    php joomla.php extension:list --type library
    php joomla.php extension:list --type module
    php joomla.php extension:list --type package
    php joomla.php extension:list --type plugin
    php joomla.php extension:list --type template

    php joomla.php extension:discover --help
    php joomla.php extension:discover
    php joomla.php extension:discover:list
    php joomla.php extension:discover:install --eid=

    php joomla.php extension:install --help
    php joomla.php extension:install --path=
    php joomla.php extension:install --url=

    php joomla.php extension:remove --help
    php joomla.php extension:remove

### Finder

Leert und erstellt den Index neu (Suchfilter bleiben erhalten).

    php joomla.php finder:index --help
    php joomla.php finder:index
    php joomla.php finder:index purge

![Ausgabe von Finder-Index leeren](../../../en/images/command-line-interface/using-the-cli/09-cli-finder-index-purge.png)

### Planer

Listen, ändern Sie den Status oder führen Sie geplante Aufgaben aus.

    php joomla.php scheduler:list --help
    php joomla.php scheduler:list

    php joomla.php scheduler:state --help
    php joomla.php scheduler:state (interaktives Eingabefeld für Aufgaben-ID)

    php joomla.php scheduler:run --help
    php joomla.php scheduler:run --id ID
    php joomla.php scheduler:run --all

### Sitzung

Führen Sie die Garbage Collection für die Sitzung durch.

    php joomla.php session:gc --help
    php joomla.php session:gc
    php joomla.php session:gc --application administrator

    php joomla.php session:metadata:gc --help
    php joomla.php session:metadata:gc

### Webseite

Schaltet die Webseite offline oder online.

    php joomla.php site:down --help
    php joomla.php site:down

    php joomla.php site:up --help
    php joomla.php site:up

### Aktualisierung

Prüft auf anstehende Erweiterungs-Updates. Entfernt alte Dateien, die während eines Joomla-Updates
hätten gelöscht werden sollen.

    php joomla.php update:extensions:check --help
    php joomla.php update:extensions:check

    php joomla.php update:joomla:remove-old-files --help
    php joomla.php update:joomla:remove-old-files

![Ausgabe von Joomla alte Dateien entfernen](../../../en/images/command-line-interface/using-the-cli/10-cli-update-remove-old-files.png)

### Benutzer

Listen und verwalten von Benutzern.

    php joomla.php user:list --help
    php joomla.php user:list

    php joomla.php user:add --help
    php joomla.php user:add --username cinderella --name Cinderella --email cinders@localhost --usergroup Manager (Eingabeaufforderung für Passwort)
    php joomla.php user:add (auffordert nach Daten)

![Ausgabe von Benutzer hinzufügen mit Aufforderungen](../../../en/images/command-line-interface/using-the-cli/11-cli-add-user.png)

    php joomla.php user:addtogroup --help
    php joomla.php user:addtogroup (auffordert nach Daten)
    php joomla.php user:addtogroup --usernam=cinderella --group=Manager

    php joomla.php user:removefromgroup --help
    php joomla.php user:removefromgroup (auffordert nach Daten)
    php joomla.php user:removefromgroup --usernam=cinderella --group=Manager

    php joomla.php user:reset-password --help
    php joomla.php user:reset-password (auffordert nach Daten)
    php joomla.php user:reset-password --username=cinderella (auffordert nach Passwort)

    php joomla.php user:delete --help
    php joomla.php user:delete (auffordert nach Benutzernamen)
    php joomla.php user:delete --username=cinderella (auffordert nach Bestätigung - "y" zur Bestätigung)

*Übersetzt von openai.com*

