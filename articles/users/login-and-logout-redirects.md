<!--
{
  "source": "https://docs.joomla.org/J4.x:Login_and_Logout_Redirects",
  "title": "Anmelde- und Abmeldungsweiterleitungen ",
  "description": "", 
  "author": ""
}
-->

## Standardwerte

Für Login und Logout gibt es Optionen, um eine Seite auszuwählen, zu der im Erfolgsfall weitergeleitet werden soll. Es gibt Standardwerte, aber diese sind möglicherweise nicht für Ihre Seite geeignet. Beispielsweise führt das Login-Formular standardmäßig zur Benutzerprofilseite. Das wird lästig, wenn es keinen guten Grund gibt, die Profilseite bei jedem Login zu sehen.

Dieser Beitrag behandelt die Umleitungsoptionen, die nach einem erfolgreichen Login oder Logout verfügbar sind.

## Login-Modul

Das Standardverhalten eines Login-Moduls besteht darin, auf derselben Seite zu bleiben, nachdem man sich ein- oder ausgeloggt hat. Das einzige Problem bei diesem Verhalten ist, dass ein Benutzer, der sich von einer eingeschränkten Seite abmeldet, erneut zur Anmeldung aufgefordert wird. Wenn dies störend ist, besteht eine einfache Lösung darin, die Startseite als Umleitungsseite im Feld "Logout-Umleitungsseite" der Moduleinstellungen auszuwählen.

![Logout-Menüformular, das auf registrierten Zugriff beschränkt ist](../../../en/images/users/login-and-logout-redirects/01-login-redirects-login-form.png)

Tipp: Sie könnten zwei Login-Module verwenden. Eines mit **Gast**-Zugriff mit dem Titel **Anmelden**. Das zweite mit **Registriert**-Zugriff mit dem Titel **Abmelden**.

## Login-Menüpunkt

Der Menüpunkt-Typ "Login" kann sowohl für das Ein- als auch für das Ausloggen verwendet werden. Wenn er für beide Zwecke genutzt wird, sollte er einen Titel wie "Login/Logout" haben. Falls Ihnen das umständlich erscheint, können Sie separate Menüpunkte für Login und Logout verwenden.

Der Menüpunkt-Typ "Login" erlaubt die Wahl des Login-Umleitungstyps: nach Menüpunkt oder nach interner URL. Standardmäßig ist "Menüpunkt" ausgewählt, jedoch nicht konfiguriert, sodass der Login zur Benutzerprofilseite führt. Sie können einen Menüpunkt auswählen oder die URL einer Seite angeben. Beispielsweise könnten Sie eine Systemstatusseite mit einer individuell gestalteten Nachricht des Tages haben.

![Logout-Menüformular, das auf registrierten Zugriff beschränkt ist](../../../en/images/users/login-and-logout-redirects/02-login-redirects-login-menu-options.png)

Das Standardverhalten beim Logout ist die Weiterleitung zur Startseite der Website. Sie könnten auch zu etwas anderem umleiten, wie zum Beispiel einer Verabschiedungsnachricht, die mit einem Menüpunkt oder einer internen URL verknüpft ist.

## Abmelde-Menüpunkt

Der Abmelde-Menüpunkt ist einfach. Standardmäßig bleibt man nach der Abmeldung auf derselben Seite. Wenn das unpraktisch ist, wähle die Startseite der Website.

![Abmelde-Menüformular auf registrierten Zugriff beschränkt](../../../en/images/users/login-and-logout-redirects/03-login-redirects-logout-menu-options.png)

*Übersetzt von openai.com*

