<!--
{
  "source": "https://docs.joomla.org/J4.x:Global_Configuration",
  "title": "Globale Konfiguration ",
  "description": "", 
  "author": ""
}
-->

## Übersicht

Bei der Installation erstellt eine Joomla-Seite eine Datei mit dem Namen **configuration.php** im Wurzelverzeichnis der Seite. Diese Datei enthält die Werte der Konfigurationsvariablen, die für die gesamte Seite gelten. Beispiele umfassen den Seitennamen und die Datenbankanmeldedaten, die während des Installationsprozesses eingegeben wurden. Es gibt viele weitere Variablen, die anfänglich mit geeigneten Werten versehen werden.

Das Formular für die Globale Konfiguration ermöglicht es einem Super User, die Konfigurationsvariablen den Bedürfnissen der Seite anzupassen. Zusätzlich zu den in der configuration.php gespeicherten Variablen hält das Formular Informationen über Protokollierung, Filterung und Zugangskontrolle fest, von denen einige in der Datenbank gespeichert werden.

## Bildschirmfoto

Das Formular zur globalen Konfiguration hat sechs Registerkarten, von denen einige lange Listen von Parametern enthalten. Verwenden Sie die Schaltfläche *Inline-Hilfe umschalten* in der Symbolleiste, um mehr oder weniger Informationen zu jedem Parameter anzuzeigen.

![Registerkarte Globale Konfiguration - Website](../../../en/images/configuration/global-configuration/01-global-configuration-site-tab.png)

Einige Parameter zeigen oder verbergen andere Parameter, wenn sie ausgewählt werden. Zum Beispiel zeigt die **Website offline**-Schaltfläche mehr Felder an, wenn sie auf *Ja* gesetzt ist, als wenn sie auf *Nein* gesetzt ist. Mit erweiterter Inline-Hilfe sind die meisten Felder ausreichend gut dokumentiert, sodass hier keine weitere Erklärung erforderlich ist, abgesehen von einigen zusätzlichen Benutzerhinweisen auf jeder Registerkarte.

## Site-Registerkarte

### Site-Panel

- **Site-Name** Dies ist der Name der Website, der im Administrator-Login-Formular und im Site-Link in der Titelleiste angezeigt wird. Passen Sie ihn bei Bedarf an.
- **Seite offline** Es gibt ein separates [Tutorial](jdocmanual?article=user/configuration/site-offline) zu diesem Thema.
- **Standard-Listenlimit** legt die maximale Standardanzahl von Elementen pro Seite in Listenansichten fest. Standardmäßig ist dieser Parameter auf 20 eingestellt, aber Listenansichten enthalten normalerweise ein Dropdown-Menü zur Auswahl anderer Werte im Bereich von 5 bis 100. Weniger Werte werden schneller verarbeitet und erfordern weniger Scrollen durch den Benutzer.

### Metadaten-Panel

