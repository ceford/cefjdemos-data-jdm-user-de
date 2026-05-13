<!--
{
  "source": "https://docs.joomla.org/J4.x:Guest_Access",
  "title": "Gastzugriff ",
  "description": "", 
  "author": ""
}
-->

## Zugriffsebenen

Website-Besucher können Beiträge, Module und Menüeinträge sehen, da diese Elemente standardmäßig der Zugriffsebene Öffentlich zugewiesen sind. Diese Zugriffsebene ermöglicht es auch angemeldeten Benutzern, die gleichen Inhalte zu sehen. Es gibt jedoch Situationen, in denen es unangebracht ist, dass ein angemeldeter Benutzer einen Inhaltselement sieht. Beispielsweise sollte ein Menüeintrag für die Anmeldung von Benutzern gesehen werden, die nicht angemeldet sind, aber nicht von Benutzern, die angemeldet sind. Dafür gibt es die Zugriffsebene Gast. Angemeldete Benutzer sollten stattdessen einen Menüeintrag für die Abmeldung sehen. Solche Elemente müssen der Zugriffsebene Registriert zugewiesen werden.

In einigen Fällen ist es auch angebracht, den Zugriff auf einen Beitrag oder ein Modul auf Benutzer zu beschränken, die nicht angemeldet sind, oder auf Benutzer, die angemeldet sind.

## Gastzugang

Die Verwendung des Gastzugriffs kann mit einem Anmelde-Menüpunkt veranschaulicht werden:

- Wählen Sie **Menüs → Hauptmenü → +** aus dem Administrator-Menü. 
  Verwenden Sie das Menü Ihrer Wahl für die neuen Einträge.
- Geben Sie im Formular **Menüs: Neuer Eintrag** einen passenden Titel in das
  Feld **Titel** ein, zum Beispiel **Login**.
- Verwenden Sie im Feld **Menüeintragstyp** die Schaltfläche **Auswählen**, um den
  Popup-Dialog für Menüeintragstypen zu öffnen.
- Wählen Sie in der Liste **Menüeintragstyp** den Abschnitt Benutzer und 
  den Eintrag **Anmeldeformular** aus.
- Stellen Sie im Formular **Menüs: Neuer Eintrag** das Feld **Zugriff** auf **Gast** ein.
- Speichern
- Optional: Wählen Sie die Liste Bestellung aus und wählen Sie den Eintrag **nach** dem Sie den Anmeldeeintrag anzeigen lassen möchten.

![Anmeldeformular-Menü für Gastzugang eingeschränkt](../../../en/images/users/guest-access/01-guest-access-menu-login.png)

- Speichern und Schließen.
- Sehen Sie sich die Website an. Überprüfen Sie, ob der Anmelde-Menüpunkt funktioniert. Prüfen Sie, ob er nach dem Anmelden verschwindet.

## Registrierter Zugriff

Die Nutzung der Zugriffsebene "Registriert" kann mit einem Logout-Menüpunkt veranschaulicht werden:

- Wählen Sie **Menüs → Hauptmenü → +** aus dem Administrator-Menü.
  Verwenden Sie das Menü Ihrer Wahl für die neuen Elemente.
- Geben Sie im Formular **Menüs: Neues Element** einen geeigneten Titel im Feld **Titel** ein, zum Beispiel **Logout**.
- Verwenden Sie im Feld **Menüpunkt-Typ** die Schaltfläche **Auswählen**, um den Popup-Dialog für Menüpunkttypen zu öffnen.
- Wählen Sie in der Liste **Menüpunkt-Typ** den Abschnitt Benutzer und den Punkt **Logout** aus.
- Stellen Sie im Formular **Menüs: Neues Element** das Feld **Zugriff** auf **Registriert**.
- Speichern
- Optional: Wählen Sie das Dropdown-Menü Reihenfolge und wählen Sie den Punkt, **nach dem** das Login-Element erscheinen soll.

![Abmeldeformular, beschränkt auf registrierten Zugriff](../../../en/images/users/guest-access/02-guest-access-menu-logout.png)

- Speichern und Schließen.
- Besichtigen Sie die Website. Überprüfen Sie, ob der Logout-Menüpunkt funktioniert. Stellen Sie sicher, dass er nach dem Abmelden verschwindet.

*Übersetzt von openai.com*

