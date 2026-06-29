<!--
{
  "source": "https://docs.joomla.org/J4.x:Access_Control",
  "title": "Zugriffskontrolle ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Joomla verfügt über einen ausgeklügelten Mechanismus zur Steuerung, wer Inhalte auf einer Joomla-Seite sehen und manipulieren kann. Der **wer**-Teil wird in den Benutzerkomponentenoptionen mit Benutzergruppen und Zugriffsebenen eingerichtet. Der **manipulieren**-Teil wird in den Aktionsberechtigungen eingerichtet, entweder in den Einstellungen der globalen Konfiguration, in den Komponenteneinstellungen oder in den Einstellungen der einzelnen Elemente. Beispielsweise können in den globalen Berechtigungen festgelegte Standardwerte in den Beitragsberechtigungen (alle Beiträge) überschrieben werden, und Beitragsberechtigungen können in den Berechtigungen einzelner Beiträge überschrieben werden.

## Benutzergruppen

Benutzergruppen werden verwendet, um die Benutzer einer Webseite in Gruppen mit unterschiedlichen Verantwortlichkeiten zu unterteilen. Zum Beispiel haben Mitglieder der Benutzergruppe Autor die Berechtigung, sich auf der Webseite anzumelden, Beiträge zu erstellen und ihre eigenen Beiträge zu bearbeiten. Nichts weiter! Mitglieder der Gruppe Super Benutzer sind für alle Aspekte der Webseitenverwaltung und des Betriebs verantwortlich. Joomla bietet neun Standardbenutzergruppen an, und Sie können bei Bedarf weitere erstellen.

![Liste von Benutzergruppen](../../../en/images/users/access-control/01-access-control-users-groups-list.png)

Die Standardbenutzergruppen sind mit Eltern-Kind-Beziehungen eingerichtet, um die Duplizierung von Berechtigungen zu minimieren. Beispiele für Vererbung:

- Ein Mitglied der Registrierten Gruppe hat keine Berechtigung für den Administrator-Login. Weder der Editor noch der Publisher haben diese Berechtigung.
- Ein Mitglied der Autorengruppe hat die Berechtigung zum Erstellen und Bearbeiten eigener Beiträge. Das gilt auch für Editor und Publisher, aber sie haben zusätzliche Berechtigungen.

Sie können bei Bedarf neue Benutzergruppen für besondere Zwecke erstellen. Zum Beispiel möchten Sie möglicherweise eine Gruppe erstellen, die Administrator-Login-Berechtigung hat, deren Zugriff jedoch auf eine einzelne Komponente beschränkt ist. Am Ende dieses Tutorials gibt es ein Beispiel für eine solche benutzerdefinierte Benutzergruppe.

## Zugriffsebenen

Jedes Mal, wenn Sie ein Objekt erstellen, wie beispielsweise einen Beitrag, ein Modul oder ein Menüelement, sehen Sie ein Zugriffsfeld, normalerweise in der rechten Spalte des Dateneingabeformulars. Es ist eine Dropdown-Liste, die eine Auswahl zwischen Öffentlich, Gast, Registriert, Speziell und Super Benutzer bietet. Der Standardwert ist Öffentlich. Die standardmäßigen Zugriffsebenen für die Ansicht werden im folgenden Screenshot angezeigt:

![Benutzer-Zugriffsebenen](../../../en/images/users/access-control/02-access-control-users-access-levels.png)

Beispiele:

- Wenn Sie ein Seitenmodul erstellen und den Zugriff auf Registriert setzen, wird es nur von Benutzern gesehen, die auf der Seite angemeldet sind.
- Wenn Sie ein Menüelement der Seite erstellen und den Zugriff auf Super Benutzer setzen, wird es nur von Super Benutzern gesehen, die auf der Seite angemeldet sind.

## Berechtigungen

Die Berechtigungen der globalen Konfiguration sind der Ausgangspunkt, von dem aus Berechtigungseinstellungen in Komponenten oder einzelnen Beiträgen geerbt oder überschrieben werden können. Screenshot:

![globale Konfiguration Berechtigungen](../../../en/images/users/access-control/03-access-control-global-configuration-permissions.png)

Der Screenshot zeigt, dass Mitglieder der Gruppe Public keine Berechtigungen haben, um irgendwelche Aktionen durchzuführen. Wenn Sie jede Gruppe der Reihe nach auswählen, werden Sie sehen, wie sich die Berechtigungen von Gruppe zu Gruppe ändern. Beachten Sie, dass Manager und Administratoren die Administrator-Anmeldung erlaubt haben, während Author, Editor und Publisher dies nicht haben. Letztere sind effektiv Rollen für die Website und nicht für den Administrator.

Alle Gruppenberechtigungen erben von der Gruppe Public. Diese hat keine Berechtigungen für irgendwelche Aktionen. Standardmäßig können jedoch Elemente in der Gruppe Public angesehen werden, sodass das Zuweisen von öffentlichen Berechtigungen zu einem Element dazu führt, dass es von allen Seitenbesuchern gesehen werden kann, unabhängig davon, ob sie angemeldet sind oder nicht.

### Beiträge Berechtigungen

Die Beiträge Berechtigungen unterscheiden sich von den Berechtigungen der globalen Konfiguration. Nicht vorhanden sind Elemente, die mit der Anmeldung zu tun haben, während Elemente, die mit Arbeitsabläufen zu tun haben, vorhanden sind. Dies ist ein ziemlich typisches Muster: Eine Komponente wird Berechtigungen haben, die für die Komponente relevant sind; ein Element einer Komponente (wie ein Beitrag) wird Berechtigungen haben, die für dieses eine Element relevant sind.

![Inhaltsberechtigungen](../../../en/images/users/access-control/04-access-control-global-content-permissions.png)

### Einzelbeitrag Berechtigungen

Die Einzelbeitrag Berechtigungen haben nur drei Punkte: Löschen, Bearbeiten und Bearbeitungsstatus:

![Einzelbeitrag Berechtigungen](../../../en/images/users/access-control/05-access-control-article-permissions.png)

## Beispiel für Zugriffskontrolle: Benutzer mit Sonderaufgaben

Angenommen, Sie müssen eine Benutzergruppe für Benutzer erstellen, die nur eine Verantwortung haben. In diesem Beispiel ein Beitragsadministrator. Benutzer in dieser Gruppe sollten Berechtigungen für den Administrator-Login haben, aber nichts anderes als die Inhalte sehen dürfen. Vorgehensweise:

### Erstellen Sie eine neue Benutzergruppe

- Wählen Sie **Benutzer → Gruppen** aus dem Administrator-Menü.
- Wählen Sie die Schaltfläche `Neu` in der Werkzeugleiste.
- Füllen Sie das Feld Gruppentitel aus: Beitragsadministrator
- Die übergeordnete Gruppe muss Öffentlich sein - sie hat keine Berechtigungen für irgendetwas.

![Neues Benutzergruppenformular](../../../en/images/users/access-control/06-access-control-new-group.png)

### Zu Spezial zuweisen

- Wählen Sie **Benutzer → Zugriffsebenen** aus dem Administrator-Menü.
- Wählen Sie das **Spezial**-Element.
- Aktivieren Sie das Kontrollkästchen Beitragsadministrator im Formular **Benutzer: Zugriffsebene Bearbeiten**.
- Speichern & Schließen.

![Zugriff für Gruppe auswählen](../../../en/images/users/access-control/07-access-control-select-access-for-group.png)

### Globale Konfigurationseinstellungen

- Wählen Sie **Start-Dashboard → Globale Konfiguration** aus dem Administrator-Menü.
- Wählen Sie den **Berechtigungen**-Tab.
- Wählen Sie die Gruppe **Beitragsadministrator**.
- Setzen Sie **Administrator-Login** auf Erlaubt.
- Speichern & Schließen.

![Zugriff für Gruppe auswählen](../../../en/images/users/access-control/08-access-control-article-administrator-global-permissions.png)

### Berechtigungen für Beitragsoptionen

- Wählen Sie **Inhalt → Beiträge** aus dem Administrator-Menü.
- Wählen Sie die Schaltfläche `Optionen` aus der Werkzeugleiste.
- Wählen Sie den **Berechtigungen**-Tab.
- Wählen Sie die Gruppe **Beitragsadministrator**.
- Setzen Sie alle Elemente außer den ersten beiden (Konfigurieren von ACL & Optionen und Nur Optionen konfigurieren) auf Erlaubt.
- Speichern & Schließen.

![Zugriff für Gruppe auswählen](../../../en/images/users/access-control/09-access-control-article-administrator-content-permissions.png)

### Benutzer erstellen oder bearbeiten

- Erstellen Sie einen neuen Benutzer oder bearbeiten Sie einen bestehenden Benutzer, der keiner Gruppe zugewiesen ist.
- Wählen Sie **Beitragsadministrator** im Tab **Zugewiesene Benutzergruppen** des Benutzerbearbeitungsformulars.
- Speichern & Schließen.
- Melden Sie sich als Benutzer in der Gruppe Beitragsadministrator an. Das Menü sollte nur beitragsbezogene Elemente anzeigen:

![Zugriff für Gruppe auswählen](../../../en/images/users/access-control/10-access-control-article-administrator-home-dashboard.png)

*Übersetzt von openai.com*