- **Metadatenbeschreibung der Seite** Dies ist die standardmäßige Metadatenbeschreibung, die verwendet wird, wenn eine solche Beschreibung nicht in einem Meta-Beschreibungsfeld des Beitrags oder eines Menü-Meta-Beschreibungsfeldes angegeben ist. Wenn alle drei leer sind, wird die Metadatenbeschreibung von der Seitenanzeige weggelassen. Suchmaschinen verwenden diese oft, um einen beschreibenden Text für eine Seite bereitzustellen. Fehlt sie, verwenden Suchmaschinen möglicherweise Text aus dem Inhalt der Seite, was unpassend sein kann. Empfohlen wird eine Beschreibung des Zwecks der Seite mit etwa 20 Wörtern.
- **Urheberrechte des Inhalts** legt den *Rechte*-Metadateneintrag fest. Falls zutreffend, beschreiben Sie hier, welche Rechte andere haben, diesen Inhalt zu nutzen. Dieser Metadateneintrag wird von Webseiten weggelassen, wenn dieser Eintrag leer ist. Beispiel: Creative Commons-Lizenz Namensnennung 4.0 International (siehe den [Creative Commons-Lizenzwähler](https://creativecommons.org/choose/)).

### SEO-Panel

SEO ist ein Akronym für *Suchmaschinenoptimierung*. Einstellungen in dieser Gruppe ändern das Format der URLs für Seiten auf der Website, was erhebliche Auswirkungen auf das Suchranking einzelner Seiten und die gesamte Website haben kann. SEO-URLs sind lesbarer für Menschen.

**Tipp** Nach Änderungen der Einstellungen in dieser Gruppe aktualisieren Sie bitte die bereits in Ihrem Webbrowser geöffneten Seiten der Website (in der Regel erledigen dies Strg+R oder Cmd+R). Ein Versäumnis zu aktualisieren kann bedeuten, dass das Format der internen Weblinks der Seite nicht mehr mit dem übereinstimmt, was Joomla erwartet, was den Anschein von defekten Links erwecken könnte.

**Tipp** Vermeiden Sie nach Möglichkeit, die SEO-Einstellungen zu ändern, sobald eine Website etabliert ist. Dadurch können defekte Links von anderen Websites und möglicherweise ein vorübergehender Rückgang des Suchmaschinenrankings entstehen.

- **Unicode-Aliase** Das Ändern dieses Parameters wirkt sich nicht rückwirkend auf Aliase aus, sondern ändert das Verhalten der automatischen Alias-Generierung für zukünftige Inhaltsbearbeitungen und -erstellungen. *Transliteration* (Nein) ist die Standardeinstellung.

### Cookie-Panel

- **Cookie-Domain** Überschreibt die Standard-Cookie-Domain der Website mit der hier hinzugefügten Domain. Die wahrscheinlichste Situation, in der dies erforderlich ist, ist, wenn die Joomla-Website mit anderen Websites (z. B. Forum oder E-Commerce) in Subdomains der Joomla-Website „überbrückt“ ist. Die Standard-Cookie-Domain kann wie `www.example.com` sein, aber die Verwendung von `.example.com` (beachten Sie den führenden Punkt) wird hier Cookies bereitstellen, die für jede Subdomain von example.com gültig sind.
- **Cookie-Pfad** Überschreibt den Standardpfad der Website, für den das Cookie gültig ist, mit dem hier hinzugefügten Pfad. Dies kann erforderlich sein, wenn Sie mehrere Joomla-Installationen in benachbarten Ordnern haben.

## System-Tab

![Global-Konfiguration System-Tab](../../../en/images/configuration/global-configuration/02-global-configuration-system-tab.png)

### Debug-Panel

Die Punkte in diesem Panel werden durch die Inline-Hilfe gut erklärt. Sollten Sie jedoch auf ein Problem stoßen, das den normalen Zugriff auf die Administratoroberfläche verhindert, müssen Sie möglicherweise das Debug-System einstellen, indem Sie die Datei configuration.php mit einem Texteditor bearbeiten. Auf den meisten Linux-basierten Hosting-Systemen sind die Dateiberechtigungen auf 444 gesetzt, was das Speichern mit einem Texteditor verhindert. Ändern Sie die Berechtigung auf 644, bevor Sie mit der Bearbeitung beginnen. Setzen Sie dann \$debug = `true`; und setzen Sie \$error_reporting = `'maximum'`; und speichern. Sie sollten dann einen Stack-Trace erhalten, der genau identifiziert, wo das Problem auftritt. Damit können Sie im Forum um Hilfe bitten. Die meisten Probleme entstehen durch inkompatible Drittanbieter-Erweiterungen oder durch Probleme mit der Hosting-Umgebung.

## Server-Tab

![Globales Konfigurations-Server-Tab](../../../en/images/configuration/global-configuration/03-global-configuration-server-tab.png)

### E-Mail-Panel

Eine Joomla-Website sollte in der Lage sein, ausgehende E-Mails zu versenden. Unter anderem werden automatisierte Nachrichten an den Website-Betreiber gesendet, wenn Updates verfügbar sind. Einige Hosting-Dienste schränken jedoch die Methoden ein, mit denen ausgehende E-Mails versendet werden dürfen.

#### Test-E-Mail senden

Vor Joomla 5.3 wurde über die Schaltfläche **Testmail senden** eine Nachricht an die im Feld **Absender-E-Mail** konfigurierte Adresse gesendet. Seit Version 5.3 wird die Testmail direkt an die E-Mail-Adresse des angemeldeten Administrators gesendet.

- Versuchen Sie zuerst PHP Mail und wählen Sie die Schaltfläche *Test-Mail senden*. Wenn die E-Mail ankommt, ist alles in Ordnung. Andernfalls:
- Probieren Sie die Sendmail-Option. Wenn das nicht funktioniert:
- Versuchen Sie die SMTP-Option. Diese muss für einen spezifischen Mail-Server eingerichtet werden. Es könnte einer sein, der von Ihrem Hosting-Dienst bereitgestellt wird. Es könnte ein GMail-Konto sein.
- **SMTP-Host** Der Hostname des SMTP-Servers (z.B. *smtp.example.com*).
  - **SMTP-Port** Der Port, der beim Verbinden mit dem SMTP-Server verwendet wird. Dieser ist normalerweise *25*, wenn SMTP-Sicherheit auf *Keine* gesetzt ist, oder *465* oder *587*, wenn SMTP-Sicherheit auf `SSL/TLS` oder `STARTTLS` gesetzt ist. Fragen Sie Ihren SMTP-Dienstleister, welchen Port Sie verwenden sollen.
  - **SMTP-Sicherheit** Die Form der Sicherheit, die der SMTP-Server erfordert: *Keine*, *SSL/TLS* oder *STARTTLS*. Standard ist *Keine*.
  - **SMTP-Authentifizierung** Ob der externe SMTP-Server eine Authentifizierung erfordert, bevor ausgehende E-Mails akzeptiert werden. Standard ist *Nein*.
  - **SMTP-Benutzername** Der Benutzername, der beim Verbinden mit dem SMTP-Server im SSL- oder TLS-Modus verwendet wird. Kann leer gelassen werden, wenn keine SMTP-Authentifizierung erforderlich ist.
  - **SMTP-Passwort** Das Passwort, das beim Verbinden mit dem SMTP-Server im SSL- oder TLS-Modus verwendet wird. Kann leer gelassen werden, wenn keine SMTP-Authentifizierung erforderlich ist.

### Gmail als Mail-Server verwenden

Wenn Sie ein funktionierendes Gmail-Konto haben, können Sie Gmail als Mail-Server verwenden, indem Sie es in der globalen Konfiguration einstellen. Auf dem Server-Tab stellen Sie folgendes ein:

- Mailer: SMTP
- SMTP-Host: smtp.gmail.com
- SMTP-Port 465
- SMTP-Sicherheit: SSL/TLS
- SMTP-Authentifizierung: Ja
- Füllen Sie die nächsten zwei Zeilen mit Ihren Informationen aus. Sie müssen ein app-spezifisches Passwort (ASP) verwenden, das unten beschrieben ist.
- SMTP-Benutzername: Ihr Gmail-Benutzername
- SMTP-Passwort: das app-spezifische Passwort (ASP), das Sie generiert haben, wie unten beschrieben.

Die folgenden Kombinationen funktionieren ebenfalls:

- SMTP-Port 587
- SMTP-Sicherheit: STARTTLS
- SMTP-Port 25
- SMTP-Sicherheit: STARTTLS

#### Hinweise

- Das SSL-Modul muss in Apache nicht aktiviert sein.
- Die OpenSSL-Erweiterung muss in PHP aktiviert sein. Die Details finden Sie auf der [php.net Installationsseite](https://www.php.net/manual/en/openssl.installation.php).
- Wenn Sie WAMP unter Windows verwenden, ist das openssl-Modul standardmäßig nicht aktiviert, und Sie müssen es aktivieren. Dazu:
  - Öffnen Sie die php.ini-Datei und heben Sie die Auskommentierung der Zeile `extension=php_openssl.dll` auf, indem Sie das Semikolon ; am Anfang der Zeile entfernen.
  - Speichern Sie die php.ini-Datei und starten Sie den Apache-Dienst neu.
- Wenn Sie die 2-Schritt-Verifizierung in Gmail verwenden, müssen Sie ein neues Passwort hinzufügen unter Einstellungen - Konten - Kontoeinstellungen ändern - Andere Google-Kontoeinstellungen - Sicherheit - 2-Schritt-Verifizierung - Verwalten Sie Ihre application-spezifischen Passwörter.
- Wenn das neue Application Specific Password (ASP) in Gruppen von vier Zeichen angezeigt wird, die durch Leerzeichen getrennt sind, stellen Sie sicher, dass Sie **nicht die Leerzeichen** in das SMTP-Passwort in den Mail-Server-Einstellungen in Joomla eingeben.
- Application Specific Passwords (ASPs): Sehen Sie die Google Support-Seite an, um zu erfahren, wie Sie sich mit [App-Passwörtern anmelden](https://support.google.com/accounts/answer/185833).
- 2-Schritt-Verifizierung: Sehen Sie die Google Support-Seite an, um zu erfahren, wie Sie die [2-Schritt-Verifizierung aktivieren](https://support.google.com/accounts/answer/185839).

## Protokollierungs-Tab

![Registerkarte zur globalen Konfiguration der Website](../../../en/images/configuration/global-configuration/04-global-configuration-logging-tab.png)

Im Normalbetrieb sollte bei einer Joomla-Website die Protokollierung deaktiviert sein. Wenn es Probleme gibt, können Sie die Protokollierung aktivieren, indem Sie das Feld **Fast alles protokollieren** auf `Ja` setzen. Das Feld **Veraltete API protokollieren** ist wirklich nur für Entwickler gedacht. Das Feld **Pfad zum Protokollordner** zeigt Ihnen, wo Sie nach Protokollen suchen können, wenn Sie die Protokollierung zur Unterstützung beim Debuggen eingerichtet haben. Die dort gefundenen Fehlerprotokolle sind nur diejenigen, die von Joomla erfasst wurden. Es kann jedoch andere Fehler geben, die nur in den Fehlerprotokollen Ihres Servers erscheinen.

## Der Tab "Textfilter"

![Globale Konfiguration Seitenreiter](../../../en/images/configuration/global-configuration/05-global-configuration-filters-tab.png)

Die Textfilter-Einstellungen werden auf alle Texteditor-Felder angewendet, die von Benutzern in den ausgewählten Gruppen übermittelt werden. Diese Filteroptionen bieten mehr Kontrolle über das HTML, das Ihre Inhaltsanbieter einreichen. Sie können so streng oder liberal sein, wie es die Anforderungen Ihrer Website erfordern. Das Filtern ist optional, und die Standardeinstellungen bieten einen guten Schutz gegen Markup, das häufig mit Angriffen auf Websites in Verbindung gebracht wird.

## Registerkarte "Berechtigungen"

![Registerkarte für globale Konfiguration der Website](../../../en/images/configuration/global-configuration/06-global-configuration-permissions-tab.png)

Berechtigungen steuern, was Benutzer in jeder Benutzergruppe sehen und tun können. Die Einträge in der Registerkarte "Berechtigungen" legen die Standardberechtigungen für die Website fest.

Es gibt umfassende Beschreibungen zur Verwendung der Einstellungen unter dieser Registerkarte sowie zu den allgemeinen Prinzipien der Funktionsweise und Einrichtung von Berechtigungen in einem [Tutorial zur Zugangskontrollliste](jdocmanual?article=user/users/access-control).

*Übersetzt von openai.com*
