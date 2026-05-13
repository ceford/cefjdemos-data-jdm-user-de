<!--
{
  "source": "https://docs.joomla.org/Help4.x:Components_Privacy_Outline",
  "title": "Datenschutzübersicht ",
  "description": "", 
  "author": ""
}
-->

## Inhalt

Die Joomla Privacy Tool Suite besteht aus folgenden Teilen:

- **Administrator-Komponente** Verwalten der Datenschutzanfragen von Benutzern.
- **Modul - Datenschutz-Dashboard** Fügt ein Datenschutzfeld zum Haupt-Dashboard hinzu.
- **Modul - Datenschutzanfragen** Fügt ein Panel für Datenschutzanfragen auf dem Datenschutz-Dashboard hinzu.
- **Modul - Datenschutzstatus** Fügt ein Panel für den Datenschutzstatus auf dem Datenschutz-Dashboard hinzu.
- **Menüpunkt - Anfrage erstellen** Zeigt ein Formular an, um eine Informationsanfrage darzustellen. Soll erstellt werden.
- **Plugin - System - Datenschutzeinwilligung** Fügt Zustimmungsfelder zu Formularen für persönliche Informationen wie die Registrierung hinzu. Soll aktiviert werden.
- **Plugin - Benutzer - Allgemeine Geschäftsbedingungen** Fordert die Zustimmung des Benutzers zu den Allgemeinen Geschäftsbedingungen der Website an. Soll aktiviert werden.
- **Plugin - Inhalte - Einwilligung bestätigen** Fügt einem Formular ein erforderliches Kontrollkästchen hinzu, zum Beispiel dem Standardkontaktformular. Soll aktiviert werden.
- **Plugin - Datenschutz - Verschiedene** Weitere Plugins, standardmäßig aktiviert, ohne bedeutende Parameter, die eingestellt werden müssen.

Nach der Installation ist die Privacy Tool Suite für die Verwendung durch Administratoren bereit, ohne dass Plugins aktiviert oder ein Menüpunkt erstellt werden muss.

## Arbeitsablauf

Dies ist eine typische Abfolge von Ereignissen:

- Eine Informationsanfrage trifft ein. Diese muss eine gültige E-Mail-Adresse
  eines Daten-Subjekts enthalten. Das Subjekt muss kein registrierter Benutzer sein.
  Zum Beispiel kann das Subjekt ein vom Administrator hinzugefügter Kontakt sein.
- Wenn die Nachricht nicht vom Subjekt über ein Persönliches
  Informationsformular der Website eingereicht wird:
  - Der Administrator geht zu
    **Benutzer → Datenschutz → Anfragen → Neu**, um eine neue
    Informationsanfrage zu erstellen. Eine Nachricht wird an die angegebene E-Mail-Adresse gesendet,
    die das Subjekt dazu einlädt, diese Anfrage zu bestätigen.
- Wenn die Nachricht über ein Persönliches Informationsformular der Website eingereicht wird,
  wird automatisch eine Bestätigungsanfrage an das Subjekt gesendet.
- Das Subjekt wählt den Link in der E-Mail-Nachricht aus, um das
  Bestätigungsformular zu öffnen. Nach dem Absenden sieht das Subjekt eine Bestätigungsnachricht.
- Der Administrator sieht, dass Private Nachrichten in der Titelleiste ausstehende Nachrichten haben.
  Es gibt auch eine systemgenerierte E-Mail-Nachricht.
- Der Administrator geht zu **Benutzer → Datenschutz → Anfragen** und
  sieht, dass sich der Anfragestatus zu **Bestätigt** geändert hat.
- Bei einer Datenexportanfrage gibt es benachbarte Export- und E-Mail-Schaltflächen.
  - Der Administrator wählt die Export-Schaltfläche, um die
    zu exportierenden Daten anzusehen. Diese liegen im XML-Format vor, werden aber
    in Firefox sinnvoll angezeigt.
  - Der Administrator wählt die E-Mail-Schaltfläche, um die exportierten Daten
    an das Subjekt zu senden.
- Bei einer Datenlöschungsanfrage gibt es eine benachbarte Löschen-Schaltfläche.
  - Der Administrator wählt die Löschen-Schaltfläche, um die Daten
    für den Benutzer zu anonymisieren. Der Benutzer kann sich nicht länger anmelden.
- Wählen Sie die E-Mail-Adresse des Daten-Subjekts aus, um das
  Informationsanfrage-Review-Formular zu öffnen.
- Wählen Sie die Schaltfläche „Abschließen“ in der Werkzeugleiste.
- Die Liste der Informationsanfragen zeigt den Status als Abgeschlossen und die
  Aktion-Schaltflächen sind verschwunden.

Beachten Sie, dass diese Suite kein Cookie-Berechtigungsformular anzeigt.

*Übersetzt von openai.com*

