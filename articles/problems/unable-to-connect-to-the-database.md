<!--
{
  "source": "https://docs.joomla.org/Unable_to_connect_to_the_database",
  "title": "Datenbankverbindung",
  "description": "", 
  "author": ""
}
-->

## Fehler: Verbindung konnte nicht hergestellt werden

Wenn Sie während der Installation einen Fehler "**Verbindung zur Datenbank konnte nicht hergestellt werden**" erhalten, überprüfen Sie, ob Sie Ihre MySQL/MariaDB-Datenbankdetails korrekt eingegeben haben. Das **Installationsskript** lässt Sie nicht fortfahren, sofern die Details nicht korrekt sind.

Beachten Sie, dass von Ihnen nicht erwartet wird, während der Installation einen Datenbankbenutzer und ein Passwort zu erstellen. Diese müssen im Vorfeld erstellt werden.

Wenn der Fehler nach dem Umzug Ihrer Website zu einem anderen Host auftritt, überprüfen Sie die folgenden Elemente Ihrer *configuration.php*-Datei. Die üblichen Datenbankeinstellungen sind die folgenden:

```php
    public $dbtype = 'mysqli';
    public $host = 'localhost';
    public $user = 'yourdbuser';
    public $password = 'yourdbpassword';
    public $db = 'yourdbname';
    public $dbprefix = 't6q6i_';
```

Wenn der Fehler an einer Seite auftritt, die vorher funktioniert hat, gibt es mehrere mögliche Gründe, die manchmal vorübergehend und manchmal zufällig sind.

## Die häufigsten Fehler

1. Manchmal sehen Sie diese Meldung, wenn MySQL/MariaDB auf Ihrem Server gestoppt wurde. Ihr Serveradministrator kann MySQL/MariaDB vorübergehend herunterfahren, um Wartungsarbeiten durchzuführen. In solchen Fällen wird Ihre Website wahrscheinlich bald wieder verfügbar sein.
2. Ihr Datenbankbenutzer wurde gelöscht. Sollte dies der Fall sein, müssen Sie Ihren Datenbankbenutzer mit demselben Benutzernamen und Passwort, das bei der ersten Installation von Joomla vorhanden war, neu erstellen. Verwenden Sie das Kontrollpanel Ihrer Domain, um dies zu verwalten, oder kontaktieren Sie Ihren Serveradministrator.
3. Ihr Datenbankbenutzername oder Passwort hat sich geändert.

*Übersetzt von openai.com*

