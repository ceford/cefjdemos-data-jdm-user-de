<!--
{
  "source": "https://docs.joomla.org/J4.x:User_Registration",
  "title": "Benutzerregistrierung",
  "description": "", 
  "author": ""
}
-->

## Registrierungsrichtlinie

Auf einer Joomla-Website dürfen registrierte Benutzer Inhalte ansehen oder mit Inhalten interagieren, die unregistrierte Benutzer nicht einsehen können. Der Seiten-Login und der Administrator-Login werden separat behandelt, obwohl es in der globalen Konfiguration eine Einstellung gibt, die es ermöglicht, diese zu kombinieren. Einige Websites haben eine geringe Anzahl von Benutzern, die von einem Administrator erstellt werden. Andere Websites haben so viele Benutzer, dass sie sich selbst registrieren und ihre Konten selbst aktivieren müssen. Wie sich Benutzer für Ihre Website registrieren, wird im Formular *Benutzer: Optionen* konfiguriert.

## Selbstregistrierung erlauben

Die Selbstregistrierung von Benutzern ist standardmäßig nicht erlaubt. Jeder neue Benutzer muss von einem Manager oder Administrator erstellt werden. Die Selbstregistrierung kann mit einigen einfachen Änderungen im Formular *Benutzer: Optionen* erlaubt werden.

- Wählen Sie **Benutzer → Verwalten** aus dem Administrator-Menü.
- Wählen Sie die *Optionen*-Schaltfläche aus der Symbolleiste.
- Setzen Sie **Benutzerregistrierung erlauben** auf **Ja**.
- Die **Neue Benutzerregistrierungsgruppe** sollte **- Registriert -** sein, es sei denn, es gibt einen guten Grund, dass sie etwas anderes sein sollte.
- Die **Neue Benutzerkontenaktivierung** sollte **Selbst** oder **Administrator** sein.
  - Selbst: Der Benutzer erhält eine E-Mail mit einem Aktivierungslink. Das Konto wird aktiviert, wenn der Benutzer auf den Aktivierungslink klickt.
  - Administrator: Der Benutzer erhält eine E-Mail mit einem Aktivierungslink. Wenn der Benutzer auf diesen Link klickt, wird der Seitenadministrator per E-Mail benachrichtigt. Der Seitenadministrator muss dann das Konto des Benutzers aktivieren.

![Benutzerkonfiguration Benutzeroptionen-Registerkarte](../../../en/images/users/user-registration/01-users-configuration-user-options.png)

- **Speichern & Schließen**
- Fügen Sie ein *Login*-Modul hinzu. Oder
- Fügen Sie ein Menüelement *Benutzer: Login-Formular* und ein Menüelement *Benutzer: Logout* hinzu.

## Selbstregistrierung deaktivieren

- Setzen Sie **Benutzerregistrierung zulassen** auf **Nein**.

## Hinzufügen eines neuen Benutzers

Wenn die Selbstregistrierung nicht erlaubt ist, muss jeder neue Benutzer von einem Administrator erstellt werden. Gehen Sie wie folgt vor:

- Wählen Sie das **Benutzer +**-Symbol im Home-Dashboard-Site-Panel. Oder
- Wählen Sie **Benutzer** → **Verwalten +** im Administrator-Menü.
- Füllen Sie das Formular **Benutzerdetails hinzufügen** aus. Die meisten Felder haben geeignete Standardwerte.

![Neue Benutzerdaten-Eingabeseite](../../../en/images/users/user-registration/02-users-new-user.png)

- Wählen Sie den Tab **Zugeordnete Benutzergruppen** und aktivieren Sie das Kontrollkästchen der gewünschten Benutzergruppe. Registriert ist standardmäßig aktiviert.
- **Speichern & Schließen**.
- Überprüfen Sie in der Benutzerliste, ob das neue Benutzerkonto aktiviert ist (grüner Haken in den Aktivierungsspalten).

## Einen Benutzer sperren

Die beste Methode, mit einem störenden Benutzer umzugehen, ist, das Benutzerkonto zu deaktivieren, anstatt es zu löschen. Diese Maßnahme kann genutzt werden, um den Benutzer zu suspendieren, und sie kann rückgängig gemacht werden, wenn der Benutzer verspricht, sich gut zu benehmen. Das Löschen eines Kontos würde jegliche Verbindung zu benutzerbeigetragenen Inhalten wie Beiträge-Autorenschaft unterbrechen und könnte dem Benutzer die Möglichkeit bieten, sich erneut mit derselben E-Mail-Adresse zu registrieren.

Um einen Benutzer zu sperren:

- Wählen Sie **Benutzer → Verwalten** aus dem Administratormenü.
- Suchen Sie den Benutzer in der *Benutzer* Liste. Nutzen Sie den Textfilter, falls nötig.
- Wählen Sie das Aktiviert-Symbol, das als grüner Haken neben dem Benutzernamen erscheint. Beim Überfahren mit der Maus erscheint ein **Sperren**-Label.

![Neue Benutzerdateneingabeseite](../../../en/images/users/user-registration/03-users-hover-block.png)

- Wählen Sie das *Aktiviert*-Symbol. Die Seite wird neu geladen, wobei das Aktiviert-Symbol als graues Kreuz erscheint.

## Benutzer entsperren

Einfach:

- Das Symbol *Aktiviert* wieder auf ein grünes Häkchen umschalten.

*Übersetzt von openai.com*

