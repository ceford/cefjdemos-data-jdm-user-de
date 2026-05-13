<!--
{
  "source": "https://docs.joomla.org/How_to_debug_SMTP_mail_in_Joomla_4",
  "title": "SMTP-Mail und Gmail ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Auf der Seite Globale Konfiguration im Server-Panel gibt es eine Option zur Auswahl eines Mail-Delivery-Agenten. Die Standardeinstellung ist *PHP Mail*. Wenn dies nicht funktioniert, könnte es ratsam sein, SMTP zu verwenden. Es nutzt denselben Mechanismus wie Ihre Mail-Anwendung. Es gibt mehrere Einstellungen, die korrekt konfiguriert werden müssen. Kurz zusammengefasst:

Gehen Sie zu **Globale Konfiguration** und wählen Sie den **Server**-Tab. Suchen Sie nach dem *Mail*-Panel am unteren Ende des Formulars.

- **Mailer** auf SMTP einstellen. Es erscheinen mehrere weitere Felder.
- **SMTP Host** Standardmäßig ist dies localhost, aber das wird wahrscheinlich nicht funktionieren. Es muss auf den Host eingestellt werden, der Ihre ausgehende Mail verarbeitet, zum Beispiel ein Gmail-Konto.
- **SMTP Port** Der Standardwert ist 25. Überprüfen Sie, ob dies dem Wert entspricht, den Ihr SMTP-Host erwartet.
- **SMTP Sicherheit** Der Standard ist *Keine*, aber es ist wahrscheinlich, dass Sie STARTTLS benötigen.
- **SMTP Authentifizierung** Dies kann möglicherweise nicht erforderlich sein, wenn Sie ein Heimnetzwerk verwenden, das erwartet, dass ausgehende E-Mails keine Authentifizierung erfordern. Andernfalls:
- **SMTP Benutzername** und **SMTP Passwort** Geben Sie die Werte ein, die Sie verwenden, um auf Ihr E-Mail-Konto über das Internet zuzugreifen.
- Wählen Sie die Schaltfläche **Testmail senden**.

## Verwendung von Gmail

Wenn Sie ein funktionierendes Gmail-Konto haben, können Sie Gmail als Ihren Mail-Server verwenden, indem Sie es in der globalen Konfiguration einstellen.

Auf der Registerkarte Server setzen Sie die folgenden Einstellungen:

- Mailer: SMTP
- SMTP-Host: smtp.gmail.com
- SMTP-Port: 465
- SMTP-Sicherheit: SSL/TLS
- SMTP-Authentifizierung: Ja
- Setzen Sie die nächsten beiden Zeilen mit Ihren Informationen. Sie müssen ein anwendungsspezifisches Passwort (ASP) verwenden, wie unten beschrieben.
- SMTP-Benutzername: Ihr Gmail-Benutzername
- SMTP-Passwort: das anwendungsspezifische Passwort (ASP), das Sie erstellt haben, wie unten beschrieben.

Folgende Kombinationen funktionieren ebenfalls:

- SMTP-Port: 587
- SMTP-Sicherheit: STARTTLS
- SMTP-Port: 25
- SMTP-Sicherheit: STARTTLS

Das SSL-Modul muss in Apache nicht aktiviert sein.

Die OpenSSL-Erweiterung muss in PHP aktiviert sein. Die Details finden Sie auf der [php.net-Installationsseite](https://www.php.net/manual/en/openssl.installation.php).

Wenn Sie WAMP unter Windows verwenden, ist das openssl-Modul standardmäßig nicht aktiviert, und Sie müssen es aktivieren. Um dies zu tun:

1. Öffnen Sie die php.ini-Datei und kommentieren Sie die Zeile `extension=php_openssl.dll` aus, indem Sie das Semikolon ; am Anfang der Zeile entfernen.
2. Speichern Sie die php.ini-Datei und starten Sie den Apache-Dienst neu.

Beachten Sie, dass wenn Sie die 2-Stufen-Verifizierung in Gmail verwenden, Sie ein neues Passwort unter Einstellungen - Konten - Kontoeinstellungen ändern - Sonstige Google Kontoeinstellungen - Sicherheit - 2-Stufen-Verifizierung - Verwaltung Ihrer anwendungsspezifischen Passwörter hinzufügen müssen.

Wenn das neue anwendungsspezifische Passwort (ASP) in Gruppen von vier Zeichen dargestellt wird, die durch Leerzeichen getrennt sind, stellen Sie sicher, dass Sie **die Leerzeichen NICHT eingeben** in das SMTP-Passwort in den Mail-Server-Einstellungen in Joomla.

- Anwendungsspezifische Passwörter (ASPs): Siehe die Google Support-Seite mit dem Titel 
  [Anmelden mit App-Passwörtern](https://support.google.com/accounts/answer/185833).
- 2-Stufen-Verifizierung: Siehe die Google Support-Seite mit dem Titel 
  [Zwei-Faktor-Authentifizierung aktivieren](https://support.google.com/accounts/answer/185839).

## Debugging

Wenn die E-Mail nicht gesendet wird oder nie ankommt:

- Wählen Sie **Plugins** aus dem **Home Dashboard → Site-Bereich**.
- Suchen und aktivieren Sie das **System - Debug** Plugin und konfigurieren Sie es:
- Setzen Sie **Erlaubte Gruppen** auf *Super Users*, um die Debug-Ausgabe auf Ihre 
  eigene Anmeldesitzung sowohl im Backend als auch im Frontend zu beschränken. 
  Wenn Sie sich nicht als Super User im Frontend anmelden möchten, erstellen Sie 
  eine eindeutige Benutzergruppe für Ihre Testaktivitäten und wählen Sie diese 
  Benutzergruppe aus der Liste der erlaubten Benutzergruppen aus.
- **Speichern & Schließen**

- Wählen Sie **Globale Konfiguration** aus dem **Home Dashboard → Site-Bereich**.
- Stellen Sie im *System*-Tab **Systemdebugging** auf *Ja*.
- Stellen Sie im *Server*-Tab **Fehlerberichterstattung** auf *Maximum*.
- Notieren Sie sich im *Logging*-Tab den Inhalt von *Pfad zum Log-Verzeichnis*, 
  normalerweise *\[etwas\]/administrator/logs*.
- Setzen Sie **Beinahe alles protokollieren** auf *Ja*.
- Setzen Sie im *Benutzerdefiniertes Protokollieren*-Bereich das Feld 
  *Log-Kategorien* auf *mail* (keine Anführungszeichen).
- **Speichern** Sie, um die Debug-Einstellungen zu speichern.
- Wählen Sie im **Server**-Tab den *Test-E-Mail senden*-Button am unteren 
  Rand der Seite.

Wenn es während der Tests Probleme im Code gibt, sollten Sie eine 
*Stack Trace* erhalten, die Ihnen oder anderen hilft, das Problem 
zu diagnostizieren. Suchen Sie auch nach einer Datei im Logs-Verzeichnis 
mit einem Namen wie *administrator/logs/everything.php* und öffnen Sie sie 
mit einem Texteditor. Es kann hilfreich sein zu sehen, was protokolliert 
wurde, als die Nachricht gesendet wurde.

*Übersetzt von openai.com*

