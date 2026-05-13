<!--
{
  "source": "https://docs.joomla.org/J5.x:Managing_Mail_Template_Layout",
  "title": "E-Mail-Vorlagen ",
  "description": "", 
  "author": ""
}
-->

## Einführung

E-Mail-Vorlagen werden verwendet, um System-E-Mail-Nachrichten in **nur-Text** oder **HTML** oder beidem zu senden, ausgewählt im Formular *E-Mail-Vorlagen: Optionen*. Wenn nur eine Methode ausgewählt ist, wird die Alternative im Nachrichtenbearbeitungsformular nicht vorhanden sein.

Der folgende Screenshot zeigt eine Auswahl der 26 standardmäßigen Mail-Templates. Die Liste ist verfügbar, indem Sie **System -> Mail Templates** aus dem Administratormenü auswählen.

![mail templates list](../../../en/images/templates/mail-templates/01-mail-templates-list.png)

Die E-Mail-Nachrichten können angepasst werden, um Layout, Erscheinungsbild und Wortlaut an die Bedürfnisse Ihrer Website anzupassen. Zum Beispiel möchten Sie vielleicht ein Website-Logo und ein Farbschema in den E-Mails verwenden, die an Kunden gesendet werden. Die Anpassung von E-Mails, die an Administratoren gesendet werden, ist weniger wichtig.

Es gibt zwei Anpassungsmethoden: über die *Mail Template: Optionen* für alle Mailvorlagen und über die *Per Template Mail Settings*.

## Mailvorlage: Optionen

Wählen Sie die Schaltfläche **Optionen** in der Toolbar der *Mail-Vorlagen* Liste, um Zugriff auf die allgemeinen Einstellungen der Mail-Vorlagen zu erhalten. Wählen Sie die Schaltfläche *Inline-Hilfe umschalten*, um zu sehen, ob irgendeines der Formularfelder zusätzliche Hilfe bietet.

![mail templates options](../../../en/images/templates/mail-templates/02-mail-templates-options.png)

### E-Mail-Format

Seien Sie sich bewusst, dass ein Empfänger seinen E-Mail-Client so einstellen kann, dass er einfaches HTML oder Nur-Text verwendet, um den Download von Bildern zu vermeiden. Daher ist es möglicherweise am besten, das *E-Mail-Format* auf *Nur-Text* oder *Beides* festzulegen.

### Pro-Vorlage-Mail-Einstellungen

Wenn dies auf **Ja** eingestellt ist, haben die einzelnen E-Mail-Vorlagen-Bearbeitungsformulare einen zusätzlichen *Optionen*-Tab, der es Ihnen ermöglicht, die E-Mail-Einstellungen für diese Vorlage zu ändern und optional eine Kopie (BCC) an eine bestimmte E-Mail-Adresse zu senden, vorausgesetzt, dass das **Kopie senden**-Feld hier ebenfalls auf **Aktiviert** eingestellt ist.

## Beitragsvorlagen-Formular

In der Liste der E-Mail-Vorlagen können Sie eine beliebige Vorlage zur Bearbeitung auswählen. Der Titellink führt zum Bearbeitungsformular der Standardvorlage in Englisch. Jede Flagge ist ein Link zur gleichen Vorlage in dieser Sprache.

### Der Reiter Mail

![edit mail template form](../../../en/images/templates/mail-templates/03-mail-template-edit.png)

Der Inhalt der Bereiche Betreff und Text wird zunächst in Sprach-Strings gespeichert. Dies erleichtert das Zurücksetzen auf den Standardbetreff oder Text. Sobald jedoch eine spezifische E-Mail-Vorlage bearbeitet wurde, werden ihre Betreff- und Textfelder in der Tabelle `#__mail_templates` gespeichert.

