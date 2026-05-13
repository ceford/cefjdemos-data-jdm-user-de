<!--
{
  "source": "https://docs.joomla.org/J4.x:Logging_in_to_Joomla",
  "title": "Anmelden bei Joomla ",
  "description": "", 
  "author": ""
}
-->

## Einführung

Eines der großartigen Dinge an Joomla! ist, dass es die Flexibilität bietet, Aufgaben über das Administrator-Dashboard (oft als Backend bezeichnet) auszuführen und, wenn aktiviert, Aufgaben direkt von der Außenseite der Website (Frontend) aus durchzuführen.

Der Zugriff auf das Frontend ist eine einfache und effiziente Möglichkeit, Inhaltsautoren das schnelle Hinzufügen oder Bearbeiten von Beiträgen zu ermöglichen, ohne das Administrator-Dashboard aufrufen zu müssen.

Die Joomla-Anmeldung ist so konfiguriert, dass sie kontrolliert, was Benutzer mit Hilfe der Benutzerkomponente von Joomla und den leistungsstarken Zugriffskontrollstufen (ACL) sehen und tun (oder nicht tun) können. Dies bedeutet, dass eine Joomla-Website Benutzer haben kann, die nur das Backend nutzen, einige, die nur das Frontend nutzen, und andere, die beides nutzen.

Das Folgende behandelt das An- und Abmelden sowohl vom Backend als auch vom Frontend einer Joomla-Website.

**Hinweis:** Ein Joomla-Administrator kann den Frontend-Zugriff deaktiviert haben, sodass alle Aufgaben über das Backend-Administrator-Dashboard durchgeführt werden müssen.

### Administrator-Anmeldung

Navigieren Sie zur Administrator-Anmeldeseite. Dies ist die Webadresse der Website, ergänzt um /administrator, z. B. my-joomla-website.com/administrator, was die Joomla-Administrator-Anmeldeseite aufruft:

![Administrator-Anmeldeformular](../../../en/images/getting-started/logging-in-to-joomla/01-logging-in-to-joomla-administrator-login-form.png)

1.  Geben Sie Ihren **Benutzernamen** ein
2.  Geben Sie Ihr **Passwort** ein

Wählen Sie die Schaltfläche **Anmelden**, um zum Joomla! Home-Dashboard weitergeleitet zu werden.

**Hinweis:**

1.  Joomla bietet eine Option zur Einrichtung und Nutzung der Web-Authentifizierung. 
    Dies liegt nicht im Umfang dieses Tutorials.
2.  Wenn auf einer Website mehrere Sprachen installiert sind, können Sie vor der Anmeldung eine Sprache aus einer Dropdown-Liste auswählen.

### Administrator-Abmeldung

Um sich abzumelden, wählen Sie das **Benutzermenü** und dann **Abmelden**.

![Administrator-Abmeldelink](../../../en/images/getting-started/logging-in-to-joomla/02-logging-in-to-joomla-logout-link.png)

### Seitenanmeldung

Wenn der Frontend-Zugriff aktiviert ist, wurde ein Anmeldeformular auf der Website hinzugefügt. Joomla erlaubt verschiedene Möglichkeiten, dies zu tun. Eine Standardinstallation enthält ein Anmeldeformular in der Seitenleiste der Website, aber Sie könnten finden, dass ein Link in das Menü der Website oder vielleicht in der Fußzeile hinzugefügt wurde. In einigen Fällen könnte ein *Seite erstellen*-Link existieren. Das Design der Website bestimmt, wo Sie das Anmeldeformular aufrufen.

Dieses Beispiel verwendet ein Anmeldeformular, das sich in der rechten Seitenleiste befindet.

![Seitenanmeldemodul](../../../en/images/getting-started/logging-in-to-joomla/03-logging-in-to-joomla-site-login-form.png)

Im **Anmeldeformular**

1.  Geben Sie Ihren **Benutzernamen** ein
2.  Geben Sie Ihr **Passwort** ein

Wählen Sie die Schaltfläche **Anmelden**.

Wenn Sie sich vom Frontend der Website anmelden, bleiben Sie möglicherweise auf derselben Seite, von der Sie sich angemeldet haben, oder Sie werden zu Ihrer Profilseite weitergeleitet. Sie werden feststellen, dass das Anmeldeformular auch eine **Abmelden** Schaltfläche enthält.

### Seitenabmeldung

![Seitenabmeldemodul](../../../en/images/getting-started/logging-in-to-joomla/04-logging-in-to-joomla-site-logout-form.png)

Um sich abzumelden, gehen Sie zum Anmeldeformular und wählen Sie die Schaltfläche **Abmelden**.

## Tipps

- Einige Joomla-Website-Administratoren installieren Erweiterungen, die den Zugriff auf das Backend-Administrator-Dashboard verbergen oder einschränken. Möglicherweise müssen Sie zusätzliche Schritte unternehmen oder eine alternative Anmelde-URL besuchen.
- Wenn Sie Änderungen über den Frontend-Login vornehmen, sparen Sie Zeit, indem Sie sich auf der Seite anmelden, die Sie bearbeiten möchten.

*Übersetzt von openai.com*  

