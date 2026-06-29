<!--
{
  "source": "https://docs.joomla.org/J4.x:Site_Offline",
  "title": "Seite Offline",
  "description": "", 
  "author": ""
}
-->

## Nur für Website-Benutzer

Es kann vorkommen, dass Sie Ihre Joomla!-Website für kurze Zeit für Besucher nicht verfügbar machen müssen. Für diesen Zweck gibt es einen einfachen **Seite offline** Konfigurationsschalter, der je nach Bedarf von **Nein** auf **Ja** geändert werden kann. Wenn er auf *Ja* gestellt ist, sehen alle Besucher der Website eine Offline-Nachrichtenseite mit Anmeldeformular. Das standardmäßige Offline-Formular kann mit einem Bild angepasst werden:

![Bildschirm der Seite offline](../../../en/images/configuration/site-offline/01-site-offline.png)

Der Offline-Schalter für die Website gilt nicht für die Administratoroberfläche, und Benutzer, die sich im Backend anmelden können, können sich weiterhin im Frontend anmelden. Der Frontend-Login ist nur für Benutzer in den Benutzergruppen Registriert, Autor, Editor und Beiträge gesperrt.

## Offline schalten

- Wählen Sie im Administrator-Menü **Home Dashboard → Globale Konfiguration** aus.
- Stellen Sie im **Site**-Tab den Schalter **Website offline** auf **Ja**.
- Sie können dann eine der folgenden Optionen auswählen:
  - **Benutzerdefinierte Nachricht verwenden**, was der Text im Feld für benutzerdefinierte Nachrichten ist. Oder...
  - **Die Standardmeldung der Website-Sprache**, die auf Englisch lautet **Diese Website ist wegen Wartungsarbeiten offline. Bitte versuchen Sie es bald wieder.** oder die entsprechende Meldung in der ausgewählten Sprache der Website. Diese Option ermöglicht auch die Auswahl eines Bildes. Oder...
  - **Verbergen**, um überhaupt keine Nachricht anzuzeigen.
- Wählen Sie **Speichern & Schließen** in der Symbolleiste.
- Führen Sie die erforderlichen Wartungsarbeiten durch.
- Kehren Sie zum Formular der globalen Konfiguration zurück.
- Setzen Sie den Schalter Website offline auf **Nein**.
- Wählen Sie **Speichern & Schließen** in der Symbolleiste.

## Alle Benutzer

Sie können den Zugriff auf Ihre Website einschränken, indem Sie das Joomla-Verzeichnis mit einem Passwort schützen. Nur Benutzer, die den Benutzernamen und das Passwort für den Verzeichnisschutz kennen, können die Seite betreten. Sie können mehr als einen solchen Benutzer einrichten. Mit dem cPanel Hosting-Kontrollpanel:

- Melden Sie sich in Ihrem cPanel-Konto an.
- Wählen Sie im Abschnitt Dateien **Verzeichnisschutz**.
- Wenn das Stammverzeichnis Ihrer Seite in einem Unterverzeichnis von public_html liegt:
  - Wählen Sie das Verzeichnis public_html.
- Wählen Sie die Schaltfläche Bearbeiten für das Verzeichnis, das Ihre Seite enthält (public_html, wenn Ihre Seite im Web-Stammverzeichnis liegt).
- Aktivieren Sie das Kontrollkästchen **Dieses Verzeichnis mit Passwort schützen**.
- Geben Sie einen Namen für das geschützte Verzeichnis ein: Standardmäßig könnte ausreichend sein.
- Wählen Sie die Schaltfläche **Speichern**.
- Es erscheint eine Erfolgsmeldung mit einem Link zum Zurückkehren, wählen Sie ihn aus.
- Erstellen Sie einen Benutzer für den Zugriff auf das geschützte Verzeichnis.
- Geben Sie einen Benutzernamen ein.
- Geben Sie ein Passwort ein und wiederholen Sie es (merken Sie sich das Passwort oder notieren Sie es).
- Wählen Sie **Speichern**.

Überprüfen Sie jetzt, ob das Verzeichnis ein Passwort für den Zugriff über das Web erfordert. Wenn Sie Ihre Seite besuchen, werden Sie nach Ihrem Benutzernamen und Passwort für den Verzeichnisschutz gefragt. Diese können sich vollständig von Ihrem Joomla-Benutzernamen und Passwort unterscheiden.

Um den Passwortschutz des Verzeichnisses zu entfernen:

- Melden Sie sich in Ihrem cPanel-Konto an.
- Wählen Sie im Abschnitt Dateien **Verzeichnisschutz**.
- Wenn das Stammverzeichnis Ihrer Seite in einem Unterverzeichnis von public_html liegt:
  - Wählen Sie das Verzeichnis public_html.
- Wählen Sie die Schaltfläche **Bearbeiten** für das Verzeichnis, das Ihre Seite enthält (public_html, wenn Ihre Seite im Web-Stammverzeichnis liegt). Es wird nun ein Schlosssymbol und Ja unter der Überschrift Privat anzeigen.
- **Deaktivieren** Sie das Kontrollkästchen **Dieses Verzeichnis mit Passwort schützen**.
- Wählen Sie die Schaltfläche **Speichern**.

Um zu überprüfen, dass der Passwortschutz entfernt wurde, verwenden Sie einen anderen Browser, um auf Ihre Seite zuzugreifen, oder schließen und öffnen Sie Ihren vorhandenen Browser erneut und greifen dann erneut auf Ihre Seite zu.

*Übersetzt von openai.com*