Die Elemente in geschweiften Klammern sind Platzhalter-Tags, die durch echte Werte ersetzt werden, wenn die E-Mail gesendet wird. Im obigen Beispiel würde `{SITENAME}` durch den gewählten Namen für Ihre Seite ersetzt werden. `{Method}` würde durch die ausgewählte E-Mail-Transportmethode ersetzt werden: `PHP Mail`, `Sendmail` oder `SMTP`.

Die verfügbaren Platzhaltertags variieren von E-Mail zu E-Mail. Sie könnten Ihre eigenen benutzerdefinierten Platzhaltertags hinzufügen, aber das erfordert ein benutzerdefiniertes Plugin, das in einem [Magazin-Beitrag](https://magazine.joomla.org/all-issues/february-2025/joomla-5-email-templates-how-to-add-variables-via-plugin) vom Februar 2025 beschrieben wird.

### Der Tab Optionen

Dieser Tab ist nur vorhanden, wenn die *Pro Vorlage Mail-Einstellungen* auf *Ja* in den *Mail-Vorlagen: Optionen* gesetzt ist. Die Abbildung unten zeigt einen Screenshot mit den *Mail-Einstellungen* auf *Nein*. Wenn auf *Ja* gesetzt, erscheinen mehr Formularfelder, die die in der globalen Konfiguration, Server-Tab festgelegten Mail-Optionen überschreiben.

![edit mail template form](../../../en/images/templates/mail-templates/04-mail-template-edit-options.png)

Wenn Sie eine Blindkopie einer ausgehenden E-Mail an eine bestimmte E-Mail-Adresse senden möchten, können Sie diese im Feld *Kopie an E-Mail senden* eingeben.

## Mail-Vorlagen-Überschreibungen

Um eine E-Mail-Vorlagenüberschreibung innerhalb einer benutzerdefinierten Vorlage zu erstellen:

1. Gehen Sie zu System -> Site-Vorlagen -> Öffnen Sie Ihre Vorlage (z.B. Cassiopeia).
2. Wählen Sie im Tab Überschreibungen erstellen joomla -> mail aus.
3. Joomla kopiert die Datei `mailtemplate.php` in das Verzeichnis `/html/layouts/joomla/mail/` Ihrer Vorlage, wo Sie sie nach Bedarf anpassen können.

Sobald die Überschreibung erstellt ist, können Sie das Layout und die Stile Ihrer E-Mails anpassen, ohne die Basisschablone zu beeinflussen.

## Liste der Mailvorlagen

| Titel | Erweiterung | Beschreibung |
|-------|-----------|-------------|
| Benutzeraktionen-Log: Benachrichtigungs-E-Mail | Benutzeraktionen-Log | E-Mail, die Administratoren über neue Einträge im Benutzeraktionen-Log informiert. |
| Globale Konfiguration: Test-E-Mail | Konfiguration | Wird gesendet, wenn du auf die Schaltfläche "Test-Mail senden" in der globalen Konfiguration klickst. Sie wird an die in den Mail-Einstellungen festgelegte Absenderadresse gesendet. |
| Kontakte: Kontaktformular-E-Mail | Kontakte | Die "Kontaktformular"-E-Mail. |
| Kontakte: Kontaktformular-E-Mail-Kopie | Kontakte | Wird an den Absender einer E-Mail mit dem Kontaktformular gesendet, wenn die optionale Funktion "Kopie an Absender senden" aktiviert und ausgewählt ist. |
| Nachrichten: Neue Nachricht | Nachrichten | E-Mail mit einer im Nachrichtensystem erstellten Nachricht. |
| Datenschutz: Antrag auf Datenexport (Admin) | Datenschutz | E-Mail zur Information des Nutzers, dass ein Antrag zum Exportieren der Daten von dieser Website durch den Administrator erstellt wurde. |
| Datenschutz: Antrag auf Datenlöschung (Admin) | Datenschutz | E-Mail zur Information des Nutzers, dass ein Antrag zur Löschung der Daten von dieser Website durch den Administrator erstellt wurde. |
| Datenschutz: Antrag auf Datenexport | Datenschutz | E-Mail zur Bestätigung, dass die Daten eines Nutzers von der Website exportiert werden sollen. |
| Datenschutz: Antrag auf Datenlöschung | Datenschutz | E-Mail zur Bestätigung, dass die Daten eines Nutzers von der Website gelöscht werden sollen. |
| Datenschutz: Nutzer-Datenexport | Datenschutz | E-Mail mit dem Export von Nutzerdaten. |
| Benutzer: Massenmail an Benutzer | Benutzer | Die "Massenmail an Benutzer"-E-Mail. |
| Benutzer: Passwort zurücksetzen | Benutzer | Wird an einen Benutzer über den Link „Passwort vergessen?“ gesendet, z.B. in einem Anmeldeformular. |
| Benutzer: Benachrichtigung über neues Konto an Admin | Benutzer | Benachrichtigung an den Admin, dass ein neues, aktiviertes Konto erstellt wurde. |
| Benutzer: Anfrage an Admin, neues Konto zu verifizieren | Benutzer | Benachrichtigung an Administratoren, ein neues verifiziertes Konto zu überprüfen. |
| Benutzer: Konto durch Admin aktiviert | Benutzer | Benachrichtigung an den Benutzer, dass das neue Konto durch einen Administrator aktiviert wurde. |
| Benutzer: Neues Konto mit Admin-Aktivierung | Benutzer | Benachrichtigung über neues Konto an den Benutzer, welches nun durch einen Admin aktiviert werden muss. |
| Benutzer: Neues Konto mit Admin-Aktivierung (mit PW) | Benutzer | Benachrichtigung über neues Konto an den Benutzer, welches nun durch einen Admin aktiviert werden muss. Das Klartext-Passwort ist in der E-Mail enthalten. |
| Benutzer: Neues Konto ohne Aktivierung | Benutzer | Benachrichtigung über neues Konto an den Benutzer. Das Konto ist bereits aktiviert. |
| Benutzer: Neues Konto ohne Aktivierung (mit PW) | Benutzer | Benachrichtigung über neues Konto an den Benutzer. Das Konto ist bereits aktiviert. Das Klartext-Passwort ist in der E-Mail enthalten. |
| Benutzer: Neues Konto mit Selbstaktivierung | Benutzer | Benachrichtigung über neues Konto an den Benutzer, welches der Benutzer nun selbst aktivieren muss. |
| Benutzer: Neues Konto mit Selbstaktivierung (mit PW) | Benutzer | Benachrichtigung über neues Konto an den Benutzer, welches der Benutzer nun selbst aktivieren muss. Das Klartext-Passwort ist in der E-Mail enthalten. |
| Benutzer: Erinnerungs-E-Mail für Benutzername | Benutzer | Wird an einen Benutzer über den Link „Benutzernamen vergessen?“ gesendet, z.B. in einem Anmeldeformular. |
| Code per E-Mail gesendet | Multi-Faktor-Authentifizierung - Authentifizierungscode per E-Mail | Wird an Benutzer von der Multi-Faktor-Authentifizierungsseite gesendet, wenn die Option „Authentifizierungscode per E-Mail“ verwendet wird. |
| Aufgabe - Datenschutz-Zustimmung: Zustimmung erneuern | Aufgabe - Datenschutz-Zustimmungen | Erinnerung, die Datenschutz-Zustimmung für diese Website zu erneuern. |
| Joomla: Update-Benachrichtigung | Aufgabe - Joomla! Update-Benachrichtigung | Wird an die Seitenadministratoren gesendet, wenn das „Joomla! Update-Benachrichtigung“-Aufgaben-Plugin ein Update erkennt. |
| Benutzer: Neuer Benutzer | Benutzer - Joomla! | Wird an einen neuen Benutzer gesendet, wenn dieser im Backend erstellt wird. |

*Übersetzt von openai.com*

