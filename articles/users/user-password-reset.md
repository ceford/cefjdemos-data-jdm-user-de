<!--
{
  "source": "https://docs.joomla.org/J4.x:User_Password_Reset",
  "title": "Benutzer-Passwort zurücksetzen  ",
  "description": "", 
  "author": ""
}
-->

## Benutzer-Zurücksetzung

Wenn Ihre Benutzer die Anmeldung auf der Website erlaubt ist und ein Benutzer sich entweder nicht an den Benutzernamen oder das Passwort erinnern kann, ist es am besten, von der Person zu verlangen, die Anmeldeinformationen selbst zurückzusetzen, indem sie die Links im Anmeldeformular verwendet:

![Anmeldemodul für Website-Benutzer](../../../en/images/users/user-password-reset/01-user-site-login-module.png)

In jedem Fall führt das Auswählen eines Links zu einem Formular, in dem die mit dem Konto verknüpfte E-Mail-Adresse eingetragen werden muss:

![Formular zum Zurücksetzen des vergessenen Passworts auf der Website](../../../en/images/users/user-password-reset/02-user-forgot-password-reset.png)

Der gesamte Prozess wird vom Benutzer durchgeführt, ohne dass ein Eingreifen eines Administrators erforderlich ist. Dies ist das Formular zur Bestätigung des vergessenen Passworts:

![Formular zur Bestätigung des vergessenen Passworts auf der Website](../../../en/images/users/user-password-reset/03-user-forgot-password-confirm.png)

Und schließlich muss der Benutzer ein neues Passwort eingeben:

![Formular zum Zurücksetzen des vergessenen Passworts auf der Website](../../../en/images/users/user-password-reset/04-user-forgot-password-complete.png)

## Administrator-Zurücksetzung

Wenn es nur eine Administrator-Anmeldung gibt, muss ein Zurücksetzen des Benutzerpassworts von einem Super User oder Administrator durchgeführt werden. Wenn es der einzige Super User ist, der die Anmeldeinformationen nicht kennt, siehe den separaten Beitrag zur Wiederherstellung des Administratorpassworts. Andernfalls:

- Wählen Sie **Benutzer → Verwalten** aus dem Administrator-Menü oder wählen Sie
  *Benutzer* aus dem Home Dashboard-Site-Panel.
- Suchen Sie den Benutzer, dessen Passwort zurückgesetzt werden muss.
- Wählen Sie den verlinkten **Name**, um das Formular *Benutzer: Bearbeiten* zu öffnen.
- Geben Sie ein neues Passwort in die Felder Passwort und Passwort wiederholen ein.
- Setzen Sie das Feld **Passwort zurücksetzen erforderlich** auf *Ja*.
- **Speichern & Schließen**

![Benutzerbearbeitungsformular für Administratoren](../../../en/images/users/user-password-reset/05-users-edit-user-john-doe.png)

Sie müssen dann eine E-Mail an den Benutzer senden, die das neue vorläufige Passwort im Klartext enthält. Nach dem Login kann der Benutzer die Startseite der Website sehen, aber jeder Versuch, zu einer anderen Seite zu navigieren, führt den Benutzer zum neuen Passwortformular.

*Übersetzt von openai.com*

