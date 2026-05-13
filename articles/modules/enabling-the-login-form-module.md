<!--
{
  "source": "https://docs.joomla.org/Enabling_the_Login_Form_module",
  "title": "Anmeldeformular   ",
  "description": "", 
  "author": ""
}
-->

## Anmeldemethoden auf der Website

Es gibt zwei Möglichkeiten, um registrierten Benutzern das Einloggen in das Frontend einer Website zu ermöglichen. Es gibt ein **Login-Formular** als Menüpunkt, der in der Benutzergruppe der Menüpunkte zu finden ist. Die Zugriffsberechtigungen hierfür müssen auf *Gast* gesetzt werden. Ein zweiter *Logout*-Menüpunkt wird benötigt, dessen Zugriffsberechtigungen auf *Registriert* gesetzt werden müssen.

Die Alternative ist das **Login-Formular**-Modul. Es wird standardmäßig in der Position *sidebar-right* in einer neuen Joomla-Installation installiert. Dieses Modul kann in eine andere Position verschoben, unpubliziert, in den Papierkorb verschoben und gelöscht werden. Letzteres bezieht sich auf eine Instanz des Moduls und nicht auf den Modulcode. Daher können Sie ein neues *Login-Formular*-Modul erstellen oder eine Kopie anfertigen, möglicherweise für die Verwendung in verschiedenen Vorlagen. Das Login-Formular-Modul ändert seine Anzeige nach dem Einloggen, um einen *Logout*-Button anzuzeigen.

## Das Login-Formular-Modul

Um ein unveröffentlichtes Login-Formular zu veröffentlichen:

* Wählen Sie **Inhalt → Seitenmodule** im Administrator-Menü aus.
* Suchen Sie das **Login-Formular**-Modul.
* Wenn das **Status**-Symbol ein grünes Häkchen in einem Kreis ist, ist es bereits aktiviert. Wenn das Statussymbol ein graues Kreuz ist, ist es derzeit deaktiviert. Wählen Sie das Symbol, um das Modul zu aktivieren.
* Wenn das *Login-Formular*-Modul nicht in der Liste vorhanden ist, stellen Sie die Filteroptionen ein,
  *- Wählen Sie Status - Feld auf *Alle* oder *Papierkorb*, um zu sehen, ob es in den Papierkorb verschoben wurde. Wenn ja, lässt es sich durch Auswahl seines Papierkorbsymbols veröffentlichen.
* Wenn das Login-Formular-Modul fehlt, erstellen Sie ein neues.

Um ein neues Login-Formular oder ein zweites Login-Formular zu erstellen:

* Wählen Sie **Inhalt → Seitenmodule** im Administrator-Menü aus.
* Wählen Sie die **Neu**-Schaltfläche in der Toolbar aus.
* Wählen Sie aus der Modulliste das **Login**-Element aus.
* Füllen Sie das *Module: Login* Datenformular aus.
  - Geben Sie einen eindeutigen Titel ein.
  - Wählen Sie eine Vorlagenposition oder erstellen Sie eine benannte Position für die Verwendung in einem Beitrag.
  - Füllen Sie andere Felder nach Bedarf aus.
* **Speichern & Schließen**
* Testen Sie, ob das Modul korrekt in der Frontend-Ansicht der Seite erscheint.

## Zuweisen des Login-Formularmoduls zu ausgewählten Webseiten

Sie können das Login-Formularmodul auf einer oder mehreren Seiten anzeigen lassen, indem Sie es ausgewählten Menüeinträgen zuweisen. Dies erfolgt über die Felder in der Gruppe Menüzuweisung auf dem Modulbearbeitungsbildschirm:

- Wählen Sie die Registerkarte **Menüzuweisung**.
- Die Liste **Modulzuweisung** hat vier Optionen:
  - **Auf allen Seiten**: Das Login-Formularmodul wird auf allen Seiten angezeigt.
  - **Keine Seiten**: Das Login-Formularmodul wird auf keiner Seite angezeigt.
  - **Nur auf den ausgewählten Seiten**: Eine Liste aller Menüs und Menüeinträge Ihrer Website wird angezeigt. Das Login-Formularmodul wird auf den Seiten angezeigt, die in dieser Liste ausgewählt sind.
  - **Auf allen Seiten außer den ausgewählten:** Das Login-Formular wird auf allen nicht ausgewählten Seiten angezeigt.
- **Menüauswahl**: Zeigt eine Liste aller Menüs und Menüeinträge, von denen ein oder mehrere ausgewählt werden können. Dieses Feld wird nur verwendet, wenn das Feld **Menüs** auf **Menüeintrag/Einträge aus der Liste auswählen** eingestellt ist.

  ![Modulmenüzuweisung](../../../en/images/modules/enabling-the-login-form-module/01-modules-login-menu-assignment.png)

## Anpassen des Anmeldeformular-Moduls

Wenn Sie das Erscheinungsbild des Anmeldemoduls ändern möchten, können Sie entweder Bootstrap-Stile oder Ihre eigenen in Ihrer Template-Datei user.css definierten Stile hinzufügen. Fügen Sie die Stile im **Erweitert**-Tab des Moduls „Anmelden“ im Bearbeitungsformular hinzu.

Wenn Sie die im Anmeldeformular angezeigten Informationen ändern möchten, können Sie ein Template-Override erstellen. Weitere Details finden Sie im Abschnitt über [Template Overrides](jdocmanual?article=user/templates/template-overrides).

*Übersetzt von openai.com*

